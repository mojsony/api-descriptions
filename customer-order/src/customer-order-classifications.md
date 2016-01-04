   
Classifications
===============

Card Replacement Reason
-------------- 
This classification contains reasons for card replacement.

Literal 				      | Code   | Description
------------------------------|--------|-------------------------------------------
`card-losses`	  			  | 00001  | Card lost and new one should be issued.
`stolen-card`	  			  | 00002  | Card stolen and new one should be issued
`damaged-card`	  			  | 00003  | Card damaged and new one should be issued.


Card Blockade Reason
-------------- 
This classification contains reasons for card blockade.

Literal 				      			  | Code   | Description
------------------------------------------|--------|--------------------------------------------------
`temporary-blockage`	  				  | 00001  | Temporary blockage on client request.


WorkItem Processing Status
-------------- 
This classification represents status of request. 

Literal 				      			| Code   | Description
----------------------------------------|--------|-------------------------------------------
`proposed`	  			      			| 00003  | WorkItem is prepared, but not approved yet..
'external-processing-in-progress'		| 00006  | WorkItem is sent to external processing.
'external-processing-succeded'			| 00007  | External processing of WorkItem is successfully completed.
`canceled`	  			  				| 00009  | WorkItem is canceled.
`approved`	  			  				| 00020  | WorkItem is approved.
