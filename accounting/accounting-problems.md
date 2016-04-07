---
visibility: public
---
Possible Accounting API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `54800-54999`.

Common problems
---------------

First 50 codes in a range `54800-54849` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 54800 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 54801 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 54802 | Requested resource could not be found
gone                             | 54803 | Requested resource is no longer available
internal-error                   | 54804 | Unexpected error condition has occurred
not-implemented                  | 54805 | Service does not currently implement the operation, or it lacks the capability to fulfil the request. This implies possible future implementation
service-unavailable              | 54806 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state
