---
visibility: public
---
Entitlements API Classifications
===============

Bank Services
-----

List of bank services allowed by mandates and tracked by limits.  These are groupings of more granular operations.

Literal       | Code  | Description
--------------|-------|------------
any           | 00001 | Any
transfers     | 00002 | Transfers
exchanges     | 00003 | Exchanges
mandates      | 00004 | Mandates
maintenance   | 00005 | Maintenance
balances      | 00006 | Balances
statements    | 00007 | Statements
payments      | 00008 | Payments
withdrawals   | 00009 | Withdrawals
turnover-inq  | 00010 | Turnover Inquiries
...           | ...   | ...

Limit categories
-----

List of limit categories used for limit groups


Literal       | Code  | Description
--------------|-------|------------
domestic-card-use     | 00001 | Use of payment card within a country of issue
cross-border-card-use    | 00002 | Use of payment card abroad
...           | ...   | ...



Entitlements API Enumerations
===============

Channels
-----

Channels for which mandates and limits can be set 

Literal       | Description
--------------|------------
`online`      | Online self-service eg. direct banking, digital branch, mobile, home banking
`branch`      | Branches
`call-center` | Call Center
`atm`         | ATM
`pos`         | Point of Sales (PoS)
`vpos`        | Virtual PoS 
`any`         | Any


Limit Kinds
----

Literal          | Description
-----------------|------------
transaction-limit | Limit for a single transaction
period-limit  | Limit for multiple transactions in a period od time
