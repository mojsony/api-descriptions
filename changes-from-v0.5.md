Changes from v0.5 to v1 
===============

As **v1** is the first version available to public, we took the opportunity to clean up and increase quality of APIs. With **v1** we achieved following goals:
- clarified boundaries, naming of APIs and their responsibilities
- consistent style of rest endpoints (learn once apply anywhere)
- free of implementation specifics (standard ASEE API not belonging to any particural application)
- free of customization specifics
- consistent use of string formats, enumerations and classifications
- increased generality (not tailored for specific UI need or bank customization)
- simplified endpoints (as simple as possible but no simpler)
- backward compatibility rules defined
- standardized API definition format on Swagger 2.0
- improved quality of our documentation

New features accross APIs
---------
- **Shaping**. All APIs now support response shaping thanks to shaping filer in facade pipeline and shaping parameters passed to implementations.
- **Conditional requests**. All APIs now support conditional requests with E-Tags thanks to filter.
- **Authorization**. Access to APIs endpoints is now controlled by configurable authorization rules interpreted and enforced by authorization filter.
- **Versioning**. Versioning supported in routes thanks to middleware filter
- **Client SDKs**. Thanks to Swagger 2.0 ecosystem of generators client SDKs can be generated for many platforms

Removed features
-------------
- XML representations are no longer supported
- Hypermedia links and actions are no longer supported



New APIs in v1
--------
###Entitlements API **`NEW`**
Entitlements API lets you check and enforce access entitlements with customer mandates and limits. Mandates are given per arrangement and can specify allowed services, applicable channels and any limits set for each mandate holder. Mandate model is aligned with ISO 20022.
###Device API **`NEW`**
Device API manages customer owned devices such as mobile phones and tracks state of bank issued devices such payment cards and authentication devices such as hardware tokens.
###Identity API **`NEW`**
Identity API manages online identity and credentials of users. This covers signup process, confirmations of contact points, changing and recovery of forgotten passwords and usernames. Logins from external identity providers can be linked to user profile. Hint pictures, security questions and password policy enhance user experience and security of the recovery processes. 
###Accounting API **`NEW`**
Accounting API tracks positions and transactions on customer account arrangements. Account arrangements have their accounts that track positions
affected by entries posted with transactions. Statements report changes during certain time period.
> This API is not used directly by channel applications. Its batch based interface is used to synchronize data to hub for situations where backend core system is not available or does not provide convenient and performant access to transactions.


How responsibilities of v0.5 APIs changed in v1?
------------------------------

###What happened to Party Authentication API?
- Renamed to **Authentication API**
- Identity management responsibilities moved to new Identity API
- Multi-factor responsibilities moved to Authorization API
- Token issuing endpoints compliant with OpenIDConnect standard
- Refactored endpoints

###What happened to Party Profile API?
- Renamed to **Profile API**
- Mandates moved to new Entitlements API
- Arrangements moved to Arrangement API
- Basic party information and contact preferences moved to Party API
- Images moved to Content API
- Refactored endpoints

###What happened to Customer Account API?
- Renamed to **Account Data API**
- Limit data moved to new Entitlements API
- Arrangement data moved to Arrangement API
- Account usage data moved to Profile API
- Images moved to Content API
- Refactored endpoints

###What happened to Payment Order API?
- Renamed to **Payment API**
- Banks moved to Reference API
- Now responsible for bill payments
- Now responsible for bill standing orders
- Images moved to Content API
- Refactored endpoints

###What happened to Offer Management API?
- Renamed to **Offer API**
- Terminations moved to Order API
- Now responsible for amendments
- Images moved to Content API
- Refactored endpoints

###What happened to Currency Exchange API?
- Renamed to **Exchange API**
- Refactored endpoints

###What happened to Location Data API?
- Renamed to **Location API**
- Now responsible for streets and places
- Refactored endpoints

###What happened to Content Management API?
- Renamed to **Content API**
- Refactored endpoints

