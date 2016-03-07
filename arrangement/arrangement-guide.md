<span class="icon"></span>Arrangement API Guide
=========================
Arrangement API gives you access to all durable arrangements customer has with financial institution such as current accounts, loans, deposits, card access arrangements, electronic access arrangements, etc. It also provides detailed arrangement information such as financial terms and conditions, party roles, installment plan, etc. It maps to BIAN Sales Product Agreement service domain.

Key Resources
-------------
Top-level resource is arrangement (arrangements) which has specializations by kind. Main subresources are installment-plan and arrangement-conditions. 

Resource | Description
----------- |-----------
*arrangement*  | Represents a deal/agreement between bank as product/service provider and its customer as a consumer of the same product. Non-product agreements are not covered by this resource. Specializations of arrangement are: current-account, demand-deposit, term-deposit, term-loan, overdraft-facility, credit-facility, credit-card-facility, card-access-arrangement, electronic-acess-arrangement, other-product-arrangement
*installment-plan*      | A list of scheduled payments for entire arrangement lifecycle.
*arrangement-conditions*    | Arrangement terms and conditions listed in three separate lists: fees, interest-rates and other. 

Getting started tutorial
---------------
To get started follow these steps:
###1. Authenticate your app
Sales Arrangement API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication]() section.

###2. URL Root
Now that you've authenticated your app, you can call the Sales Arrangement API with your access token against the URL root below, combined with one of the root resources.  Sales Arrangement API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Sales Arrangement | `https://api.asse.co/sales-arrangement`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /arrangements/{id}` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Retrieve the list of arrangements for a customer
Let's see the list of arrangements - products used by a customer. Note that the list returns only arrangements for which the party from calling context plays customer role. If you want to see arrangement in which calling party plays other roles, this should be specified by party-role-param. 
You can list arrangements at following endpoint:
```
GET /arrangements
```
You will receive `200 OK` status code and json representation with a list of arrangements. 

```json
{
  "items": [
    {
      "arrangement-number": "0000100002378",
      "kind": "current-account",
      "product-code": "RT-CA-STD-001",
      "status": "effective"
    },
    {
      "arrangement-number": "0042201082794",
      "kind": "term-loan",
      "product-code": "RT-LN-CAR-002",
      "status": "effective"
    }
  ]
}
```


###4. See arrangement details
Arrangement details are accessible from arrangement list and also can be accessed from account list or from any context where we can found arrangement number. We will use include-param to include party-role and arrangement-account-info subresources (under parties and accounts properties): 

```
GET /arrangements/0042201082794?include=parties, accounts
```

You will receive `200 OK` status code and json representation with arrangement details. 

```json
{
  "arrangement-number": "0042201082794",
  "kind": "term-loan",
  "product-code": "RT-LN-CAR-002",
  "status": "effective",
  "contract-date": "2013-10-21T00:00:00",
  "parties": [
    {
      "party-number": "IGNE002",
      "party-name": "Milivoje Klafovic",
      "role-kind": "customer",
      "role-status": "current"
    },
    {
      "party-number": "MRQW031",
      "party-name": "Leopold Zec",
      "role-kind": "guarantor",
      "role-id": "G1",
      "role-status": "current"
    },
    {
      "party-number": "MRQW031",
      "party-name": "Teodor Brkic",
      "role-kind": "guarantor",
      "role-id": "G2",
      "role-status": "current"
    }
  ],
  "accounts": [
    {
      "account-number": "0042201082794",
      "role-kind": "primary-account"
    },
    {
      "account-number": "0000100002378",
      "role-kind": "settlement-account"
    }
  ],
  "term":
    {
      "period": 4,
      "unit-of-time": "Y"
    },
  "grace": 
    {
      "period": 3,
      "unit-of-time": "M"
    },
  "maturity-date": "2017-10-21T00:00:00",
  "initial-amount": 8000.00,
  "primary-currency": "EUR",
  "eapr": 9.79,
  "napr": 9.0
}
```

###5. Retrieve arrangement installment plan
Installment plan is specific arrangement subresource which exists only for some kinds of arrangement - usually only for term loans and deposits. We will use paging to get first 6 installment plan rows:

```
GET /arrangements/0042201082794/installment-plan?page-size=6&page-number=1
```

You will receive `200 OK` status code and json representation with installment plan details. 

