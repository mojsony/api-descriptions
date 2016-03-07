   
Possible problems
=================

When request is valid and no standard status code describes situation, CustomerOrder API will return status code `440` with one of the following problems in the payload. 
To learn more see general guidance on [error handling]()


Literal 				                                     	| Code 	 | Description
----------------------------------------------------------------|--------|----------------------------------------
`forbidden`														|		 | Operation not authorized
`request-already-exists`			            				| 		 | This type of request has already been made.
`request-status-not-eligible-for-cancelation`              		| 		 | Request is in status that does not allow cancelation.
`active-request-already-exists`			            		 	| 		 | Same request has already been added and it's in one of active status.
`active-additional-card-already-exists`		           		 	| 		 | Active additional card already exists.
`owner-can-not-have-additional-card`							| 		 | Additional card can only be requested for authorized person.
`policy-violation`												|		 | Request can not be processed due to violation {violation-id} of bank's business policy {policy-id}

