<span class="icon"></span>Location API Guide
=======================
Location API provides information on bank's physical facilities and help work with structured addresses. For facilities you can get addresses, geographic coordinates and other location or relevant data like working hours. You can also find facilities located near place or geographic coordinates. Elements of structured addresses such as official listo of places and streets is available along with option to validate address and get postal address code that is used for optimized postal delivery.
   
Key Resources
-------------
Location API has four top-level resources: facilities, addresses, places and streets. 

Resource | Description
----------- |-----------
*facilities*  | Physical facilities such as branches and atms through which bank offers its services
*addresses*  | Postal addresses of interest to bank. Validation of postal addresses is offered as a service.
*places*  | Populated places of interest to bank
*streets*  | Official list of streets in populated places of interest to bank

Getting started
---------------
To get started follow these steps:
###1. Authenticate your app
Location API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication](common-getstarted.html#authentication) section.

###2. API base path
Now that you've authenticated your app, you can call the Location API with your access token against the URL root below, combined with one of the root resources. Location API URLs are relative to the following base path unless otherwise noted.

API | Base path
--------|---------
Location | `https://dev.asseco-see.com/v2/location`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /facilities/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Get list of facilities searched by place code
Let's assume that you want to preview list of all facilities in financial institution for specified place code. You can do that at following endpoint:
```
GET /facilities?place-code=791091
```
You will get back `200 OK` status code and json representation for fetched request. 

```json
{
  "total-count": 2,
  "page-size": 1,
  "page-number": 1,
  "total-pages": 1,
  "items": [
    {
      "id": 40733,
      "name": "Airport City",
      "type": "ATM",
      "capabilities": [],
      "address": {
        "text": "Omladinskih brigada 90",
        "street": "Omladinskih brigada",
        "building": "90",
        "door": null,
        "floor": null,
        "city": "Beograd",
        "place": "11070",
        "place-name": "Novi Beograd",
        "country-code": "SRB",
        "country-name": "SRBIJA",
        "state": null,
        "location": {
          "latitude": 44.8112911,
          "longitude": 20.398722799999973
        }
      },
      "working-hours": [
        {
          "period-description": "Radnim danom",
          "working-time": "08-16h"
        },
        {
          "period-description": "Subotom",
          "working-time": "09-13h"
        }
      ],
      "phone-number": null,
      "email": null
    },
    {
      "id": 41737,
      "name": "Banjica",
      "type": "ATM",
      "capabilities": [],
      "address": {
        "text": "Paunova 24",
        "street": "Paunova",
        "building": "24",
        "door": null,
        "floor": null,
        "city": "Beograd",
        "place": "11010",
        "place-name": "Beograd Vozdovac",
        "country-code": "SRB",
        "country-name": "SRBIJA",
        "state": null,
        "location": {
          "latitude": 44.7567628,
          "longitude": 20.476506100000051
        }
      },
      "working-hours": [
        {
          "period-description": "Radnim danom",
          "working-time": "08-17h"
        }
      ],
      "phone-number": null,
      "email": null
    },
```
###4. Get list of facilities searched by GPS coordinates of the location 
Let's assume that you want to preview list of all facilities in financial institution by GPS coordinates of the location. You can do that at following endpoint
```
GET/facilities?latitude=44.3&longitude=20.3&search-radius=100
```
You will get back `200 OK` status code and json representation for fetched request.

```json
{
  "total-count": 13,
  "page-size": 10,
  "page-number": 1,
  "total-pages": 2,
  "items": [
    {
      "id": 40733,
      "name": "Airport City",
      "type": "ATM",
      "capabilities": [],
      "address": {
        "text": "Omladinskih brigada 90",
        "street": "Omladinskih brigada",
        "building": "90",
        "door": null,
        "floor": null,
        "city": "Beograd",
        "place": "11070",
        "place-name": "Novi Beograd",
        "country-code": "SRB",
        "country-name": "SRBIJA",
        "state": null,
        "location": {
          "latitude": 44.8112911,
          "longitude": 20.398722799999973
        }
      },
      "working-hours": [
        {
          "period-description": "Radnim danom",
          "working-time": "08-16h"
        },
        {
          "period-description": "Subotom",
          "working-time": "09-13h"
        }
      ],
      "phone-number": null,
      "email": null
    },
    {
      "id": 41737,
      "name": "Banjica",
      "type": "ATM",
      "capabilities": [],
      "address": {
        "text": "Paunova 24",
        "street": "Paunova",
        "building": "24",
        "door": null,
        "floor": null,
        "city": "Beograd",
        "place": "11010",
        "place-name": "Beograd Vozdovac",
        "country-code": "SRB",
        "country-name": "SRBIJA",
        "state": null,
        "location": {
          "latitude": 44.7567628,
          "longitude": 20.47650610000005
        }
      },
      "working-hours": [
        {
          "period-description": "Radnim danom",
          "working-time": "08-17h"
        }
      ],
      "phone-number": null,
      "email": null
    },
    {
      "id": 40734,
      "name": "Banovo brdo",
      "type": "ATM",
      "capabilities": [],
      "address": {
        "text": "Požeška 108a",
        "street": "Požeška",
        "building": "108a",
        "door": null,
        "floor": null,
        "city": "Beograd",
        "place": "11030",
        "place-name": "Beograd Cukarica",
        "country-code": "SRB",
        "country-name": "SRBIJA",
        "state": null,
        "location": {
          "latitude": 44.773886,
          "longitude": 20.413765
        }
      },
      "working-hours": null,
      "phone-number": null,
      "email": null
    }
```


###5. Get list of streets
Let's assume you want to preview list of streets for specifed place name, page number and page size.
You can do that at following endpoint:

```
GET/streets?place-name=Subotica&page-size=3&page=1
```
You will get back 200 OK status code and json representation for fetched request.
```json
{
  "total-count": 1002,
  "page-size": 3,
  "page-number": 1,
  "total-pages": 335,
  "items": [
    {
      "name": "A B ŠIMIĆA",
      "alternative-names": [],
      "code": "823605531",
      "place-name": "SUBOTICA",
      "country-name": "SRBIJA"
    },
    {
      "name": "ACINA ULICA",
      "alternative-names": [],
      "code": "609702737",
      "place-name": "SUBOTICA",
      "country-name": "SRBIJA"
    },
    {
      "name": "ADAČKA",
      "alternative-names": [],
      "code": "823605546",
      "place-name": "SUBOTICA",
      "country-name": "SRBIJA"
    }
  ]
}
```




**Congratulations!** You have completed getting started tutorial on most common steps when working with Location API. To learn more look at the reference documentation for [available operations](swagger-ui).