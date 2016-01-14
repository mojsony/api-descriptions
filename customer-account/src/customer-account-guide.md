Customer Account API 
======================
Customer Account API provides access to data regarding to accounts and cards of customers.
   
Key Resources
-------------
Customer Account has two top level collection resources: accounts and cards.

Resource | Description
----------- |-----------
*accounts*  | Contains methods for getting and setting various data about accounts.
*cards*  | Contains methods for getting and setting various data about cards.


Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Customer Account API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Customer Account API with your access token against the URL root below, combined with one of the root resources.  Content Management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Customer Account | `https://api.asse.co/customer-account/v2`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /customer-account/v2/accounts/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.


###3. Get accounts list


Before You can choose an account you can get account list for authenticated user.
```
GET /accounts
```
You will get back `200 OK` status code and json representation with a list of accounts.
```json

[
  {
    "account-id":"115000000005037565",
    "iban":"RS35115000000005037565",
    "sub-account":"",
    "currency-code":"USD",
    "kind":"transactional",
    "description":"",
    "status":"active",
    "status-reason":null,
    "opening-date":"2015-10-26T00:00:00",
    "live-date":"2015-10-26T00:00:00",
    "closing-date":"0001-01-01T00:00:00",
    "first-salary-date":null,
    "related-arrangement":"",
    "contract-delivery-method":null,
    "next-payment-date":null,
    "remaining-installments":null,
    "total-installments":null,
    "delay-period":null,
    ...
    
```



###4. Get account details

For particular account id user can get account details.

```
GET accounts/{account-id}
```
You will get back `200 OK` status code and json representation with account details.
```json
{
  "account-id":"115-0000000050375-65",
  "iban":"RS35115000000005037565",
  "sub-account":"",
  "currency-code":"EUR",
  "kind":"transactional",
  "description":"",
  "status":"active",
  "status-reason":"",
  "opening-date":"2015-10-26T00:00:00",
  "live-date":"2015-10-26T00:00:00",
  "closing-date":"0001-01-01T00:00:00",
  "first-salary-date":null,
  "related-arrangement":"",
  "contract-delivery-method":null,
  "next-payment-date":null,
  "remaining-installments":null,
  "total-installments":null,
  "delay-period":null,
  "limits":{"total-count":0,
  "page-size":0,
  "page-number":0,
  "total-pages":0,"items":[]},
  "balances":{"items":[{"kind":"ledger-balance",
  "credit-debit":"debit",
  "amount":{"code":"RSD",
  "amount":26054.88},
  "value-date":"2015-12-08T00:00:00",
  "calculation-date":"2015-12-08T00:00:00"},
  {"kind":"ledger-balance",
  "credit-debit":"debit",
  "amount":{"code":"USD","amount":0.12},
  "value-date":"2015-12-08T00:00:00",
  "calculation-date":"2015-12-08T00:00:00"},
  {"kind":"ledger-balance","credit-debit":"debit"
     ...
```

###5. Get transaction list
For particular account id user can get list of transactions. 

```
GET accounts/{account-id}/transactions
```
You will get back `200 OK` status code and json representation with a list of accounts.
```json
[
  {
    "currency-code":"RSD",
    "total-entries":{"count":48,"sum":0.0},
    "total-credit-entries":{"count":1,"sum":0.0},
    "total-debit-entries":{"count":26,"sum":0.0}
   }
 ],
 
 "agregate-balances":{"items":
 [
   {
     "kind":"ledger-balance",
     "credit-debit":"debit",
     "amount":{"code":"EUR","amount":120.09},
     "value-date":"2015-12-08T16:37:36",
     "calculation-date":"2015-12-07T16:37:36"}
     ...
```
###6. Get transaction details
You can get transaction details.

```
GET accounts/{account-id}/transactions/{transaction-id}

```
You will get back `200 OK` status code and json representation with details of accounts.
```json
{
  "instruction-identification":"93200003601001",
  "transaction-identification":"93200003601001",
  "mandate-identification":"5574892911103104",
  "value-date":"2015-11-30T08:51:55",
  "acceptance-date":"2015-12-01T08:51:55",
  "creditor":{"name":"","address":{"street-name":"",
  "number":"","post-code":"","town":"","country-code":""},
  "agent":{"bic":"","clearing-id":"",
  "name":"","postal-address":{"street-name":"",
  "number":"","post-code":"","town":"","country-code":""}}},
  "debtor":{"name":"Nikola Stojanovic",
  "address":{"street-name":"ĐERĐA DOŽE 1/ 1",
  "number":"","post-code":"24430",
  ...
```


**Congratulations!** You have completed getting started tutorial on most common steps when working with Customer Account API. 
To learn more look at the reference documentation for [available operations](swagger-ui).
