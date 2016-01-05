![Folders](http://cdn.flaticon.com/png/64/98/98193.png)
Fraud detection API v2
=========================
Fraud Detection API enables to prevent fraud activitis according to legal requirements of finanacial institution. With Fraud Detection API you can:
        - Check client AML status
        - Check whether client is on banks black list
   
Key Resources
-------------
Fraud detection API has two top level collection resources: aml lists, black lists

Resource | Description
----------- |-----------
*aml lists*  | Includes detection of suspicious activity such as predictive crimes of money laundering, financing of terrorism, securities fraud and market manipulation.
*black lists*    | Includes a list of persons, organizations or nations suspected or convicted of fraudulent, illegal or criminal activity, and therefore excluded from a service or penalized in some other manner. A blacklist may be maintained by any entity, ranging from a small business enterprise to an inter-governmental body. Depending on the scope of the blacklist, it may either be secret or public.

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Fraud detection API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Fraud detection API with your access token against the URL root below, combined with one of the root resources. Fraud detection API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Fraud detection  | `https://api.asse.co/fraud-detection`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /aml-status` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Check customer AML status
Let's assume that you want to check client aml risk assessment. You can do that at following endpoint:
```
GET /aml-status?personal-identification-number=0607983130013&first-name=Branislav&last-name=Vuković
```
You will get back `200 OK` status code and json representation for fetched request. 

```json
{
  "rating-value": "0",
  "reliability": "low-risk"
}
```
###4. Check whether client is on black lists
Let's assume that you want to check whether client is on any black list and if so what is the percentage of the match. You can do that at following endpoint
```
GET/black-list-status?personal-identification-number=0607983130013&first-name=Branislav&last-name=Vuković
```
You will get back `200 OK` status code and json representation for fetched request. 
```json
{
  "items": [
    {
      "percentage": "80",
      "name": "EU black list"
    },
    {
      "percentage": "75",
      "name": "UN black list"
    }
  ]
}
```

**Congratulations!** You have completed getting started tutorial on most common steps when working with Fraud detection API. To learn more look at the reference documentation for [available operations](swagger-ui).
