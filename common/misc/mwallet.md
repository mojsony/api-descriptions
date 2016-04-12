---
visibility: public
---
<span class="icon"></span>API walkthrough for mWallet integration
======================

Integration use cases (provided by mt:s team)
--------
1.	Customer Links bank account to Wallet -> Customer will actually link their card via the mt:s web site, mWallet will pick up the customers bank account details from the CRM
2.	Customer Fund in via Bank Account -> Customer will transfer funds from their linked account to their wallet. This is based on the understanding that the Bank API will allow a request from mWallet to transfer funds from the customer account to the wallet account.
3.	Customer Fund Out via Bank Account -> Reverse of 2.
4.	Other use cases as necessary ...

> **IMPORTANT** Use cases outlined in this document reflect our current understanding of bank's needs. 
Document will be updated as new requirements are specified during gap analysis. 
This document assumes that proper authentication is established and gives examples for *happy path* scenario where everything goes as expected. Possible errors are listed in reference documentation.


### 1. Link bank account to wallet
Customer uses mt:s mWallet application to link mt:s bank account to wallet for future funding and withdrawals. 
During this process mWallet application needs to verify the following:

- mt:s customer is recognized as active bank customer
- mt:s customer owns transactional account with bank that is effective (in order and active)

#### Look for active individual customer using personal id number (JMBG)
To look for customer using JMBG send following request:
```http
GET /v1/party/parties?id-number=120596272635& HTTP/1.1
id-kind=personal-id-number
&kind=individual
&statuses=active
&trim=*
&include=parties.party-number

Host: bankapi.net
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dC...
```
If customer record that matches criteria exists in bank's system you will get back `200 OK` status code and `application/json` representation of party list with `party-number`. 
You should keep `party-number` as identification of customer in mt:s bank and use it in subsequent requests.

```http
HTTP/1.1 200 Ok
Content-Type: application/json

{
    parties: [
          {"party-number":"nodjo001"}
    ]
}

```
If customer record matching criteria does not exist in bank's system you will get https status code `404 Not found`.
> For more information visit [method reference](https://bankapi.net/docs/public/party.html#get-parties)

#### Look for current accounts owned by customer
To look for transactional accounts owned by customer send following request:
```http
GET /v1/arrangement/arrangements?customer-id=nodjo001& HTTP/1.1
kinds=current-account
&role-kinds=customer
&statuses=effective
&trim=*
&include=items.arrangement-number 

Host: bankapi.net
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dC...
```
You will get back `200 OK` status code and `application/json` representation of all effective current accounts owned by specified customer. 

```http
HTTP/1.1 200 Ok
Content-Type: application/json

{
    items: [
          {"arrangement-number":"360000128918381878"}
    ]
}

```
If specified customer does not owns at least one effective current account you will get `404 Not found`.
> For more information visit [method reference](https://bankapi.net/docs/public/arrangement.html#get-arrangements) 


### 2. Fund mWallet from linked current account
To add funds to mWallet from customer's linked current account you need to send following request:

```http
POST /v1/payment/transfers/wallet-transfers  HTTP/1.1
Host: bankapi.net
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dC...
Content-Type: application/json

{
  "kind": "wallet-transfer",
  "customer-number": "nodjo0001",
  "wallet-number": "MW008819020",
  "linked-account": "361003000091091095",
  "instructed-amount": {
    "amount": 10000,
    "code": "RSD"
  },
  "direction": "top-up"
}
```
You will get back `202 Accepted` status code and `application/json` representation of identifier for transfer. 
Location header contains URL where you can get details of accepted wallet transfer instruction. 

```http
HTTP/1.1 202 Accepted
Location: /v1/payment/transfers/6997191902819
Content-Type: application/json

"6997191902819"
```
If you do not supply well-formed and valid transfer instruction you will get `400 Bad request` status code with `application/json` representation of validation errors. 
If your supply well-formed and valid transfer instruction but it cannot be processed due to bank's business rules you will get `440 Business problem` status code with `application/json` representation of the problem details.
> For more information visit [method reference](https://bankapi.net/docs/public/payment.html#post-transfers-wallet-transfers)
 
### 3. Withdraw funds from mWallet to linked current account

To withdraw funds to mWallet from customer's linked current account you need to send following request:

```http
POST /v1/payment/transfers/wallet-transfers  HTTP/1.1
Host: bankapi.net
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dC...
Content-Type: application/json

{
  "kind": "wallet-transfer",
  "customer-number": "nodjo0001",
  "wallet-number": "MW008819020",
  "linked-account": "361003000091091095",
  "instructed-amount": {
    "amount": 5000,
    "code": "RSD"
  },
  "direction": "withdrawal"
}
```

You will get back `202 Accepted` status code and `application/json` representation of identifier for transfer.
Location header contains URL where you can get details of accepted wallet transfer instruction.

```http
HTTP/1.1 202 Accepted
Location: /v1/payment/transfers/7699191819917
Content-Type: application/json

"7699191819917"
```

If you do not supply well-formed and valid transfer instruction you will get `400 Bad request` status code with `application/json` representation of validation errors. 
If your supply well-formed and valid transfer instruction but it cannot be processed due to bank's business rules you will get `440 Business problem` status code with `application/json` representation of the problem details.
> For more information visit [method reference](https://bankapi.net/docs/public/payment.html#post-transfers-wallet-transfers)

### 4. Synchronize transactions from mt:s account
In order to synchronize wallet funding and withdrawal transactions from bank, mWallet application needs to poll for all new transactions on mt:s special purpose account since some point marked by timestamp.

You can get bulk list of transactions for `360000000000000121` mt:s account by sending following request: 
```http
GET /transactions?accounts=360000000000036021& HTTP/1.1
sync-timestamp=26447002
&trim=*
&include=transfer.transfer-id,counterparty.reference,amount-local,direction,transaction-time,sync-timestamp,description 

Host: bankapi.net
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dC...
Content-Type: text/csv; charset=UTF-8
Accept-Encoding: gzip, deflate
```

You will get back `200 OK` status code and `text/csv` representation of transaction list having only the fields you specified.

```http
HTTP/1.1 200 Ok
Content-Type: text/csv

transfer.transfer-id,counterparty.reference,amount-local,direction,transaction-time,sync-timestamp,description
6997191902819,MW008819020,10000.00,c,2016-02-23T11:25:00,26447479,Wallet funding
7699191819917,MW008819020,5000.00,d,2016-02-23T11:27:00,26447512,Wallet withdrawal

```
> For more information visit [method reference](https://bankapi.net/docs/public/account-data.html#get-transacations-sync)