---
visibility: public
---
Campaign API Classifications
===============

Zone Kinds
---------

Classification explains in which presentation zone on client application
marketing resource should be displayed.

Literal              | Code  | Description
---------------------|-------|----------------------------------
`pre-login`          | 00001 | Pre login screen
`sms`                | 00002 | Sms.
`dashboard`          | 00003 | Dashboard screen
`side`               | 00004 | Side part of the screen
`post`               | 00005 | Post zone on web.


Campaign API Enumerations
===============

Campaign Action
--------------

Enumeration that distinguishes between kinds of possible actions in
response to campaign offer.

Literal       | Description
--------------|--------------
presented | Offer presented to customer
declined | Offer presented to customer
clicked | Offer details inquired by customer
form-filled | Offer form filled by customer
accepted | Offer accepted by customer
activated | Offer activated

Campaign Priority
--------------

Enumeration that distinguishes possible campaign priorities.

Literal     | Description
------------|--------------
low | Low priority campaign
medium | Medium priority campaign
high | High priority campaign
