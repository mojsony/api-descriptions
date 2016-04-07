---
visibility: public
---
Payment API Classifications
===============

Filing Purpose
--------------
This classification explains intended use of document in business context.
Commonly used filing purposes are document, customer-picture

Literal 				   | Code  | Description
---------------------------|-------|------------------------
`agreement`				   | 00001 | Agreement document
`mandate`				   | 00002 | Mandate document
`customer-picture`	       | 00003 | Profile picture for customer
`account-picture`		   | 00004 | Profile picture for account
`payment-order`		       | 00005 | Payment order document
`offer`					   | 00006 | Offer document

Countries
------------
This clasification contains countries from which banks or beneficiaries are from.

Literal         | Code  | Description
----------------|-------|------------
`UK`            | 00001 | United Kingdom
`USA`           | 00002 | United States of America
`EU`            | 00003 | European Union

Currencies
--------------
This classification contains codes for currencies. For example for Eoropean currency Euro € has code EUR.

Literal 				   | Code  | Description
---------------------------|-------|------------------------
`EUR`	    			   | 00001 | European Dollar
`USD`				       | 00002 | American Dollar
`CHF`	                   | 00003 | Switzerland Franc
`JPY`		               | 00004 | Japanese Yen
`AED`		               | 00005 | Emirati Dihram
`RSD`					   | 00006 | Serbian Dinar

Categories
--------------
This classification contains PFM codebook.

Literal 				   | Code  | Description
-------------------|-------|------------------------

Purpose Codes
--------------
This classification contains purpose codes for transfers.

Literal 				   | Code  | Description
---------------------------|-------|------------------------

Payment API Enumerations
=========

Payout Methods
-----

Literal 				   | Description
-------------------|------------------------
cash | Cash
cheque | Cheque

Transfer Statuses
-----

Literal 				   | Description
-------------------|------------------------
pending| Pending
scheduled| Scheduled
executed| Executed (final status)
rejected| Rejected (final status)
canceled| Canceled (final status)

Income Statuses
-----

Literal 				   | Description
-------------------|------------------------
pending| Pending
executed| Executed (final status)
in-process| In-Process

Incoming Cross Border Transfer Statuses
-----

Literal 				   | Description
-------------------|------------------------
pending| Pending
executed| Executed (final status)

Account Kinds
-----

Literal 				   | Description
-------------------|------------------------
current-account|Current Account
demand-deposit-account|Demand-Deposit Account
term-deposit-account|Term-Deposit Account
term-loan-account|Term-Loan Account
overdraft-account|Overdraft Account
credit-facility-account|Credit-Facility Account
credit-card-account|Credit-Card Account
investment-account|Investment Account

Party Kinds
-----

Literal 				   | Description
-------------------|------------------------
facebook|Facebook
google|Google
twitter|Twitter
msisdn|MSISDN (Mobile Phone)
email|Email

P2P Party Kinds
-----

Literal 				   | Description
-------------------|------------------------
facebook|Facebook
msisdn|MSISDN (Mobile Phone)
email|Email

Content Types
----

Literal 				   | Description
-------------------|------------------------
image/png| PNG image
image/jpg| JPG image
image/tiff| TIFF image
application/pdf| PDF document
application/msword| Microsoft Word Document
application/vnd.ms-excel| Microsoft Excel Document

Transfer Kinds
-----

Literal 				   | Description
-------------------|------------------------
balance-transfer|Balance Transfer
credit-transfer|Credit Transfer
cross-border-transfer|Cross-Border Transfer
nonresident-transfer|Non-Resident Transfer
p2p-transfer|P2P transfer
topup|Topup
bill-payment|Bill Payment

Transfer Directions
-----

Literal 				   | Description
-------------------|------------------------
inpayment| Inpayment
outpayment| Outpayment
internal| Internal

Transfer Urgencies
-----

Literal 				   | Description
-------------------|------------------------
ACH| Automated Clearing House
RTGS| Real Time Gross Settlement

Charged Parties
-----

Literal 				   | Description
-------------------|------------------------
ordering-customer| Ordering Customer
shared| Shared - both of the parties are charged for the transaction
beneficiary| Beneficiary

Collection Methods
----

Literal 				   | Description
-------------------|------------------------
internal | Internal
external | External
atm | ATM
