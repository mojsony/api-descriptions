Working with REST APIs
======================
Asseco REST APIs represent collection endpoints that serve the needs of banking applications. While each API exposes specific functionality, technical concerns of API usage have been designed in a consistent manner to enable easier integration into channel applications. This section describes concerns and usage patterns that are common to all APIs.

Authentication
--------------
API endpoints that require authentication expect an [**OAuth2**][OAuth2] access token from client.

Before your client application can make API calls it must be registered to obtain its `client-id` and `client-secret` that will be used to identify client application itself and control access to APIs on per application basis. Registration process is completed manualy by administrator and each application is granted permissions for minimal scope of APIs necessary for its function.  

User facing client applications  authenticate users (customers or agents) by following [**OpenID Connect**][OpenIDConnect] protocol implemented by **Authentication API**. 

>APIs that call other APIs pass the original token they received in their backend requests.

To get access token client application follows one of the OpenID Connect flows with following endpoints hosted on **Authentication API**:

- **Authorize endpoint**: As defined in OAuth2 framework, this endpoint performs authentication and authorisation. Think of it as interacting with humans, it performs the login, consent, renders a UI, etc. Located at `v1/authentication/connect/authorize`.
- **Token endpoint**: Again from OAuth2, this endpoint allows the requester to get an access token, an ID token and optionally a refresh token. If the authorize endpoint is human interaction, this endpoint is machine to machine interaction (it is a web API). Located at `v1/authentication/connect/token`.
- **UserInfo endpoint**: New to OpenID Connect, this endpoint allows you to make a request using your access token to receive claims about the authenticated end-user. This user information could be included in the identity token, however this can cause bloat especially if we include things like profile pictures. Located at `v1/authentication/connect/userinfo`.
Credentials from user are presented at OAuth 2.0 endpoint that issues a bearer token with preconfigured set of claims.

```
+--------+                                   +----------------+
| Client |                                   | Authentication |
|        |                                   |      API       |
|        |                                   |----------------|
|        |---------(1) AuthN Request-------->|                |
|        |  +--------+                       |                |
|        |  |        |                       |                |
|        |  |  End-  |<--(2) AuthN & AuthZ-->|   /authorize   |
|        |  |  User  |                       |   /token       |
|        |  |        |                       |                |
|        |  +--------+                       |                |
|        |                                   |                |
|        |<--------(3) AuthN Response--------|                |
|        |                                   |----------------|
|        |---------(4) UserInfo Request----->|                |
|        |                                   |   /userinfo    |
|        |<--------(5) UserInfo Response-----|                |
|        |                                   |                |
+--------+                                   +----------------+
```
Using **Implicit** and **hybrid** flow you can authenticate end user and client with one roundtrip to Authentication API:

1. The Client sends a request to Authentication API `/authorize` enpoint.
2. The Authentication API authenticates the End-User based on passed or entered credentials.
3. The Authentication API responds with an `ID Token` and an `Access Token`.
4. The Client can send a (optionaly) request with the `Access Token` to the `/userinfo` endpoint.
5. The `/userinfo` endpoint returns `Claims` about the End-User.

Versioning
----------
Each API has multiple versions available to access at any one time. Each API is versioned independently as it evolves through major versions. Backward compatible changes such as adding additional elements, endpoints are not versioned.

Version label is an opaque string placed in URI just before API basepath. Examples:
```
       <---- host -----><ver><-- basepath -->
http://api.server-01.com/v1/correspondence/
http://api.server-01.com/v2/correspondence/
http://api.server-01.com/v1/location/
http://api.server-01.com/v1beta/location/
```
###Interface stability
Our banking APIs support wide variety of scenarios with resources and methods as interfaces. Some of these interfaces are standard and very stable. Others offer new functionality that is continuing to evolve.

We realize that you invest in these interfaces, and therefore must know when and how we expect them to change. For that reason, we define interface stability labels and uses these in definitions of API methods.

| Label| Meaning|
|-|-|
| **Stable** | This documented interface is expected to undergo only backwards-compatible changes between major releases. Once we release new major version we are still supporting a previous major version for a period of `one year`. |
| **Evolving** | This documented interface is continuing to evolve and so is expected to change, potentially in backwards-incompatible ways even in between major releases. Changes are announced as documentation updates `90 days` before API releases. 
| **Deprecated** | This interface is deprecated and likely to be removed in a future release. For previously stable interfaces, the change was likely announced in a previous release. Deprecated interfaces will be removed from our APIs. |

###Backward compatibility policy for stable APIs
Different changes of APIs can have different impact on your client. Your implementation of client code should tolerate backward compatible changes and handle breaking changes gracefully.  

