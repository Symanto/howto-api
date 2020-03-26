# How to authenticate to use the symanto API

## Preparation

You need:

* client-id
* client-secret
* endpoint

To get this, please contact info@symanto.net.

## Authentication

To authenticate against our API, you need a Bearer Token.

To get the Bearer Token you have to send the following request:

Endpoint: https://{endpoint}/connect/token

Method: Post

Returns: Object including the Bearer Token ( will be needed to authenticate )

In this example, please replace {client-id} and {client-secret}.

```
curl -X POST https://{endpoint}/connect/token -F client_id={client-id} -F client_secret={client-secret} -F grant_type=client_credentials
```
