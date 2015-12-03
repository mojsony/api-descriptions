
API Documentation Guidelines
===================================
Here are some guidelines to keep in mind when documenting APIs.
- [Documenting API problems](documenting-api-problems)
- [Documenting API validations](documenting-api-validations)
- [Documenting API overview](documenting-api-overview)
- [Documenting API methods](documenting-api-methods)
- [Documenting API models](documenting-api-models)

> This page is work in progress. The list of guidelines will be expanded very soon.

Documenting API problems
-----------------------------
Problems and their literals explain situations when request passes validation but will not be processed due to some business rule. Each problem is uniquely identified by its literal. Each literal is paired with numeric code that is easier to map in backend system.
For problems we use custom HTTP status code 440 as none of the standard HTTP status codes can be used for this. 

> ####DO
- Document all problems in a table with literal, code and description in `{api-name}-problems.md` markdown document
- When describing the problem explain the situation represented by literal in problems table and suggest resolution
- For each method that returns HTTP status code 440, list possible problems as bullets in description of 440 response. Format each bullet as hyperlink to `{api-name}-problems.md` markdown document that explains all possible problems for API. 

> ####DONT
 - Document internal implementation errors from system behind API interface


Documenting API validations
------------------------------
When API request fails validation, response with HTTP status code 400 contains list of validation errors for each invalid field. Validation error is uniquely identified by its literal. Validations are 

> ####DO
- Check wheather generic validation is already documented in `common-validations.md`
- Document all validations specific for an API in a table with literal and description in `{api-name}-validations.md` markdown document
- When describing the validation explain the failed assertion represented by literal in validations table as formatted message. For example, max-lenght validator with "Maximum {0} characters allowed"

> ####DONT
- Describe 400 response for your methods as they are described in general guidelines on error handling
- Define specific literals where shared generic literals can be used. For example, instead of max-lenght-5 use max-length and as  5 in message template "Maximum {0} characters allowed".

Documenting API overview
------------------------
> TODO

Documenting API methods
-----------------------
> TODO

Documenting API models
------------------
> TODO
