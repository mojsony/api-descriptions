Classifications
===============

Product Kinds
-------------- 
This classification contains types of products that can be offered through Product catalog.

Comment - ds - 20150113: 
In this file only classifications should be declared, not the enums. Enums are directly declared in swagger/yaml code. Please, rewise this document.


Literal 				      | Code   | Description
------------------------------|--------|-----------------------------
`deposit`		  			  | 00001  | Identifies a particular type of Product in which funds are placed with the modeled organization according to agreed upon conditions.
`current-account`  			  | 00002  | Refers to a type of Deposit Product made with a financial institution that permits the withdrawal of funds and allows checks to be written against the balance.
`demand-deposit`  			  | 00003  | Particular type of Deposit Product that is used for handling day-to-day transactions and can be used to accumulate savings.
`term-deposit`  			 	  | 00004  | Identifies a particular type of Deposit Product. A term deposit is a money deposit at a banking institution that cannot be withdrawn for a certain "term" or period of time.  
`finance-service`  			  | 00005  | Identifies a particular type of Product where the modeled organization extends credit to another Involved Party in the form of actual funds, or as an obligation to provide funds in the future under specific conditions.  
`term-loan`		  			  | 00006  | Identifies a particular type of Finance Service. A term loan is a monetary loan that is repaid in regular payments over a set period of time.
`credit-facility`	  		  | 00007  | Identifies a particular type of  Finance Service where the modeled organization extends credit to another InvolvedParty in the form of actual funds, or as an obligation to provide funds in the future under specific conditions.
`overdraft-facility` 		  | 00008  | Identifies a particular type of Finance Service.
`product-access`  			  | 00009  | Identifies a Product which allows a Customer to obtain access to a Financial Product Arrangement.
`card-access`	  			  | 00010  | Identifies a Product Access Service which enables a Product to be accessed by use of a card such as a credit card or a debit card.
`electronic-access` 			  | 00011  | Identifies a Product Access Service which enables a Product to be accessed by use of an on-line system, such as a computer terminal or telephone.

Product Customer Centric Status
-------------- 
This classification represents statuses for a Product usage from Customer perspective.

Literal 				      	| Code   | Description
--------------------------------|--------|-----------------------------------------------------
`already-used-by-client`	  	| 00001  | Identifies a Product that is already used by client.
`coming-soon`	  				| 00002  | Identifies a Product that is not yet available.
`not-used-by-client`	  		| 00003  | Identifies a Product that is not used by client.

Card Access Type
-------------- 
A Classification Scheme that distinguishes between Card Accesses according to the type of card that is used to access the Product.

Literal 				      	| Code   | Description
--------------------------------|--------|-----------------------------------------------------
`credit-card`	  				| 00001  | Identifies a Card Access that enables use of a line of credit offered by the issuer of the Card.
`debit-card`	  					| 00002  | Identifies a Card Access that allows debits to a customer's account with the card issuer when the card is used for purchases.
`gift-card`				  		| 00003  | Identifies a Card Access that enables use of prepaid stored-value money. Usually used as an alternative to cash for purchases within a particular store or related businesses.

Financial Transaction Card Brand
-------------- 
A Classification Scheme that distinguishes between Financial Transaction Card Brand based on the card type and card issuer.

Literal 				      	| Code   | Description
--------------------------------|--------|----------------------------------------
`american-express`	  			| 00001  | American Express (Amex) card brand.
`dina-card`		  				| 00002  | Dina Card card brand.
`diners`				  			| 00003  | Diners card brand.
`maestro`				  		| 00004  | Maestro card brand.
`master`				  			| 00005  | Master card brand.
`visa`				  			| 00006  | Visa card brand.
`visa-electron`			  		| 00007  | Visa Electron card brand.

Type Of Funding
-------------- 
A Classification Scheme that distinguishes between  different types of product funding.	

Literal 				      	| Code   | Description
--------------------------------|--------|---------------------
`cash`				  			| 00001  | Cash.
`invoice`		  				| 00002  | Invoice.
`refinancing`					| 00003  | Refinancing.
`refinancing-ob-product`			| 00004  | RefinancingOB product.

Document Type
-------------- 
This classification represents  documet types. 

Literal 				  				    	| Code   | Description
------------------------------------------------|--------|-----------------------
`statement`				  						| 5022	 | Statement.
`withdraw-conscent-for-credit-bureau-report`		| 5047   | Withdraw conscent for credit bureau-report.
`service-document`				  				| 		 | Service Document.
`product-application-creation-phase-checklist`	| CL-PA-CRE| Product Application Creation Phase Checklist.
`employment-cerificate`				  			| 5081	| Employment cerificate.
`application`				  					|  		| Application.
