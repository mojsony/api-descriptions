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
    "Items": [
        {
            "case-id": "WI0000497288",
            "case-type": "Complaint",
            "case-class": "Complaint",
            "registered-by-id": null,
            "registered-by-name": "Stevan.Kostoski",
            "updated-by-id": null,
            "updated-by-name": "Stevan.Kostoski",
            "customer-id": "1104977710344",
            "customer-name": "Ime237069 Prezime23706",
            "customer-ident-num": null,
            "registration-date": "2015-11-13T16:26:24.853",
            "state": "Accepted",
            "resolution": null,
            "importance": "Standard",
            "title": null,
            "details": null,
            "arrangement-num": null,
            "attachments": []
        },
        {
            "case-id": "WI0000497285",
            "case-type": "Complaint",
            "case-class": "Complaint",
            "registered-by-id": null,
            "registered-by-name": "Stevan.Kostoski",
            "updated-by-id": null,
            "updated-by-name": "Stevan.Kostoski",
            "customer-id": "1104977710344",
            "customer-name": "Ime237069 Prezime23706",
            "customer-ident-num": null,
            "registration-date": "2015-11-13T13:30:40.39",
            "state": "Accepted",
            "resolution": null,
            "importance": "Standard",
            "title": null,
            "details": null,
            "arrangement-num": null,
            "attachments": []
        },
        {
            "case-id": "WI0000497284",
            "case-type": "Complaint",
            "case-class": "Complaint",
            "registered-by-id": null,
            "registered-by-name": "Stevan.Kostoski",
            "updated-by-id": null,
            "updated-by-name": "Stevan.Kostoski",
            "customer-id": "1104977710344",
            "customer-name": "Ime237069 Prezime23706",
            "customer-ident-num": null,
            "registration-date": "2015-11-13T13:07:06.62",
            "state": "Accepted",
            "resolution": null,
            "importance": "Standard",
            "title": null,
            "details": null,
            "arrangement-num": null,
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
    "case-id": "WI0000497282",
    "case-type": "Complaint",
    "case-class": "Complaint",
    "registered-by-id": null,
    "registered-by-name": "Stevan.Kostoski",
    "updated-by-id": null,
    "updated-by-name": "Stevan.Kostoski",
    "customer-id": "1104977710344",
    "customer-name": "Ime237069 Prezime23706",
    "customer-ident-num": null,
    "registration-date": "2015-11-13T11:14:17.697",
    "state": "Resolved",
    "resolution": "tetete",
    "importance": "Standard",
    "title": null,
    "details": "Menja status predmeta",
    "arrangement-num": null,
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
POST /complaints
```

```json
{
  "case-id": "string",
  "registered-by-id": "string",
  "registered-by-name": "string",
  "customer-id": "string",
  "customer-name": "string",
  "customer-ident-num": "string",
  "importance": "Low",
  "details": "string",
  "arrangement-num": "string",
  "comm-reason": "string",
  "comm-reply-address": "string",
  "comm-reply-address-code": "string",
  "comm-type": "Email",
  "case-type": "string",
  "rel-case-id": "string"
}
```

You will get back  `201 Created` status code and json representation with the details.

```json
{
  "id": "string",
  "created-record-status": "string"
}
```

###7. Create new service request
Operation opens new customer service request. Operation returns service-request identifier.

```
POST /service-requests
```

```json
{
  "case-id": "string",
  "registered-by-id": "string",
  "registered-by-name": "string",
  "customer-id": "string",
  "customer-name": "string",
  "customer-ident-num": "string",
  "importance": "Low",
  "details": "string",
  "arrangement-num": "string",
  "comm-reason": "string",
  "comm-reply-address": "string",
  "comm-reply-address-code": "string",
  "comm-type": "Email",
  "case-type": "string",
  "rel-case-id": "string"
}
```

You will get back  `201 Created` status code and json representation with the details.

```json
{
  "id": "string",
  "created-record-status": "string"
}
```

###8. Create new callback request
Operation opens new customer callback-request. Operation returns callback-request identifier.

```
POST /callback-requests
```

```json
{
  "callback-request-time": "2015-12-22T13:33:17.588Z",
  "categorry": "Cards",
  "party-id": "string"
}
```

You will get back  `201 Created` status code and json representation with the details.

```json
{
  "id": "string",
  "created-record-status": "string"
}
```

###9. Add attachment (file/documnet) to existing customer case
Operation attach document/file to the existing Case

```
POST /cases/{case-id}/attachments
```

```json
{
  "case-id": "string",
  "file-id": "string",
  "file-name": "string",
  "customer-id": "string"
}
```

You will get back  `200 OK` status code and json representation with the details.

```json
{
  "id": "string",
  "created-record-status": "string"
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
