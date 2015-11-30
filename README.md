![API](http://www.onedesk.com/wordpress/wp-content/uploads/2012/10/API-128x128.png) 
Documentation for ASEE public APIs
==================================

Guidelines
----------
Be sure to check the [guidelines](guidelines.md) before you start writing.

Writing Tools
-------------
These tools that will make it easier to write swagger and markdown text files.
- [Api Studio](http://playground.apistudio.io/) `web based` `yaml+swagger` `json+swagger`
- [Stack Edit](https://stackedit.io) `web based` `markdown`
- [Visual Studio Code](https://code.visualstudio.com) `desktop` `markdown` `yaml`

> These tools are just suggestions, you are free to pick other tools or work in notepad if you prefer

Client library generator
------------------------
Use Autorest to generate client library in C# and verify that generated code compiles properly.
- [Autorest](https://www.nuget.org/packages/autorest/) 

Organization of source files 
----------------------------
See how we [organize](organization.md) documentation source files.


Build process
-------------
1. Documentation writer checks-in yaml / markdown file
2. Build script converts swagger files from yaml to json
3. Build script generates static html from markdown using templates and pretzel tool
4. Build script publishes documentation site
