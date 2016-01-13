   
Possible problems
=================

When request is valid and no standard status code describes situation, device management API will return status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling]()

Literal 													 | Code   | Description
-------------------------------------------------------------|--------|-----------------------------------------
`nickname-not-unique`										 | 52401  | Device nickname must be unique for specified customer.
`imei-not-unique`											 | 52402  | Device IMEI must be unique for all active or blocked devices.
`not-valid-device-status`           						 | 52403  | Device status is not valid for requested operation.
