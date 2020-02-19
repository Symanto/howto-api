# How to use the Symanto API

We will describe some use cases on how to use our API.
If you want access to our services please contact us.

## Preparation

You need:

* client-id
* client-secret
* company-id

To get this, please contact info@symanto.net.

## Authentication

To authenticate against our API, you need a Bearer Token.

To get the Bearer Token you have to send the following request:

Endpoint: https://staging-account.symanto.net/connect/token

Method: Post

Returns: Object including the Bearer Token ( will be needed to authenticate )

In this example, please replace {client-id} and {client-secret}.

```
curl -X POST https://staging-account.symanto.net/connect/token -F client_id={client-id} -F client_secret={client-secret} -F grant_type=client_credentials
```
## Create Survey Insights Project

Endpoint: https://symanto-configuration-api-staging.azurewebsites.net/project/{company-id}

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

```
curl -X POST \
  https://symanto-configuration-api-staging.azurewebsites.net/project/{company-id} \
  -H 'Authorization: Bearer {bearer-token}' \
  -H 'Content-Type: application/json' \
  -d '{
    "name": "name of your project",
    "language": "en"
  }'
```

## Add Data to your Survey Insights Project

Endpoint: https://symanto-configuration-api-staging.azurewebsites.net/project/{company-id}/add-data

Method: Post

Returns: 200 - OK including **transaction-id**

**IMPORTANT: with this transaction-id you can get the status of your transaction**

```
{
  "transactionId": "string"
}
```

In this example, please replace {project-id} and {bearer-token}.
This will create an example project with example data.

```
curl -X POST \
  https://symanto-configuration-api-staging.azurewebsites.net/project/{project-id}/add-data \
  -H 'Authorization: Bearer {bearer-token}' \
  -H 'Content-Type: application/json' \
  -d '{
  "data": [
    {
      "id": "some-id-1",
      "text": "I have a great time in this awesome company.",
      "date": "2020-01-30T14:52:56.780Z",
      "metaData": {
      	"anyfield": "anyvalue", "anyfield1": "anyvalue1"
      }
    },
    {
      "id": "some-id-2",
      "text": "The greatest company I ever worked for!",
      "date": "2020-01-30T14:52:56.780Z",
      "metaData": {
      	"anyfield": "anyvalue", "anyfield1": "anyvalue1"
      }
    }
  ]
}'
```

## Get The Status Of My Transaction

Endpoint: https://symanto-configuration-api-dev.azurewebsites.net/project/status?transactionId={transaction-id}

Method: GET

Returns:

Status can be one of: "Finished", "InProgress", "Unknown"

```
{
    "progress": 0,
    "status": "string"
}
```

In this example, please replace {transaction-id} and {bearer-token}.
This will return you the status of your transaction.

```
curl -X GET \ 
  'https://symanto-configuration-api-dev.azurewebsites.net/project/status?transactionId={transaction-id}' \
  -H 'Authorization: Bearer {bearer-token}'
```

## Get The Processed Data

Please have in mind, that it will take some time until you will be able to see the data.

Endpoint: https://symanto-configuration-api-staging.azurewebsites.net/project?projectId={project-id}&transactionId={transaction-id}

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

In this example, please replace {project-id}, {nr-of-posts-to-return} and {transaction-id}. 
This call will return you the data related to that transaction. 

TransactionId is **optional**, if not provided it will return all data for that project.

```
curl -X GET \
  'https://symanto-configuration-api-staging.azurewebsites.net/project?projectId={project-id}&take={nr-of-posts-to-return}&transactionId={transaction-id}' \
  -H 'Authorization: Bearer {bearer-token}'
```
