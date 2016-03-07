   
Possible problems
=================

When request is valid and no standard status code describes situation, device management API will return status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling]()

Literal                               | Code   | Description
--------------------------------------|--------|-----------------------------------------
`nickname-not-set`                    | 52401  | Device nickname must be set in order to register device.
`operating-system-not-set`            | 52402  | Device operating system must be set in order to register device.
`imei-not-set`                        | 52403  | Device nickname must be unique for specified customer.
`nickname-not-unique`                 | 52404  | Device nickname must be unique for specified customer.
`imei-not-unique`                     | 52405  | Device IMEI must be unique for all active or blocked devices.
`device-not-exist`                    | 52406  | Device with specified imei does not exist.
`valid-push-registration-exist`       | 52407  | Valid push registration for specified device exist.
`device-status-not-valid`             | 52408  | Device status is not valid for requested operation.

