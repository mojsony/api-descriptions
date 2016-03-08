Possible Content API Problems
=================

To learn more see general guidance on [error handling](common-getstarted.html#error-handling).
Range of problem codes for this API is `55000 - 55199`.


Common problems
---------------

First 50 codes in a range `55000-55049` are reserved for situations described by standard http status codes.

Literal |  Code | Description                                          
------------------------------------ | -----:| ---------------------------------------------------  
bad-request                      | 55000 | Request is not valid. Field {field:} failed following validation {error:} 
forbidden                        | 55001 | User is not authorized to access resource or perform such a command on a resource
not-found                        | 55002 | Requested resource could not be found
gone                             | 55003 | Requested resource is no longer available
internal-error                   | 55004 | Unexpected error condition has occurred
not-implemented                  | 55005 | Service does not currently implement the operation, or it lacks the capability to fulfill the request. This implies possible future implementation
service-unavailable              | 55006 | Service is currently unavailable (because it is overloaded or down for maintenance). This is a temporary state



Content API Specific Problems
---------------

When request is valid and no standard status code describes situation, API will return http status code `440` with one of the following problems in the payload.

Literal                    | Code  | Description
---------------------------------|--------|-----------------------------------------
folder-locked             | 55001 | Folder {folder-name:} has been locked for changes.
folder-archived              | 55002 | Folder has been archived.
document-locked              | 55003 | Document has been locked for changes.
document-archived              | 55004 | Document has been archived.
max-upload-size-exceeded       | 55004 | Maximum size of content for upload has been exceeded. See details for current limit.
