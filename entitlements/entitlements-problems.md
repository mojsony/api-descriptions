---
visibility: public
---
Entitlements API Possible problems
=================

When request is valid and no standard status code describes situation, API will return status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling](common-getstarted.html#error-handling).

Range of problem codes for this API is `50200 - 50399`.

Common problems
---------------

First 50 codes in a range `50200-52049` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 52000 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 52001 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 52002 | Requested resource could not be found
gone                             | 52003 | Requested resource is no longer available
internal-error                   | 52004 | Unexpected error condition has occurred
not-implemented                  | 52005 | Service does not currently implement the operation, or it lacks the capability to fulfill the request. This implies possible future implementation
service-unavailable              | 52006 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state

Entitlements API Specific Problems
------------

Literal               |  Code | Description                        
--------------------- | -----:| -----------------------------------
locked-out            | 50250 | Locked out                         
max-attempts-reached  | 50251 | Max login attempts has been reached
authorization-expired | 50252 | Authorization expired   
