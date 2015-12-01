
API Design and Documentation Guidelines
===================================
Here are some guidelines to keep in mind when writing documentation and descriptions.

> This page is work in progress. The list of guidelines will be expanded very soon.

Problems
--------
Problem codes help in situations when request is formally valid and none of the standard HTTP status codes explaines the problem well. Each problem is uniquely identified by its literal. Each literal is paired with numeric code that is easier to map in backend system. 

> ####DO
- Return HTTP status code 440 for API specific problems
- Keep your literals as short as possible
- Name literals with lowercase dash convention for multiple words eg. `account-limit-reached`
- Name literals using passive voice and verbs in past tense eg. `document-locked`
- Make literals more generic and then supply specific details in `details` field for problem instance
- Reserve a range of 200 codes between 50000 and 60000

> ####DONT
- Pass internal implementation eror codes and messages without mapping to public literals

> ####CONSIDER
- Naming literals with abbreviated words eg. `max-upload-size-reached` vs `maximum-upload-size-reached`

Request validation
------------------
When request fails serverv validation, response should contain list of validation errors for each invalid field. Validation error is uniquely identified by its literal.

> ####DO
- Return HTTP status code 400 for request validation problem
- Keep validation error literals as short as possible
- Name literals with lowercase dash convention for multiple words eg. `out-of-range`
- Make literals more generic and then supply specific details in `details` field for problem instance

> ####DONT
- Pass internal implementation eror codes and messages without mapping to public literals
