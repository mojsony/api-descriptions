<span class="icon"></span>Account Data API 
======================
Account Data API provides simplified access to balance and histories of customer account arrangements. Beyond traditional access to account balances and transactions, more advanced capabilities such as full text search and geospatial information are available. When PFM feature is present transactions also have spending categories and customer assigned tags. Clients that have capabilities to store data locally can use sync optimized endpoints to transactions that occurred since last synchronization.
   
Key Resources
-------------
Account Data API has four top-level collection resources: accounts, transactions, balances and statements. 

Resource | Description
----------- |-----------
*account*  | Represents a record of transactions, posting entries and balances for specific types of product arrangements (account arrangements), maintained by a bank party on behalf of one or more owning parties.
*transaction*   | Represents a recorded change on monetary positions (balances) of interest to customers and bank - principal, outstanding debt, advance, available. Change recorded as transaction is sometimes effect of processing  instruction that bank receives from customers or payment networks, but it can also be result of internally initiated bank's processes.
*balance*    | Represent a monetary value tracked on the account. Different kinds of balances are calculated according to banks policy by summing posting entries. 
*statement* | Represent recorded report of booked entries and balances on account in specified period of time. Statements are always incremental, whether they are generated automatically on specific frequency agreed with customer on demand based on customer request. Banks generate statement document as a printable report that includes basic statement information but also marketing and other

Getting started
---------------
To get started follow these steps:
###1. Authenticate your app
Account Data API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. Base URL
Now that you've authenticated your app, you can call the Account Data API with your access token against the base URL below, combined with one of the root resources. Account Data API URLs are relative to the following base URL unless otherwise noted.

API | Base URL
--------|---------
Account Data | `https://dev.asseco-see.com/v1/account-data`

> **Note**: Throughout the document, we use relative URLs such as: 
`GET /transactions` for the sake of brevity. 
Prefix the path with the correct root base URL in order to obtain the full resource path or URL.

###3. Get status of customer accounts and balances
Often you need to get basic information and status of customer accounts together with balances. While balances are available at its own endpoint, you can reduce number of requests for this common scenario by specifying `include` parameter. Let's assume that you need to get status and available balances for two accounts.
You can get list of accounts by issuing following query:
```http
GET /accounts?accounts=00210102101,00310003334&include=balances&balance-kinds=available HTTP/1.1
```
You will get back `200 OK` status code and json representation of account list that includes balances for each account. 

```http
HTTP/1.1 200 Ok
Content-Type: application/json

[
  {
    "account-number": "00310003334",
    "effective-date": "2016-01-01",
    "status-date": "2016-01-01",
    "currency": "EUR",
    "status": "open",
    "posting-status": "post-all",
    "kind": "demand-deposit",
    "balances": [
        {
          "account-number":"00310003334",
          "amount": 700.00,
          "amount-local": 85400.00,
          "currency": "RSD",
          "direction": "d",
          "balance-kind": "available",
          "calculated": "2016-02-23T15:50:00.000Z"
        }
     ]    
  },
  {
    "account-number": "00210102101",
    "effective-date": "2016-01-01",
    "status-date": "2016-01-01",
    "currency": "RSD",
    "status": "open",
    "posting-status": "post-all",
    "kind": "current-account",
    "balances":[
        {
          "account-number": "00210102101",
          "amount": 12283.50,
          "amount-local": 12283.50,
          "currency": "RSD",
          "direction": "d",
          "balance-kind": "available",
          "calculated": "2016-02-23T15:50:00.000Z"
        }
     ]      
  }
]

```
> **NOTE**: Multi-currency accounts are returned as multiple items having distinct combinations of account-number and currency.  

