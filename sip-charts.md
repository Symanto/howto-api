# How to use the sip charting endpoints

In this document, we will describe how to use the charting endpoints.

## Preparation

You need:

* bearer token [How to get the bearer token](https://github.com/Symanto/howto-api/blob/master/authentication.md)
* project-id
* endpoint

# Sentiment By Topic Endpoint

Endpoint: https://{endpoint}/charting/{project-id}/topicFeatures

Method: **POST**

Optional Query Parameters:
 
* **metaKey:** breakdown option you want to compare, e.g. brand, product, etc.
* **metaValues:** select at least two values to define the subsets of data you want to compare against. You can send [multiple values](https://stackoverflow.com/questions/24059773/correct-way-to-pass-multiple-values-for-same-parameter-name-in-get-request) 

Returns:

```
[
  {
    "key": "string",
    "value": [
      {
        "name": "string",
        "category": "string",
        "positiveCount": 0,
        "negativeCount": 0,
        "neutralCount": 0,
        "totalCount": 0,
        "positivePercentage": 0,
        "negativePercentage": 0,
        "neutralPercentage": 0,
        "netSentimentScore": 0
      }
    ]
  }
]
```

Meaning of attributes:

* **category:** the category of the the topic found
* **name:** the topic name
* **positiveCount:** the number of positive occurances of this topic
* **negativeCount:** the number of negative occurances of this topic
* **neutralCount:** the number of neutral occurances of this topic
* **totalCount:** the number of texts containing this topic
* **positivePercentage:** the positive percentage of this topic
* **negativePercentage:** the negative percentage of this topic
* **neutralPercentage:** the neutral percentage of this topic
* **netSentimentScore:** the net sentiment score of this topic

[Volume Comparison](https://help.symanto.com/knowledge/comparison)