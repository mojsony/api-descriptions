---
visibility: public
---
Profile API Classifications
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

Profile API Enumerations
===============

Individual Profile Lifecycle Statuses
----

Literal			| Description
------------|------------------------
living      | Living
deceased    | Deceased
missing     | Missing
unknown     | Unknown

Organization Profile Lifecycle Statuses
----

Literal					| Description
----------------|------------------------
active | Active
closed | Closed
formed | Formed
potential | Potential
inactive | Inactive
suspended | Suspended
unknown | Unknown

Arrangement Profile Lifecycle Statuses
----

Literal					| Description
----------------|------------------------
effective | Effective
termminated | Terminated
completed | Completed
suspended | Suspended
dormant | Dormant

Housing Tenures
----

Literal					| Description
----------------|------------------------
owned-with-mortgage | Owned with mortgage
owned-without-mortgage | Owner without mortgage
rented | Rented
unknown | Unknown
