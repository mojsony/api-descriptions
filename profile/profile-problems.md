---
visibility: public
---
Possible Profile API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `53600-53799`.

Common problems
---------------

First 50 codes in a range `53600-53649` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 53600 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 53601 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 53602 | Requested resource could not be found
gone                             | 53603 | Requested resource is no longer available
internal-error                   | 53604 | Unexpected error condition has occurred
not-implemented                  | 53605 | Service does not currently implement the operation, or it lacks the capability to fulfil the request. This implies possible future implementation
service-unavailable              | 53606 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state
