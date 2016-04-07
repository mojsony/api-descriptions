---
visibility: public
---
Possible xxx API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `54400-54599`.

Common problems
---------------

First 50 codes in a range `54400-54449` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 54400 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 54401 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 54402 | Requested resource could not be found
gone                             | 54403 | Requested resource is no longer available
internal-error                   | 54404 | Unexpected error condition has occurred
not-implemented                  | 54405 | Service does not currently implement the operation, or it lacks the capability to fulfil the request. This implies possible future implementation
service-unavailable              | 54406 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state
