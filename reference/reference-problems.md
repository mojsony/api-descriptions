---
visibility: public
---
Possible Reference API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `54200-54399`.

Common problems
---------------

First 50 codes in a range `54200-54249` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 54200 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 54201 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 54202 | Requested resource could not be found
gone                             | 54203 | Requested resource is no longer available
internal-error                   | 54204 | Unexpected error condition has occurred
not-implemented                  | 54205 | Service does not currently implement the operation, or it lacks the capability to fulfil the request. This implies possible future implementation
service-unavailable              | 54206 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state