| Change area | Backward compatible change (documentation update) | Breaking change (release of new major version) |
|----|----|----|
| Resources (collection, singleton) | New resource, sub-resource, command, representation; Moving resource to new URI with redirection from previous | Removing existing resource without redirection; Removing existing operation |
| Resource URIs and verbs |	New URI template and endpoint | Changing URI path template; Adding mandatory query argument; Renaming existing query argument; Changing the type of existing argument; Changing HTTP verb |
| Command and resource models	| Adding optional field; Changing the order of existing fields; Making mandatory field optional | Adding mandatory field; Renaming existing field; Changing type of existing field; Changing the placement of existing field in representation structure; Removing existing field |
| Problems| Introducing new problem code  | Changing the meaning of existing problem code|
| Validations |	Introducing new command field or URI argument validation rule with warning severity | Changing existing validation rule to be more tolerant than before; Removing existing validation rule; Introducing new command field or URI argument validation rule with error severity; Changing existing validation rule to be more strict than before |
| Enumerations | New enumeration; New enumeration literal; Changing descriptions or translations | Removing enumeration literal; Forcing enumeration on previously unrestricted field |
| Classifications | New classification; New classification value; Removing classification value; Changing descriptions or translations; Renaming classification literal | Forcing classification on previously unrestricted field |

Enumerations and classifications
--------------------------------
String parameters and fields in API contracts can be restricted to predefined list of acceptable  literals and codes. **Enumerations** represent closed set of values that developers who consume API can refer to in their implementation and expect to be stable across different implementations. **Classifications**, on the other hand, are open set of values that may be extended and changed over time and across different implementations. Developers refering to specific classification literals in their code must expect changes over time and across different implementations.
Enumeration values are part of contract, while classification values are not.

> By convention name of enumeration or classification is plural as it describes set of values. Literal name is in *kebab case*, while title is in *title case*. For example, classification with title: `Transaction Codes` by convention has literal name `transaction-codes`.
Enumerations values are explained with `literal` and `description`, while classification values also have optional short mnemonic or numeric `code` that uniquely identifies classification value.

Error handling
--------------
Requests made to our APIs can result in a number of different error responses, and there are a few basic recovery tactics. The following topic describes the recovery tactics, and provides a list of error values with a map to the most common recovery tactic to use.
Error is always indicated with standard 4xx and 5xx http status codes. With status code 400 we return more details on validation errors, while with status code 440 we return more details on specific business rules that were violated by request.

###Common http status codes used accross APIs

| status code | when used |
|--|--|
| `401 Not authorized` | Used to indicate that request must be authenticated but valid access token was not supplied  |
| `403 Forbidden` | Used to indicate that access to API is not allowed, even though the request was authenticated with valid access token. |
| `404 Not found` | Used to indicated that there are no resources that match the request. For GET request that fetch single resource based on identifiers supplied in path this means that resource with such identifier was not found. For GET requests that filter or page result this means that no resource matches filter predicates. For POST requests that send commands at identified resource this means that resource with such identifier was not found.  |
| `500 Internal error` | Used to indicate that API implementation encountered an unexpected condition which prevented it from fulfilling the request. |
| `503 Not implemented` | Used to indicate that API implementation does not yet support the functionality of a documented method. |

### 400 - Validation errors
When request fails server validation, response contains list of validation errors for each invalid field. Validation error is uniquely identified by its literal and is not specific to APIs.

Example problem response payload (json):
```json
{
  [
    {
      "field": "phone-number",
      "errors": [
          {
              "error":"invalid-format",
              "message":"Data supplied for the field is in invalid format"
          },
          {
              "error":"max-length",
              "message":"Data supplied for the field exceeds maximum allowed length"
          }
      ]
    },
    {
      "field": "account-number",
      "errors": [
          {
              "error":"check-digit-invalid",
              "message":"Check digit is invalid for this field"
          }
      ]
    }    
      
  ]
}
```

Elements of validation errors model:

| Property Name	| Type/Format |	Description  |
|-|-|-|
|`[]`|array| List of fields with errors |
|`[].field`|string| Name of the field that has some validation errors  |
|`[].errors[]`|array| List of validation errors for a specific field |
|`[].errors[].error`|string| Unique literal that identifies validation error |
|`[].errors[].message`|string| Message explaining failed validation. |

Validation errors:

|Validation error literal| Description |
|--|--|
|`max-length`| Value supplied exceeds maximum allowed length |
|`min-length`| Value supplied does not meet minimum length |
|`required` | Mandatory field or parameter was not supplied |
|`out-of-range`| Value supplied was out of allowed range |
|`invalid-format`| Value supplied does not have expected format |
|`unknown-enum` | Value supplied does not belong to enumeration | 
|`not-on-list` | Value supplied does not belong to classification | 
|`check-digit-invalid` | Value supplied does not conform to check digit validation |
|`combination-required` | Parameter must be used with other parameters that were not supplied |

