Product API
======================
Product API provides product information needed for channel applications. The main functions are search over product catalog and kind-specific detailed product information. Besides arrangement-based products, product catalog also contains all services bundled into these arrangement-based products.
   
Key Resources
-------------
Product Matching has `products` top-level collection with `bundled-products` and `documents` as sub-resources. 

Resource | Description
----------- |-----------
*products* | Catalogue of products offered by bank
*bundled products* | Products bundled with master product
*documentation* | Documentation necessary during different arrangement phases

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Product API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Product API with your access token against the URL root below, combined with one of the root resources. Product API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Product | `https://dev.asseco-see.com/v1/product`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /current-account-products/{product-number}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. List product catalog
Operation returns list of products available through product catalog. 
Following params are user to filer product catalog result:
- `kind`	- Product types to be shown. If set, only products of these kinds will be returned, if not - none will be returned.
- `status` 	- Customer centric statuses to be shown. If set, only products of these statuses will be returned, if not - none will be returned.
- `name`	- Name or part of the products name. If not set, all products will be returned.
- `product-family` -  Name of product family. If set, only products that belongs to specified product family will be returned. If not set, all products will be returned.
- `channel-code` - Filter product catalog by product channel availability.
- `page-number`	- Page index of result.
- `page-size`	- Number of items on a page result.
- `sort-order`	- Sort order (`asc` or `desc`).
- `sort-type`	- Attribute of the collection item to sort by.

```
GET/products?status=coming-soon, already-used-by-client, not-used-by-client&page-number=1&page-size=100&kind=deposit, current-account, demand-deposit, term-deposit, finance-service, term-loan, credit-facility, product-access&channel-code=web
```

You will get back `200 OK` status code and json representation with a list of products. 
```json
{
	"total-count": 23,
	"page-size": 1,
	"page-number": 1,
	"total-pages": 23,
	"items":[  
      {  
         "product-number":"TMCY_0001",
         "name":"Multivalutni rn - PAKET 1",
         "description":"Multivalutni rn - PAKET 1",
         "market-features":"Uz viševalutni tekući račun klijent ima mogućnost korišćenja sledećih usluga:  • Visa classic debitna kartica  • Štednja po viđenju u domaćoj valuti  ",
         "family-name":"Multivalutni rn - PAKET 1",
         "status":"not-used-by-client",
         "kind":"current-account",
         "primary-market-segment-name":"PREPAID",
         "is-package":false,
         "image": null,
         "application-process-description":"Proces apliciranja preko web-a",
         "required-documentation":"Ponesite ličnu kartu",
         "allowed-currencies":[  
            {  
               "alphanumeric-code":"EUR",
               "currency-code":978
            },
            {  
               "alphanumeric-code":"RSD",
               "currency-code":941
            },
            {  
               "alphanumeric-code":"USD",
               "currency-code":840
            }
         ],
         "is-recommended":false,
         "campaign-code":null
      }
   ]
}
```

###4. Get current account product
To overview specific product details, which in this example is type of `current-account` , we need to call:
```
GET/current-account-products/TMCY_0001
```

You will get back `200 OK` status code and json representation for fetched request. 
```json
{  
   "product-number":"TMCY_0001",
   "name":"Multivalutni rn - PAKET 1",
   "family-name":"Multivalutni rn - PAKET 1",
   "status":"not-used-by-client",
   "primary-market-segment-name":"PREPAID",
   "description":"Multivalutni rn - PAKET 1",
   "benefits-info":"- Оtvaranje i održavanje viševalutnog tekućeg računa se ne naplaćuje  - Mesečna naknada za paket iznosi 300 RSD  - Jedan izvod mesečno je bez naknade, svaki naredni izvod se naplaćuje 200 RSD  - SMS notifikacije o prilivu na tekući račun se ne naplaćuje  - SMS notifikacija  o odlivu sa tekućeg računa se ne naplaćuje  - Izdavanje MasterCard osnovne kartice se ne naplaćuje  - Izdavanje MasterCard dodatne  kartice  – 200 RSD po kartici  - Podizanje gotovine  na bankomatima drugih banaka: - u zemlji - prvih pet transakcija besplatno, svaka naredna 50 RSD, - u inostranstvu 1% (min. 400 RSD)  - Podizanje gotovine  na šalterima drugih banaka u zemlji i inostranstvu  1% min. 600 RSD.  - Vrsta i visina svih naknada i troškova koje padaju na teret klijenta su promenljive, tako da Banka može kvartalno i to svakog 01. 01.; 01. 04.; 01. 07.; 01. 10. da promeni visinu naknada iznad ugovorenog iznosa. ",
   "image": null,
   "cover-image": null,
   "application-process-description":"Proces apliciranja preko web-a",
   "required-documentation":"Ponesite ličnu kartu",
   "campaign-code":null,
   "primary-currency":{  
      "alphanumeric-code":"RSD",
      "currency-code":941
   },
   "allowed-currencies":[  
      {  
         "alphanumeric-code":"EUR",
         "currency-code":978
      },
      {  
         "alphanumeric-code":"RSD",
         "currency-code":941
      },
      {  
         "alphanumeric-code":"USD",
         "currency-code":840
      }
    ],
   "term-scale":[  
      {  
         "minimal-period":0,
         "minimal-unit-of-time":"M",
         "maximal-period":3,
         "maximal-unit-of-time":"M"
      }
   ],
   "interest-rate":{  
      "referent-rate":"EUR6M",
      "referent-rate-value":0.23,
      "referent-rate-unit-of-time":"Y",
      "spread-rate-value":15,
      "spread-rate-unit-of-time":"Y",
      "calculated-rate-value":15.25,
      "calculated-rate-unit-of-time":"Y",
      "interest-calculation-method":"Compound 30/Actual",
      "condition-name":"Basic interest",
      "condition-type":"BasicInterest",
      "calculation-status":"",
      "default-parameters":"",
      "unresolved-parameters":""
   },
   "notification":[  
      {  
         "product-number":"welcome-benefit",
         "name":"Dobrodošlica",
         "description":"Dobrodošlica"
      }
   ]
}
```

###5. Get list of bundled products for specific master product

To get list of all budled products for specific master product:
```
GET/current-account-products/TMCY_0001/bundled-products
```
You will get back `200 OK` status code and json representation for fetched request. 
```json
{  
   "items":[  
      {  
         "product-name":"Visa classic debitna kartica",
         "product-number":"VisaClassicDebit",
         "product-kind":"card-access",
         "status":"not-used-by-client",
         "image": null,
         "is-optional":false,
         "minimal-number-of-instances":0,
         "maximal-number-of-instances":0
      },
      {  
         "product-name":"Štednja po viđenju u domaćoj valuti",
         "product-number":"DEP-avista-standard-rsd",
         "product-kind":"demand-deposit",
         "status":"not-used-by-client",
         "image":null,
         "is-optional":false,
         "minimal-number-of-instances":0,
         "maximal-number-of-instances":0
      }
   ]
}
```

**Congratulations!** You have completed getting started tutorial on most common steps when working with Product API. To learn more look at the reference documentation for [available operations](swagger-ui).