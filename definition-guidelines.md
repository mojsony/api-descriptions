API Definition Guidelines
===================================
Here are some guidelines to keep in mind when defining an API interface.
- [General guidelines](#general-guidelines)
- [Paths](#paths)
- [Operations](#operations)
- [Models](#models)
- [Errors](#errors)

> This page is work in progress. The list of guidelines will be expanded very soon.

General guidelines
------------------
> ####DO
- Use swagger 2.0
- Use markdown syntax in descriptions and summaries 
- Define tags at the beginning of yaml file and reference them for each operation.
- Define `default` response for each operation that cover general 4xx and 5xx errors other than 440
- Define `application/json` media type on API level not on operation level. 
- Define media types such as image/png or multipart/form-data at operation level.
- Define list of possible values formally as enum and also in description of a field or parameter.
- Name parameters that represent list of values in plural.
- Explain not only what request parameter represents but also how it affects processing of the request


> ####DON'T
- Don't define 400 response for every operation. This is covered by general error handling guidelines.
- Don't include default values of swagger in the file. Example: `deprecated: false`
- Don't define 440 response for GET request
- Don't repeat the name of the thing being typed if it is clear from the context. Instead of `/accounts?account-kinds` use `/accounts?kinds`

Resources and paths
-------------------
In a RESTful API, resources are key information abstraction concept ([learn more](http://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_2_1_1)).
Resource is an entity of certain kind, with associated data, relationships to other resources, and a set of methods that operate on it. 
Path is endpoint address of a resource that follows the base path for an API. Base path is named entrypoint for an API. Relationship between resources can be represented in path as subresources.
Resources are either collections or singletons. Collection resources typically have child resources that are addressable.

> ####DO
- Define base path for API 
- Use kebab-case naming convention for path names
- Use nouns to name resources
- Use plural form of a noun to name collection resources
- Group specialized resources that have generic base. Transfers/ internal transfers credit transfers
- Use plural form of a noun phrase that describes process name for work item resources without request, order, case or similar suffix. Use `card-activations` instead of `card-activation-requests`

> ####DON'T
- Don't include base path in path definition for specific resoruce
- Don't use verbs in names of work item collection resources. Instead of `activate-card-requests` use `card-activations` noun phrase.

Query parameters
----------------
> ####DO
- Define all filter query parameters on a collection resource as optional. This applies for customer-id filter parameter as some applications do .
- Define optional customer-id filter parameter for collection resources that expose customer specific resources. Authorization rules must decide if the caller (customer, employee or automated process) is allowed to access the resource. 
 
> ####DON'T
- Don't use claims from bearer tokens such as customer-id for result filtering. Declare optional query parameter instead.

Operations
----------
API operations represent combination of an http method (GET, POST, PUT, PATCH, DELETE) and a resource path. 
When it comes to operations that modify state of a resource, **CQRS** style APIs exposes domain specific **commands** and **rich domain logic**, while **CRUD** style APIs expose resources for **data manipulation** with domain logic reduced to simple structural constraints and validation. 
In client side libraries and server-side implementation stubs operations are named as rpc methods grouped arround a resource.

> ####DO
- Group operations on a resource by prefixing operation name with resource name in swagger `operationId` as follows: `{resource}_{operation}`
- Keep operation names short
- Use `POST` http verb for commands that affect state in domain specific semantics such as activate, cancel, terminate, reject etc. when server is responsible for domain logic.
- Use `PUT` http verb to allow clients to replace a resource when client is responsible for domain logic and server just stores the data in CRUD manner.
- Use `PATCH` http verb to allow clients to modify any part of resource when client is responsible for domain logic and server just stores the data in CRUD manner.
- Define success https status codes appropriate for http request verbs
    - GET: `200 OK`
    - POST:
        - `201 Created` for requests and commands that create new resource instance
        - `202 Accepted` for requests and commands accepted but not performed immediately
        - `200 OK` for commands and requests that are performed immediately
    - PUT:
        - `200 OK` when response contains representation of replaced resource 
        - `204 No Content` when response does not contain representation of a replaced resource
    - PATCH:
        - `200 OK` when response contains representation of modified resource 
        - `204 No Content` when response does not contain representation of a modified resource        
    - DELETE:
        - `200 OK` when response contains representation of a deleted resource 
        - `204 No Content` when response does not contain representation of a deleted resource
- When resource has a subresource such as `accounts/{id}/balances` parent resource should enable including subresource in response to `GET` with response shaping. Default assumption should be that subresources are not included

> ####DON'T
- Don't repeat resource name in operation name. Repositories_GetList instead Repositories_GetReporitoryList
- Don't use PUT method at collection resource
- Don't use DELETE verb for operations that have semantic other than delete such as cancellation, termination, closing etc.


Models
------
In general we define 3 kinds of models as request/response payloads depending on the API style. CQRS style APIs have command models and read models. CRUD style APIs use same CRUD models for both read and write operations. To define event payloads that an API publishes we use event models.

> ####DO
- Name command models in imperative form with `{verb}-{noun-phrase}`. Example: `register-device`
- Name events in past tense `{noun-phrase}-{verb}`. Example: `device-registered`
- Name singular read models in CQRS and CRUD models consistently as resource names. Example: for singular read model returned at `/accounts/123` use name `account`.
- Name collection read models as singular resource name with suffix `list`. Example: for collection read model returned at `/accounts` use name `account-list` instead of `accounts`.
- Use same verbs and nouns for both command and resulting event
- Inherit common paged-list model for read models that support paging.

> ####DON'T
- Don't include prefixes such as API name in model name. Instead of `content-management.folder` use just `folder`.


Enumerations and classifications
-------------------------
When modeling request parameters and fields we often need to constraint its value to a predefined list of acceptable values.
Classifications and enumerations are important part of API contract as they hide internal implementation codes.
While classifications are open lists maintained by financial institution, enumerations are closed lists of acceptable values defined by ASEE that are modified and versioned with as a part of contract. 
Developers of API client applications can safely refer to specific enumeration values in their code, 
but should refrain from refering to specific classification values as those are open for modification at any time.
  
> ####DO
- Define literals to represent enumeration and classification values in fields and parameters
- Make literals short and use single word literals when ever possible
- Make literals standard across different implementations (PUB, EXP, BAPO, ABSOLUT...)
- Use `kind` as name of the parameter or the field in model that describes primary class of something.
- Define `/classifications` resource that lists all classification schemes used in API contracts
- Define `/classifications/{scheme}` resource that lists all classification values for a given classification scheme
- Define `status` classifications that specify possible statuses of a certain kind of work item 
- Use common `customer-friendly-status` enumeration that describes simplified status of all work items initiated by customer. Possible values:     
    -	`active`
    -	`abandoned`
    -	`expired`
    -	`suspended`
    -	`complete`
    -	`rejected`

> ####DON'T
- Don't use numeric codes to represent enumeration and classification values in fields and parameters
- Don't use internal implementation codes of specific implementation (PUB, EXP, BAPO, ABSOLUT...)
- Don't use `type` to define primary class or category of a concept. Use `kind` instead of `type`.

Errors
------
###Problems
Problem codes help in situations when request is formally valid and none of the standard HTTP status codes explaines the problem well. Each problem is uniquely identified by its literal. Each literal is paired with numeric code that is easier to map in backend system. 

> ####DO
- Return HTTP status code 440 for API specific problems
- Keep your literals as short as possible
- Name literals with lowercase dash convention for multiple words eg. `account-limit-reached`
- Name literals using passive voice and verbs in past tense eg. `document-locked`
- Make literals more generic and then supply specific details in `details` field for problem instance
- Reserve a range of 200 codes between 50000 and 60000

> ####DON'T
- Don't pass internal implementation eror codes and messages without mapping to public literals
- Don't use http status codes other than 440 for problems

> ####CONSIDER
- Consider naming literals with abbreviated words eg. `max-upload-size-reached` vs `maximum-upload-size-reached`

###Validations

When request fails server validation, response should contain list of validation errors for each invalid field. Validation error is uniquely identified by its literal.

> ####DO
- Return HTTP status code 400 for request validation problem
- Keep validation literals as short as possible
- Name literals with lowercase dash convention for multiple words eg. `out-of-range`

> ####DON'T
- Don't define specific literals where shared generic literals can be used. For example, instead of max-lenght-5 use max-length and as  5 in message template "Maximum {0} characters allowed".
