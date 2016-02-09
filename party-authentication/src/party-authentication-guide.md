Party Authentication API 
======================
Party Authentication API provides way to authenticate as user of application.
   
Key Resources
-------------
Party authentication has one common top level collection resource, and other resources that represent particular methods.

Resource | Description
----------- |-----------
*users*  | Contains methods that are used to view and modify various details associated with user as password, hint picture and similar.


Getting started tutorial
---------------
To get started follow these steps:
###1. Get bearer token
You get an access token that authenticates your app with a particular set of permissions for the user. You provide an access token through an HTTP header:
```
POST /authentication/token
```
You will get back `200 OK` status code and json representation with a customer Id and token value.

```json

{
  "customer-id": "1400113",
  "token-value": "qhh-yaI27SlXkjx_pMPnwrAnLT0g8rnQefgQuuv0WYXVU6dfhkNRvG69PUcTLl-Pj33lOMmUGpN1iJ7R0LAYGyOTUIzi6eh7d1m50jSHtUWeCh4WAPwzDvKbK4-9Ora8gH9F4KjrjSJqInpepe7Mo52Syik0h2tmpFNo-PuiiSAmAH1bES7AS6y8GXgi_v1r0eT6R1RIbKfP-mSP0bjdhFXr4G5loCVj-gnNe5Ps7W-KS-znZXfRwz8qQ4lNExg6_eGDdnHAZnhyZCtudr505b9J1mbF-fPWMuO-Ssmrx8HY75EmVVLNusVPaZdF7zHO3mnPw_vKjigT_Y6fYIOtJza5ozM5JdiaH0C9FAnYhjoXNM3KmmAunos_tZ3CQzKOtzkaaeQLYxdTefLc2LtwaUh5b4NOCXo0Gc045evn2DsX0uPOJGZJWWjWby8nGayiOvBIMSu417lwg8f3aY0Lou_8bwE2n8iSA5EocaSbepwxpcIM"
}

```

###2. Generate e-mail confirmation token
Now that you've authenticated your app, You can generate e-mail confirmation token.

```

POST /authentication/users/email/validation-tokens

```
You will get back `200 OK` status code and json representation with customer Id and token value.

```json

{
  "customer-id": "1400113",
  "token-value": "GKIOnGDUcuhbPN41ZRb/ZK0oER4CdPpV6XtrcQXjNgGNTsjaqPtTnYQoMhtzvMhGXtGfmHg0VqBH4dFUlmoO+34ggag="
}

```


###3. Get user info

It is possible to view details about You as authenticated user when customer Id is provided as query parameter.
```
GET /authentication/users/info
```
You will get back `200 OK` status code and json representation with a details about user.

```json

{
  "last-login-on": "2015-12-16T12:50:21.46",
  "name": "Andrej Vrbassski",
  "customer-id": "1400113",
  "email": "valentin.rep@gmail.com",
  "msisdn": "38160222333",
  "external-login-providers": null,
  "status": "active"
}

```


###4. Get authentication methods

It is possible to view authentication methods For You as authenticated user.

```
GET /authentication/users/authentication-methods
```
You will get back `200 OK` status code and json representation with Your authentication methods.

```json
{
  "customer-id": "1400113",
  "authentication-methods": [
    {
      "method-identifier": "sms-otp",
      "method-description": "One time password",
      "two-factor": true
    }
  ]
}

```

###5. Card operations allowed
For particular account id user can check if card operations are allowed.

```
GET /authentication/users/card-operations-allowed
```
You will get back `200 OK` status code and value true if card operations are allowed.

```json

true

```

###6. Create user

You can create user with details about him as customer Id, e-mail and so on.

```
POST /authentication/users/

```
You will get back `201 created` status code and json representation with Id and created record status Created.

```json
{
  "id": "10101010",
  "created-record-status": "created"
}

```


**Congratulations!** You have completed getting started tutorial on most common steps when working with Party Authentication API. 
To learn more look at the reference documentation for [available operations](swagger-ui).
