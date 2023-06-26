# How to use the Symanto Insight Platform API

We will describe some use cases on how to use our API.
If you want access to our services please contact us.

## Preparation

You need:

* bearer token [How to get the bearer token](https://github.com/Symanto/howto-api/blob/master/authentication.md)
* company-id
* endpoint

For help, please contact info@symanto.net

## Create Project

Endpoint: https://{endpoint}/project/{company-id}

Method: Post

**IMPORTANT: YOU NEED THE RETURNED ID FROM THIS CALL, THAT'S THE {project-id} WHICH YOU NEED FOR THE OTHER CALLS**

Returns:

```
{
  "id": 0,
  "companyId": 0,
  "companyName": "string",
  "usedQuota": 0,
  "configurationId": 0,
  "processedMessageCount": 0,
  "lastProcessTime": "2020-01-30T15:13:01.580Z",
  "createdBy": "string",
  "lastModifiedBy": "string",
  "isArchived": true,
  "isFavourite": true,
  "isLive": true,
  "lastrerunDate": "2020-01-30T15:13:01.580Z",
  "lastDictionaryChange": "2020-01-30T15:13:01.580Z",
  "owner": "string",
  "state": "Active",
  "projectName": "string",
  "workspaceId": "string",
  "showProfileSection": true,
  "description": "string",
  "imagePath": "string",
  "type": "Normal"
}
```

In this example, please replace {company-id} and {bearer-token}.
This will create an example project with example data.

You can choose the industry that your data related to in the body of request in industry field.
if you don't have any idea, automatically we would choose Generic for you.
Industries that we have are:
        Generic,
        Employee ,
        ECommerce ,
        Restaurant ,
        Hotel ,
        CarDealership,
        Retail ,
        Banking ,
        Pharma ,
        ConsumerElectronics 

```
curl -X POST \
  https://{endpoint}/project/{company-id} \
  -H 'Authorization: Bearer {bearer-token}' \
  -H 'Content-Type: application/json' \
  -d '{
    "name": "name of your project",
    "language": "en",
    "industry" : "Restaurant"
  }'
```

## Add Data to your Project

Endpoint: https://{endpoint}/project/{project-id}/add-data

Method: Post

Returns: 200 - OK including **project-id**

In this example, please replace {project-id} and {bearer-token}.
This will create an example project with example data.

```
curl -X POST \
  https://{endpoint}/project/{project-id}/add-data \
  -H 'Authorization: Bearer {bearer-token}' \
  -H 'Content-Type: application/json' \
  -d '{
  "data": [
    {
      "postid": "some-id-1",
      "text": "I have a great time in this awesome company.",
      "date": "2020-01-30T14:52:56.780Z",
      "metaData": {
      	"anyfield": "anyvalue", "anyfield1": "anyvalue1"
      }
    },
    {
      "postid": "some-id-2",
      "text": "The greatest company I ever worked for!",
      "date": "2020-01-30T14:52:56.780Z",
      "metaData": {
      	"anyfield": "anyvalue", "anyfield1": "anyvalue1"
      }
    }
  ]
}'
```

## Get The Status Of My Data

Endpoint: https://{endpoint}/project/status?projectId={project-id}

Method: GET

Returns:

Status can be one of: "Finished", "InProgress", "Unknown"

```
{
    "progress": 0,
    "status": "string"
}
```

In this example, please replace {project-id} and {bearer-token}.
This will return you the status of your transaction.

```
curl -X GET \ 
  'https://{endpoint}/project/status?projectId={project-id}' \
  -H 'Authorization: Bearer {bearer-token}'
```

## Get The Processed Data

Please have in mind, that it will take some time until you will be able to see the data.

Endpoint: https://{endpoint}/project?projectId={project-id}

Method: Get

Returns: 

```
{
  "data": [
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
  ],
  "total": 0
}
```

In this example, please replace {project-id}, and {nr-of-posts-to-return}. 
This call will return you the data related to that project. 



```
curl -X GET \
  'https://{endpoint}/project?projectId={project-id}&take={nr-of-posts-to-return}&skip={nr-of-posts-to-skip}' \
  -H 'Authorization: Bearer {bearer-token}'
```
