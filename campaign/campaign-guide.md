<span class="icon"></span>Campaign API Guide
==========================================
Campaign API lets you execute campaigns from your self-service and assisted channel applications. You get 
history or post responses to leads. You can also capture customer’s interest for products or services by generating
custom leads directly into the system.
   

> ##THIS API GUIDE IS UNDER CONSTRUCTION. COME BACK SOON.
   

Key Resources
-------------
Campaign Execution has campaign as a top-level resource with targeted offers, responses and benefits as its sub-resources.

Resource | Description
----------- |-----------
*campaign*  | Represent a marketing project to reach out to customers in order to some fulfill business objective. For direct campaigns that are targeted at specific customer segment objective is usually to get customers to buy more products and services or to use more product features.
*targeted offer*    | Represents offer available to customer targeted in a campaign. Offer contains both text and visual media optimized for a presentation on a specific channel such as mobile or ATM.
*benefit* | Represent benefits that targeted customer gets if he accepts the offer (e.g. lower interest rate, x free transactions on atm)

Getting started
---------------
To get started follow these steps:
###1. Authenticate your app
Campaign API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication](common-getstarted.html#authentication) section.

###2. URL Root
Now that you've authenticated your app, you can call the Campaign API with your access token against the base path below, combined relative paths of exposed API resources.  Campaign API URLs are relative to the following root unless otherwise noted.

API | Base path
--------|---------
Campaign  | `https://dev.asseco-see.com/v1/campaign`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /campaigns` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.



**Congratulations!** You have completed getting started tutorial on most common steps when working with Campaign API. To learn more look at the reference documentation for [available operations](campaign.html).
