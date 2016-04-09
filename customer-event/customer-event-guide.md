---
visibility: internal
---

![Folders](http://cdn.flaticon.com/png/64/98/98193.png)
Customer Event API v2
=========================
Customer event API gives you access to all events registered for a customer and also you can register new events for customers.
   
Key Resources
-------------
Customer event has several types of events that can be associated with customers.  

- communication 
- social
- accounting transaction
- customer case
- arrangement activity
- profile maintenance
- chargable activity



Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Content Management API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Offer Management API with your access token against the URL root below, combined with one of the root resources.  Offer Management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Customer event | `https://bankapi.net/customer-event`


> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /customer-event/events` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.


###3. Get list of all events for some customer
Let's assume that we have some customer number and we want to retrieve all the customer events that are associated with that customer.
To get the list of events you must get To create current account request 

```
GET /customer-event/events
```

For this example we are using customer-number 1400269

```
http://localhost:62233/customer-event/events?customer-number=1400269
```


You will get back `200 OK` status code and the list of events. Note that every event in the list has link where you can navigate to see more details about that event.

```json
{
    "total-count": 2298,
    "page-size": 20,
    "page-number": 1,
    "total-pages": 115,
    "items": [
        {
            "event-id": 258242,
            "creation-datetime": "2014-10-10T12:34:36.69",
            "description": null,
            "event-kind": "SecurtyEvent",
            "uri": "http://localhost:62233/customer-event/v2.0/events/258242"
        },
        {
            "event-id": 258220,
            "creation-datetime": "2014-10-10T11:21:01.49",
            "description": null,
            "event-kind": "SecurtyEvent",
            "uri": "http://localhost:62233/customer-event/v2.0/events/258220"
        },
        ...
		...
		...
        {
            "event-id": 256102,
            "creation-datetime": "2014-10-07T14:38:22.197",
            "description": null,
            "event-kind": "SecurtyEvent",
            "uri": "http://localhost:62233/customer-event/v2.0/events/256102"
        }
    ],
    "navigations": [
        {
            "href": "http://localhost:62233/customer-event/v2.0/events?page-size=20&page-number=2&customer-number=1400269",
            "rel": "next"
        }
    ]
}
```


###4. Get details about some event
Using this API you're able to receive details about some event by its Id

```
GET /customer-event/events/{event-id}
```

For this example we are using event with id = 258242

```
http://localhost:62233/customer-event/events/258242
```


You will get back `200 OK` status code and json representation with the details about the event.

```json
{
    "event-id": 258242,
    "creation-datetime": "2014-10-10T12:34:36.69",
    "description": null,
    "event-kind": "SecurtyEvent",
    "event-data-xml": "<customer-login><customer-id>1400269</customer-id><event-id>a65ebbb2-5f23-42de-b0b2-b2362a03b392</event-id><occured-on>2014-10-10T12:34:28.203063+02:00</occured-on><user-id>8001186336</user-id><login-type>authorization-code</login-type><channel>mobile</channel></customer-login>",
    "event-data-key-values": [
        {
            "event-data-xml-parent-key": "customer-login",
            "event-data-xml-key": "customer-id",
            "event-data-xml-value": "1400269"
        },
        {
            "event-data-xml-parent-key": "customer-login",
            "event-data-xml-key": "event-id",
            "event-data-xml-value": "a65ebbb2-5f23-42de-b0b2-b2362a03b392"
        },
        {
            "event-data-xml-parent-key": "customer-login",
            "event-data-xml-key": "occured-on",
            "event-data-xml-value": "2014-10-10T12:34:28.203063+02:00"
        },
        {
            "event-data-xml-parent-key": "customer-login",
            "event-data-xml-key": "user-id",
            "event-data-xml-value": "8001186336"
        },
        {
            "event-data-xml-parent-key": "customer-login",
            "event-data-xml-key": "login-type",
            "event-data-xml-value": "authorization-code"
        },
        {
            "event-data-xml-parent-key": "customer-login",
            "event-data-xml-key": "channel",
            "event-data-xml-value": "mobile"
        }
    ]
}
```
###5. Get details about communication event
Using this request you're able to retrieve details about communication event.

```
GET /customer-event/communication-events/{event-id}
```

You will get back  `200 OK` status code and json representation with the details. 

###6. Get details about social event
Using this request you're able to retrieve details about communication event.

```
GET /customer-event/social-events/{event-id}
```

You will get back  `200 OK` status code and json representation with the details.

###7. Get details about accounting transaction event
Using this request you're able to retrieve details about communication event.

```
GET /customer-event/accounting-transaction-events/{event-id}
```

You will get back  `200 OK` status code and json representation with the details.

###8. Get details about customer case event
Using this request you're able to retrieve details about communication event.

```
GET /customer-event/customer-case-events/{event-id}
```

You will get back  `200 OK` status code and json representation with the details.


###9. Get details about arrangement activity event
Using this request you're able to retrieve details about communication event.

```
GET /customer-event/arrangement-activity-events/{event-id}
```

You will get back  `200 OK` status code and json representation with the details.

###10. Get details about profile maintenance event
Using this request you're able to retrieve details about communication event.

```
GET /customer-event/profile-maintenance-events/{event-id}
```

You will get back  `200 OK` status code and json representation with the details.


###11. Get details about chargable activity event
Using this request you're able to retrieve details about communication event.

```
GET /customer-event/chargable-activity-events/{event-id}
```

You will get back  `200 OK` status code and json representation with the details.

###12. Post new communication event
Usign this web api you're able to create/post new communication event

```
POST /customer-event/communication-events
```

```json
{
  "customer-number": "1400269",
  "workitem-id": "WI0000492929", 
  "description": "some description",
  "from": "Joe",
  "to": "Tom",
  "title": "SomeTitle",
  "medium": "Mail",
  "purpose": "TestPorpose",
  "return-address": "SomeAddress"
}
```

You will get back  `200 OK` status code and json representation with the details.

```json
{
  "id": "WI0000492929",
  "CreatedRecordStatus": "Created"
}
```

**Congratulations!** You have completed getting started tutorial on most common steps when working with CustomerEvent API. To learn more look at the reference documentation for [available operations](swagger-ui).
