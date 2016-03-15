   
Possible Exchange API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `51200` - `51399`.

Common problems
---------------

First 50 codes in a range `51200-51249` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 51200 | Request is not valid. Field {field:} failed following validation {error:}
forbidden                        | 51201 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 51202 | Requested resource could not be found
gone                             | 51203 | Requested resource is no longer available
internal-error                   | 51204 | Unexpected error condition has occurred
not-implemented                  | 51205 | Service does not currently implement the operation, or it lacks the capability to fulfill the request. This implies possible future implementation
service-unavailable              | 51206 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state

Exchange API Specific Problems
---------------

When request is valid and no standard status code describes situation, API will return http status code `440` with one of the following problems in the payload.

Literal                              |  Code | Description                                                                           
------------------------------------ | -----:| --------------------------------------------------------------------------------------                          
night-exchange-closed                | 51250 | The transactions of exchange for this night are closed.
source-account-check-failed          | 51251 | Check of source account failed.
destination-account-check-failed     | 51252 | Check of destination account failed.
account-type-not-appropriate         | 51253 | Source and destination accounts have to be either current account or saving on demand.
amount-limit-exceeded                | 51254 | This amount exceeds withdrawal limit on source account.
frequency-limit-exceeded             | 51255 | Number of withdrawals for the time period exceeded
temporary-unavailable                | 51256 | Exchange order can not be processed at the moment. Please try again later.
insufficient-balance                 | 51257 | Source account does not have sufficient available balance.
