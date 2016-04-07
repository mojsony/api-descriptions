---
visibility: internal
---

Bill Presentment API 
======================
Bill Presentment API presents info about bill issuers, subscriptions and bills. It also provides way to subscribe and unsubscribe for bills at bill issuers, and to snooze bills.  

  
Key Resources
-------------
Bill Presentment has three top level collection resources: bills, issuers and subscriptions.

Resource        | Description
----------------|-----------
*bills*         | Provides way to view info about bills and to snooze particular bills. It is usefull because it is possible to filter list of own bills by search criteria: name, address and/or status.
*issuers*       | Serves for gettin info about bills issuers.
*subscriptions* | Allows to view info about subscriptions, subscribe for new and unsubscribe from old ones at bills issuers. It is usefull when it is needed to pay bills from the account or through standing orders.
 
Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Bill Presentment API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user.
You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Bill Presentment API with your access token against the URL root below, combined with one of the root resources.  
Bill Presentment API URLs are relative to the following root unless otherwise noted.


API | URL Root
--------|---------
Bill Presentment | `https://api.asse.co/bill-presentment/v2`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /bills/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Get bill issuers list

Assume that You have some bills that You pay going to a bank. Now You want to pay some of them using e-banking. You search bill issuer from list that is obtained by this call.
```
GET /issuers/
```
You will get back `200 OK` status code and json representation with a bill issuers list.

```json
{
  "total-count": 53,
  "page-size": 10,
  "page-number": 1,
  "total-pages": 6,
  "items": [
    {
      "issuer-id": "36",
      "group-id": "6",
      "issuer": 
      {
        "name": "Electro Suplies Company",
        "address": "Nemanjina 33",
        "city": "Beograd"
      }
     },
    {
      "issuer-id": "30",
      "group-id": "6",
      "issuer": 
      {
        "name": "TELENOR",
        "address": "Omladinskih brigada 90",
        "city": "Novi Beograd"
      }  
        ...
             ]
}
```

###4. Get bill issuer details.

Assume that You got list of bill issuers, and now You want to view details for one particular bill issuer. This is usefull when You find bill issuer that You want to subscribe for bills and want to see info about him.

```
GET /issuers/{issuer-id}
```

You will get back `200 OK` status code and json representation of bill issuer details.

```json
{
  "issuer-id": "36",
  "group-id": "6",
  "issuer": 
            {
                "name": "Electro Supply company",
                "address": "Nemanjina 33",
                "city": "Beograd"
                ...
            }
}
  
```

###5. Get bill list

If You already subscribed for bills at some issuer, You can view list of bills that are issued to You when they received for payment. It is usefull when You want to view all Your bills.

```
GET /bills

```
You will get back `200 OK` status code and json representation of bill list. Here exists only one bill in the example.

```json
{
  "bills-payment-amount-sum": 1202,
  "bills-fee-sum": 0,
  "total-count": 1,
  "page-size": 10,
  "page-number": 1,
  "total-pages": 1,
  "items": [
    {
      "bill-id": "9990015521100120150424",
      "nickname": "MyService",
      "bill-issuer": {
        "name": "TELENOR",
        "address": "Omladinskih brigada 90",
        "city": "Novi Beograd",
        ...
                    }
     },
     ...
           ]
}
```

If You want to see info about particular bill You can call bill details. It is useful to view all details about one bill.
###6. Get Bill details

```
GET /bills/{bill-id}
```

You will get back `200 OK` status code and json representation with a bill details.

```json
{
  "bill-id": "9990015521100120150424",
  "nickname": "MyService",
  "bill-issuer": {
    "name": "TELENOR",
    "address": "Omladinskih brigada 90",
    "city": "Novi Beograd",
    "country-code": "",
    ...
                  }
   ...
}
```

**Congratulations!** You have completed getting started tutorial on most common steps when working with Bill Presentment API. 
To learn more look at the reference documentation for [available operations](swagger-ui).
