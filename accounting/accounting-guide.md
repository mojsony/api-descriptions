
<span class="icon"></span>Accounting API Guide 
======================
Accounting API tracks positions and transactions on customer account arrangements. Account arrangements have their accounts that track positions affected by entries posted with transactions. Statements report changes during certain time period.

> **Note**: Exposed endpoints are optimized for bulk access and support incremental synchronization
   
Key Resources
-------------
Accounting has four top-level collection resources: accounts, transactions, balances and statements. 

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
Accounting API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. Base URL
Now that you've authenticated your app, you can call the Accounting API with your access token against the base URL below, combined with one of the root resources. Accounting API URLs are relative to the following base URL unless otherwise noted.

API | Base URL
--------|---------
Accounting | `https://dev.asseco-see.com/v1/accounting`

> **Note**: Throughout the document, we use relative URLs such as: 
`GET /transactions` for the sake of brevity. 
Prefix the path with the correct root base URL in order to obtain the full resource path or URL.

###3. Get bulk list of changed accounts
Your application can choose to synchronize changed accounts for all customers since some point marked by timestamp. If you don't supply a timestamp all accounts will be returned. 
You can get bulk list of changed accounts by issuing following query:
```http
GET /accounts?sync-timestamp=237436981 HTTP/1.1
Content-Type: text/csv; charset=UTF-8
Accept-Encoding: gzip, deflate
```
You will get back `200 OK` status code and `text/csv` representation of account list. Your application is responsible to choose optimal synchronization interval and it is assumed that initial synchronization will take place during a time window when backend servers are not heavily used. To reduce response payload size we recommend use of http compression with `Accept-Encoding` header.

```http
HTTP/1.1 200 Ok
Content-Type: text/csv

account-number,effective-date,status-date,currency,status,posting-status,kind,sync-timestamp
00210102101,2016-01-01,2016-01-01,EUR,open,post-all,demand-deposit,25722121
00210102101,2016-01-01,2016-01-01,RSD,open,post-all,current-account,24732399
...

```
 In order to synchronize incrementally after initial synchronization, your application should record the highest timestamp it processed successfully and send it in next request.
 > You should expect `503 Service unavailable` if server is under heavy load and your request requires large data set.  

###4. Get available balance for specific accounts
Let's assume that a you need to get available balances for a customer that has two accounts.
You can get available balances for specific account using following query:

```http
GET /balances?kinds=available&accounts=00210102101,00310003334 HTTP/1.1
```
You will get back `200 Ok` status code and json representation with list of balances. Location header will contain URL for newly created folder.
```http
HTTP/1.1 200 Ok
Content-Type: application/json

[
  {
    "account-number": 00210102101,
    "amount": 12283.50,
    "amount-local": 12283.50,
    "currency": "RSD",
    "direction": "d",
    "balance-kind": "available",
    "calculated": "2016-02-23T15:50:00.000Z",
    "sync-timestamp": 26447476
  },
  {
    "account-number": 00310003334,
    "amount": 100,
    "amount-local": 12200.00,
    "currency": "EUR",
    "direction": "d",
    "balance-kind": "available",
    "calculated": "2016-02-23T11:25:00.000Z",
    "sync-timestamp": 26447211
  }
]

```

###5. Get bulk transactions with specific fields
Sometimes you need to synchronize latest transactions but you do not need all the fields. Thanks to support for response shaping you can specify fields to `include` or `trim` from response. For more details see [response shaping](common-getstarted.html#shaping) section of the guide.
 
You can get bulk list of transactions with specific fields accounts by issuing following query:
```http
GET /transactions?sync-timestamp=224323222&include=account-number,amount-local,book-date,direction,sync-timestamp HTTP/1.1
Content-Type: text/csv; charset=UTF-8
Accept-Encoding: gzip, deflate
```
You will get back `200 OK` status code and `text/csv` representation of transaction list having only the fields you specified.

```http
HTTP/1.1 200 Ok
Content-Type: text/csv

account-number,amount-local,direction,book-date,description,sync-timestamp
00301000102101,12000.00,d,2016-02-22,ATM Cash Withdrawal,26447479
00210000105501,340000.00,c,2016-02-22,Payment received from Asseco SEE d.o.o.,26447479
...

```
>If you do not specify fields to include or trim response will have fields that are returned by default

###6. Get bulk list of statements
Like other items, bulk list of statement headers is available for synchronization. 
You can get bulk list of statements by issuing following query:
```http
GET /statements?sync-timestamp=237436981 HTTP/1.1
Content-Type: text/csv; charset=UTF-8
Accept-Encoding: gzip, deflate
```
You will get back `200 OK` status code and `text/csv` representation of statement list.

```http
HTTP/1.1 200 Ok
Content-Type: text/csv

from-date,to-date,account-number,sequence-number,generated,document,total-credits,total-debits,currency,opening-balance,closing-balance,sync-timestamp
2016-01-01,2016-01-31,00210102101,26,2016-02-01T01:25:00,AS-0021000102101-26,1,3,EUR,20.00,180.00,26447476
2015-12-01,2015-12-31,00210102101,25,2016-01-01T01:27:00,AS-0021000102101-25,2,5,EUR,45.00,20.00,25244711
...

```
> Statement header contains a reference to printable statement `document` kept in DMS.

**Congratulations!** You have completed getting started tutorial on most common steps when working with Accounting API. To learn more look at the reference documentation for [available operations](accounting.html).
