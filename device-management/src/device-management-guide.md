![Folders](http://cdn.flaticon.com/png/64/98/98193.png)
Device Management API v2
=========================
Device Management API enables you to register devices, mange device statuses, enable device for push notifications etc. 
   
Key Resources
-------------
Device Management API has two top level collection resources:

Resource | Description
----------- |-----------
*devices*  | Includes basic data about devices such as nickname, device imei, device status, customer etc. Beside this basic data it contains some data whichregards push notifications.
*device models*    | Includes basic data about devices models such as name, device model code, brand name etc. 

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Device management API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Device management API with your access token against the URL root below, combined with one of the root resources. Device management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Device Management | `https://api.asse.co/device-management`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /devices/{imei}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Register Device
 You need to post `devices` metadata representation as json to following endpoint:
```
POST /devices
```
```json
{
  "imei": "990000862471854",
  "operating-system": "iOS 9.x",
  "nickname": "My Phone",
  "device-model-code": "IP-6S"
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
      "device-model-code": "IP-6S"
      "device-model-name": "IPhone 6S"
      "installation-id": 
      "registration-id": 
      "registration-id-expiration-date": 
}
```

###5. Unregister Device
Let's unregister device from step 4:
```
POST /devices/990000862471854/unregister
```

You will get back `202 OK` status code. 


**Congratulations!** You have completed getting started tutorial on most common steps when working with Device Management API. To learn more look at the reference documentation for [available operations](swagger-ui).
