---
visibility: public
---
Exchange API Classifications
===============

Exchange List Kind
---------

The classification lists different kinds of exchange rate lists according to use intended by list publisher.

Literal 				           | Code  | Description
---------------------------|-------|------------------------------------------------
cb-cash                    | 00001 | Central bank exchange rates for cash
cb-forex                   | 00002 | Central bank exchange rate for foreign exchange
cash                       | 00003 | Exchange rates for cash
forex                      | 00004 | Exchange rates for foreign exchange
bank-employees             | 00005 | Exchange rates for bank employees
vip-clients                | 00006 | Exchange rates for VIP clients
loan-disbursement          | 00007 | Exchange rates for loan disbursement
loan-repayment             | 00008 | Exchange rates for loan repayment.
loan-repayment             | 00009 | Exchange rates for loan repayment.

Exchange API Enumerations
===============

Order Statuses
---------

Enumeration for possible statuses of the orders.

Literal 				           | Description
---------------------------|------------------------------------------------
executed | Executed (final status)
pending | Pending
rejected | Rejected (final status)

Exchange Directions
---------

Enumeration that distinguishes between possible directions of the Exchange Transaction.

Literal 				           | Description
---------------------------|------------------------------------------------
purchase | Currency purchasing transaction
sell | Currency selling transaction
