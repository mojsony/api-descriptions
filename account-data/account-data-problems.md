Possible Account Data API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `51400 - 51599`.

Common problems
---------------

First 50 codes in a range `51400-51449` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 51400 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 51401 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 51402 | Requested resource could not be found
gone                             | 51403 | Requested resource is no longer available
internal-error                   | 51404 | Unexpected error condition has occurred
not-implemented                  | 51405 | Service does not currently implement the operation, or it lacks the capability to fulfill the request. This implies possible future implementation
service-unavailable              | 51406 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state



Account Data API Specific Problems
---------------

When request is valid and no standard status code describes situation, API will return http status code `440` with one of the following problems in the payload.

Literal                              |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
account-nickname-in-use              | 51450 | Nickname {nickname:} is used for another account
