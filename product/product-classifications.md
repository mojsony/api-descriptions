Product API Classifications
===============

Card Brand
-------------- 
A Classification Scheme that distinguishes between Financial Transaction Card Brand based on the card type and card issuer.

Literal 				      	| Code   | Description
--------------------------------|--------|----------------------------------------
`american-express`	  			| 00001  | American Express (Amex) card brand
`dina-card`		  				| 00002  | Dina Card card brand
`diners`						| 00003  | Diners card brand
`maestro`				  		| 00004  | Maestro card brand
`master`				 		| 00005  | Master card brand
`visa`				  			| 00006  | Visa card brand
`visa-electron`			  		| 00007  | Visa Electron card brand

Document Type
-------------- 
This classification represents document types. 

Literal 				  				    	| Code		| Description
------------------------------------------------|-----------|-----------------------
`application`				  					| 00001		| Application.
`installment-plan`								| 00002		| Intallment plan.
`statement`				  						| 5022		| Statement.
`employment-cerificate`				  			| 5081		| Employment cerificate.
`contract`										| 2135		| Contract.
`employment-and-income-data`					| 5081		| Certified data of the employment and income verified by the employer
`application-checklist-creation`	| CL-PA-CRE	| Product application creation phase checklist.

Financing Kind
-------------- 
This classification identifies kinds of financing that product provides

Literal 				  		   	| Code	| Description
------------------------------------|-------|-------------------------------------
`cash`				  				| 00001	| Cash.
`refinancing-other-bank-product`	| 00002	| Refinancing other bank product plan.
`refinancing-inside-bank-product`	| 00003	| Refinancing inside bank product.
`invoice`				  			| 00004	| Invoice


Product API Enumerations
===================

Card Kind
-------------- 
A Classification Scheme that distinguishes between Card Accesses according to the type of card that is used to access the Product.

Literal 				      	| Code   | Description
--------------------------------|--------|-----------------------------------------------------
`credit-card`	  				| 00001  | Card that enables use of a line of credit offered by the issuer of the Card.
`debit-card`	  				| 00002  | Card that allows debits to a customer's account with the card issuer when the card is used for purchases.
`gift-card`				  		| 00003  | Card that enables use of prepaid stored-value money. Usually used as an alternative to cash for purchases within a particular store or related businesses.
`prepaid-card`				  		| 00003  | Card that enables use of prepaid stored-value money. Usually used as an alternative to cash for purchases within a particular store or related businesses.

