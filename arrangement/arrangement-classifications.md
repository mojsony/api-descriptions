Arrangement API Enumerations
===============

Arrangement Kinds
---

Enumeration that distinguishes between kinds of arrangement.  

|Literal| Description|
|---|---|
|current-account| Current Account|
|demand-deposit| Demand Deposit|
|term-deposit| Term Deposit|
|term-loan| Term Loan|
|overdraft-facility| Overdraft Facility|
|credit-facility| Credit Facility|
|credit-card-facility| Credit Card Facility|
|card-access-arrangement| Card Access Arrangement|
|electronic-access-arrangement| Electronic Access Arrangement|
|other-product-arrangement| Other Product Arrangement|

Arrangement Party Roles
---

Enumeration that distinguishes between role kinds of the party related to
the arrangement.

|Literal| Description|
|---|---|
|customer| Customer|
|authorized-person| Authorized Person|
|co-debtor| Co-debtor|
|guarantor| Guarantor|
|other| Other|

Arrangement Statuses
---

Enumeration that distinguishes between current status of the arrangement
according to the arrangement lifecycle.

|Literal| Description|
|---|---|
|accepted| Accepted, but not active yet|
|effective| Effective, active|
|suspended| Suspended, can be activated again|
|completed| Completed|
|termination-requested| Termination Requested, has limitations on transactions|
|terminated| Terminated|

Arrangement Account Role Kinds
---

The role account plays in context of the arrangements.

|Literal| Description|
|---|---|
|primary-account| Primary Account|
|settlement-account| Settlement Account|
|sub-account| Sub-account|
|other| Other|

Installment Activity Kinds
---

Kinds of one activity in Instalment Plan (one row).

|Literal| Description|
|---|---|
|disbursement| Disbursement|
|downpayment| Down payment|
|repayment| Repayment|
|interest-payment| Interest payment|
|fee-payment| Fee payment|
|cash-collateral-pledging| Cash Collateral Pledging|
|cash-collateral-release| Cash Collateral Release|

Price Variation Origin
---

The origin of the price variation

|Literal| Description|
|---|---|
|product| Product|
|bundle| Bundle|
|campaign| Campaign|
|loyalty-scheme| Loyalty Scheme|
|collective-benefit| Collective Benefit|
|relationship-benefit| Relationship Benefit|
|sales-discount| Sales Discount|

Interest Rate Kinds
---

Classification of interest rates due to their purpose.
Note that penalty interest applies to loans while early withdrawal
interest applies to deposits.

|Literal| Description|
|---|---|
|regular-interest| Regular interest|
|penalty-interest| Penalty interest|
|early-withdrawal-interest| Early withdrawal interest|

Fee Condition Kinds
---

Classification of fees due to their purpose.
Note that early repayment fee applies to loans while early withdrawal
fee applies to deposits.

|Literal| Description|
|---|---|
|origination-fee| origination-fee|
|management-fee| management-fee|
|early-repayment-fee| early-repayment-fee|
|early-withdrawal-fee| early-withdrawal-fee|
|service-fee| service-fee|
|expense| expense|
|other| other|

General Condition Categories
---

Categoty which can be used for grouping conditions.

|Literal| Description|
|---|---|
|general| General|
|repayment| Repayment|
|withdraval| Withdraval|
|termination| Termination|
|collaterals| Collaterals|
|servicing| Servicing|
|dependencies| Dependencies|
|relationship| Relationship|
