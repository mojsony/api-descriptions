---
visibility: public
---
Possible Product API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `54000-54199`.

Common problems
---------------

First 50 codes in a range `54000-54049` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 54000 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 54001 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 54002 | Requested resource could not be found
gone                             | 54003 | Requested resource is no longer available
internal-error                   | 54004 | Unexpected error condition has occurred
not-implemented                  | 54005 | Service does not currently implement the operation, or it lacks the capability to fulfil the request. This implies possible future implementation
service-unavailable              | 54006 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state
