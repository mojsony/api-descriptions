---
visibility: internal
---

<span class="icon"></span>Profile API Guide
=========================
Profile API gives you access to facts on customers, their behavior and usage of arrangements so you can optimize real-time operational decisions and interactions.

> ##UNDER CONSTRUCTION. PLEASE COME BACK SOON.

Key Resources
-------------
Profile API has three top-level collection resources: `individual-profiles`, `organization-profiles` and `arrangement-profiles`.

Resource						| Description
------------------------------- |------------------------------------
*individual profiles*			| Profile of individual customer with details on product usage, channel and social media behavior, customer, demographic, financial and household data.
*organization profiles*		| Profile of organizational customer with details on organization and customer profile, product usage and channel behavior. Financial profile of organization will be added in future versions.
*arrangement profiles*		| Profile of arrangement and facts on its usage that are not tracked by accounting balances.


Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Customer Survey API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Content Management API with your access token against the URL root below, combined with one of the root resources.  Content Management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Party Profile | `https://api.asse.co/party-profile`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /dms/documents/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Get list of contact preferences for the individual customer
Before you can store and retreive documents you need to pick correct repository. In most cases there will be two repositories, one for more offical documentation such as contracts and another for more relaxed content such as profile images.
You can list available reposcontact preferences at following endpoint:
```
GET /individual-profiles/314/contact-preference
```
You will get back `200 Success` status code and json representation with a list of contact preferences.
```json
[
	contact-preference
	{
		"contact-preference-id": "integer",
		"preferred-language": "string",
		"contact-purpose": "string", 
		"arrangement-number": "string", 
		"start-date": "2015-08-03 00:00:00.000",
		"end-date": null
	}
]
```


###4. Create contact preference
To create contact preference for the customer, we'll need customer id (party-id). To create contact preference as json to following endpoint:

```
POST /individual-profiles/314/contact-preference/

```

```json
[
	register-contact-preference-command
	{
		"id": "string",
		"contact-preference-id": "integer",
		"contact-id": "integer",
		"party-id": "304",
		"arrangement-number": "string",
		"preferred-language": "string",
		"contact-purpose": "string",
		"start-date": "2016-01-11 00:00:000",
		"end-date": null,
		"opt-ins":
			{
				"List of services that the customer wishes to receive informations": "string"
			}
		"opt-outs:
			{
				"List of services that the customer wishes to receive no further informations": "string"
			}
	}
] 
```
You will get back `201 Created` status code and json representation with an Id of the newly created contact preference and 'created' record status.


**Congratulations!** You have completed getting started tutorial on most common steps when working with Content Management API. To learn more look at the reference documentation for [available operations](swagger-ui).