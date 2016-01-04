![Folders](http://cdn.flaticon.com/png/64/98/98193.png)
Reference data API v2
=========================
Reference data API gives you access to a repository of registries maintained by the financial institution.
With Reference data API you can:
        - Get the list of countries
        - Get the list of currencies 
        - Get the list of channels 
        - Get the list of places 
        - Get the list of streets 
   
Key Resources
-------------
Reference data API has five top level collection resources: countries, currencies, channels, places and streets.

Resource | Description
----------- |-----------
*countries*  | Register of official countries.
*currencies*      | Register of all currencies that one finanacial institution can work.
*channels*    | Identifies a conduit through which products and services are made available to a Customer and by which the Organization and Customers communicate with each other.
*places*    | Register of official places (cities, towns, villages) per country.
*streets* | Register of official streets per place.

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Reference data API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Reference data API with your access token against the URL root below, combined with one of the root resources.  Reference data API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Reference data  | `https://api.asse.co/content`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /places` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Get list of countries
Let's assume you want to preview list of countries that is displayed on specified page number and page size.
You can do that at following endpoint:
```
GET /countries?page=1&page-size=3
```
You will get back 200 OK status code and json representation for fetched request. 
```json
{
  "total-count": 74212,
  "page-size": 3,
  "page-number": 1,
  "total-pages": 24738,
  "items": [
    {
      "name": "SVETA JELENA",
      "translation-name": "Sveta Jelena",
      "code": "654",
      "alpha2": "SH",
      "alpha3": "SHN",
      "country-status": "Existing",
      "is-eu-member": false,
      "iban-prefix": null,
      "iban-length": 0
    },
    {
      "name": "FRANCE",
      "translation-name": "Francuska",
      "code": "250",
      "alpha2": "FR",
      "alpha3": "FRA",
      "country-status": "Existing",
      "is-eu-member": true,
      "iban-prefix": null,
      "iban-length": 0
    },
    {
      "name": "SAINT BARTHELEMY",
      "translation-name": "Sveti Bartolomej",
      "code": "652",
      "alpha2": "BL",
      "alpha3": "BLM",
      "country-status": "Existing",
      "is-eu-member": false,
      "iban-prefix": null,
      "iban-length": 0
    }
   ]
}
```


###4. Get list of streets
Let's assume you want to preview list of streets for specifed place name, page number and page size.
You can do that at following endpoint:

```
GET/streets?place-name=Subotica&page-size=3&page=1
```
You will get back 200 OK status code and json representation for fetched request.
```json
{
  "total-count": 1002,
  "page-size": 3,
  "page-number": 1,
  "total-pages": 335,
  "items": [
    {
      "name": "A B ŠIMIĆA",
      "alternative-names": [],
      "code": "823605531",
      "place-name": "SUBOTICA",
      "country-name": "SRBIJA"
    },
    {
      "name": "ACINA ULICA",
      "alternative-names": [],
      "code": "609702737",
      "place-name": "SUBOTICA",
      "country-name": "SRBIJA"
    },
    {
      "name": "ADAČKA",
      "alternative-names": [],
      "code": "823605546",
      "place-name": "SUBOTICA",
      "country-name": "SRBIJA"
    }
  ]
}
```

###5. Get list of curencies
Let's assume you want to preview list of currencies for specified page number and page size. You can do that at following endpoint:

```
GET/currencies?page-size=3&page=1
```
You will get back 200 OK status code and json representation for fetched request.
```json
{  
  "total-count": 1002,
  "page-size": 3,
  "page-number": 1,
  "total-pages": 335,
  "items": [
    {
      "name": "Euro",
      "translated-name": null,
      "currency-symbol": "€",
      "currency-code": "978",
      "alphanumeric-code": "EUR",
      "is-convertible": true
    },
    {
      "name": "Dinars",
      "translated-name": null,
      "currency-symbol": "RSD",
      "currency-code": "941",
      "alphanumeric-code": "RSD",
      "is-convertible": true
    },
    {
      "name": "Francs",
      "translated-name": null,
      "currency-symbol": "CHF",
      "currency-code": "756",
      "alphanumeric-code": "CHF",
      "is-convertible": true
    }
   ]
}
```
**Congratulations!** You have completed getting started tutorial on most common steps when working with Reference data API. To learn more look at the reference documentation for [available operations](swagger-ui).
