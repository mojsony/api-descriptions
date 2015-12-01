Organization of source files
============================
[Swagger files](#swagger-files)
[Markdown files](#markdown-files)

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
Swagger files are machine readable descriptions that conform to Swagger 2.0 schema. Swagger can be written in yaml or json format. We use yaml as it is easier to read and write and than generate json from it as it is understood by wider set of tools.
####API specific
| file | description |
|------|-------------|
| `{api-name}.yaml` | Description of REST API operations and models |
| `{api-name}-events.yaml` | Description of events published by the module |

####Shared
| file | description |
|------|-------------|
|`responses.yaml` | Description of responses that are commonly used in many APIs. Examples are `validation-problem-response` and `default-response` |
|`models.yaml` | Description of models that are comonly used in many APIs. Examples are `currency` and `paged-list` |
|`parameters.yaml` | Description of parameters that are comonly used in many APIs. Examples are `sort-by` and `trim` |

Markdown files
---------------------------------
####API specific
| file | description |
|------|-------------|
| `{api-name}-guide.md` | Quick introduction guide for developers that will consume the API. |
| `{api-name}-guide.md#key-resources` | Description of key resources in the API. |
| `{api-name}-guide.md#getting-started` | Scenario with 3-6 steps that let developers taste most common operations |
| `{api-name}-problems.md` | Getting started guide for developers that will consume the API |
| `{api-name}-validations.md` | Getting started guide for developers that will consume the API |
| `{api-name}-classifications.md` | Getting started guide for developers that will consume the API |

####Shared
| file | description |
|------|-------------|
|`general-guide.md` | General guide with sections that explain handling of common topics |
|`general-guide.md#authentication` | How we handle authentication |
|`general-guide.md#versioning` | How we version our APIs |
|`general-guide.md#error-handling` | How we report errors |
|`general-guide.md#response-shaping` | How we let developers trim and expand data in responses |
|`general-guide.md#paging` | How we support paging of long lists |
|`general-guide.md#sorting` | How we support sorting of list items |
|`general-guide.md#filtering` | How we support filering of list items |
|`general-guide.md#searching` | How we support searching for matching items |
|`general-guide.md#hypermedia` | How we use hypermedia links |
|`general-guide.md#content-negotiation` | How we handle multiple representations |
|`general-guide.md#asynchronous-requests` | How we handle requests that take long to complete |
|`general-guide.md#events` | How we publish events |
|`general-guide.md#classifications-and-enumerations` | How we specify list of possible values in a field |
| `common-validations.md` | Literals and descriptions of common validations |
