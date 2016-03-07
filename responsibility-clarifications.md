Clarification of API boundaries and responsibilities
====================================================

Defining principle of BIAN service landscape is that blocks are normalized and their functions do not overlap. 
Maintaining clear boundaries and avoiding overlaps is what makes a difference between stable coherent set of APIs and random chaos in the long term.
Tight project schedule for delivery of v1 APIs, structure of project teams and business units and lack of code reviews led to v1 API definitions that did not respect boundaries and responsibilities between APIs.

- [Account Data v1 Clarifications](responsibility-clarifications.md#account-data-v1-clarifications)

Responsibility problems in practice
-----------------------------------
In practice problems happen when one API *hijacks* some responsibilities (logic and/or data) of another.

| problem | description |
|--------:|-------------|
| `operation-hijack` | Providing operation that is responsibility of another API. This often happens when there is misunderstanding of aggregates (BIAN control record). Remedy is to remove information from API definition and specify removed elements |
| `delegation-hijack` | Missing mandatory delegation to another API. This often happens with process oriented APIs that receive request but should delegate the final exection |
| `information-hijack` | Returning information maintained by another API. This often happens when there is misundarstanding of a resource (aggregate) that some information belongs to such as account vs arrangement. Exceptions are allowed for APIs whose responsibility is to aggregate information such as party-profile and channel-dialog.|

Account Data v1 Clarifications
----------------------------------
| v0 implementor | v1 api method |  issue | responsible api | v1 responsible method | elements to remove |
|----------------|---------------|--------|-----------------|-----------------------|--------------------|
| PUB RT	| `GET /accounts/{id}` | `information-hijack` | `customer-arrangement` | `GET /arrangements/{id}` | 

