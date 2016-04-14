---
visibility: internal
---
Case API Classifications
===============

Callback Categories
-----------------

This classification declares the category of problem for which the customer asks callback support.

Literal                       | Code   | Description
------------------------------|--------|-------------------------------------------
`payments`                    | 00001  | Asking for support for payment processes
`limit`                       | 00002  | Asking for support for payment limits
`credit`                      | 00003  | Asking for support for loans
`cards`                       | 00004  | Asking for support for payment cards
... | ... | ...

Case Topics
----------

This classification declares the topic of the case for complaint or service request.

Literal                       | Code   | Description
------------------------------|--------|-------------------------------------------
`general-enquiry`             | 00001  | General enquiry or question
`service-request`             | 00002  | Service request
`suggestion`                  | 00003  | Suggestion
`complaint`                   | 00004  | Complaint
`other`                       | 00005  | Other
... | ... | ...

Case API Enumerations
===============

Case Statuses
--------------

Enumeration that distinguishes status of particular case.

Literal           | Description
------------------|------------------------
accepted          | Accepted
active            | Active
rejected          | Rejected
canceled          | Canceled
resolved          | Resolved
closed            | Closed

Case Kinds
--------------

Enumeration that distinguishes different kinds of cases

Literal           | Description
------------------|------------------------
complaint         | Complaint
service-request   | Service Request
callback-request  | Callback Request

Case Channels
--------------

Communication channel through which case was received

Literal                        | Description
-------------------------------|------------------------
email                          | Email
face-to-face                   | Face-To-Face
fax                            | Fax
phone                          | Telephone
mail                           | Mail
other-communication-technology | Other Communication Technology
web-app                        | WEB Application
mobile-app                     | Mobile Application

Case Importances
--------------

The level of importance of the case

Literal           | Description
------------------|------------------------
low               | Low
medium            | Medium
high              | High


Complaint Importances
--------------

The level of importance of the complaint

Literal           | Description
------------------|------------------------
low               | Low
standard          | Standard
very-important    | Very Important

Service Request Importances
--------------

The level of importance of the service request

Literal           | Description
------------------|------------------------
low               | Low
medium            | Medium
high              | High
