---
visibility: internal
---

<span class="icon"></span>Payment API Guide
======================
Payment API provides access to documents stored in content management repositories. Any form of unstructured content (files) such as documents, templates and images can be organized into a folder structure that follows conventions understood by applications. API exposes operations to upload and download content and manipulate its metadata.
   
Key Resources
-------------
Payment API has four top level collection resources: transfers, beneficiaries, drafts and templates.

Resource | Description
----------- |-----------
*transfers* | Allows viewing all kinds of transfers, their status and all other data about them. Also provides way to initiate, validate, and cancel transfers.
*beneficiaries* | Provides methods for viewin, creating, updating and deleting beneficiaries.
*drafts* | Consist of methods for viewing details, create, update and delete drafts for all kinds of transfers.
*templates* | Consists of methods that get, create, update and delete templates.

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Payment API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Content Management API with your access token against the URL root below, combined with one of the root resources.  Content Management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Payment | `https://dev.asseco-see.com/v1/payment`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /transfers/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Query transfers
It is 
```
GET /transfers
```
You will get back `200 OK` status code and json representation with a list of transfers.
```json
{
  "total-count": 0,
  "page-size": 10,
  "page-number": 1,
  "total-pages": 0,
  "items": [],
  "navigations": [
    {
      "href": null,
      "rel": "first"
    },
    {
      "href": null,
      "rel": "previuos"
    },
    {
      "href": null,
      "rel": "self"
    }
  ]
}
```


###4. Create folder to store some documents
Let's assume that someone has created folder called `customers` in `dms` repository for you to store customer profile documents for each customer.
To create folder you need to post `folder` metadata representation as json to following endpoint:

```
POST /dms/folders
```

```json
{
  "kind": "folder", 
  "name": "jabon0007",
  "path": "customers", 
  "folder-purpose": "customer-profile"
}
```
You will get back `201 Created` status code and json representation with a created folder. Location header will contain URL for newly created folder.
```
Location: http://api.asse.co/content/dms/folders/ee48b17534c9
```

```json
{
  "kind": "folder",
  "name": "jabon0007",
  "path": "customers",
  "folder-purpose": "customer-profile",
  "id": "ee48b17534c9",
  "created-on": "2015-11-23T07:08:30.000Z", 
  "created-by": "jabon007", 
  "changed-on": "2015-11-23T07:08:30.000Z"
}
```
To store documents you will need folder id or path.
###5. Upload some documents to folder
Now you are ready to upload your first document. You will need to post multipart/form-data representation with file pased in content-stream parameter.

```
POST dms/folders/ee48b17534c9
Content-Type: multipart/form-data

content-stream: C:\users\james\documents\headshot.png
name: headshot.png
media-type: image/png
filing-purpose: customer-picture
```
You will get back `201 Created` status code and json representation with a created document. Location header will contain URL for download.

```
Location: http://api.asse.co/content/dms/documents/mj20b12534r4
```
```json
{
  "kind": "document",
  "name": "headshot.png",
  "path": "customers/jabon0007",
  "filing-purpose": "customer-picture",   
  "id": "mj20b12534r4",
  "changed-on": "2015-10-20T23:22:10.000Z",
  "created-on": "2015-11-23T07:08:30.000Z",
  "created-by": "jabon0007"
}
```
###6. List folder contents
Now lets list the folder contents and verify that it contains on image.
```
GET /dms/folders/ee48b17534c9
```

You will get back `200 OK` status code and json representation with a list of repository names. To access content in repository you will use `folders` and `documents` resources prefixed with repository name.
```json
{
  "items": [
    {
      "kind": "document",
      "name": "headshot.png",
      "path": "customers/jabon0007",  
      "id": "mj20b12534r4",
      "changed-on": "2015-10-20T23:22:10.000Z",
      "created-on": "2015-11-23T07:08:30.000Z",
      "created-by": "jabon0007"
    }
  ],
  "total-count": 1, 
  "page-size": 10,
  "page": 1,
  "total-pages": 1,
  "sort-order": "asc", 
  "sort-by": "created-on"  
}
```
###7. Download the document
Finally lets use that url we got back in step 4. and download the document and verify that it is indeed the same image.
Just paste this in browser address bar:
```
GET http://api.asse.co/content/dms/documents/mj20b12534r4
```
You will get back `200 OK` and binary content stream with appropriate Content Type and Content Disposition headers. Download will start immediately.
```
Content-Type: image/png
Content-Disposition: attachment; filename="headshot.png"
``` 

**Congratulations!** You have completed getting started tutorial on most common steps when working with Content Management API. To learn more look at the reference documentation for [available operations](swagger-ui).
