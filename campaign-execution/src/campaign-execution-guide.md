![Folders](http://cdn.flaticon.com/png/64/98/98193.png)
Campaign Execution API v2
=========================
Campaign execution API gives you access to active campaigns for customer, list customer active leads, read lead
history or post responses to leads. You can also capture customer’s interest for products or services by generating
custom leads directly into the system.
   
Key Resources
-------------
Campaign Execution has four top level collection resources: campaigns, resources, leads and benefits.

Resource | Description
----------- |-----------
*campaign*  | Defines data about campaign, product in campaign, benefits etc. Also provides metadata to help you visually represent the offer to customers.
*resource*      | Base64 representation of resources used in campaigns
*lead*    | Sales lead is object defined as "agent per customer per campaign offer". In other words, it represents a person or a company that might be interested in your product or service. Lead history can be tracked trough changes of lead status in time.
*benefit* | Benefits that campaign provides (e.g. lower interest rate, x free transactions on atm.. )

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Campaign Execution API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Campaign Execution API with your access token against the URL root below, combined with one of the root resources.  Campaign Execution API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
campaign execution | `https://api.asse.co/campaign-manager`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /campaigns/{campaign-code}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Get all active campaigns for the customer
In order to propose actual promotions to the customer, you need to get all active campaign offers for that customer. 
```
GET /campaigns
```
You will get back `200 OK` status code and json representation with a list of campaign offers. Based on response data you have informations about products on promotion and benefits customer gets.
Also you have all required information to acheve proper visual presentation of the offer.
```json
[
  {
  "items": [
    {
      "campaign-id": "sample string 1",
      "zone-code": "sample string 2",
      "ad-code": "sample string 3",
      "ad-weight": "sample string 4",
      "campaign-priority": "sample string 5",
      "ad-text": "sample string 6",
      "zone-type": "sample string 7",
      "media-uri": "sample string 8",
      "campaign-code": "sample string 9",
      "customer-code": "sample string 10",
      "resource-title": "sample string 11",
      "resource-description": "sample string 12",
      "product-code": "sample string 13",
      "redirect-uri": "sample string 14"
    },
    {
      "campaign-id": "sample string 1",
      "zone-code": "sample string 2",
      "ad-code": "sample string 3",
      "ad-weight": "sample string 4",
      "campaign-priority": "sample string 5",
      "ad-text": "sample string 6",
      "zone-type": "sample string 7",
      "media-uri": "sample string 8",
      "campaign-code": "sample string 9",
      "customer-code": "sample string 10",
      "resource-title": "sample string 11",
      "resource-description": "sample string 12",
      "product-code": "sample string 13",
      "redirect-uri": "sample string 14"
    }
  ]
}
]
```


###4. Register lead for the customer 
Let's assume that customer has shown interest in campaign offer. Now you need to register lead for the customer in status `qualified`.

```
POST /leads
```

```json
{
  "customer-number": "sample string 2",
  "channel-code": "sample string 3",
  "campaign-code": "sample string 4",
  "status": "sample string 5",
  "product-code": "sample string 6",
  "description": "sample string 7"
}
```
You will get back `201 Created` status code and id that represents `lead-number` of created lead. 
```
Location: http://api.asse.co/campaign-execution/leads
```

```json
{
  "id": "sample string 1",
  "created-record-status": "sample string 2"
}
```
For further processing  you will need lead id (`lead-number`).
###4. Upload some documents to folder
Let's assume that customer accepted the offer. You need to change customer lead's status to `won` and activate campaign execution workflow that manage approval of benefits in campaign. 


```json
{
  "id": "sample string 1",
  "lead-id": "sample string 2",
  "channel-code": "sample string 3",
  "status": "sample string 4",
  "description": "sample string 5",
  "party-id": "sample string 6",
  "campaign-code": "sample string 7",
  "product-code": "sample string 8",
  "PAN": "sample string 9",
  "SourceURI": "sample string 10",
  "is-provisioning-campaign": true
}
```

You will get back `201 Created` status code and json representation with a id of the lead changed. Campaign offer succedded and benefits are approved. Enjoy!

```
Location: http://api.asse.co/campaign-execution/leads
```
```json
{
  "id": "sample string 1",
  "created-record-status": "sample string 2"
}
```


**Congratulations!** You have completed getting started tutorial on most common steps when working with Campaign Execution API. To learn more look at the reference documentation for [available operations](swagger-ui).
