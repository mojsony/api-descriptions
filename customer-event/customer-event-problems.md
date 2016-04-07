Possible Customer Event API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `51800-51999`.

Common problems
---------------

First 50 codes in a range `51800-51849` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 51800 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 51801 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 51802 | Requested resource could not be found
gone                             | 51803 | Requested resource is no longer available
internal-error                   | 51804 | Unexpected error condition has occurred
not-implemented                  | 51805 | Service does not currently implement the operation, or it lacks the capability to fulfil the request. This implies possible future implementation
service-unavailable              | 51806 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state
