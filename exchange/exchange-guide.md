<span class="icon"></span>Exchange API Guide 
======================
Exchange API provides access to data regarding to exchange between currencies
   
Key Resources
-------------
Exchange API has three top level collection resources: transactions, offers and rates.

Resource | Description
----------- |-----------
*transactions*  | Contains methods for getting data about transactions for the user, and making new transactions.
*offers* | Contains method for currency exchange offer. 
*rates* | Contains methods for currency exchange rates on the specific date and for history.


Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Exchange API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Exchange API with your access token against the URL root below, combined with one of the root resources.  
Exchange API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Exchange | `https://dev.asseco-see.com/v1/exchange`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /transactions` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.


###3. Get transaction list


Before You can choose a transaction you can get transaction list for authenticated user.
```
GET /transactions
```
You will get back `200 OK` status code and json representation with a list of transactions.
```json

{
	"total-count":82,
	"page-size":10,
	"page-number":1,
	"total-pages":9,
	"items":
			[
				{
					"source-account":{"currency-code":"EUR",
					"account-number":"115-0000000050378-56"},
					"destination-account":{"currency-code":"RSD",
					"account-number":"115-0000000050378-56"},
					"currency":{"code":"EUR","amount":0.18},
					"client-id":"1402682",
					"status":{"code":"executed","description":"transaction executed",
					"effective-date":"2015-11-05T12:58:01"},
					"value-date":"2015-11-05T12:58:01",
					"posted-date":"2015,
					","posted-date":"2015-11-05T12:58:01",
					"executed-date":"2015-11-05T12:58:01",
					"transaction-id":"99900155225005",
					"payment-description":"Buying foreign currency",
					"purpose-code":797,"debit":false,
					"picture":null,
					"has-picture":false,
					"category":"",
					"geolocation":{"lat":"","lon":"","mapped-address":""},
					"uri":"https://api.asse.co/currency-exchange/v2/transactions/99900155225005"},
					{
						"source-account":{"currency-code":"RSD",
						"account-number":"115-0000000050378-56"
					},
					"destination-account":{"currency-code":"EUR",
					"account-number":"115-0000000050378-56"},
					"currency":{"code":"RSD","amount":21.00},
					"client-id":"1402682",
					"status":{"code":"executed",
					"description":"transaction executed",
					"effective-date":"2015-11-05T12:58:01"},
					"value-date":"2015-11-05T12:58:01",
					"posted-date":"2015-11-05T12:58:01",
					"executed-date":"2015-11-05T12:58:01",
					"transaction-id":"99900155225001",
					"payment-description":"Buying foreign currency",
					"purpose-code":0,
					"debit":true,
					"picture":null,
					"has-picture":false,
					"category":"",
					"geolocation":{"lat":"","lon":"","mapped-address":""},
					"uri":"https://api.asse.co/currency-exchange/v2/transactions/99900155225001"},
					{
						"source-account":{"currency-code":"RSD","account-number":"115-0000000050378-56"},
						"destination-account":{"currency-code":"EUR","account-number":"115-0000000050378-56"},
						"currency":{"code":"RSD","amount":2.00},
						"client-id":"1402682",
						"status":{
									"code":"executed",
									"description":"transaction executed",
									"effective-date":"2015-11-05T12:57:35"},
									"value-date":"2015-11-05T12:57:35",
									"posted-date":"2015-11-05T12:57:35",
									"executed-date":"2015-11-05T12:57:35",
									"transaction-id":"99900155224001",
									"payment-description":"Buying foreign currency",
									"purpose-code":0,
									"debit":true,
									"picture,":null,
									"has-picture":false,
									"category":"",
									"geolocation":{
													"lat":"",
													"lon":"",
													"mapped-address":""},
													"uri":"https://api.asse.co/currency-exchange/v2/transactions/99900155224001"},
													{"source-account":{"currency-code":"EUR","account-number":"115-0000000050378-56"},
													"destination-account":{"currency-code":"RSD",
													"account-number":"115-0000000050378-56"},
													"currency":{"code":"EUR","amount":0.02},
													"client-id":"1402682"
													
    ...
    
```



###4. Get transaction details

For particular transaction identifier user can get transaction details.

```
GET /transactions/{transaction-id}
```
You will get back `200 OK` status code and json representation with transaction details.
```json
{
	"source-account":{
						"currency-code":"RSD",
						"account-number":"115-0000000050378-56"
					 },
	"destination-account":{
							"currency-code":"EUR",
							"account-number":"115-0000000050378-56"
						  },
	"currency":{
				"code":"RSD",
				"amount":25696.61
				},
	"client-id":"1402682",
	"status":{
				"code":"executed",
				"description":"transaction executed",
				"effective-date":"2015-11-19T13:01:56"
			 },
	"value-date":"2015-11-19T13:01:56",
	"posted-date":"2015-11-19T13:01:56",
	"executed-date":"2015-11-19T13:01:56",
	"transaction-id":"99900155290001",
	"payment-description":"Buying foreign currency",
	"purpose-code":0,
	"debit":true,
	"picture":null,
	"has-picture":false,
	"category":"",
	"geolocation":{
					"lat":"",
					"lon":"",
					"mapped-address":""
				  },
	"uri":"https://api.asse.co/currency-exchange/v2/transactions/99900155290001"
}
```

###5. Get curency exchange rates history

User can get curency exchange rates history. 

```
GET /rates/history
```
You will get back `200 OK` status code and json representation with rates history.
```json
{
	"total-count":886,
	"page-size":10,
	"page-number":1,
	"total-pages":0,
	"items":[
				{
					"date-created":"2015-11-19T00:00:00",
					"list-type":"",
					"rate-number":80077,
					"total-count":0,
					"page-size":0,
					"page-number":0,
					"total-pages":0,
					"items":[
							
							]
				}
			]
}
```


###6. Get curency exchange rates

You can get curency exchange rates for specific date.

```
GET /rates/2015-11-19

```
You will get back `200 OK` status code and json representation with details of exchange rates for specific date.
```json
{
  "date-created": "2015-11-19T00:00:00",
  "list-type": "",
  "rate-number": 80077,
  "total-count": 5,
  "page-size": 10,
  "page-number": 1,
  "total-pages": 0,
  "items": [
    {
      "buy": 91.4128,
      "buy-cache": 91.3291,
      "country-code": "CHF",
      "country-name": "Switzerland",
      "currency-code": "CHF",
      "for-local": 1,
      "max-sell-cache": 97.1136,
      "middle": 95.0133,
      "rate": 95.0133,
      "sell": 97.0137,
      "sell-cache": 97.1136
    },
    {
      "buy": 113.7678,
      "buy-cache": 113.7143,
      "country-code": "EU",
      "country-name": "European Union",
      "currency-code": "EUR",
      "for-local": 1,
      "max-sell-cache": 118.177,
      "middle": 115.9067,
      "rate": 115.9067,
      "sell": 118.1145,
      "sell-cache": 118.177
    },
    {
      "buy": 137.9641,
      "buy-cache": 137.9573,
      "country-code": "GBR",
      "country-name": "Great Britain",
      "currency-code": "GBP",
      "for-local": 1,
      "max-sell-cache": 143.9341,
      "middle": 140.6293,
      "rate": 140.6293,
      "sell": 143.6606,
      "sell-cache": 143.9341
    },
    {
      "buy": 13.6786,
      "buy-cache": 13.4829,
      "country-code": "NOR",
      "country-name": "Norway",
      "currency-code": "NOK",
      "for-local": 1,
      "max-sell-cache": 14.0635,
      "middle": 13.857,
      "rate": 13.857,
      "sell": 14.0334,
      "sell-cache": 14.0635
    },
    {
      "buy": 82.3737,
      "buy-cache": 82.2948,
      "country-code": "USA",
      "country-name": "United States of America",
      "currency-code": "USD",
      "for-local": 1,
      "max-sell-cache": 86.4326,
      "middle": 84.4801,
      "rate": 84.4801,
      "sell": 86.3434,
      "sell-cache": 86.4326
    }
  ]
}
```


**Congratulations!** You have completed getting started tutorial on most common steps when working with Exchange API. 
To learn more look at the reference documentation for [available operations](swagger-ui).
