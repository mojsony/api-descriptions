   
Classifications
===============


Search Category
-------------- 
Defines category of search parameter.

Literal 			| Code	| Description
--------------------|-------|------------------------
`phone`				| 00001	| Phone
`mobile`			| 00002	| Mobile Phone
`email`				| 00003	| E-mail Address
`postal-address`	| 00004	| Postal Address
`facebook-account`	| 00005	| Facebook Account
`customer-number`	| 00006	| Customer Number
`pin`				| 00007	| Personal Identification Number



Arrangement Category 
--------------
Identifies the type associated with an <Arrangement>. This type may be hierarchical.

Literal 				    | Code 	| Description
----------------------------|-------|------------------------
`bank-transit-account`		| 00001 | Bank Transit Account
`cash-drawer`				| 00002 | Cash Drawer
`local-currency-card`		| 00003 | Local Currency Card
`deposit-card`				| 00004 | Deposit Card
`dedicated-account`			| 00005 | Dedicated Account
`non-resident-account`		| 00006 | Non-resident Account
`deposit-account`			| 00007 | Deposit Account


Arrangement Lifecycle Status 
--------------
Identifies the lifecycle status associated of the arrangement

Literal 				    | Code 	| Description
----------------------------|-------|------------------------
`canceled`					| 00001 | Identifies an <Arrangement> which did not become effective due to lack of agreement on the ultimate conditions or due to intervening circumstances.  For example, a Service Arrangement was offered and accepted by both Involved Parties but was never put into effect due to unforeseen events and was therefore cancelled. A Cancelled Arrangement differs from a Terminated Arrangement in that the latter was at one time an Effective Arrangement and there may be different penalties associated with the two
`completed`					| 00002 | Identifies an <Arrangement> in which the obligations have been fully discharged by the terms of the contract.     For example, a Term Loan Arrangement which has been fully repaid having met all the conditions attached to that Arrangement.
`suspended`					| 00003 | Identifies an <Arrangement> that has been temporarily put on hold until further notice.
`accepted`					| 00004 | Identifies an <Arrangement> that has completed any required negotiation and is officially agreed upon.  For example, a Loan Arrangement for which documentation has been closed and signed, a purchase order for a quantity of stock.
`offered`					| 00005 | Identifies an <Arrangement> whose condition values have been determined and a binding offer has been submitted to a potential counter-party.  For example, a <Customer> is quoted an interest rate of 7.5% on a Deposit Arrangement.
`requested`					| 00006 | Identifies an <Arrangement> which has been solicited from an <Involved Party>. Normally the buyer initiates the request for an Arrangement from the seller under this Life Cycle Status.  For example, a <Customer> requests interest rate conditions on a Deposit Arrangement.
`termination-requested`		| 00007 | Termination Requested
`terminated`				| 00008 | Identifies an <Arrangement> in which the obligations have not been fully met within the period of the Arrangement and in which one party to the Arrangement has ended the Arrangement prematurely.  For example, a bank card cancelled by the modeled organization due to slow payment.
`proposed`					| 00009 | Identifies an <Arrangement> whose condition values have been generally determined and discussed, but a binding offer has not yet been made.  Normally the seller initiates the proposal under this Life Cycle Status.
`effective`					| 00010 | Identifies an <Arrangement> which is currently active and operating under the specified terms and conditions.  For example, an active contract.
`rejected`					| 00011 | Identifies an <Arrangement> that was rejected by modeled organization.
`incomplete`				| 00012 | Identifies an <Arrangement> in which the obligations have not been fully discharged by the terms of the contract.


Record Status
--------------
Gets or sets the created, updated, deleted record status.

Literal 		| Code 	| Description
----------------|-------|------------------------
`created`		| 00001 | Created record status
`updated`		| 00002 | Updated record status
`deleted`		| 00003 | Deleted record status


Contact Address Category
--------------
Category of the contact address of the individual customer.

Literal						| Code 	| Description
----------------------------|-------|------------------------
`postal-address`			| 00001 | Postal address
`telecommunication-number`	| 00002	| Telecommunication number
`electronic-address`		| 00003	| Electronic address


Category of Individuals
-------------- 
Defines category of individual customer, based on its residential status or age or some other differentiation that bank needs.

Literal 					| Code	| Description
----------------------------|-------|------------------------
`resident-individuals`		| 00001	| Resident Individuals
`non-resident-individuals`	| 00002	| Non-Resident Individuals
`minors`					| 00003	| Minors



Customer Lyfecycle Status
-------------- 
Identifies the state of a Customer within a lifecycle model.

Literal					| Code 	| Description
------------------------|-------|------------------------
`rejected`				| 00001	| Identifies a Customer Life Cycle Status in which the object <Involved Party> has sought to initiate an active relationship with the subject Involved Party (the seller of a product or service), but the seller has refused to establish the active relationship.
`declined`				| 00002	| Identifies a Customer Lifecycle State in which the subject <Involved Party> has been contacted by the object <Involved Party> (the seller of a product or service) in order to establish an active Customer Relationship, but the Prospective <Customer> has rejected the offer and has opted not to establish an active relationship.
`dormant`				| 00003	| Identifies a Customer Lifecycle Status in which the <Involved Party> has previously accepted and acquired the goods or used the services offered by the modeled organization, but has not acquired goods or used services for a specified period of time.
`potential`				| 00004	| Identifies a Customer Life Cycle State in which the 'subject' <Involved Party> (the <Customer>) has been identified as a possible participant in an active customer relationship with the object Involved Party but in which the modeled organization has not contacted the subject Involved Party.
`active`				| 00005	| Identifies a Customer Lifecycle Status in which the <Customer> has accepted and is using a product or service offered by the modeled organization.
`former`				| 00006	| Identifies a Customer Lifecycle Status in which the <Involved Party> (the <Customer>) previously had an active customer relationship with the modeled organization but currently is inactive with no open <Product Arrangement>s in force.
`prospective`			| 00007	| Identifies a lifecycle state where an <Involved Party> (the <Customer>) has been identified as a possible active customer by the modeled organization and has been contacted by the modeled organization.


Primary Identification Document
-------------- 
Acceptable primary proof of identity entered from original or certified documents with full name and date of birth.

Literal							| Code 	| Description
--------------------------------|-------|------------------------
`passport`						| 00001	| Passport
`driving-licence`				| 00002	| Driving licence
`personal-identification-card`	| 00003	| Personal identification card


Registration Number 
--------------
Kind of identification number of individual customer. 

Literal 							| Code 	| Description
------------------------------------|--------|------------------------
`national-identification-number`	| 00001 | National identification number
`tax-identification-number`			| 00002	| Tax identification number
`social-security-number`			| 00003	| Social security number
`driver-licence-number`				| 00004	| Driver licence number
`passport-number`					| 00005	| Passport number
`identity-card-number`				| 00006	| Idenitity card number


Contact Usage
--------------
Usage type of the contact.

Literal 		| Code 	| Description
----------------|-------|------------------------
`seasonal`		| 00001 | Seasonal
`assistant`		| 00002	| Assistant
`work`			| 00003	| Work
`home`			| 00004	| Home
`default`		| 00005	| Default
`business`		| 00006	| Business
`legal`			| 00007	| Legal

