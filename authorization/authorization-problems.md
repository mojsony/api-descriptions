---
visibility: public
---
Possible Authorization API Problems
=================

When request is valid and no standard status code describes situation, API will return status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling](common-getstarted.html#error-handling).

Range of problem codes for this API is `53800-53999`.

Common problems
---------------

First 50 codes in a range `53800-53949` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
`bad-request`                      | 53800 | Request is not valid. Field {field:} failed following validation {error:}
`forbidden`                        | 53801 | User is not authorized to access resource or perform such a command on a resource
`not-found`                        | 53802 | Requested resource could not be found
`gone`                             | 53803 | Requested resource is no longer available
`internal-error`                   | 53804 | Unexpected error condition has occurred
`not-implemented`                  | 53805 | Service does not currently implement the operation, or it lacks the capability to fulfill the request. This implies possible future implementation
`service-unavailable`              | 53806 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state

Authorization API Specific Problems
---------------

When request is valid and no standard status code describes situation, API will return http status code `440` with one of the following problems in the payload.

Literal               |  Code | Description                        
--------------------- | -----:| -----------------------------------
`bad-otp`             | 53850 | Bad OTP was supplied  
`replayed-otp`        | 53851 | The OTP was used before
`no-such-user`        | 53852 | User {user:} not found  
`no-such-verification`| 53853 | Ongoing verification {verification:} not found