### 440 - Business problem
Business problems may be returned for request with verbs that affesct state (POST, PUT, PATCH, DELETE) in situations when request is formally valid, business rule or policy does not allow processing and none of the standard HTTP status codes explaines the situation well enough. 

Each problem is uniquely identified by stable literal and numeric code that is used to map to backend system implementations. APIs document their domain specific problems in a `Problems` page of their documentation. In documentation for specific API request, when 440 response is possible, documentation lists possible problems.

Example problem payload (json):
```json
{
  "problem": "document-locked",
  "message": "Document you are trying to manipulate is locked by another user.",
  "details": "User john.doe has locked the document."
}
```
Elements of problem model:

| Property Name	| Type/Format |	Description  |
|-|-|-|
|`problem`|string| Unique literal that identifies specific problem |
|`message`|string| Message explaining the situation and optionaly remedies.  |
|`details`|string| Optional details supplied for troubleshooting |


Events
------
Events are used to publish the fact that something happened to interested subscribers. Each API specifies events published and their payload in `Events` page. Events contain minimal payload that describes what happened and triggers subscriber processing. Subscriber is expected to get any additional information that may be needed in a "push to pull" manner. 

Each event publsihed by API is uniquely identified by its name. Events happen in a lifecycle of a resource that is classified by `aggregate-kind` and identified by `aggregate-id`. 

Bulk optimizations
-----------------
When API endpoint is optimized for bulk reads and bulk writes you can expect that their payload contract is flattened, default content type to be `text/csv` and http compression to be used by default. This minimizes network traffic and simplifies processing at other end.

Commonly used query parameters
-----------------------
###Pagination
When a collection resource supports pagination of results you can supply pagination control parameters and expect pagination related fields in response payload.
```http
GET correspondence/communications?page=1&page-size=5 HTTP/1.1
```
| Parameter	| Type/Format |	Description  |
|-|-|-|
|`page`|integer| One based index of the page to return. Default index `1` s used when parameter is not supplied  |
|`page-size`|integer| Number of items to return on a page. Default size `10` is used when parameter is not supplied |

```json
{
    "page": "1",
    "page-size": "5",
    "total-count": "123",
    "total-pages": "21",
    ...
}
```

###Sorting
When a collection endpoint supports sorting of results you can supply sorting control parameters 
`sort-by` and `sort-order` and expect a sort related fields in the sorted response payload.

```http
GET correspondence/communications?sort-by=status&sort-order=desc HTTP/1.1
```
```json
{
    "sort-order": "desc",
    "sort-by": "status",
    ...
}
```
| Parameter	| Type/Format |	Description  |
|-|-|-|
|`sort-by`|string| Name of the response field to sort by. Field must be supplied on lowercase dash naming convention |
|`sort-order`|string enum: `asc`, `desc`| Ascending or descending order. Default order `asc` is used when parameter is not supplied |

###Shaping
When an endpoint supports shaping of responses to GET requests you can supply shaping control query parameters `trim` and `include` and expect only specified set of fields in the response payload. 
If you do not specify fields to include or trim, response will contain fields returned by default according to reference documentation. You can remove default set of returned fields by using `trim=*` and then add only fields you need with include. Reverse also applies so you can start from full set of fields with `include=*` and then remove only fields you don't need with trim.

If endpoint supports shaping, scalar fields in a response model object are returned by default while nested objects and arrays are returned according to sensible defaults specified in documentation.

```http
GET correspondence/communications?include=history&trim=history.description HTTP/1.1
```
| Parameter	| Type/Format |	Description  |
|-|-|-|
|`trim`|string format:`csv`| Comma separated list of fields to trim from response. Field names must be supplied on lowercase dash naming convention. Nested fields are accesed with dot notation. |
|`include`|string format:`csv`| Comma separated list of fields to include in response. Field names must be supplied on lowercase dash naming convention. Nested fields are accesed with dot notation.  |

###Synchronization
When a collection resource supports incremental synchronization you can supply `sync-timestamp` as query parameter and expect only collection items that were added, changed or deleted since point in time represented by timestamp. Each collection item will have a `sync-timestamp` field so API consumer is responsible to keep track of latest synchronization timestamp processed for specific collection. Synchronization timestamp can have any implementation and format as long as it is guaranteed to be monotonicaly increasing with every change.


###Filtering
Many collection resources accept a list of predefined optional query parameters that filter returned results. Parameters are combined with a logical AND. Unless otherwise specified parameters that filter text will assume case-insensitive match. When parameter contains multiple values, unless otherwise specified, result is matched on any of the supplied values.

```http
GET correspondence/communications?contact-medium=sms&status=delivered HTTP/1.1
```


###Searching
Some collection enpoints enable expression based search queries. 

```http
GET party-data/individuals?q=John+Doe HTTP/1.1
```


[OpenIDConnect]:http://openid.net/specs/openid-connect-core-1_0.html
[OAuth2]:http://oauth.net/2/