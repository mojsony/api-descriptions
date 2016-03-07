<span class="icon"></span>Party API
=========================
Party API gives you access to individuals and organizations registered with the financial institution whether they are customers or just prospects or related parties. Also you can get all party related information like identification documents, contacts, financial reports, classifications and arrangements. Party data service can be used to register new prospects in the system.
With Customer survey API you can:
    - Get list of individual customers
    - Create new individual customer with full set of data
    - Create new potential individual customer
    - Get list of identification documents for individual customer
    - Get data of the individual customer 
    - Creates postal address for individual customer
    - Creates telecommunication number for individual customer
    - Creates electronic address for individual customer
    - Get contacts data for individual customer
    - Get postal address for individual customer
    - Get telecommunication number for individual customer
    - Get electronic address for individual customer
    - Get contact preference for individual customer
    - Get identification document for individual customer
    - Get classification schema values
   
Key Resources
-------------
Party Data has five top level collection resources: individuals, identification documents, contacts, contact preferences and classifications.

Resource						| Description
------------------------------- |------------------------------------
*individuals*					| Identifies a particular type of Involved Party that is a natural person who is of interest to the modeled organization.
*identification documents*      | Represents identification document of the individual customer, sauch as identity card, passport, driving licence...
*contacts*						| Represents the method and destination of a communication contact with a Role Player. This relates to specific communication media: Postal Address, Telephone Number, Electronic Address 
*contact preferences*		    | Represents contact that has sepcific usage, like contact address used to communicate about arrangement.
*classifications*			    | Identifies a grouping of <Business Model Object>s, for example; Single Males Under 30, Married People over 50, etc...  A Classification Value can be further partitioned into several sub-classifications according to different criteria, each of which is represented in turn by a Classification Scheme.

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
Party | `https://dev.asseco-see.com/v1/party`

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