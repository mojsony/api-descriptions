---
visibility: internal
---

<span class="icon"></span>Device API Guide
=========================
Device API manages customer owned devices such as mobile phones and tracks state of bank issued devices such payment cards and authentication devices such as hardware tokens.

> ##THIS API GUIDE IS UNDER CONSTRUCTION. COME BACK SOON.

Key Resources
-------------
Device API has only two top-level collection resources: `owned-devices` and `issued-devices`

Resource | Description
----------- |-----------
*owned-devices*  | Devices owned by customer such as mobile phone, smart watch or tablet. Devices are registered in order to enhance security during authorization checking and to enable push notifications.
*issued-devices* | Devices issued by bank such as payment cards and hardware tokens. Besides basic details, resource exposes status of the device. 


Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Device API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Device API with your access token against the URL root below, combined with one of the root resources. Device API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Device  | `https://dev.asseco-see.com/v1/device`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /devices/{imei}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Register Device
 You need to post `devices` metadata representation as json to following endpoint:
```
POST /owned-devices
```
```json
{
  "external-device-identifier": "990000862471854",
  "operating-system": "iOS 9.x",
  "nickname": "My Phone",
  "brand-name": "Apple IPhone",
  "model-name": "IP-6S"
}
```
You will get back `200 OK` status code device IMEI and device status. 

```json
{
  "id": "990000862471854",
  "CreatedRecordStatus": "active"
}
```

###4. Retreive details for registred device
Now lets preview registred device from step 3:
```
GET /devices/990000862471854
```

You will get back `200 OK` status code and json representation for fetched request. 
```
```json
{
      "imei": "990000862471854"
      "customer-id": "MIGR00002"
      "status": "active"
      "nickname": "My Phone"
      "operating-system": "iOS 9.x"
      "brand-name": "Apple IPhone",
      "model-name": "IP-6S"
      "installation-id": 
      "push-id": 
      "push-expiration-date": 
}
```

###5. Unregister Device
Let's unregister device from step 4:
```
POST /devices/990000862471854/unregister
```

You will get back `202 OK` status code. 


**Congratulations!** You have completed getting started tutorial on most common steps when working with Device API. To learn more look at the reference documentation for [available operations](swagger-ui).