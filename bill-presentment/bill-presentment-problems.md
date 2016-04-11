---
visibility: internal
---
Possible Bill Presentment API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `50400-50599`.

Common problems
---------------

First 50 codes in a range `50400-50449` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 50400 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 50401 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 50402 | Requested resource could not be found
gone                             | 50403 | Requested resource is no longer available
internal-error                   | 50404 | Unexpected error condition has occurred
not-implemented                  | 50405 | Service does not currently implement the operation, or it lacks the capability to fulfil the request. This implies possible future implementation
service-unavailable              | 50406 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state

Bill Presentment API specific problems
---------------

Literal                          |  Code | Description                                                            
-------------------------------- | -----:| -----------------------------------------------------------------------
debtor-account-not-active        | 50450 | Debtor account number not valid, there is no such active account.
nickname-already-exists          | 50451 | User has already set this nickname for another subscription.
subscription-already-registered  | 50452 | User has already set bill payment subscription for this issuer.
subscription-not-active          | 50453 | Bill payment subscription is not active.
unpaid-bills-exist               | 50454 | There are active bills, subscription cannot be canceled.
standing-order-scheduled         | 50455 | Subscription cannot be canceled, standing order is scheduled for today.
