Possible problems
=================

When request is valid and no standard status code describes situation,
content management API will return status code `440` with one of the
following problems in the payload. To learn more see general
guidance on [error handling]()

Literal                    | Code  | Description
---------------------------------|--------|-----------------------------------------
folder-locked             | 55001 | Folder {folder-name:} has been locked for changes.
folder-archived              | 55002 | Folder has been archived.
document-locked              | 55003 | Document has been locked for changes.
document-archived              | 55004 | Document has been archived.
max-upload-size-exceeded       | 55004 | Maximum size of content for upload has been exceeded. See details for current limit.
