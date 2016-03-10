<span class="icon"></span> Correspondence API Guide
=========================

Correspondence API handles the automated generation of batches of pre-formatted correspondence, typically integrating customer/product specific data in correspondence templates for variable aspects of content. Channel applications can use this API to deliver alerts, reminders, advices, past due notices, announcements, campaign offers, statements and other arrangement reports. Correspondence API also offers rendering of documents in .pdf and .docx formats from predefined templates and supplied data. For self-service applications such as mobile or web, Correspondence API offers virtual mailbox for private exchange of messages between bank and customer.

> ##THIS API GUIDE IS UNDER CONSTRUCTION. COME BACK SOON.

Key Resources
-------------

Correspondence has three top level collection resources: communications,  templates and mailbox.

Resource | Description
----------- |-----------
*communications*  | Represent messages communicated to customers over any contact-medium such as a telephone call, a letter, a fax, an e-mail, electronic message, a meeting, etc. It may have occurred or be planned to occur in the future. In each case, a discrete occurrence of a communication is identifiable.
*mailbox*   |  Virtual customer mailbox for self-service applications such as mobile and web.
*templates*    | Correspondence templates used to render document such as agreements and offers in pdf and word format.

Getting started tutorial
---------------

To get started follow these steps:

###1. Authenticate your app
Correspondence API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:

```
Authorization: bearer {token}
```

To obtain an access token and sign the user in, see [authentication](common-getstarted.html#authentication) section.

###2. URL Root
Now that you've authenticated your app, you can call the Correspondence API with your access token against the URL root below, combined with one of the root resources.  Correspondence API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Correspondence | `https://dev.asseco-see.com/v1/correspondence`

> **Note**: Throughout this documentation, only partial syntax such as:
`GET /communications` is used for the sake of brevity.
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Get communications
Before you can choose communication, you can get the list of communications that are no longer waiting for delivery:

```
GET /communications
```

You will get back `200 OK` status code and json representation with a list of communication items.
```json
[
  {
      "communication-id": null,
      "contact": {
        "usage": null,
        "kind": "",
        "details": "",
        "contact-preference": {
          "preferred-language": null,
          "opt-ins": null,
          "opt-outs": null
        }
      },
      "customer-number": null,
      "date-created": "2015-12-28T08:29:38.6794345+01:00",
      "status": "pending",
      "sent": "2015-12-30T08:29:38.6794345+01:00",
      "expires": "2016-01-28T08:29:38.6794345+01:00",
      "data": "",
      "message-type": null,
      "priority": null,
      "reference-number": null,
      "retry-count": 0,
      "message": null,
      "conversation-type": null
    },
    {
      "communication-id": null,
      "contact": {
        "usage": null,
        "kind": "",
        "details": "",
        "contact-preference": {
          "preferred-language": null,
          "opt-ins": null,
          "opt-outs": null
        }
      },
      "customer-number": null,
      "date-created": "2015-12-28T08:29:38.6794345+01:00",
      "status": "pending",
      "sent": "2015-12-30T08:29:38.6794345+01:00",
      "expires": "2016-01-28T08:29:38.6794345+01:00",
      "data": "",
      "message-type": null,
      "priority": null,
      "reference-number": null,
      "retry-count": 0,
      "message": null,
      "conversation-type": null
    }
]
```

###4. Get communication details
Now you can get the details for specific communication. You will need to pass communication-id parameter which represents the unique identifier of the communication.

```
GET /communications/{communication-id}:
```

You will get back `200 OK` status code and json representation with a communication details.

```json
{
  "communication-id": null,
  "contact": {
    "usage": null,
    "kind": "",
    "details": "",
    "contact-preference": {
      "preferred-language": null,
      "opt-ins": null,
      "opt-outs": null
    }
  },
  "customer-number": null,
  "date-created": "2015-12-28T10:21:18.3451808+01:00",
  "status": "pending",
  "sent": "2015-12-30T10:21:18.3451808+01:00",
  "expires": "2016-01-28T10:21:18.3451808+01:00",
  "data": "",
  "message-type": null,
  "priority": null,
  "reference-number": null,
  "retry-count": 1,
  "message": null,
  "conversation-type": null
}
```

###5. Communication summary

You can get the list of communication summary items, which represents the summary of communication delivery status.

```
GET /communication-summaries
```

```json
 "items": [
    {
      "status": "pending",
      "total-count": 2,
      "high-count": 3,
      "medium-count": 4,
      "low-count": 5
    },
    {
      "status": "delivered",
      "total-count": 2,
      "high-count": 3,
      "medium-count": 4,
      "low-count": 5
    }
  ]
```

You will get back `200 OK` status code and json representation with a list of communication summary items.

###6. Render document
Now you can render documents using templates.

```
POST /templates/render
```

You will get back `200 OK` status code and json representation of data.

```json
{
  "data": "QEA="
}
```

**Congratulations!** You have completed getting started tutorial on most common steps when working with Correspondence API. To learn more look at the reference documentation for [available operations](correspondence.html).
