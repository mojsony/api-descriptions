![Folders](http://cdn.flaticon.com/png/64/98/98193.png)
Party Profile API v2
=========================
Party Profile API gives you access to subset of customer data needed in real-time operational interaction, servicing, fulfillment and sales. This is an operational view on data already exposed through other APIs optimized to serve the channel’s needs. Here you can quickly access to customers basic information such are name, customer id, demographics data, summary of arrangements with only the basic information and terms and conditions applicable for the calling channel, contact preferences and mandates.  Also a list of authorized persons on user arrangements and their mandates is available on request.
   
Key Resources
-------------
Party Profile has five top level collection resources: individual profiles, mandates, authorized persons, contact preference and arrangements.

Resource						| Description
------------------------------- |------------------------------------
*individual profiles*			| Profile with personal information about individual decoupled from base entity and other profiles because of specific protection and versioning needs.
*mandates*						| Identifies the terms and conditions governing the use of a Service and specifies the access permissions for <Arrangement>s covered by this Mandate.
*authorized persons*			| Represents the person(s) formally authorized by customer to perform specific operations (withdrawal, payment...) under certain conditions (limits, authorization...)
*contact preferences*		    | Represents contact that has sepcific usage, like contact address used to communicate about arrangement.
*arrangements*					| Identifies a potential or actual agreement between an Organization and one or more Involved Partys that provides and affirms the rules and obligations associated with that agreement.

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
