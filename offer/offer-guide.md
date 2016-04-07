---
visibility: internal
---

![Folders](http://cdn.flaticon.com/png/64/98/98193.png)
Offer Management API v2
=========================
Offer Management API v2 lets you initiate, track and execute offers for loans, limits and accounts. It provides simulation of conditions for potential products and services.

Key Resources
-------------
Offer Management has four top level collection resources: drafts, applications, calculation and classification.  

Resource | Description
----------- |-----------
*drafts*  |  Workitem used to prepare a version of application before the final version of application.
*applications*      | Workitem used to capture details of client request for a product or service. Serves as a ticket for tracking progression of the workflow through phases and states, from draft to closed.
*calculations*    | Represents the result of calculating; determining terms, fees and taxes by mathematical or logical methods, like calculate service fee.
*classifications* | Represents classification schemes and values. Systems of organizing data or information, usually involving categories of items with similar characteristics.   


Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Offer API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Offer API with your access token against the URL root below, combined with one of the root resources.  Offer API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Offer      | `https://api.asse.co/offer`

> **Note**: Throughout this documentation, only partial syntax such as:
`GET /applications/{application-number}` is used for the sake of brevity.
Prefix the path with the correct root URL in order to obtain the full resource path or URL.


###3. Create current account opening
Let's assume that you want to create current account opening for fully registered customer.
To create current account request you need to post `current account opening` metadata representation as json to following endpoint:

```
POST /applications/deposit-openings
```

```json
{
  "deposit-opening-kind":"current-account",
  "customer-number": "1400054",
  "product-code": "TMCY_0001",
  "requested-account-number": "33333333333333",
  "campaign-id": "",
  "signing-option": "branch"
}
```

You will get back `201 Created` status code and workitem number of created current account opening.

```json
{
  "id": "WI0000492475",
  "CreatedRecordStatus": "Created"
}
```


###4. Retreive created request details

You can get created current account opening details at following endpoint:

```
GET /applications/WI0000492475
```

You will get back `200 OK` status code and json representation of created current account opening.

```json
[
  {
    "application-number": "WI0000492475",
    "kind":"current-account-opening",
    "status":"active",
    "customer-number": "1400054",
    "customer-name": "Milutin Cvetkovic",
    "product-code": "TMCY_0001",
    "product-name": "Multivalutni rn - PAKET 1",
    "created": "2015-12-10T10:16:56.8807659+01:00",
    "request-date": "2015-12-10T10:16:56.8807659+01:00",
    "expiration-date": "2015-22-10T10:16:56.8807659+01:00",
    "status-changed": "2015-12-10T10:16:56.8807659+01:00",
    "last-modified ": "2015-12-10T10:16:56.8807659+01:00",
    "created-by-name": "Biljana Davidovic",
    "comments": "Novi racun za klijenta",
    "workitem-phase": "",
    "primary-currency": "RSD",
    "request-date": "2015-12-10T10:16:56.8807659+01:00",
    "requested-account-number": "33333333333333"
  }
]
```
###5. List customer requests
Now lets list the requests for customer and verify that it contains created current account opening.

```
GET /applications?customer-number=1400054
```

You will get back  `200 OK` status code and json representation with a list of product account openings.

```json
{
  "items": [
    {
      "application-number": "WI0000492475",
      "kind":"current-account-opening",
      "status":"active",
      "customer-number": "1400054",
      "customer-name": "Milutin Cvetkovic",
      "product-code": "TMCY_0001",
      "product-name": "Multivalutni rn - PAKET 1",
      "created": "2015-12-10T10:16:56.8807659+01:00",
      "request-date": "2015-12-10T10:16:56.8807659+01:00",
      "expiration-date": "2015-22-10T10:16:56.8807659+01:00",
      "status-changed": "2015-12-10T10:16:56.8807659+01:00",
      "last-modified ": "2015-12-10T10:16:56.8807659+01:00",
      "created-by-name": "Biljana Davidovic",
      "comments": "Novi racun za klijenta",
      "workitem-phase": "",
      "primary-currency": "RSD",
      "request-date": "2015-12-10T10:16:56.8807659+01:00",
      "requested-account-number": "33333333333333"
  }
    }
  ],
  "total-count": 1,
  "page-size": 10,
  "page": 1,
  "total-pages": 1,
  "sort-order": "asc",
  "sort-by": "created-on"  
}
```



**Congratulations!** You have completed getting started tutorial on most common steps when working with Offer Management API. To learn more look at the reference documentation for [available operations](swagger-ui).
