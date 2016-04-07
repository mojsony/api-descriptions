---
visibility: public
---
Possible Offer API Problems
=================

When request is valid and no standard status code describes situation, API will return http status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling](common-getstarted.html#error-handling).

Range of problem codes for this API is `53000 - 53199`.

Common problems
---------------

First 50 codes in a range `53000-53049` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 53000 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 53001 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 53002 | Requested resource could not be found
gone                             | 53003 | Requested resource is no longer available
internal-error                   | 53004 | Unexpected error condition has occurred
not-implemented                  | 53005 | Service does not currently implement the operation, or it lacks the capability to fulfill the request. This implies possible future implementation
service-unavailable              | 53006 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state

Offer API Specific Problems
------------

Literal 				                        | Code 	 |   Description
----------------------------------------|--------|-----------------------------------------
`deposit-application-maxnumber`	        | 53050	 | Customer can not have more then one current-account application.
`requested-account-range`	              | 53051	 | Incorrect requested-account-number. Not in range 5001.
`current-account-arrangement-maxnumber`	| 53052	 | Customer can not have more then one current-account arrangement.
`customer-not-found`		                | 53053  | Can not find customer for IdentificationNumber "%s", Country "%s", of Type "%s". PartyExternalId = "%s".
`account-exists`                        | 53054  | Destination system already contains account for the given Arrangement!  
`product-not-valid`                     | 53055	 | Actual product not valid.
`deposit-account-opening-maxnumber`     | 53056	 | Customer exceeded the maximum number of deposit accounts.
