
Guidelines
==========
Here are some guidelines to keep in mind when writing documentation and descriptions. 

API specific problem codes
------
> ####DO
- Return 440 HTTP status code
- Specify problem literals and their codes for sitations that go beyond request field validations
- Keep your literals as short as possible
- Name literals with lowercase dash convention for multiple words eg. account-limit-reached
- When naming literals use passive voice and verbs in past tense document-locked
- Make codes more generic and supply details in text message
- Reserve a range of 500 codes above 50000 and below

>####DONT
- Pass internal eror codes and messages without mapping to public literals

>####CONSIDER
- Abbreviated workds in literal eg. max-upload-size vs maximum-upload-size-reached

