---
visibility: public
---
Entitlements API Classifications
===============

Bank Services
-----

List of bank services allowed by the mandates

Literal       | Code  | Description
--------------|-------|------------
any           | 00001 | Any
transfers     | 00002 | Transfers
exchanges     | 00003 | Exchanges
mandates      | 00004 | Mandates
maintenance   | 00005 | Maintenance
balances      | 00006 | Balances
statements    | 00007 | Statements
payment       | 00008 | Payment
withdrawal    | 00009 | Withdrawal
turnover-inq  | 00010 | Turnover Inquiry
...           | ...   | ...

[any, transfer, payment, exchange, withdrawal, mandate, maintenance, balance-inquiry, turnover-inquiry]

Entitlements API Enumerations
===============

Channels
-----

Channels for which mandates can be inquired

Literal       | Description
--------------|------------
`online`      | Online
`branch`      | Branch
`call-center` | Call Center
`atm`         | ATM
`pos`         | POS
`vpos`        | VPOS
`any`         | Any

Mandate Services
-----

List of Bank Services allowed by the mandate. These are groupings of more granular operations

Literal          | Description
-----------------|------------
any	             |	Any Service
transfer	       |	Transfer
payment	         |	Payment
exchange	       |	Exchange
withdrawal	     |	Withdrawal
mandate	         |	Mandate
maintenance	     |	Maintenance
balance-inquiry	 |	Balance Inquiry
turnover-inquiry |	Turnover Inquiry

Limit Kinds
----

Literal          | Description
-----------------|------------
amount-in-period | Amount of transactions in period
count-in-period  | Count of transactions in period
