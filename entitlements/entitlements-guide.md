---
visibility: internal
---

<span class="icon"></span> Entitlements API Guide
======================

"Entitlements API lets you check and enforce access entitlements with customer mandates and limits. Mandates are given per arrangement and can specify allowed services, applicable channels and any limits set for each mandate holder. Mandate model is aligned with ISO 20022. Setting preferred limits is possible in two modes - *unconstrained* and *constrained*. Unconstrained mode lets you set any limit value within acceptable range while constrained mode makes you pick from a predefined list of limits and limit groups."

> ##THIS API GUIDE IS UNDER CONSTRUCTION. COME BACK SOON.

Key Resources
-------------

Entitlements API four top level resources: `mandates`, `limits` with two specialized sub resources - `card-access`, `online-access` for card and online access limits

Resource | Description
----------- |-----------
*mandates* | Entitlements that allow mandate holders to access to services within arrangements
*limits* | Predefined limits
*limits/card-access* | Effective limits for payment cards 
*limits/online-access* | Effective online access limits for customers

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
Action Authoirization | `https://bankapi.net/...`

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
]
}
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
