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

Endpoint: https://symanto-configuration-api-staging.azurewebsites.net/surveysolutions/{company-id}/survey-solutions

Method: Post

Returns: Object including Project Id ( will be needed to get the results later )

In this example, please replace {company-id} and {bearer-token}.
This will create an example project with example data.

```
curl -X POST \
  https://symanto-configuration-api-staging.azurewebsites.net/surveysolutions/{company-id}/survey-solutions \
  -H 'Authorization: Bearer {bearer-token}' \
  -H 'Content-Type: application/json' \
  -d '{
    "choosenColumnNames": [
      "Please describe your experience!"
    ],
    "metaDataColumnNames": [
      "Response ID",
      "Age"
    ],
    "weightColumnName": "Weight",
    "projectName": "the name of your project, again",
    "language": "en",
    "fileUrl": "https://github.com/Symanto/howto-api/raw/master/sample-files/sample-restaurant-reviews.xlsx",
    "showProfileSection": true,
    "description": "a description for your project",
    "type": "SurveySolution"
  }'
```

## Get The Processed Data

Please have in mind, that it will take some time until you will be able to see the data.

Endpoint: https://symanto-configuration-api-staging.azurewebsites.net/post

Method: Get

Returns a Json Array of Posts ( the processed data )

In this example, please replace {project-id} and {nr-of-posts-to-return}. 

```
curl -X GET \
  'https://symanto-configuration-api-staging.azurewebsites.net/post?model.analysisProjectId={project-id}&model.take={nr-of-posts-to-return}' \
  -H 'Authorization: Bearer {bearer-token}'
```
