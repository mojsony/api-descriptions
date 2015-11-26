Content Management API 
======================
Content Management API provides access to documents stored in content management repositories. Any form of unstructured content (files) such as documents, templates and images can be organized into a folder structure that follows conventions understood by applications. API exposes operations to upload and download content and manipulate its metadata.     
   ![Folders](http://www.easysitecms.net/_resources/assets/inline/custom/23/875.png)
   
Key Resources
-------------
Content Management has three top level collection resources: repositories, folders and documents. Documents have additional content stream resource.

Resource | Description
----------- |-----------
*repository*  | Represents a top level container for content. Behind API repository is always hosted on a single system such as full blown DMS or simplified DMS using file system and database store. Different repositories are often used to separate official correspondence such as contracts and legal documents from web content such as images and banners.
*folder*      | Serves as the anchor for a collection of documents and child folders. The folder has an implicit hierarchical relationship with each document or other folder in its collection. A folder object does not have its own *content stream* and is not versionable. Folder structure and folder metadata attributes are used according to conventions expected by consuming applications.
*document*    | Represents elementary information entity managed by the repository like contract, image or template. Depending on its kind, a document object may be discoverable by search query operations. Once document is uploaded it gets unique id provided by repository that can be used to get the content irrespective of folder structure. Document can also be located by concatenating folder path with document file name. Documents contain binary *content stream* and metadata attributes that follow application conventions. Documents can be versioned.
*content stream* | A blob containing a binary stream of content. Each content stream has a MIME Media Type, as deﬁned by RFC2045 and RFC2046. A content stream’s attributes are represented as properties of the content stream’s containing document. There is no MIME type speciﬁc attribute or name directly associated with the content stream outside of the document object.

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
Now that you've authenticated your app, you can call the Content Management API with your access token against the URL root below, combined with one of the root resources.  Content Management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Content Management | `https://api.asse.co/content`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /dms/documents/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Pick your repository
Before you can store and retreive documents you need to pick correct repository. In most cases there will be two repositories, one for more offical documentation such as contracts and another for more relaxed content such as profile images.
You can list available repositories at following endpoint:
```
GET /repositories
```
You will get back `200 OK` status code and json representation with a list of repository names. To access content in repository you will use `folders` and `documents` resources prefixed with repository name.
```json
[
  {
    "repository-id": 1,
    "repository-name": "mchub"
  },
  {
    "repository-id": 2,
    "repository-name": "dms"
  }
]
```


###4. Create folder to store some documents
Let's assume that someone has created folder called `customers` in `dms` repository for you to store customer profile documents for each customer.
To create folder you need to post `folder` metadata representation as json to following endpoint:

```
POST /dms/folders
```
```json
{
  "kind": "folder" 
  "name": "jabon0007", //convention
  "path": "customers", //create under this path
  "folder-purpose": "customer-profile", //convention
}
```
You will get back `201 Created` status code and json representation with a created folder. Location header will contain URL for newly created folder.
```
Location: http://api.asse.co/content/dms/folders/ee48b17534c9
```
```json
{
  "kind": "folder"
  "name": "jabon0007",
  "path": "customers",
  "folder-purpose": "customer-profile"
  "id": "ee48b17534c9", //server assigned
  "created-on": "2015-11-23T07:08:30.000Z", //server assigned
  "created-by": "jabon007", //server assigned
  "changed-on": "2015-11-23T07:08:30.000Z", //server assigned  
}
```
To store documents you will need folder id or path.
###4. Upload some documents to folder
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
  "kind": "document"
  "name": "headshot.png",
  "path": "customers/jabon0007",
  "filing-purpose": "customer-picture",   
  "id": "mj20b12534r4",
  "changed-on": "2015-10-20T23:22:10.000Z",
  "created-on": "2015-11-23T07:08:30.000Z",
  "created-by": "jabon0007",
}
```
###5. List folder contents
Now lets list the folder contents and verify that it contains on image.
```
GET /dms/folders/ee48b17534c9
```

You will get back `200 OK` status code and json representation with a list of repository names. To access content in repository you will use `folders` and `documents` resources prefixed with repository name.
```json
{
  "items": [
    {
      "kind": "document"
      "name": "headshot.png",
      "path": "customers/jabon0007",  
      "id": "mj20b12534r4",
      "changed-on": "2015-10-20T23:22:10.000Z",
      "created-on": "2015-11-23T07:08:30.000Z",
      "created-by": "jabon0007"
    }
  ]
  "total-count": 1, //endpoint supports paging
  "page-size": 10,
  "page": 1,
  "total-pages": 1,
  "sort-order": "asc", //endpoint supports sorting
  "sort-by": "created-on",  
}
```
###6. Download the document
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