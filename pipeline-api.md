
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
      "text": "string",
      "profileCode": "string",
      "textHash": "string",
      "cleanText": "string",
      "errorText": "string",
      "companyId": "string",
      "projectId": "string",
      "transactionId": "string",
      "processedAt": "2020-01-30T15:13:01.589Z",
      "postDate": "2020-01-30T15:13:01.589Z",
      "language": "string",
      "currentStatus": "None",
      "targetStatus": "None",
      "gender": {
        "label": "string",
        "confidence": 0
      },
      "profiles": [
        {
          "label": "string",
          "confidence": 0
        }
      ],
      "classification": {
        "label": "string",
        "confidence": 0
      },
      "metaData": [
        {
          "type": "string",
          "value": "string"
        }
      ],
      "features": [
        {
          "start": 0,
          "end": 0,
          "feature": "string",
          "text": "string",
          "source": "Normal",
          "confidence": 0,
          "featureTerm": "string",
          "subCategory": "string",
          "category": "string",
          "parentCategory": "string",
          "grandParentCategory": "string",
          "emotionConfidence": 0,
          "emotionLabel": "string"
        }
      ],
      "sentiments": [
        {
          "start": 0,
          "end": 0,
          "text": "string",
          "positive": true,
          "scale": 0,
          "category": "string",
          "parentCategory": "string",
          "negationTerm": "string"
        }
      ],
      "featureSentiments": [
        {
          "featureStart": 0,
          "featureEnd": 0,
          "feature": "string",
          "sentence": "string",
          "sentimentText": "string",
          "featureText": "string",
          "featureTerm": "string",
          "featureSubCategory": "string",
          "featureCategory": "string",
          "featureParentCategory": "string",
          "featureGrandParentCategory": "string",
          "sentimentStart": 0,
          "sentimentEnd": 0,
          "positive": true,
          "sentimentScale": 0,
          "sentimentCategory": "string",
          "sentimentParentCategory": "string",
          "sentimentNegationTerm": "string"
        }
      ],
      "fullFeatureSentiments": [
        {
          "featureStart": 0,
          "featureEnd": 0,
          "feature": "string",
          "sentence": "string",
          "sentimentText": "string",
          "featureText": "string",
          "featureTerm": "string",
          "featureSubCategory": "string",
          "featureCategory": "string",
          "featureParentCategory": "string",
          "featureGrandParentCategory": "string",
          "sentimentStart": 0,
          "sentimentEnd": 0,
          "positive": true,
          "sentimentScale": 0,
          "sentimentCategory": "string",
          "sentimentParentCategory": "string",
          "sentimentNegationTerm": "string"
        }
      ],
      "emotions": [
        {
          "label": "string",
          "confidence": 0
        }
      ],
      "hashtags": [
        "string"
      ],
      "appsStates": [
        "string"
      ],
      "sentimentDiscrete": 0,
      "weight": 0,
      "isSpam": true,
      "id": "string"
    }
```

## Example call

```
curl --location --request POST 'https://{endpoint}/pipeline' \
--header 'Authorization: Bearer {bearer-token}' \
--header 'Content-Type: application/json' \
--data-raw '{text: "esta es una prueba abatida", "language": "es" projectid: {project-id}}'
```
