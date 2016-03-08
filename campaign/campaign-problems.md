   
Possible Campaign API Problems
=================


To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `50800 - 50999`.

Common problems
---------------

First 50 codes in a range `50800-50849` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 50800 | Request is not valid. Field {field:} failed following validation {error:} 
forbidden                        | 50801 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 50802 | Requested resource could not be found
gone                             | 50803 | Requested resource is no longer available
internal-error                   | 50804 | Unexpected error condition has occurred
not-implemented                  | 50805 | Service does not currently implement the operation, or it lacks the capability to fulfill the request. This implies possible future implementation
service-unavailable              | 50806 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state



Campaign API Specific Problems
---------------

When request is valid and no standard status code describes situation, API will return http status code `440` with one of the following problems in the payload.

Literal                              |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
benefit-already-activated            | 50850 | Benefits from campaign {campaign:} are already activated for customer {customer:}
campaign-expired                     | 50851 | Campaign {campaign:} has expired  