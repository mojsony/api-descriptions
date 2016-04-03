   
Classifications
===============




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


