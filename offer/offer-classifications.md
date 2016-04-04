Offer API Classifications
========

Cancelation Reasons
--------------

This classification represents customer's reason to cancel active application.

Literal                 | Code  | Description
------------------------|-------|------------------------
`CompetitorWon`         | 0     | Competitor Won.
`CustomerSecondThought` | 1     | Customer Second Thought
`Other`                 | 9     | Other

Document Types
--------------

Specific purpose of document.

Literal                                     | Code  | Description
--------------------------------------------|-------|------------------------
`Application`                               | 0     | Request for specific bank product.
`Contract`                                  | 1     | Contract with term and conditions of using bank product.
`Instruction`                               | 2     | Instruction
`Statement`                                 | 3     | Statement
`InstallmentPlan`                           | 4     | Installment plan.
`EmploymentCerificate`                      | 5     | Employment certificate.
`BusinessRegisterExcerpt`                   | 6     | Business register excerpt.
`TransactionCertificate`                    | 7     | Transaction certificate.
`ProductApplicationAcceptancePhaseChecklist`| 8     | Application acceptance phase checklist
`ProductApplicationCreationPhaseChecklist`  | 9     |  Application creation phase checklist.
`ProductApplicationApprovalPhaseChecklist`  | 10    |  Application approval phase checklist
`ProductApplicationActivationPhaseChecklist`| 11    |  Application activation phase checklist
`WithdrawConscentForCreditBureauReport`     | 12    | Withdraw conscent for credit bureau report

Installment Activity Kinds
--------------

This classification represents status of request.

Literal                 | Code  | Description
------------------------|-------|------------------------
`FeeRepayment`          | 2     | Fee repayment.
`InterestRepayment`     | 1     | Interest repayment.
`PrincipalRepayment`    | 0     | Principal repayment.

Loan Types
-----

This classification represents loan types.

Literal           | Code  | Description
------------------|-------|------------------------
Loan              |0      | Loan
CreditCard        |1      | Credit card
Guarantee         |2      | Guarantee
LetterOfCredit    |3      | Letter of credit
Overdraft         |4      | Overdraft

Employment Position Categories
-----

This classification represents employment positions categories

Literal                   | Code  | Description
--------------------------|-------|------------------------
Worker                    |0      | Worker
Farmer                    |1      | Farmer
LowManager                |2      | Low manager
MiddleManager             |3      | Middle manager
HighManager               |4      | High manager
ExecutiveManager          |5      | Executive manager
OfficeEmployee            |6      | Office employee
GovernmentEmployee        |7      | Government employee
TeachingEmployee          |8      | Teaching employee
MedicalEmployee           |9      | Medical employee

Education Levels
-----

Literal            | Description
-------------------|------------------------
NoFormalEducation  |0   | No school
Primary            |1   | Elementary school
LowerSecondary     |2   | III degree
UpperSecondary     |3   | High school
BachelorDegree     |4   | College
MasterDegree       |5   | Master degree
Doctorate          |6   | Doctorate
Bachelor           |7   | Bachelor
PrefeNotToAnswer   |8   | Prefer not to answer

Employment Types
-----

Literal           | Code  | Description
------------------|-------|-----------------
Permanent         |0      | Permanent
Temporary         |1      | Temporary
Pensioner         |2      | Pensioner
SelfEmployed      |3      | Self employed
Unemployed        |4      | Unemployed

Employer Types
-----

Literal                         | Code  | Description
--------------------------------|-------|-----------------
BudgetaryAndPublic              |0      | Budgetary and public
EnterpreneurEmployerType        |1      | Enterpreneur employer type
JoinStockCompanyAD              |2      | Join stock company AD
LLC                             |3      | LLC
OtherEmployerType               |4      | Other employer type

Offer API Enumerations
===============

Income Sources
------

Literal           | Description
------------------|------------------------
salary            | Salary
pension           | Pension
contract          | Contract
rent              | Rent
alimony           | Alimony
royalty           | Royalty
board-membership  | Board Membership
separation-allowance | Separation Allowance

Application Statuses
------

Literal              | Description
---------------------|------------------------
accepted | Accepted
active   | Active
rejected | Rejected
canceled | Canceled
approved | Approved

Application Kinds
-----

Literal                 | Description
------------------------|------------------------
deposit-opening         | Deposit Opening
current-account-opening | Current Account Opening
loan-origination        | Loan Origination

Deposit Opening Kinds
----

Literal               | Description
----------------------|------------------------
term-deposit | Term Deposit
sight-deposit | Sight Deposit
current-account | Current Account

Signing Options
-------

Indicates how and where customer chose to sign agreement documents

Literal           | Description
------------------|------------------------
branch | In the branch
courier | Courier
online | Online

Loan Origination Kinds
-----

Literal           | Description
------------------|------------------------
term-loan | Term Loan
overdraft | Overdraft
credit-card | Credit Card
mortgage | Mortgage

Home Ownerships
-----

Literal           | Description
------------------|------------------------
owns | Owns
rents | Rents
lives-with-relatives | Lives With Relatives
not-disclosed | Not Disclosed

Car Ownerships
-----

Literal           | Description
------------------|------------------------
owns | Owns
does-not-own | Does Not Own
not-disclosed | Not Disclosed
