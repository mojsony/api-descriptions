   
   
Possible Authorization API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `50200-50399`.


Common problems
---------------

First 50 codes in a range `50200-50249` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
`bad-request`                      | 50200 | Request is not valid. Field {field:} failed following validation {error:} 
`forbidden`                        | 50201 | User is not authorized to access resource or perform such a command on a resource
`not-found`                        | 50202 | Requested resource could not be found
`gone`                             | 50203 | Requested resource is no longer available
`internal-error`                   | 50204 | Unexpected error condition has occurred
`not-implemented`                  | 50205 | Service does not currently implement the operation, or it lacks the capability to fulfill the request. This implies possible future implementation
`service-unavailable`              | 50206 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state



Authorization API Specific Problems
---------------

When request is valid and no standard status code describes situation, API will return http status code `440` with one of the following problems in the payload.


Literal               |  Code | Description                        
--------------------- | -----:| ----------------------------------- 
`bad-otp`             | 50250 | Bad OTP was supplied  
`replayed-otp`        | 50251 | The OTP was used before
`no-such-user`        | 50252 | User {user:} not found  
`no-such-verification`| 50253 | Ongoing verification {verification:} not found