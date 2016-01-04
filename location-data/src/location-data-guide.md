![Folders](http://cdn.flaticon.com/png/64/98/98193.png)
Location data API v2
=========================
Location data API gives you access to branch, ATM and other financial-institution facilities addresses, GPS coordinates and other location or relevant data like working hours. You can also query for facilities based on place or GPS coordinates to get the nearest ones. With Location data API you can:.
With Customer order API you can:
        - Get the list of branches
        - Get the list of ATMs
        - Query for the nearest facilities around and location based on coordinates or place
        - Get pack based on adress details
   
Key Resources
-------------
Location data API has two top level collection resources: facilities, branches, atms, addresses,classifications

Resource | Description
----------- |-----------
*facilities*  | Includes organization units and channels of financial institution.
*branches*    | Includes organization units for providing financial services.
*atms*  | Includes channel of financial institution such as automated teller cash machines.
*addresses*    | Physical address of the item.
*classifications*    | Identifies a structure used to organize and manage business information by defining categories that satisfy certain criteria or form a group subject to a human decision. 

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Location data API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Location data API with your access token against the URL root below, combined with one of the root resources. Location data API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Location data | `https://api.asse.co/location-data`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /atms/{atm-id}` is used for the sake of brevity. 
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


###5. Retreive details of specific atm
Now lets preview details of specific atm form step 3:
```
GET /atms/40733
```

You will get back `200 OK` status code and json representation for fetched request. 
```json
{
  "ownership-type": "bank-owned",
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
}
```




**Congratulations!** You have completed getting started tutorial on most common steps when working with Location Data API. To learn more look at the reference documentation for [available operations](swagger-ui).
