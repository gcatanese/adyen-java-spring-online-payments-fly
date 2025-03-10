# Adyen Node Sample on Fly.io
This is a fork of adyen-java-spring-online-payments repository to demo how to deploy the Adyen Sample application on Fly.io using Docker.

Read mode about [Docker deployment on Fly.io](https://medium.com/geekculture/deploy-docker-images-on-fly-io-free-tier-afbfb1d390b1).

## Pre-requisites
You must satisfy the following pre-requisites:

* Have an Fly.io account (free tier is enough)
* Have Fly CLI (`flyctl`) installed

## Adyen keys and configuration

Login in the [Adyen Customer Area](https://docs.adyen.com/plugins/magento-2/set-up-adyen-customer-area) to configure the Developer Credentials necessary to access the Adyen platform

- API key
- Client key
- Merchant Account
- HMAC signature for validating the Webhook notifications

Check [Drop-on Integration Guide](https://docs.adyen.com/online-payments/web-drop-in) to understand the workflow and configuration.


## Steps

Launch the application with `flyctl launch`

```
  % flyctl launch
```

When prompted provided the required information:
* name of the application
* region (ie EU)
* PostgreSQL DB? No (not necessary)
* Deploy now? No

Set the secrets with the values obtained in the Customer Area (see above)

```
  % flyctl secrets set ADYEN_API_KEY="xxxx"
  % flyctl secrets set ADYEN_MERCHANT_ACCOUNT="xxxx"
  % flyctl secrets set ADYEN_CLIENT_KEY="xxxx"
  % flyctl secrets set ADYEN_HMAC_KEY="xxxx"
```

## Allowed origin

In the Customer Area remember to include `https://*.fly.dev` in the list of Allowed Origins
for the API credential setup for this application.

## Deploy 
You are now ready to deploy 
```
  % flyctl deploy
```


