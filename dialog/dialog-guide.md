<span class="icon"></span>Dialog API Guide
======================
Dialog API provides various methods for 

Key Resources
-------------
Dialog API has nine top level collection resources: Analitics controller, Application storage controller, Configuration controller, FAQ controller, Localization controller, 
Orchestration controller, Tips controller, UI controller, UIFlow controller.

Resource | Description
----------- |-----------
*application storage* | Contains CRUD operations for values that are stored in database.
*configuration* | Channel applications configuration data
*FAQ* | (FAQ) Frequently Asked Questions 
*Localization* | Repository of localized values
*orchestration* | Presents more complex scenarios for testing several methods at once.
*tips* | Tips and tricks for 
*UI* | Definition of UI (pages, zones, part)

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Dialog API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Dialog API with your access token against the URL root below, combined with one of the root resources.  
Dialog API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Dialog | `https://dev.asseco-see.com/v1/dialog`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /storage-items/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Add storage value
Before you can view Your values You can add them to database. Required parameter is value that is to be added.
```
POST /storage-items/
```
You will get back `200 OK` status code and json representation with Id of added value and created record status Accepted.
```json
{
  "id": "6ff3ea18-16ab-4c9c-962a-73ea1a330da4",
  "created-record-status": "Accepted"
}

```


###4. Query storage values

Let's assume that You inserted some values and now want to query them. 

```
GET /storage-items/
```
You will get back `200 OK` status code and json representation with values that exist in database for You.

```json
{
  "total-count": 10,
  "page-size": 10,
  "page-number": 1,
  "total-pages": 2,
  "items": [
    {
      "item-id": "baad5130-ceab-49bc-a4b8-4bf57e43a16e",
      "value": "val4",
      "date-created": "2015-12-16T09:56:09",
      "date-modified": null
    },
    {
      "item-id": "6ff3ea18-16ab-4c9c-962a-73ea1a330da4",
      "value": "val5",
      "date-created": "2015-12-16T09:58:02",
      "date-modified": null
    }
  ]
}

```

To get value and details of specific value You need to provide item-id for fetch.
###4. Fetch storage values
Let's assume that item Id is provided through application. Then
```
GET /storage-items/{item-id}
```
You will get back `200 OK` status code and json representation with details for specified item Id of value.

```json

{
  "item-id": "6ff3ea18-16ab-4c9c-962a-73ea1a330da4",
  "value": "val5",
  "date-created": "2015-12-16T09:58:02",
  "date-modified": null
}

```


To Add value all that is needed is the value that will be added.

###5. Update storage item
Let's assume that You want to update storage value.

```
PUT /storage-items/{item-id}

```
You will get back `200 OK` status code and json representation with Id of updated value and created record status Updated.

```json
{
  "id": "6ff3ea18-16ab-4c9c-962a-73ea1a330da4",
  "created-record-status": "updated"
}

```
###6. Delete storage item
Let's assume that You want to delete storage value.

```
DELETE /storage-items/{item-id}

```
You will get back `200 OK` status code and json representation with Id of deleted value and created record status Deleted.

```json
{
  "id": "6ff3ea18-16ab-4c9c-962a-73ea1a330da4",
  "created-record-status": "deleted"
}

```

**Congratulations!** You have completed getting started tutorial on most common steps when working with Dialog API. To learn more look at the reference documentation for [available operations](swagger-ui).
