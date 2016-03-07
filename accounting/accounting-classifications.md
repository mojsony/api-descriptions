Accounting API Classifications
===============

Transaction Codes
--------------

This classification explains proprietary classification of types of transactions in analytical accounting part of specific core banking system.
> Values in a table below are just a sample **placeholder** values that will replaced with real ones upon integration with analytical accounting part of core banking system

Literal 				      | Code 	| Description
------------------------|--------|------------------------
cash-withdrawal |	CWDL	| Cash Withdrawal
cash-deposit |	CDPT	| Cash Deposit
cross-border-cash-withdrawal 	| XBCW | Cross-Border Cash Withdrawal
pos-payment-debit-card | 	POSD 	| 	Point-of-Sale (POS) Payment  - Debit Card	
pos-payment-credit-card | POSC | Credit Card Payment 
cross-border-credit-card-payment | XBCP | Cross Border Credit Card Payment
smart-card-payment |	SMRT	| Smart-Card Payment
... | ... |...


Accounting API Enumerations
===============

Account Kinds
--------------

Enumeration that distinguishes between different kinds of accounts used for tracking customer arrangements. Kind of account determines kinds of balances that make sense on an account.

Literal           | Description
------------------------|------------------------
current-account|Current Account
demand-deposit-account|Demand Deposit Account
term-deposit-account|Term Deposit Account
term-loan-account|Term Loan Account
overdraft-account|Overdraft Account
credit-facility-account|Credit Facility Account
credit-card-account|Credit Card Account
investment-account|Investment Account

Balance Kinds
--------------

Enumeration that distinguishes between kinds of possible account balances.

Literal           | Description
------------------------|------------------------
available|Available balance
current|Current balance
expected|Expected balance
blocked|Blocked balance
outstanding|Outstanding balance
advance|Advance balance
opening|Opening balance
closing|Closing balance


Transaction Kinds
--------------

Enumeration that distinguishes between accounting transactions
based on their effect on the customer accounts.

Literal           | Description
------------------------|------------------------
dep|Deposit
wdw|Withdrawal
pmt|Payment
fee|Fee
inc|Interest credit
rev|Reversal
adj|Adjustment
lnd|Loan disbursement
lnr|Loan repayment
fcx|Foreign currency exchange
aop|Account openning
acl|Account closing

Account Statuses
--------------

Enumeration that distinguishes between possible statuses of
the Customer Accounts.

Literal           | Description
------------------------|------------------------
open|Open
openning|In process of openning
closed|Closed and inactive
closing|In process of closing
archived|Archived


Transaction Statuses
--------------

This enumerated classification marks status of particular transaction.

Literal           | Description
------------------------|------------------------
p|Pending, intermediate status
b|Booked
v|Voided


Account Posting Statuses
--------------

Enumeration that distinguishes between possible posting statuses
(availabilities) of the Customer Accounts.

Literal           | Description
------------------------|------------------------
not-postable| Postings are not possible
no-further-drawings| While further drawings from customer are not possible bank is allowed to post debits to account
post-all|All transaction directions are allowed
debit-only|Only debit postings (transactions) are allowed
credit-only|Only credit postings (transactions) are allowed


Transaction Sources
--------------

This enumerated classification marks origin (source) of the transaction.
Additional details of the transaction can be found according to this value.  

Literal           | Description
------------------------|------------------------
crd|Card transaction details
pmt|Payment details
sto|Standing order details
brn|Branch transaction details
int|Internal transaction details


