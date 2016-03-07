<span class="icon"></span>Survey API Guide
=========================
Survey API gives you access to generated surveys for customer, post captured response to survey and ability to generate surveys based on templates for a customer for capturing customer satisfaction data.
With Survey API you can:
    - List surveys for customer
    - Get survey details
    - Capture response to a survey
    - Generate survey
   
Key Resources
-------------
Customer Survey has two top level collection resources: templates and surveys.

Resource | Description
----------- |-----------
*templates*  | Represents a templates of surveys (questions to be answered) that will be filled for specific customer(s). 
*surveys*      | Survey is a document that has answers of the questions defined in the survey template. Every survey is filled for the specific customer(s), based on the specific tamplate.

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Survey API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Survey API with your access token against the URL root below, combined with one of the root resources.  Content Management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Customer Survey | `https://api.asse.co/customer-survey`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /dms/documents/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Pick survey template
In order to fill the answers for the survey you need to pick survey template.
You can list available templates at following endpoint:
```
GET /templates
```
You will get back `200 OK` status code and json representation with a list of survey templates with basic survey template information.
```json
items: 
    {
      "template-id": "13529645493822864",
      "title": "Personal data",
      "description": "Personal data of individual customer",
      "date-published": "2015-09-23T00:00:00+02:00"
    },
    {
      "template-id": "15597451189579578",
      "title": "KYC survey for individual customer",
      "description": "KYC survey for individual customer",
      "date-published": "2015-10-23T00:00:00+02:00"
    },

```


###4. Pick template to fill the survey for the customer
Let's assume that there are available `survey templates` for the `customer` to be filled with answers.
To create new survey from `survey template`:

```
POST /templates/13529645493822864
```

```json
{
  "survey-id": "4387381",
  "date-created": "2015-12-21T16:34:25.9171415+01:00",
  "survey-info": {
    "template-id": "13529645493822864",
    "title": "Personal data",
    "description": "Personal data of individual customer",
    "date-published": "2015-09-23T00:00:00+02:00"
  },
  "survey-sections": [
    {
      "survey-section-id": null,
      "order": 0,
      "title": "Basics",
      "description": "Basic data of the individual customer",
      "survey-sections": [],
      "questions": [
        {
          "question-id": "13012",
          "order": 1,
          "title": "Full name",
          "description": null,
          "question-type": "text",
          "question-options": null,
          "units-of-measure": null,
          "is-mandatory": true,
          "answer": {
            "text": null",
            "bool-answer": null,
            "numeric": null,
            "date": null,
            "unit-of-measure": null,
            "option-id": null
          }
        },
        {
          "question-id": "2704",
          "order": 2,
          "title": "ID card number",
          "description": null,
          "question-type": "text",
          "question-options": null,
          "units-of-measure": null,
          "is-mandatory": false,
          "answer": {
            "text": null,
            "bool-answer": null,
            "numeric": null,
            "date": null,
            "unit-of-measure": null,
            "option-id": null
          }

```
You will get back `200 OK` status code and json representation with a survey with list og questions to be answered.
```
Location: http://api.asse.co/customer-survey/surveys
```

###4. Fill survey
Now you are ready to fill your first survey.

```
POST /surveys
```

```json
{
  "id": "4387381",
  "customer-id": "ANADO00001",
  "template-id": "13529645493822864",
  "answers": [
    {
      "question-id": "10216",
      "answer": {
        "text": "Praska 40/20",
        "bool-answer": null,
        "numeric": null,
        "date": null,
        "unit-of-measure": null,
        "option-id": null
      }
    },
    {
      "question-id": "2608",
      "answer": {
        "text": "Nambija",
        "bool-answer": null,
        "numeric": null,
        "date": null,
        "unit-of-measure": null,
        "option-id": null
      }
    },

```
You will get back `200 OK` status code and json representation with a created document. Location header will contain URL for download.

```
Location: http://api.asse.co/customer-survey/surveys
```

###5. Get survey for customer
Now lets find specific survey for specific customer.
```
/surveys/4387381:
```

You will get back `200 OK` status code and json representation with survey info.
```json
{
  "survey-id": "4387381",
  "date-created": "2015-12-21T16:34:25.9171415+01:00",
  "survey-info": {
    "template-id": "13529645493822864",
    "title": "Personal data",
    "description": "Personal data of individual customer",
    "date-published": "2015-09-23T00:00:00+02:00"
  },
  "survey-sections": [
    {
      "survey-section-id": null,
      "order": 0,
      "title": "Basics",
      "description": "Basic data of the individual customer",
      "survey-sections": [],
      "questions": [
        {
          "question-id": "13012",
          "order": 1,
          "title": "Full name",
          "description": null,
          "question-type": "text",
          "question-options": null,
          "units-of-measure": null,
          "is-mandatory": true,
          "answer": {
            "text": "Anica Dobrinovic",
            "bool-answer": null,
            "numeric": null,
            "date": null,
            "unit-of-measure": null,
            "option-id": null
          }
        },
        {
          "question-id": "2704",
          "order": 2,
          "title": "ID card number",
          "description": null,
          "question-type": "text",
          "question-options": null,
          "units-of-measure": null,
          "is-mandatory": false,
          "answer": {
            "text": "ML654654",
            "bool-answer": null,
            "numeric": null,
            "date": null,
            "unit-of-measure": null,
            "option-id": null
          }

```


**Congratulations!** You have completed getting started tutorial on most common steps when working with Survey API. To learn more look at the reference documentation for [available operations](swagger-ui).