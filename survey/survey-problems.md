   
Possible problems
=================

When request is valid and no standard status code describes situation, Customer Survey API will return status code `440` with one of the following problems in the payload. 
To learn more see general guidance on [error handling]()


Literal 				                                     	| Code 	 | Description
----------------------------------------------------------------|--------|----------------------------------------
`not-found`														|52200	 | Template with template-id not found
`invalid-answer`					            				|52201	 | Answer fot the survey question is not valid.