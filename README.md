![API](http://www.onedesk.com/wordpress/wp-content/uploads/2012/10/API-128x128.png) 
Descriptions
================
Documentation and contracts for REST and event based APIs.

Tools
-----
These tools that will make it easier to write swagger and markdown text files.
- [Api Studio](http://playground.apistudio.io/) `web based` `yaml+swagger` `json+swagger`
- [Stack Edit](https://stackedit.io) `web based` `markdown`
- [Visual Studio Code](https://code.visualstudio.com) `desktop` `markdown` `yaml`
> These tools are just suggestions, you are free to pick other tools or work in notepad if you prefer.

Guidelines
----------
Here are some guidelines to keep in mind when writing documentation and descriptions. 

###Events

###Classifications

###Validation response

###API specific problem codes
####DO
- Return 440 HTTP status code
- Specify problem literals and their codes for sitations that go beyond request field validations
- Keep your literals as short as possible
- Name literals with lowercase dash convention for multiple words eg. account-limit-reached
- When naming literals use passive voice and verbs in past tense document-locked
- Make codes more generic and supply details in text message
- Reserve a range of 500 codes above 50000 and below

###DONT
-

###CONSIDER
- Abbreviated workds in literal eg. max-upload-size vs maximum-upload-size-reached

###Validations
