   
Classifications
===============

The classifications declared below should be removed.
Device status is an enum, not classification.
Push platform is something that is not exposed through API, but is automatically determined based on Operative system of the phone and sent when push notifications are initiated for device.

Device Status
-------------- 
This classification contains statuses in which devices can be found

Literal 				| Code 	| Description
------------------------|-------|------------------------
`active`				| 00001	| Device is active and ready for use.
`blocked`				| 00002	| Device is temporarily blocked.
`unregistred`	   		| 00003	| Device is permanently unregistred.

Push Platform
--------------
Supported push notification service platforms.

Literal 				| Code 	| Description
------------------------|-------|------------------------
`mpns`					| 00001 | Windows Phone Push notifications Service.
`wns`					| 00002	| Windows Push Notification Services.
`apns`					| 00003	| Apple Push Notification Service.
`gcm`					| 00004	| Android Push Notifications Service.
