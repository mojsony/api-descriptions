<span class="icon"></span> Entitlements API Guide 
======================
Risk based authorization of customer initiated actions solved by elevated level of authentication and/or involvement of multiple authorizing parties. Action authorizations are either explicitly requested by channel application or initiated by backend or multichannel modules during transaction and workflow processing.
   
Key Resources
-------------
Action Authorization has three top level collection resources: 

Resource | Description
----------- |-----------
*customers* | Serves for getting mandates for customers.
*check* | Serves for checking authorization.
*initiate* | Serves for initiating new authorisation.

Getting started tutorial
---------------
To get started follow these steps:

###1. Authenticate your app
Entitlements API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Content Management API with your access token against the URL root below, combined with one of the root resources.  Content Management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Action Authoirization | `https://api.asse.co/...`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /dms/documents/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Get mandates list for customer

```
GET authorization/customers/{customer-number}/mandates/

```
You will get back `200 OK` status code and json representation with a list of mandates.

```json

{
  "mandates": [
    {
      "arrangements": [
        {
          "arrangement-number": "0000000050379",
          "owner": "1402683",
          "authentication-methods": null,
          "channels": [
            "atm",
            "email",
            "fax",
            "inbox",
            "mobile",
            "pos",
            "ProductCatalog",
            "push",
            "sms",
            "TNshop",
            "web"
          ],
          "kind": "mandate-for-owner",
          "limit": null
        },
        {
          "arrangement-number": "OD-0000000050379",
          "owner": "1402683",
          "authentication-methods": null,
          "channels": [
            "atm",
            "email",
            "fax",
            "inbox",
            "mobile",
            "pos",
            "ProductCatalog",
            "push",
            "sms",
            "TNshop",
            "web"
          ],
          "kind": "mandate-for-owner",
          "limit": null
        }
      ],
      "authentication-methods": null,
      "id": 0,
      "kind": null,
      "limit": null,
      "name": null,
      "registration-number": "MND-RT-301502",
      "registration-status": null,
      "service-code": "agent-defined"
    },
    {
      "arrangements": [
        {
          "arrangement-number": "0000000050379",
          "owner": "1402683",
          "authentication-methods": null,
          "channels": [
            "atm",
            "mobile",
            "web"
          ],
          "kind": "mandate-for-owner",
          "limit": null
        },
        {
          "arrangement-number": "OD-0000000050379",
          "owner": "1402683",
          "authentication-methods": null,
          "channels": [
            "atm",
            "mobile",
            "web"
          ],
          "kind": "mandate-for-owner",
          "limit": null
        }
      ],
      "authentication-methods": null,
      "id": 0,
      "kind": null,
      "limit": null,
      "name": null,
      "registration-number": "MND-RT-301502",
      "registration-status": null,
      "service-code": "bill-list"
    },

```

###4. Check authorization

```
GET authorization/check/

```
You will get back `200 OK` status code and json representation with a list available authentication types.

```json
To Do 
```

###4. Initiate new authorization

```
GET authorization/intiate/

```
You will get back `200 OK` status code and json representation with authorization number.

```json
To Do 
```

**Congratulations!** You have completed getting started tutorial on most common steps when working with Entitlements API. To learn more look at the reference documentation for [available operations](swagger-ui).