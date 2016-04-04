Offer API Classifications
========

cancelation-reasons
--------------

This classification represents customer's reason to cancel active application.

Literal                  | Code  | Description
-------------------------|-------|------------------------
`competitor-won`         | 0     | Competitor Won
`customer-second-thought`| 1     | Customer Second Thought
`other`                  | 2     | Other

document-kinds
--------------

Specific purpose of document.

Literal                                     | Code  | Description
--------------------------------------------|-------|------------------------
`application`                               | 0     | Request for specific bank product
`contract`                                  | 1     | Contract with term and conditions of using bank product
`instruction`                               | 2     | Instruction
`statement`                                 | 3     | Statement
`installment-plan`                          | 4     | Installment plan
`employment-cerificate`                     | 5     | Employment certificate
`business-register-excerpt`                 | 6     | Business register excerpt
`transaction-certificate`                   | 7     | Transaction certificate
`product-application-acceptance-phase checklist`| 8     | Application acceptance phase checklist
`product-application-creation-phase-checklist`  | 9     | Application creation phase checklist
`product-application-approval-phase-checklist`  | 10    | Application approval phase checklist
`product-application-activation-phase-checklist`| 11    | Application activation phase checklist
`withdraw-conscent-for-credit-bureau-report`    | 12    | Withdraw conscent for credit bureau report

installment-activity-kinds
--------------

This classification represents status of request.

Literal                 | Code  | Description
------------------------|-------|------------------------
`fee-repayment`         | 0     | Fee repayment
`interest-repayment`    | 1     | Interest repayment
`principal-repayment`   | 2     | Principal repayment

loan-kinds
-----

This classification represents loan types.

Literal           | Code  | Description
------------------|-------|------------------------
`loan`            |0      | Loan
`credit-card`     |1      | Credit card
`guarantee`       |2      | Guarantee
`letter-of-credit`|3      | Letter of credit
`overdraft`       |4      | Overdraft

employment-position-categories
-----

This classification represents employment positions categories

Literal                   | Code  | Description
--------------------------|-------|------------------------
`worker`                  |0      | Worker
`farmer`                  |1      | Farmer
`low-manager`             |2      | Low manager
`middle-manager`          |3      | Middle manager
`high-manager`            |4      | High manager
`executive-manager`       |5      | Executive manager
`office-employee`         |6      | Office employee
`government-employee`     |7      | Government employee
`teaching-employee`       |8      | Teaching employee
`medical-employee`        |9      | Medical employee

education-levels
-----

Literal                | Code  | Description
-----------------------|-------|----------------
`no-formal-education`  |0      | No school
`primary`              |1      | Elementary school
`lower-secondary`      |2      | III degree
`upper-secondary`      |3      | High school
`bachelor-degree`      |4      | College
`master-degree`        |5      | Master degree
`doctorate`            |6      | Doctorate
`bachelor`             |7      | Bachelor
`prefer-not-to-answer` |8      | Prefer not to answer

employment-kinds
-----

Literal           | Code  | Description
------------------|-------|-----------------
`permanent`       |0      | Permanent
`temporary`       |1      | Temporary
`pensioner`       |2      | Pensioner
`selfEmployed`    |3      | Self employed
`unemployed`      |4      | Unemployed

employer-kinds
-----

Literal                         | Code  | Description
--------------------------------|-------|-----------------
`budgetary-and-public`          |0      | Budgetary and public
`enterpreneur-employer-kind`    |1      | Enterpreneur employer kind
`join-stock-company`            |2      | Join stock company
`limeted-liability-company`     |3      | Limited liability company
`other-employer-kind`           |4      | Other employer kind

Offer API Enumerations
===============

income-sources
------

Literal           | Description
------------------|------------------------
`salary`            | Salary
`pension`           | Pension
`contract`          | Contract
`rent`              | Rent
`alimony`           | Alimony
`royalty`           | Royalty
`board-membership`  | Board Membership
`separation-allowance` | Separation Allowance

application-statuses
------

Literal              | Description
---------------------|------------------------
`accepted` | Accepted
`active`   | Active
`rejected` | Rejected
`canceled` | Canceled
`approved` | Approved

application-kinds
-----

Literal                 | Description
------------------------|------------------------
`deposit-opening`         | Deposit Opening
`current-account-opening` | Current Account Opening
`loan-origination`        | Loan Origination

deposit-opening-kinds
----

Literal               | Description
----------------------|------------------------
`term-deposit`        | Term Deposit
`sight-deposit`       | Sight Deposit
`current-account`     | Current Account

signing-options
-------

Indicates how and where customer chose to sign agreement documents

Literal           | Description
------------------|------------------------
`branch`          | In the branch
`courier`         | Courier
`online`          | Online

loan-origination-kinds
-----

Literal           | Description
------------------|------------------------
`term-loan`       | Term Loan
`overdraft`       | Overdraft
`credit-card`     | Credit Card
`mortgage`        | Mortgage

home-ownerships
-----

Literal           | Description
------------------|------------------------
`owns`            | Owns
`rents`           | Rents
`lives-with-relatives` | Lives With Relatives
`not-disclosed`   | Not Disclosed

car-ownerships
-----

Literal           | Description
------------------|------------------------
`owns`            | Owns
`does-not-own`    | Does Not Own
`not-disclosed`   | Not Disclosed
