   
Possible problems
=================

When request is valid and no standard status code describes situation, offer management API will return status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling]()

Literal 				                | Code 	 |   Description
----------------------------------------|--------|-----------------------------------------
`deposit-application-maxnumber`	        | X?	 | Customer can not have more then one current-account application.
`requested-account-range`	            | X?	 | Incorrect requested-account-number. Not in range 5001.
`current-account-arrangement-maxnumber`	| X?	 | Customer can not have more then one current-account arrangement.
`customer-not-found`		            | 100110 | Can not find customer for IdentificationNumber "%s", Country "%s", of Type "%s". PartyExternalId = "%s".
`account-exists`                        | 100002 | Destination system already contains account for the given Arrangement!  
`product-not-valid`                     | X?	 | Actual product not valid.

