Organization of source files
============================
```
/
│   README.md
│   guidelines.md  
│   organization.md
|   ...
│   
└───/{api-name}
    |
    ├───/src
    │   {api-name}.yaml
    │   {api-name}-events.yaml
    │   {api-name}-guide.md
    │   {api-name}-problems.md	
    │   {api-name}-classifications.md
    |   {api-name}-validations.md (optional)
    │   
    └───/swagger (generated)
    │   problems.json
    │   models.json
    │   parameters.json    
│   
└───/common
    |
    ├───/src
    │   responses.yaml
    │   models.yaml
    │   parameters.yaml
    |   overview.md
    │   authentication.md
    │   versioning.md	
    │   error-handling.md	
    │   response-shaping.md	
    │   paging.md	
    │   sorting.md	
    │   filtering.md	
    │   searching.md	
    │   hypermedia.md	
    │   content-negotiation.md	
    │   async-requests.md	
    │   events.md	
    │   classifications-and-enums.md	
    │   common-validations.md
    │   
    └───/swagger
    │   responses.json
    │   models.json
    │   parameters.json
```
Swagger files
---------------------------------
####API specific
| file | description |
|------|-------------|
| `{api-name}.yaml` | Getting started guide for developers that will consume the API |
| `{api-name}-events.yaml` | Getting started guide for developers that will consume the API |

####Shared
| file | description |
|------|-------------|
|`responses.yaml` | Overview of topics guide for developers that will cover following topics the API |
|`models.yaml` | Overview of topics guide for developers that will cover following topics the API |
|`parameters.yaml` | Overview of topics guide for developers that will cover following topics the API |

Markdown files
---------------------------------
####API specific
| file | description |
|------|-------------|
| `{api-name}-guide.md` | Getting started guide for developers that will consume the API |
| `{api-name}-problems.md` | Getting started guide for developers that will consume the API |
| `{api-name}-validations.md` | Getting started guide for developers that will consume the API |
| `{api-name}-classifications.md` | Getting started guide for developers that will consume the API |

####Shared
| file | description |
|------|-------------|
|`overview.md` | Overview of topics guide for developers that will cover following topics the API |
| `common-validations.md` | Literals and descriptions of common validations |
|`authentication.md` | |
|`versioning.md` | |
|`error-handling.md` | |
|`response-shaping.md` | |
|`paging.md` | |
|`sorting.md` | |
|`filtering.md` | |
|`searching.md` | |
|`hypermedia.md` | |
|`content-negotiation.md` | |
|`asynchronous-request-processing.md` | |
|`events.md` | |
|`classifications-and-enumerations.md` | |