###4. Get last 5 account transactions with specific fields
Sometimes you need to show only a few details of transactions on a map, so you need few latest transactions and only a few fields for each of them. Thanks to support for response shaping and geocoding you can specify fields to `include` or `trim` from response. For more details see [response shaping](common-getstarted.html#shaping) section of the guide.
 
You can get last 5 transactions with specific fields by issuing following query:
```http
GET /transactions?accounts=00210300231212&trim=*&include=amount-local,direction,transaction-time,coordinates&page-size=5 HTTP/1.1
```
You will get back `200 OK` status code and json representation of transaction list having only the fields you specified.

```http
HTTP/1.1 200 Ok
Content-Type: application/json

[
  {
    "amount-local": "12283.50",
    "direction": "d",
    "transaction-time": "2016-02-23T11:25:00",
    "coordinates": {
        "lat": "44.807112185659996",
        "long": "20.429377555847164"
     }    
  },
  {
    "amount-local": "987.00",
    "direction": "d",
    "transaction-time": "2016-02-23T11:25:00",
    "coordinates": {
        "lat": "44.807112185659996",
        "long": "20.429377555847164"
     }    
  }
]

```
>If you do not specify fields to include or trim, response will contain fields returned by default  according to reference documentation. You can remove default set of returned fields by using `trim=*` and then add only fields you need with `include`. Reverse also applies so you can start from full set of fields with  `include=*` and then remove only fields you don't need with `trim`.

###5. Get pending transactions
Some transactions are not yet booked against account but they still affect available balance. Optional parameter `statuses` lets you specify which transaction statuses are of interest. 
You can get pending transactions with following query:
```http
GET /transactions?accounts=00210300231212&statuses=p&trim=*&include=amount-local,direction,transaction-time HTTP/1.1
```
You will get back `200 OK` status code and json representation of pending transaction list having only the fields you specified.

```http
HTTP/1.1 200 Ok
Content-Type: application/json

[
  {
    "amount-local": "12283.50",
    "direction": "d",
    "transaction-time": "2016-02-23T11:25:00",
  },
  {
    "amount-local": "987.00",
    "direction": "d",
    "transaction-time": "2016-02-23T10:25:00",  
  }
]

```
>**NOTE**: Without explicit pagination and sorting parameters default page size of 10 is assumed and transactions are sorted by `transaction-time` in descending order. 

###6. Get all that is known about specific transaction
When you have a `transaction-id` and you want to dig deeper into details you can get details with following query:
```http
GET /transactions/8662551711?include=* HTTP/1.1
```
You will get back `200 OK` status code and json representation of transaction with full set of fields.

```http
HTTP/1.1 200 Ok
Content-Type: application/json

{
  "account-number": "00210102101",
  "transaction-id": "6525671616121",
  "instruction-id": "6525671616121",
  "statement-number": "26",
  "source": "brn",
  "amount": 100.00,
  "amount-local": 12283.50,
  "currency": "EUR",
  "direction": "d",
  "status": "b",
  "value-date": "2016-02-23",
  "book-date": "2016-02-23",
  "transaction-time": "2016-02-23T11:25:00",
  "description": "Branch cash withdrawal",
  "transaction-code": "212",
  "transaction-kind": "wdw",
  "sync-timestamp": "26447476",
  "branch": {
    "branch-code": "2120"
  },
  "coordinates": {
    "lat": 44.807112185659996,
    "long": 20.429377555847164
  },
  "pfm": {
    "category-id": "27",
    "category": "Cash"
  },
  "media": {
    "image": "/v1/conent/mchub/documents/mj20b12534r4"
  }
}

```
>**NOTE**: Null fields are not included in the result. This specific transaction has originated in branch, it was geocoded, categorized by PFM and decorated with image by customer.

###7. Get list of account statements
Sometimes you need to check account statements from previous years. 
You can get list of statements by issuing following query:
```http
GET /statements?accounts=0000100123101&years=2014,2015 HTTP/1.1
```
You will get back `200 OK` status code and json representation of statement list.

```http
HTTP/1.1 200 Ok
Content-Type: application/json

[
  {
    "from-date": "2015-01-01",
    "to-date": "2015-01-31",
    "account-number": "00210102101",
    "sequence-number": "26",
    "generated": "2015-02-01T01:25:00",
    "document": "/v1/content/dms/documents/AS-0021000102101-26",
    "total-credits": "1",
    "total-debits": "3",
    "currency": "EUR",
    "opening-balance": "20.00",
    "closing-balance": "180.00"
  },
  {
    "from-date": "2014-12-01",
    "to-date": "2014-12-31",
    "account-number": "00210102101",
    "sequence-number": "25",
    "generated": "2014-01-01T01:27:00",
    "document": "/v1/content/dms/documents/AS-0021000102101-25",
    "total-credits": "2",
    "total-debits": "5",
    "currency": "EUR",
    "opening-balance": "45.00",
    "closing-balance": "20.00"
  }
]

```
> **NOTE**: Statement header contains a relative URI pointing to printable statement `document` kept in DMS repository.

**Congratulations!** You have completed getting started tutorial on most common steps when working with Account Data API. To learn more look at the reference documentation for [available operations](accounting.html).
