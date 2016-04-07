---
visibility: public
---
Product API Classifications
===============

Card Brand
--------------

A Classification Scheme that distinguishes between Financial Transaction Card Brand based on the card type and card issuer.

Literal            | Code   | Description
-------------------|--------|----------------------------------------
`american-express` | 00001  | American Express (Amex) card brand
`dina-card`        | 00002  | Dina Card card brand
`diners`           | 00003  | Diners card brand
`maestro`          | 00004  | Maestro card brand
`master`           | 00005  | Master card brand
`visa`             | 00006  | Visa card brand
`visa-electron`    | 00007  | Visa Electron card brand

Document Type
--------------

This classification represents document types.

Literal                          | Code   | Description
---------------------------------|--------|-----------------------------------
`application`                    | 00001  | Application.
`installment-plan`               | 00002  | Installment plan.
`statement`                      | 5022   | Statement.
`employment-certificate`         | 5081   | Employment certificate.
`contract`                       | 2135   | Contract.
`employment-and-income-data`     | 5081   | Certified data of the employment and income verified by the employer
`application-checklist-creation` | CL-PA-CRE | Product application creation phase checklist.

Financing Kind
--------------

This classification identifies kinds of financing that product provides

Literal                          | Code   | Description
---------------------------------|--------|-----------------------------------
`cash`                           | 00001  | Cash.
`refinancing-other-bank-product` | 00002  | Refinancing other bank product plan.
`refinancing-inside-bank-product`| 00003  | Refinancing inside bank product.
`invoice`                        | 00004  | Invoice

Product API Enumerations
===================

Card Kinds
--------------

A Classification Scheme that distinguishes between Card Accesses according to the type of card that is used to access the Product.

Literal            | Description
-------------------|-----------------------------------------------------
`credit-card`      | Card that enables use of a line of credit offered by the issuer of the Card.
`debit-card`       | Card that allows debits to a customer's account with the card issuer when the card is used for purchases.
`gift-card`        | Card that enables use of prepaid stored-value money. Usually used as an alternative to cash for purchases within a particular store or related businesses.
`prepaid-card`     | Card that enables use of prepaid stored-value money. Usually used as an alternative to cash for purchases within a particular store or related businesses.
`charge-card`      | Charge Card
`stored-value-card`| Stored Value Card

Product Statuses
--------------

Literal                 | Description
------------------------|-----------------------------------------------------
available               | Available
no-longer-available     | No Longer Available
temporarily-unavailable | Temporarily Unavailable
coming-soon             | Coming Soon


Product Kinds
--------------

Classifies products according to its nature and scope

Literal            | Description
-------------------|-----------------------------------------------------
current-account    | Current Account
demand-deposit     | Demand Deposit
term-deposit       | Term Deposit
term-loan          | Term Loan
credit-facility    | Credit Facility
overdraft-facility | Overdraft Facility
card-access        | Card Access
electronic-access  | Electronic Access
service            | Service

Interest Rate Kinds
--------------

Classification of interest rates due to their purpose. Note that penalty interest applies to loans while early withdrawal interest applies to deposits.

Literal                   | Description
--------------------------|-----------------------------------------------------
regular-interest          | Regular Interest
penalty-interest          | Penalty Interest
early-withdrawal-interest | Early Withdrawal Interest

Calendar Basis
--------------

Day count convention used for interest calculation.

Literal       | Description
--------------|-----------------------------------------------------
30a-360       | 30a-360
30u-360       | 30u-360
30e-360       | 30e-360
30e-360-isda  | 30e-360-isda
act-act-icma  | act-act-icma
act-act-isda  | act-act-isda
act-365-fixed | act-365-fixed
act-360       | act-360
act-364       | act-364
act-365-l     | act-365-l
act-act-afb   | act-act-afb

Fee Condition Kinds
--------------

Classification of fees due to their purpose. Note that early repayment fee applies to loans while early withdrawal fee applies to deposits.

Literal              | Description
---------------------|-----------------------------------------------------
origination-fee      | Origination Fee
management-fee       | Management Fee
early-repayment-fee  | Early Repayment Fee
early-withdrawal-fee | Early Withdrawal Fee
service-fee          | Service Fee
expense              | Expense
other                | Other

Fee Condition Frequencies
--------------

Fee calculation frequency. Service fees, expenses and origination-fee are usually event-triggered.

Literal            | Description
-------------------|-----------------------------------------------------
event-triggered    | Event Triggered
monthly            | Monthly
quarterly          | Quarterly
semiyearly         | Semiyearly
yearly             | Yearly

General Condition Categories
--------------

Category which can be used for grouping conditions

Literal      | Description
-------------|-----------------------------------------------------
general      | General
repayment    | Repayment
withdrawal   | Withdrawal
termination  | Termination
collaterals  | Collaterals
servicing    | Servicing
dependencies | Dependencies
relationship | Relationship