###What happened to Reference Data API?
- Renamed to **Content API**
- Streets and places moved to Location API
- Now responisble for banks
- Refactored endpoints



Migration path for v0.5  use cases
-------------------------------------

While all use cases from **v0.5** are covered in **v1** shape of the APIs has changed significantly. There are few backward compatible methods and most of methods have breaking changes.
Here is the partial list of APIs ordered by requests for clarification coming from **v0.5** consumers.

###Priority 1 use cases

| Use case                        | v.05                               | v1                       | Note                |
|---------------------------------|------------------------------------|--------------------------|---------------------|
| Get OAuth2 authorization token | POST authentication/token        | POST authentication/connect/token | Proprietary definition replaced by OpenIDConnect standard |
| Initiate SMS OTP | POST authentication/challenges | POST authorization/otp/sms/send| Moved to Authorization API |
| List banks | GET payment-order/banks| GET reference/banks | Moved to Reference API |
| List countries | GET reference-data/countries | GET reference/countries | Renamed to Reference API |
| List purpose codes | GET payment-order/purpose-codes | GET payment/purpose-codes | Renamed to Payment API |
| Get data on specific account | GET customer-account/accounts/{param} | GET account-data/accounts/{param} | Renamed to Account Data API. Kept only basic account information | 
| ... | ...  | GET arrangement/arrangements/{param} | Arrangement data moved arrangement API |
| ... | ...  | GET entitlements/limit-balances/account-limits | Moved limits to Entitlements API |
| ... | ...  | GET profile/arrangement-profile/param | Moved arrangement usage tracking data to Profile API |
| Get account transactions | GET customer-account/accounts/{param}/transactions | GET account-data/transactions | Moved to top level resource filtered by account |
| ... | ...  | GET account-data/transactions/search | Moved text, geospatial and PFM category search to separate endpoint |
| List customer's applications  | GET offer-management/customer-product-application | GET offer/applications | Renamed to Offer API |
| ... | ...  | GET offer/drafts | Moved multi-step application entry  support to separate endpoint |
| ??? | GET authentication/users/phone/validation-tokens | N/A | **DEPRECATED** |
| ???| GET authentication/users/otp/{param} | N/A | **DEPRECATED** |
| Verify SMS OTP | POST authentication/users/msisdn/validation-tokens/verify | POST authorization/otp/sms/verify | Moved to Authorization API |
| Register new user | POST authentication/users | POST identity/users | Moved to Identity API |
| Get current account offer text | GET offer-management/deposit-indicative-offers | GET offer/calculations/deposit-offer-text | Renamed to Offer API. Generalized for deposits |
| Get deposit offer text | GET offer-management/deposit-indicative-offers | ... | ... |
| Initiate current account application | POST offer-management/initiate-current-account-application | POST offer/applications/deposit-openings | Generalized for deposits |
| Get specific deposit application | GET offer-management/deposit-application/{param} | GET offer/applications/{param} | Moved to one collection resource with polymorphic models |
| Get transactions for card | GET customer-account/cards/{param}/transactions | GET account-data/transactions | Moved to root collection resource with card-number as a one of the filters |
| Get cards for customer | GET customer-account/{param}/cards | GET arrangement/arrangements | Moved to arrangement with card-access kind as one of the filters |
| Get data on specific card | GET customer-account/cards/{param} | GET arrangement/arrangements/{param} | Basic card data moved to Arrangement API |
| ...| ... | GET device/issued-devices/{param} | Physical plastic card related data such as expriation, image, capabilities moved to Device API |
| Get exchange rates | GET currency-exchange/rates | GET exchange/rates | Renamed to Exchange API |
| Request currency exchange offer | POST currency-exchange/offer | POST exchange/offers | Renamed endpoint |
| Initiate new currency exchange order | POST currency-exchange/transactions | POST exchange/orders | Renamed endpoint |
| List bank's ATMs | GET location-data/facilities/atms | GET location/facilities | Generialized for all physical presence points  |
| List bank's branches | GET location-data/facilities/branches | .. | .. |
| Get data on specific ATM | GET location-data/facilities/atms/{param} | GET location/facilities/{param} | Generalized for all physical presence points |
| Get data on specific branch | GET location-data/facilities/branches/{param} | ... | ...
| Validate balance transfer | POST payment-order/balance-transfers/validate | POST payment/transfers/balance-transfers/validate | Renamed to Payment API. Renamed endpoint |
| Initiate balance transfer | POST payment-order/balance-transfers | POST payment/transfers/balance-transfers/ | Renamed endpoint |
| List customer's accounts | GET customer-account/accounts | GET arrangement/arrangements | Moved to Arrangemet API with customer as one of the filters |
| Get miscellaneous customer data | GET party-profile/individual-profiles/{param} | GET party/parties/{param} | Removed redundancy. Basic information on customer only in Party API |
| ... | ... | GET profile/individuals | Facts and measures on individuals kept in Profile API |
| Set preferred language for customer | POST party-data/individuals/update-profile-language | PATCH parties/party-number/contact-preference | Generalized for all contact preferences |
| Get mailbox messages | GET correspondence/communications | GET me/messages | Separated endpoint for mailbox |
| Mark message as read | PUT correspondence/communications | POST me/messages/{param}/mark-as-red | Refactored to CQRS style oriented endpoint |
| List customer's templates | GET payment-order/personal-templates | GET payment/drafts | Generalized for both templates and drafts |
| Get specific template | GET payment-order/personal-templates/{param} | GET payment/drafts/{param} | ... |
| Modify specific template | PUT payment-order/personal-templates/{param} | PUT payment/drafts/{param} | ... |
| Delete specific template | DELETE payment-order/personal-templates/{param} | DELETE payment/drafts/{param} | ... |
| List customer's personal beneficiaries | GET payment-order/personal-beneficiaries| GET payment/personal-beneficiaries | Renamed to Payment API |
| Get specific personal beneficiary | GET payment-order/personal-beneficiaries/{param} | GET payment/personal-beneficiaries/{param} | ... |
| Modify specific personal beneficiary | PUT payment-order/personal-beneficiaries/{param} | PUT payment/personal-beneficiaries/{param} | ... |
| Delete specific personal beneficiary | DELETE payment-order/personal-beneficiaries/{param} | DELETE payment/personal-beneficiaries/{param} | ... |
| List public beneficiaries | GET payment-order/public-beneficiaries | GET payment/public-beneficiaries | ... |
| Validate credit transfer | POST payment-order/credit-transfers/validate | POST payment/transfers/credit-transfers/validate | ... |
| Initiate credit transfer | POST payment-order/credit-transfers | POST payment/transfers/credit-transfers/ | ... |
| Validate cross-border transfer | POST payment-order/crossborder-transfers/validate | POST payment/transfers/cross-border-transfers/validate | ... |
| Initiate cross-border transfer | POST payment-order/crossborder-transfers | POST payment/transfers/cross-border-transfers/ | ... |
| Calculate service fee | POST offer-management/calculate-service-fee | GET offer/calculations/service-fee | Renamed to Offer API. Renamed endpoint |

###Priority 2 use cases

| Use case                        | v.05                               | v1                       | Note                |
|---------------------------------|------------------------------------|--------------------------|---------------------|
| Get loan repayment plan | GET customer-account/accounts/{param}/installment-plan | GET arrangement/arrangements/{param}/installment-plan | Moved to Arrangement API  |
| Upload file | POST Content-management/upload-file/ | POST content/{repo}/folders/{param} | Renamed endpoint and refactored to use folders |
| Register device | N/A | POST device/owned-devices | New Device API handles both owned and issued devices |
| Register device for push notifications | N/A | PUT /owned-devices/{param}/push-notification-handle | ... |
| Unregister device | N/A | POST device/owned-devices/{param}/unregister | ... |
| Block device | N/A | POST device/owned-devices/{param}/block | ... |
