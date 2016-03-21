   
Possible problems
=================

When request is valid and no standard status code describes situation, Customer Survey API will return status code `440` with one of the following problems in the payload. 
To learn more see general guidance on [error handling](common-getstarted.html#error-handling)

Possible Party API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `53400` - `53599`.

Common problems
---------------

First 50 codes in a range `53400-53449` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
`bad-request`                      | 53400 | Request is not valid. Field {field:} failed following validation {error:}
`forbidden`                        | 53401 | User is not authorized to access resource or perform such a command on a resource
`not-found`                        | 53402 | Requested resource could not be found
`gone`                             | 53403 | Requested resource is no longer available
`internal-error`                   | 53404 | Unexpected error condition has occurred
`not-implemented`                  | 53405 | Service does not currently implement the operation, or it lacks the capability to fulfill the request. This implies possible future implementation
`service-unavailable`              | 53406 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state

Exchange API Specific Problems
---------------

When request is valid and no standard status code describes situation, API will return http status code `440` with one of the following problems in the payload.


Literal 				                      | Code 	 | Description
--------------------------------------|-------:|----------------------------------------
`invalid-party-identifier`	          |53450	 | PIN is invalid
`existing-party-identifier`           |53451   | PIN already exists