# Avinor API

Access to Avinor API is controlled through Azure API Management. To get access register a new user and subscribe to those api's of interest. Some API's are not publically accessible and requires approval by Avinor.

PS. API url will change at one point to api.avinor.no.

## Sign up

To create a user to access API's follow these instructions:

1. Go to <https://avinorapi.portal.azure-api.net/>.
2. Sign up for new user, fill in Company name and Contact Person.
3. Go to Products and subscribe to a new product package.

![products](/images/products.png "Products")

## Products

### Parking whitelist

*Requires approval*

Control whitelisting of cars for parking on airports. Restricted access to parking companies.

## Programatically access API

To access API programatically a new token need to be created to call API. API's are protected with OpenID Connect and requires jwt Bearer token.

To create a token with curl run following command:

```bash
curl https://login.microsoftonline.com/avinorapi.onmicrosoft.com/oauth2/v2.0/token?p=b2c_1_resource_owner_default -X POST -d 'grant_type=password&client_id=900f6802-0f1b-4e2f-9614-8ebf97e98429&username=<username>&password=******&scope=openid 900f6802-0f1b-4e2f-9614-8ebf97e98429 offline_access' -H 'Content-Type:application/x-www-form-urlencoded' -i
```

The result will contain an `access_token` that can be used for authentication agains API's.

```bash
curl -H 'Authentication: Bearer <access_token>' https://avinorapi.azure-api.net/...
```
