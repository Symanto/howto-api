
# How to use the symanto Pipeline API

# Preparation

You need:

* bearer-token (see [How to get the bearer token](https://github.com/Symanto/howto-api/blob/master/authentication.md))
* project-id
* endpoint

For help please contact info@symanto.net

# Process your Data

|Endpoint|Method|Body|
|--------|------|----|
|https://{endpoint}/pipeline|POST|``{text: string, projectid: int, language: string}``|

Returns:

```
{
    "id": null,
    "cleanText": "",
    "processedAt": "",
    "gender": null,
    "profiles": [],
    "emotions": [],
    "classification": null,
    "features": [],
    "sentiments": [],
    "featureSentiments": [],
    "errorText": null,
    "hashTags": null,
    "currentStatus": "",
    "targetStatus": "",
    "appsStates": [],
    "sentimentDiscrete": null,
    "profileCode": null,
    "isSpam": null,
    "isSpamProbability": null,
    "sentiment": null,
    "sentimentProbability": null,
    "text": "",
    "textHash": null,
    "metaData": [],
    "language": "",
    "postDate": null,
    "weight": null
}
```

## Example call

```
curl --location --request POST 'https://{endpoint}/pipeline' \
--header 'Authorization: Bearer {bearer-token}' \
--header 'Content-Type: application/json' \
--data-raw '{text: "esta es una prueba abatida", "language": "es" projectid: {project-id}}'
```
