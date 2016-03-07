![Folders](http://cdn.flaticon.com/png/64/98/98193.png)
Offer Management API v2
=========================
Offer Management API v2 lets you initiate, track and execute offers for loans, limits and accounts. It provides simulation of conditions for potential products and services.
   
Key Resources
-------------
Offer Management has six top level collection resources: product applications, deposit applications, current account applications, envelope applications, loan applications and credit facility applications.  

Resource | Description
----------- |-----------
*product account openings*  | Workitem used to capture details of client request for a product or service. Serves as a ticket for tracking progression of the workflow through phases and states, from draft to closed.
*deposit account openings*      | Kind of product account openings. Products used for this kind are term deposit products, demand deposit products and special deposit products.
*current account openings*    | Kind of product account openings. Products used for this kind are current account products.
*bundled account openings* | Kind of product account openings. Products used for this kind are term deposit products, demand deposit products and special deposit products. This kind of product application is available only for current account bundled products.  
*loan originations* | Kind of product account openings. Products used for this kind are term loan products.
*credit facility originations* |Kind of product account openings. Products used for this kind are credit limit facility products and overdraft facility products.

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Content Management API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Offer Management API with your access token against the URL root below, combined with one of the root resources.  Offer Management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Offer Management | `https://api.asse.co/offer-management`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /current-account-openings/{workitem-id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.


###3. Create current account opening
Let's assume that you want to create current account opening for fully registered customer.
To create current account request you need to post `current account opening` metadata representation as json to following endpoint:

```
POST /current-account-openings
```

```json
{
  "customer-number": "1400054",
  "product-code": "TMCY_0001",
  "requested-account-number": "33333333333333",
  "campaign-id": "",
  "ship-to-order": "false"
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
GET /current-account-openings/WI0000492475 
```

You will get back `200 OK` status code and json representation of created current account opening. 

```json
[
  {
    "workitem-number": "WI0000492475",
    "product-number": "TMCY_0001",
    "product-name": "Multivalutni rn - PAKET 1",
    "product-family-name": "Telenor multivalutni računi",
    "customer-number": "1400054",
    "customer-name": "Milutin Cvetkovic",
    "customer-object-type-name": "Domaća fizička lica rezidenti",
    "status": "Active",
    "created-by-name": "Biljana Davidovic",
    "primary-currency": "RSD",
    "comments": "Novi klijent",
    "requested-activation-date": "2015-12-10T10:16:56.8807659+01:00",
    "request-date": "2015-12-10T10:16:56.8807659+01:00",
    "requested-account-number": "33333333333333",
    "offered-terms": {
        "base-interest-rate": 0.0,
        "stimulant-interest-rate": 0.0,
        "penalty-interest-rate": 0.1
      },
    "marketing-terms": "Multivalutni rn - PAKET 1 - Оtvaranje i održavanje viševalutnog tekućeg računa se ne naplaćuje  - Mesečna naknada za paket iznosi 300 RSD  - Jedan izvod mesečno je bez naknade, svaki naredni izvod se naplaćuje 200 RSD  - SMS notifikacije o prilivu na tekući račun se ne naplaćuje  - SMS notifikacija  o odlivu sa tekućeg računa se ne naplaćuje  - Izdavanje MasterCard osnovne kartice se ne naplaćuje  - Izdavanje MasterCard dodatne  kartice  – 200 RSD po kartici  - Podizanje gotovine  na bankomatima drugih banaka: - u zemlji - prvih pet transakcija besplatno, svaka naredna 50 RSD, - u inostranstvu 1% (min. 400 RSD)  - Podizanje gotovine  na šalterima drugih banaka u zemlji i inostranstvu  1% min. 600 RSD.  - Vrsta i visina svih naknada i troškova koje padaju na teret klijenta su promenljive, tako da Banka može kvartalno i to svakog 01. 01.; 01. 04.; 01. 07.; 01. 10. da promeni visinu naknada iznad ugovorenog iznosa."
  }
]
```
###5. List customer requests
Now lets list the requests for customer and verify that it contains created current account opening.

```
GET /product-account-openings?customer-number=1400054
```

You will get back  `200 OK` status code and json representation with a list of product account openings. 

```json
{
  "items": [
    {
      "workitem-number": "WI0000492475",
      "kind": "CurrentAccountOpening",
      "product-number": "TMCY_0001",
      "product-name": "Multivalutni rn - PAKET 1",
      "product-family-name": "Telenor multivalutni računi",
      "customer-number": "1400054",
      "customer-name": "Milutin Cvetkovic",
      "customer-object-type-name": "Domaća fizička lica rezidenti",
      "status": "Active",
      "created-by-name": "Biljana Davidovic",
      "primary-currency": "RSD",
      "comments": "Novi klijent",
      "requested-activation-date": "2015-12-10T10:16:56.8807659+01:00",
      "request-date": "2015-12-10T10:16:56.8807659+01:00",
      "requested-account-number": "33333333333333",
      "offered-terms": {
        "base-interest-rate": 0.0,
        "stimulant-interest-rate": 0.0,
        "penalty-interest-rate": 0.1
      },
      "marketing-terms": "Multivalutni rn - PAKET 1 - Оtvaranje i održavanje viševalutnog tekućeg računa se ne naplaćuje  - Mesečna naknada za paket iznosi 300 RSD  - Jedan izvod mesečno je bez naknade, svaki naredni izvod se naplaćuje 200 RSD  - SMS notifikacije o prilivu na tekući račun se ne naplaćuje  - SMS notifikacija  o odlivu sa tekućeg računa se ne naplaćuje  - Izdavanje MasterCard osnovne kartice se ne naplaćuje  - Izdavanje MasterCard dodatne  kartice  – 200 RSD po kartici  - Podizanje gotovine  na bankomatima drugih banaka: - u zemlji - prvih pet transakcija besplatno, svaka naredna 50 RSD, - u inostranstvu 1% (min. 400 RSD)  - Podizanje gotovine  na šalterima drugih banaka u zemlji i inostranstvu  1% min. 600 RSD.  - Vrsta i visina svih naknada i troškova koje padaju na teret klijenta su promenljive, tako da Banka može kvartalno i to svakog 01. 01.; 01. 04.; 01. 07.; 01. 10. da promeni visinu naknada iznad ugovorenog iznosa."
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
