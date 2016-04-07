REST API Guide and Reference
====================================
Asseco REST APIs represent collection endpoints that serve the needs of banking applications. While each API exposes specific functionality, technical concerns of API usage have been designed in a consistent manner to enable easier integration into channel applications. This section describes concerns and usage patterns that are common to all APIs.

> Read [Asseco REST API Reference License](common-license.html) before using the materials

@@@ public
##/location
###&#xE9B2
Get location and availability of branches and ATMs
[EXPLORE](location.html)
[LEARN](location-getstarted.html)

@@@

@@@ public
##/identity
###&#xEA0E
Enroll users and manage their online identity 
[EXPLORE](identity.html)
[LEARN](identity-getstarted.html)

@@@

@@@ public
##/content
###&#xE831
Store and access documents and other digital content 
[EXPLORE](content.html)
[LEARN](content-getstarted.html)

@@@

@@@ public
##/correspondence
###&#xE81A
Format and deliver customer correspondence
[EXPLORE](correspondence.html)
[LEARN](correspondence-getstarted.html)

@@@

@@@ public
##/campaign
###&#xEAD4
Target customers and prospects with offers
[EXPLORE](campaign.html)
[LEARN](campaign-getstarted.html)

@@@

@@@ public
##/authentication
###&#xEA20
Authenticate users with different credentials 
[EXPLORE](authentication.html)
[LEARN](authentication-getstarted.html)

@@@

@@@ public
##/entitlements
###&#xEA0A
Track customer access rights and usage limits
[EXPLORE](entitlements.html)
[LEARN](entitlements-getstarted.html)

@@@

@@@ public
##/authorization
###&#xEA1F
Verify sensitive actions
[EXPLORE](authorization.html)
[LEARN](authorization-getstarted.html)

@@@

@@@ internal
##/dialog
###&#xEA9F
Optimize your interaction with customers
[EXPLORE](dialog.html)
[LEARN](dialog-getstarted.html)

@@@

@@@ public
##/account-data
###&#xE886
Access and tag customer accounts and transactions
[EXPLORE](account-data.html)
[LEARN](account-data-getstarted.html)

@@@

@@@ public
##/arrangement
###&#xE869
Define and manage terms of customer agreements
[EXPLORE](arrangement.html)
[LEARN](arrangement-getstarted.html)

@@@

@@@ public
##/profile
###&#xEA1A
Get quick facts and measures from customer profiles
[EXPLORE](profile.html)
[LEARN](profile-getstarted.html)

@@@


@@@ public
##/offer
###&#xE8A7
Create and manage offers given to customers
[EXPLORE](offer.html)
[LEARN](offer-getstarted.html)

@@@

@@@ internal
##/case
###&#xEAF4
Capture and resolve issues raised by customers
[EXPLORE](case.html)
[LEARN](case-getstarted.html)

@@@

@@@ public
##/product
###&#xE8D6
Access catalogue of bank’s products and services
[EXPLORE](product.html)
[LEARN](product-getstarted.html)

@@@

@@@ public
##/party
###&#xEA06
Access data on people and organizations of interest to bank
[EXPLORE](party.html)
[LEARN](party-getstarted.html)

@@@

@@@ public
##/reference
###&#xE84C
Access reference data managed by bank
[EXPLORE](reference.html)
[LEARN](reference-getstarted.html)

@@@

@@@ public
##/payment
###&#xE8AC
Initiate and track customer payments 
[EXPLORE](payment.html)
[LEARN](payment-getstarted.html)

@@@

@@@ internal
##/order
###&#xE895
Service and execute orders received from customers
[EXPLORE](order.html)
[LEARN](order-getstarted.html)

@@@

@@@ internal
##/survey
###&#xE828
Collect feedback from customers
[EXPLORE](survey.html)
[LEARN](survey-getstarted.html)

@@@

@@@ public
##/device
###&#xE9CE
Manage customer owned and bank issued devices
[EXPLORE](devicen.html)
[LEARN](device-getstarted.html)

@@@

@@@ public
##/exchange
###&#xE8B8
Track rates, buy and sell foreign currency
[EXPLORE](exchange.html)
[LEARN](exchange-getstarted.html)

@@@

@@@ internal
##/bill-presentment
###&#xE99D
Present and manage monthly bills of customers
[EXPLORE](bill-presentment.html)
[LEARN](bill-presentment-getstarted.html)
@@@

@@@ internal
##/personal-finance
###&#xE88A
Manage personal finances of customers
[EXPLORE](personal-finance.html)
[LEARN](personal-finance-getstarted.html)
@@@

@@@ internal
##/fraud
###&#xEB2B
Manage personal finances of customers
[EXPLORE](fraud.html)
[LEARN](fraud-getstarted.html)
@@@

@@@ internal
##/customer-event
###&#xEAC3
Manage personal finances of customers
[EXPLORE](customer-event.html)
[LEARN](customer-event-getstarted.html)
@@@

@@@ public
##/accounting
###&#xE862
Track positions on analytical accounts
[EXPLORE](accounting.html)
[LEARN](accounting-getstarted.html)
@@@

###Learn how to deal with common API challenges
- [How we handle authentication](common-getstarted.html#authentication)
- [How we version our APIs](common-getstarted.html#versioning) 
- [How we validate requests](common-getstarted.html#validation  ) 
- [How we report errors](common-getstarted.html#error-handling) 
- [How we trim and expand responses](common-getstarted.html#shaping) 
- [How we page responses with long lists](common-getstarted.html#paging) 
- [How we sort items in response](common-getstarted.html#sorting) 
- [How we filtering of list items](common-getstarted.html#filtering) 
- [How we search for matching items](common-getstarted.html#searching) 
- [How we handle multiple representations](common-getstarted.html#content-negotiation) 
- [How we handle work that may take long to complete](common-getstarted.html#asynchronous-jobs) 
- [How we publish events](common-getstarted.html#events) 
- [How we enumerate allowed values](common-getstarted.html#enumerations-and-classifications)


[authentication]: common-getstarted.html#authentication
[versioning]: common-getstarted.html#versioning 
[validation]: common-getstarted.html#validation   
[error-handling]: common-getstarted.html#error-handling 
[response shaping]: common-getstarted.html#response-shaping 
[paging]: common-getstarted.html#paging 
[sorting]: common-getstarted.html#sorting 
[filtering]: common-getstarted.html#filtering 
[searching]: common-getstarted.html#searching 
[content-negotiation]: common-getstarted.html#content-negotiation 
[asynchronous-jobs]: common-getstarted.html#asynchronous-jobs 
[events]: common-getstarted.html#events 
[enumerations]: common-getstarted.html#enumerations
[classifications]: common-getstarted.html#classifications

