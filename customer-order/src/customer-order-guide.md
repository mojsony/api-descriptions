![Folders](http://cdn.flaticon.com/png/64/98/98193.png)
Customer Order API v2
=========================
Customer order API enables you to initiate, track, query and execute “Self-Care” orders. You can issue orders for opening new accounts, set up the terms and conditions of the existing and new accounts, grant and revoke mandates to self or others, manage communication preferences like notifications, alerts and contacts and manage channels or cards. All orders are treated like work items and they go through a series of steps until executed. The time to complete these steps depends on the type of the customer order.
   
Key Resources
-------------
Customer Order API has six top level collection resources:

Resource | Description
----------- |-----------
*additional card issuences*  | Workitem used to capture details of client request for a additional card. WorkItem status changes throught phases and states, from active to complete/rejected.
*card activations*    | Includes changing card status to active throught activation card request and previewing details of that request. 
*card blockades*    | Includes changing card status to suspended throught blockade card request and previewing details of that request.
*card deblockades*    | Includes changing card status from suspended to active throught deblockade card request and previewing details of that request. 
*card terminations*    | Includes changing card status to terminated throught termination card request and previewing details of that request. 
*card replacements*    | Initiates issuing of new card depending on replacement reason throught replacement card request and previewing details of that request.
*classifications*    | Identifies a structure used to organize and manage business information by defining categories that satisfy certain criteria or form a group subject to a human decision. 

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Customer Order API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Customer Order API with your access token against the URL root below, combined with one of the root resources. Customer Order API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Customer Order | `https://api.asse.co/customer-order`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /additional-card-issuances/{order-number}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Create request for additional card
Let's assume that you have already created credit limit account and for that account you want to create additional card request. You need to post `additional-card-issuances` metadata representation as json to following endpoint:
```
POST /additional-card-issuances
```
```json
{
  "authorized-customer-number": "1400054",
  "arrangement-number": "0064200001930"
}
```
You will get back `202 Accepted` status code and workitem number of created request. 

```json
{
  "id": "WI0000492475",
  "CreatedRecordStatus": "active"
}
```

###4. Retreive details for created request
Now lets preview details for created request from step 3:
```
GET /additional-card-issuances/WI0000492475
```

You will get back `200 OK` status code and json representation for fetched request. 
```
```json
{
      "id": "WI0000499335"
      "authorized-customer-number": "MIGR00002"
      "authorized-customer-name": "Mileva Grujic"
      "owner-customer-number": "BRVU00002"
      "owner-customer-name": "Branislav Vukovic"
      "arrangement-number": "0064200001930"
      "product-code": "MasterCard"
      "description": 
      "status": "proposed"
      "customer-friendly-status": "active"
      "creation-date": "2015-10-20T23:22:10"
}
```

###5. Cancel request for additional card
Let's cancel previewed request from step 4:
```
PUT /additional-card-issuances/WI0000492475/cancel
```

You will get back `204 No content` status code. 


**Congratulations!** You have completed getting started tutorial on most common steps when working with Customer Order API. To learn more look at the reference documentation for [available operations](swagger-ui).
