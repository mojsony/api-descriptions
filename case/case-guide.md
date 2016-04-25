---
visibility: internal
---

<span class="icon"></span>Case API Guide
=========================
Customer Case API gives you access to all cases that are associated with some customers and also create new ones.

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Case API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication](common-getstarted.html#authentication) section.

###2. URL Root
Now that you've authenticated your app, you can call the Case API with your access token against the URL root below, combined with one of the root resources.  Case API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Case | `https://bankapi.net/v1/case`


> **Note**: Throughout this documentation, only partial syntax such as:
`GET /cases` is used for the sake of brevity.
Prefix the path with the correct root URL in order to obtain the full resource path or URL.


###3. Get list of all events
Operation returns list of cases with basic details like registration date current lifecycle state and the name and id of the agent responsible for handling the case. When used without optional parameters all active cases are returned.
To get the list of events you must get To create current account request

```
GET /cases
```

You will get back `200 OK` status code and the list of events. Note that every event in the list has link where you can navigate to see more details about that event.

```json
{
    "total-count": 1445,
    "page-size": 20,
    "page-number": 1,
    "total-pages": 73,
    "items": [
        {
            "case-number": "WI0000497288",
            "kind": "complaint",
            "customer-number": "1104977710344",
            "customer-name": "Marko Petrovic",
            "status": "accepted",
            "resolution": "Resolution1",
            "importance": "low",
            "title": "Title1",
            "details": "Details1",
            "arrangement-number": "2344",
            "created": "2016-02-01T01:25:00",
            "status-changed": "2016-02-01T01:55:00",
            "last-modified": "2016-03-01T01:25:00",
            "attachments": []
        },
        {
            "case-number": "WI0000497285",
            "kind": "complaint",
            "customer-number": "1104977710344",
            "customer-name": "Stefan Rasic",
            "status": "accepted",
            "resolution": "Resolution2",
            "importance": "high",
            "title": "Title2",
            "details": "Details2",
            "arrangement-number": "24256",
            "created": "2016-02-01T01:25:00",
            "status-changed": "2016-02-01T01:55:00",
            "last-modified": "2016-03-01T01:25:00",
            "attachments": []
        },
        {
            "case-number": "WI0000497284",
            "kind": "complaint",
            "customer-number": "1104977710344",
            "customer-name": "David Tomic",
            "status": "accepted",
            "resolution": "Resolution3",
            "importance": "medium",
            "title": "Title3",
            "details": "Details3",
            "arrangement-number": "45432",
            "created": "2016-02-01T01:25:00",
            "status-changed": "2016-02-01T01:55:00",
            "last-modified": "2016-03-01T01:25:00",
            "attachments": []
        }        
    ]
}
```


###4. Get details about some specific case
Operation returns specific case details.

```
GET /cases/WI0000497282
```


You will get back `200 OK` status code and json representation with the details about the case.

```json
{
  "case-number": "WI0000497284",
  "kind": "complaint",
  "customer-number": "1104977710344",
  "customer-name": "David Tomic",
  "status": "accepted",
  "resolution": "Resolution1",
  "importance": "medium",
  "title": "Title1",
  "details": "Details1",
  "arrangement-number": "34534",
  "created": "2016-02-01T01:25:00",
  "status-changed": "2016-02-01T01:55:00",
  "last-modified": "2016-03-01T01:25:00",
  "attachments": []
}
```
###5. Get history for some customer case
Operation returns list of history changes associated with the specific case.

```
GET /cases/WI0000497282/history
```

You will get back  `200 OK` status code and json representation with the details.

```json
{
    "total-count": 1,
    "page-size": 100,
    "page-number": 1,
    "total-pages": 1,
    "Items": [
        {
            "case-id": "WI0000497282",
            "case-type": "Complaint",
            "updated-by-id": null,
            "updated-by-name": "Stevan.Kostoski",
            "customer-id": "1104977710344",
            "customer-name": "Ime237069 Prezime23706",
            "customer-ident-num": null,
            "registration-date": null,
            "state": "Accepted",
            "resolution": null,
            "importance": "Standard",
            "details": null,
            "arrangement-num": null,
            "version-num": "7624147733",
            "version-date": "2015-11-13T11:14:17.697"
        }
    ]
}
```

###6. Create new complaint
Operation opens new customer complaint. Operation returns complaint identifier.

```
POST /cases/complaints
```

```json
{
  "case-id": "23423423",
  "customer-number": "3456547",
  "importance": "low",
  "details": "Details1",
  "arrangement-number": "24721",
  "title": "Title1",
  "reply-address": "Resavska br.3, Beograd",
  "reply-address-code": "11000",
  "case-topic": "Topic",
  "related-case-id": "string"
}
```

You will get back  `201 Created` status code and json representation with the details.

```json
{
  "id": "string"
}
```

###7. Create new service request
Operation opens new customer service request. Operation returns service-request identifier.

```
POST /cases/service-requests
```

```json
{
  "case-number": "345467",
  "customer-number": "42342",
  "importance": "Low",
  "details": "Details",
  "arrangement-number": "string",
  "title": "Title"
}
```

You will get back  `201 Created` status code and json representation with the details.

```json
{
  "id": "string"
}
```

###8. Create new callback request
Operation opens new customer callback-request. Operation returns callback-request identifier.

```
POST /cases/callback-requests
```

```json
{
  "callback-time": "2016-02-01T01:25:00 ",
  "categorry": "Cards",
  "customer-number": "23424"
}
```

You will get back  `201 Created` status code and json representation with the details.

```json
{
  "id": "string"
}
```

###9. Add attachment (file/documnet) to existing customer case
Operation attach document/file to the existing Case

```
POST /cases/{case-number}/attachments
```

```json
{
  "attachment-url": "https://www.atturl.com/pom?v=8nm3sdfwGASryA",
  "attachment-id": "2342342",
  "document-type": "pdf"
}
```

You will get back  `200 OK` status code and json representation with the details.

```json
{
  "id": "string"
}
```

###10. Update details about some existing customer case
Operation updates the specified case progress. Operation returns customer case identifier.

```
PUT /cases/{case-id}
```

```json
{
  "case-type": "Complaint",
  "case-id": "string",
  "updated-by-id": "string",
  "updated-by-name": "string",
  "resolution": "string",
  "state": "Resolved"
}
```

You will get back  `200 OK` status code and json representation with the details.

```json
{
  "id": "string",
  "created-record-status": "string"
}
```

###11. Close customer case
Operation closes the specified case. Operation returns closed case id.


```
DELETE /cases/{case-id}
```

```json
{
  "case-type": "Complaint",
  "case-id": "string",
  "updated-by-id": "string",
  "updated-by-name": "string",
  "resolution": "string"
}
```

You will get back  `200 OK` status code and json representation with the details.

```json
{
  "id": "string",
  "created-record-status": "string"
}
```

###12. Deattach document/file from customer case.
Operation removes attaced file from case.

```
DELETE /cases/{case-id}/attachments/{file-id}
```

You will get back  `200 OK` status code and json representation with the details.


```json
{
  "id": "string",
  "created-record-status": "string"
}
```

**Congratulations!** You have completed getting started tutorial on most common steps when working with Case API. To learn more look at the reference documentation for [available operations](swagger-ui).
