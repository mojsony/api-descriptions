---
visibility: public
---
﻿Device API Possible problems
=================

When request is valid and no standard status code describes situation, device management API will return status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling](common-getstarted.html#error-handling).

Range of problem codes for this API is `52400 - 52599`.

First 50 codes in a range `52400-52449` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 52400 | Request is not valid. Field {field:} failed following validation {error:} 
forbidden                        | 52401 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 52402 | Requested resource could not be found
gone                             | 52403 | Requested resource is no longer available
internal-error                   | 52404 | Unexpected error condition has occurred
not-implemented                  | 52405 | Service does not currently implement the operation, or it lacks the capability to fulfil the request. This implies possible future implementation
service-unavailable              | 52406 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state

Device API specific problems
---------------

Literal                               | Code   | Description
--------------------------------------|--------|-----------------------------------------
`nickname-not-set`                    | 52450  | Device nickname must be set in order to register device.
`operating-system-not-set`            | 52451  | Device operating system must be set in order to register device.
`imei-not-set`                        | 52452  | Device nickname must be unique for specified customer.
`nickname-not-unique`                 | 52453  | Device nickname must be unique for specified customer.
`imei-not-unique`                     | 52454  | Device IMEI must be unique for all active or blocked devices.
`device-not-exist`                    | 52455  | Device with specified imei does not exist.
`valid-push-registration-exist`       | 52456  | Valid push registration for specified device exist.
`device-status-not-valid`             | 52457  | Device status is not valid for requested operation.
