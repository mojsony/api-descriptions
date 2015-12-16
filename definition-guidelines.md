
API Definition Guidelines
===================================
Here are some guidelines to keep in mind when definig an API interface.

> This page is work in progress. The list of guidelines will be expanded very soon.

General definition guidelines
-----------------------------
> ####DO
- Use swagger 2.0
- Use markdown syntax in descriptions and summaries
- Define tags at the begginng of yaml file and reference them for each operation.
- Define `default` response for each operation that cover general 4xx and 5xx errors other than 440
- Define `application/json` media type on API level not on operation level. 
- Define media types such as image/png or multipart/form-data at operation level.
- Define list of possible values formally as enum and also in description of a field or parameter.
- Name parameters that represent list of values in plural.
- Explain not only what request parameter represents but also how it affects processing of the request
- Use `kinds` and `kind` as name of the parameter or the field in model that describes primary class of something.  

> ####DON'T
- Define 400 response for every operation. This is covered by general error handling guidelines.
- Include default values of swagger in the file. Example: `deprecated: false`
- Define 440 response for GET request
- Do not use `type` to represent primary class or category of a concept.
Do not repeat the name of the thing being typed if it is clear from the context. Instead of `/accounts?account-kinds` use `/accounts?kinds`

Paths
-----
Paths define endpoint address of a resource after a base path for an API. Base path contains name of the api in kebab-case convention.
> ####DO
- Define base path
- Use kebab-case naming convention for path names

> ####DON'T
- Include version in path

Operations
----------
Operations combine a http method (GET, POST, PUT, PATCH, DELETE) and a resource path.
> ####DO
- Group operations on a resource by prefixing operation name with resource name in operationId as follows: {resource}_{operation}
- Keep operation names short
- When resource has a subresource such as accounts/{id}/balances parent resource should enable including subresource in response to GET with response shaping. Default assumption should be that subresources are not included

> ####DON'T
- Repeat resource name in operation name. Repositories_GetList instead Repositories_GetReporitoryList
- Use PUT method at collection resource

Model definitions
-----------------
In general we define 3 kinds of models as request/response payloads depending on the API style. CQRS style APIs have command models and read models. CRUD style APIs use same CRUD models for both read and write operations. To define event payloads that an API publishes we use event models.

> ####DO
- Name commands in imperative form (register-device) with {verb}-{noun-phrase}.
- Name events in past tense (device-registered)
- Use same verbs and nouns for both command and resulting event
- Inherit common paged-list model for read models that support paging.

> ####DON'T
- Name model definitions with prefixes such as API name. Instead of {api-name}.{model-name} use just {model-name}.


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
- Pass internal implementation eror codes and messages without mapping to public literals
- Use http status codes other than 440 for problems

> ####CONSIDER
- Naming literals with abbreviated words eg. `max-upload-size-reached` vs `maximum-upload-size-reached`

###Request validation

When request fails server validation, response should contain list of validation errors for each invalid field. Validation error is uniquely identified by its literal.

> ####DO
- Return HTTP status code 400 for request validation problem
- Keep validation literals as short as possible
- Name literals with lowercase dash convention for multiple words eg. `out-of-range`

> ####DON'T
- Define specific literals where shared generic literals can be used. For example, instead of max-lenght-5 use max-length and as  5 in message template "Maximum {0} characters allowed".
