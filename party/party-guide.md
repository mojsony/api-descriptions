---
visibility: internal
---

<span class="icon"></span>Party API
=========================
Party API gives you access to individuals and organizations registered with the financial institution whether they are customers or just prospects or related parties. In addition, you can get all party related information like identification documents, contact points and relationships.

> ## THIS GUIDE IS UNDER CONSTRUCION, PLEASE COME BACK SOON!
   
Key Resources
-------------
Party API has on top-level collection resources: parties that specializes into individuals and organizations subresources for the purpose of specific commands. Party also composes identification documents, contact points and relationships as sub-resources.

Resource						| Description
------------------------------- |------------------------------------
*parties*					| Individuals and organizations of interest to bank. Information recorded for both organizations and individuals is under this resource. Customer is one role a party can play and customer lifecycle goes from potential, through prospective and active to former.
*contact points*						| Represents the method and destination of a communication contact with a party. This relates to specific communication media: Postal Address, Telephone Number, Electronic Address


Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Customer Survey API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Customer Survey API with your access token against the URL root below, combined with one of the root resources.  Content Management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Party | `https://bankapi.net/v1/party`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /individuals/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Get list of individuals
To see individual customer data or to make some changes to individual customer data, you have to get list of individual customers.
You can list existing individual customers at following endpoint:
```
GET /individuals
```
You will get back `200 Success` status code and json representation with a list of individual customers with information of the regitered individual customers.
```json
items: 
    {
      "party-id": "314",
      "full-name": "Dalibor Davidovic",
      "gender": "Male",
      "birth-date": "1974-11-22 00:00:00.000"
      "place-of-birth": "MILOŠEVAC"
      "country-of-birth": "Srbija",
      "category": "Resident Individuals",
      "status": "Former",
      "general-contact-preference": "",
      "primary-identification": "",
      "primary-citizenship": "",
      "relationship-manager": "",
      "legal-address": "",
      "marital-status": "unmarried-individual",
      "employment-status": "employed",
      "contacts": 
                {
                 "id": "",
                 "contact-id": "",
                 "usage": "",
                 "category": "",
                 "details": "",
                 "postal-address":
                                 {
                                  "country-name": "",
                                  "locality-name": "",
                                  "street": "",
                                  "street-number": "",
                                  "apartment": "",
                                  "address-code": "",
                                  "floor": "",
                                  "municipality": "",
                                  "postal-code": "",
                                  "locality-code": "",
                                  "street-code": "" 
                                 }
                 "contact-preference": 
                                {
                                  "contact-preference-id": "",
                                  "preferred-language": "",
                                  "arangement-number": "",
                                  "start-date": "",
                                  "end-date": "",
                                  "opt-ins": "",
                                  "opt-outs": "",
                                  "uri": ""
                                }
                 "is-primary": "",
                 "uri": ""
                }
      "arrangements":
                {
                 "arrangement-number": "",
                 "category": "",
                 "navigations":
                              {
                               link:
                                  {
                                   "href": "",
                                   "rel": ""
                                  } 
                              } 
                 "commands":
                              {
                               link:
                                  {
                                   "href": "",
                                   "rel": ""
                                  } 
                              }
                 "uri": ""  
                }
     "mandates":
              {
               "mandate":
                            {
                             "customer-id": "",
                             "authorized-service":
                                              {
                                               "category": "",
                                               "limit": ""
                                              }
                             "arrangement-number": "",
                             "effective-date": "",
                             "end-date": "",
                             "uri": "" 
                            } 
              }
      "postal-legal-address":
              {
               "common-postal-address":
                                 {
                                  "country-name": "",
                                  "locality-name": "",
                                  "street": "",
                                  "street-number": "",
                                  "apartment": "",
                                  "address-code": "",
                                  "floor": "",
                                  "municipality": "",
                                  "postal-code": "",
                                  "locality-code": "",
                                  "street-code": "" 
                                 }
              }        
    },

```


###4. Pick template to fill the survey for the customer
Let's assume that there are available `survey templates` for the `customer` to be filled with answers.
To create new survey from `survey template`:

```
POST /individuals/
```

```json
cmd-register-telecommunication-number:
{
  "first-name": "string *",
  "last-name": "string *",
  "telecommunication-number": 
              {
                "usage": "string *",
                "is-primary": "true",
                "category": "mobile-phone",
                "number": "1122334",
                "areacode": "69",
                "countrycode": "381",
                "extension": null
              }
  "electronic-address":
              {
                "is-primary": "false",
                "usage": "business",
                "category": "electronic-address",
                "address-text": "ddalibor@itc.com" 
              }
  "identity-card":
              {
                "card-number": "001234567",
                "identity-card-category": "Personal identification card",
                "issuing-date": "2010-07-03 00:00:00.000",
                "end-date":  "2020-07-03 00:00:00.000",
                "start-date": "2010-07-03 00:00:00.000",
                "issuing-place": "Beograd",
                "authority": "MUP Beograd" 
              } 
  "personal-identification-number": "2211974852509",
  "birth-place-locality-code": "string",
  "birth-place-locality-name": "string",
  "birth-country-code": "SRB",
  "middle-name": "Petar",
  "country-of-residence": "string",
  "legal-address":
              {
                "country-code": "SRB",
                "locality-code": "string",
                "street-name": "Nemanjina",
                "street-code": "string",
                "building": "22",
                "floor": "3",
                "apartment": "12"
              } 
  "contact-address": 
              {       
                "country-code": "SRB",
                "locality-code": "string",
                "street-name": "Nemanjina",
                "street-code": "string",
                "building": "22",
                "floor": "3",
                "apartment": "12"
              } 
  "delivery-address": 
              {       
                "country-code": "SRB",
                "locality-code": "string",
                "street-name": "Nemanjina",
                "street-code": "string",
                "building": "22",
                "floor": "3",
                "apartment": "12"
              }
  "employment-status": "employed",
  "foreign-official": "false",
  "foregin-official-family-member": "false",
  "customer-number": "DALDA03",
  "residential-status": "resident"
} 

```
You will get back `200 Success` status code and json representation with an Id of the newly created individual customer and 'created' record status.
```
Location: http://api.asse.co/party-data/contacts
```

###4. Register telecommunication number contact for individual customer
Add phone number for individual customer.

```
POST /individuals/314/contacts/telecommunication-number
```

```json
register-telecommunication-number-contact-command
{
  "contact-id": "string",
  "party-id": "314",
  "string": "home",
  "is-primary": "false",
  "category": "phone",
  "number": "2244556",
  "end-date": null;
}  

```
You will get back `200 Success` status code and json representation  with an Id of the newly created contact customer and 'created' record status.


**Congratulations!** You have completed getting started tutorial on most common steps when working with Customer Survey API. To learn more look at the reference documentation for [available operations](swagger-ui).