Sales Arrangement API v2
=========================
Sales Arrangement API gives you access to all durable arrangements customer has with financial institution such as current accounts, loans, deposits, card access arrangements, electronic access arrangements, etc. It also provides detailed arrangement information such as financial terms and conditions, party roles, installment plan, etc. It maps to BIAN Sales Product Agreement service domain.

Key Resources
-------------
Top-level resource is arrangement (arrangements) which has specializations by kind. Main subresources are installment-plan and arrangement-conditions. 

Resource | Description
----------- |-----------
*arrangement*  | Represents a deal/agreement between bank as product/service provider and its customer as a consumer of the same product. Non-product agreements are not covered by this resource. Specializations of arrangement are: current-account, demand-deposit, term-deposit, term-loan, overdraft-facility, credit-facility, credit-card-facility, card-access-arrangement, electronic-acess-arrangement, other-product-arrangement
*installment-plan*      | A list of scheduled payments for entire arrangement lifecycle.
*arrangement-conditions*    | Arrangement terms and conditions listed in three separate lists: fees, interest-rates and other. 

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Sales Arrangement API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Sales Arrangement API with your access token against the URL root below, combined with one of the root resources.  Sales Arrangement API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Sales Arrangement | `https://api.asse.co/sales-arrangement`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /arrangements/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Retrieve the list of arrangements for a customer
Let's see the list of arrangements - products used by a customer. Note that the list returns only arrangements for which the party from calling context plays customer role. If you want to see arrangement in which calling party plays other roles, this should be specified by party-role-param. 
You can list arrangements at following endpoint:
```
GET /arrangements
```
You will get back `200 OK` status code and json representation with a list of arrangements. 

```json
[
  {
    "arrangement-number": "0000100002378",
    "kind": "current-account",
    "product-code": "RT-CA-STD-001",
    "status": "effective"
  },
  {
    "arrangement-number": "0042201082794",
    "kind": "term-loan",
    "product-code": "RT-LN-CAR-002",
    "status": "effective"
  }
]
```


###4. See arrangement details
Arrangement details are accessible from arrangement list and also can be accessed from account list or from any context where we can found arrangement number. We will use include-param to include party-role and arrangement-account-info subresources (under parties and accounts properties). 
We can access arrangement details at following endpoint:

```
GET /arrangements/0042201082794?include=parties, accounts
```

You will get back `200 OK` status code and json representation with arrangement details. 

```json
{
  "arrangement-number": "0042201082794",
  "kind": "term-loan",
  "product-code": "RT-LN-CAR-002",
  "status": "effective",
  "contract-date": "2013-10-21T00:00:00",
  "parties": [
    {
      "party-number": "IGNE002",
      "party-name": "Milivoje Klafovic",
      "role-kind": "customer",
      "role-status": "current"
    },
    {
      "party-number": "MRQW031",
      "party-name": "Leopold Zec",
      "role-kind": "guarantor",
      "role-id": "G1",
      "role-status": "current"
    },
    {
      "party-number": "MRQW031",
      "party-name": "Teodor Brkic",
      "role-kind": "guarantor",
      "role-id": "G2",
      "role-status": "current"
    }
  ],
  "accounts": [
    {
      "account-number": "0042201082794",
      "role-kind": "primary-account"
    },
    {
      "account-number": "0000100002378",
      "role-kind": "settlement-account"
    }
  ],
  "term":
    {
      "period": 4,
      "unit-of-time": "Y"
    },
  "grace": 
    {
      "period": 3,
      "unit-of-time": "M"
    },
  "maturity-date": "2017-10-21T00:00:00",
  "initial-amount": 8000.00,
  "primary-currency": "EUR",
  "eapr": 9.79,
  "napr": 9.0
}
```

###5. View arrangement installment plan
Installment plan is specific arrangement subresource which exists only for some kinds of arrangement - usually only for term loans and deposits. . 
We can reach it at following endpoint:

```
GET /arrangements/0042201082794/installment-plan
```

You will get back `200 OK` status code and json representation with installment plan details. 

```json
{
}
```

###5. List folder contents
Now lets list the folder contents and verify that it contains on image.
```
GET /dms/folders/ee48b17534c9
```

You will get back `200 OK` status code and json representation with a list of repository names. To access content in repository you will use `folders` and `documents` resources prefixed with repository name.
```json
{
  "items": [
    {
      "kind": "document",
      "name": "headshot.png",
      "path": "customers/jabon0007",  
      "id": "mj20b12534r4",
      "changed-on": "2015-10-20T23:22:10.000Z",
      "created-on": "2015-11-23T07:08:30.000Z",
      "created-by": "jabon0007"
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
###6. Download the document
Finally lets use that url we got back in step 4. and download the document and verify that it is indeed the same image.
Just paste this in browser address bar:
```
GET http://api.asse.co/content/dms/documents/mj20b12534r4
```
You will get back `200 OK` and binary content stream with appropriate Content Type and Content Disposition headers. Download will start immediately.
```
Content-Type: image/png
Content-Disposition: attachment; filename="headshot.png"
``` 

**Congratulations!** You have completed getting started tutorial on most common steps when working with Content Management API. To learn more look at the reference documentation for [available operations](swagger-ui).