```json
{
  "items": [
    {
      "ordinal": "0",
      "date": "2013-10-21T00:00:00",
      "activity-kind": "disbursement",
      "description": "Loan disbursement and fee",
      "disbursement": "8000.00",
      "starting-balance": "0.00",
      "principal-repayment": "0.00",
      "interest-repayment": "0.00",
      "annuity": "0.00",
      "fee": "80.00",
      "outstanding-balance": "8000.00",
      "net-cash-flow": "-7920.00",
      "discounted-net-cash-flow": "-7920.00"
    },
    {
      "ordinal": "1",
      "date": "2013-11-21T00:00:00",
      "activity-kind": "interest-payment",
      "description": "Interest payment",
      "disbursement": "0.00",
      "starting-balance": "8000.00",
      "principal-repayment": "0.00",
      "interest-repayment": "58.77",
      "annuity": "58.77",
      "fee": "0.00",
      "outstanding-balance": "8000.00",
      "net-cash-flow": "58.77",
      "discounted-net-cash-flow": "58.31"
    },
    {
      "ordinal": "2",
      "date": "2013-12-21T00:00:00",
      "activity-kind": "interest-payment",
      "description": "Interest payment",
      "disbursement": "0.00",
      "starting-balance": "8000.00",
      "principal-repayment": "0.00",
      "interest-repayment": "56.87",
      "annuity": "56.87",
      "fee": "0.00",
      "outstanding-balance": "8000.00",
      "net-cash-flow": "56.87",
      "discounted-net-cash-flow": "55.99"
    },
    {
      "ordinal": "3",
      "date": "2014-01-21T00:00:00",
      "activity-kind": "interest-payment",
      "description": "Interest payment",
      "disbursement": "0.00",
      "starting-balance": "8000.00",
      "principal-repayment": "0.00",
      "interest-repayment": "58.77",
      "annuity": "58.77",
      "fee": "0.00",
      "outstanding-balance": "8000.00",
      "net-cash-flow": "58.77",
      "discounted-net-cash-flow": "57.40"
    },
    {
      "ordinal": "4",
      "date": "2014-02-21T00:00:00",
      "activity-kind": "repayment",
      "description": "Repayment (interest and principal)",
      "disbursement": "0.00",
      "starting-balance": "8000.00",
      "principal-repayment": "149.99",
      "interest-repayment": "58.77",
      "annuity": "208.76",
      "fee": "0.00",
      "outstanding-balance": "7850.01",
      "net-cash-flow": "208.76",
      "discounted-net-cash-flow": "202.29"
    },
    {
      "ordinal": "5",
      "date": "2014-03-21T00:00:00",
      "activity-kind": "repayment",
      "description": "Repayment (interest and principal)",
      "disbursement": "0.00",
      "starting-balance": "7850.01",
      "principal-repayment": "156.69",
      "interest-repayment": "52.07",
      "annuity": "208.76",
      "fee": "0.00",
      "outstanding-balance": "7693.32",
      "net-cash-flow": "208.76",
      "discounted-net-cash-flow": "200.84"
    }
  ]
}
```
If you analyze this response, you will note that it consists of fields requred for effective rate calculation (EAPR). This transparently shows all planned cash flows and their discounted values as required by regulations. 

###6. Retrieve interest rates, fees and other conditions
Now, let's get arrangement's interest rates, fees and other conditions. They come in the same package - arrangement-conditions aggergate. We can use trim parameter to exclude what we don't need. So, if we need only interest rates, we will use trim parameter to exclude other two lists - fees and other (?trim=fees, other). 

In this example, let's get all conditions:  

```
GET /arrangements/0042201082794/conditions
```

You will receive `200 OK` status code and json representation of arrangement-conditions. 

```json
{
  "fees": [
    {
      "title": "Origination fee",
      "effective-date": "2013-10-21T00:00:00",
      "kind": "origination-fee",
      "percentage": "0.7",
      "lower-limit": {
        "amount": "50.00",
        "code": "EUR"
      }
    },
    {
      "title": "Yearly management fee",
      "effective-date": "2013-10-21T00:00:00",
      "kind": "management-fee",
      "percentage": "0.3",
      "frequency": "yearly"
    },
    {
      "title": "Early repayment fee",
      "effective-date": "2013-10-21T00:00:00",
      "kind": "early-repayment-fee",
      "percentage": "1"
    }
  ],
  "interest-rates": [
    {
      "title": "Regular interest",
      "effective-date": "2013-10-21T00:00:00",
      "kind": "regular-interest",
      "is-compund": "true",
      "calendar-basis": "Act-Act-ISDA",
      "rate": {
        "base-rate-id": "EURIBOR3M",
        "base-rate-value": "1.28",
        "spread-rate-value": "8.5"
      },
      "variations": [
        {
          "origin": "campaign",
          "benefit-source-id": "THRILL2013",
          "benefit-id": "DISC-023471",
          "variation-description": "Campaign discount on interest rate",
          "percentage": "-0.5"
        },
        {
          "origin": "sales-discount",
          "benefit-source-id": "AGENT-007",
          "benefit-id": "DSCNT-23617",
          "variation-description": "Seller discount",
          "percentage": "-0.28"
        }
      ],
      "calculated-rate": "9.0"
    },
    {
      "title": "Penalty interest",
      "effective-date": "2013-10-21T00:00:00",
      "kind": "regular-interest",
      "is-compund": "true",
      "calendar-basis": "Act-Act-ISDA",
      "rate": {
        "base-rate-id": "LEGPNL",
        "base-rate-value": "7.21",
        "spread-rate-value": "5.0"
      },
      "lower-limit": {
        "base-rate-id": "regular-interest",
        "base-rate-value": "9.0"
      },
      "calculated-rate": "12.21"
    }
  ],
  "other": [
    {
      "category": "collaterals",
      "description": "Purchased vehicle"
    },
    {
      "category": "collaterals",
      "description": "Bills of exchange - 2x"
    },
    {
      "category": "repayment",
      "description": "Partial early repayment without term changes is possible without going through loan approval process again."
    }
  ]
}
```

If you analyze this response you can see that complex structure of fees and interest rates is supported, with lower limits, upper limits and variations from standard product conditions. The purpose of separate presentation of these variations is price transparency - to show the customer why he got some discount and explain the scope in which it is valid. These variations are advanced concepts and are not supported by all back-end systems implementing this API.  

Also, note that interest rates may be composed of base and spread rate, where base rate is variable part. So, if base rate exists, base-rate-value represents it's value at effective-date. Final calculated interest rate value at condition effective-date is in calculated-rate and it is sum of values of base rate, spread rate and all applicable variations. Condition effective-date is the date of contract, amendment or any change in condition definition. Note that this API deals with sales arrangement and doesn't deal with changes of base rate value during arrangement lifecycle. It cares only about condition definition and it's value in moment of definition. 

**Congratulations!** You have completed getting started tutorial on most common steps when working with Arrangement API. To learn more look at the reference documentation for [available operations](arrangement.html).
