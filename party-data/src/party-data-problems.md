   
Possible problems
=================

When request is valid and no standard status code describes situation, Customer Survey API will return status code `440` with one of the following problems in the payload. 
To learn more see general guidance on [error handling]()


Literal 				                                     	| Code 	 | Description
----------------------------------------------------------------|--------|----------------------------------------
`not-found`														|53400	 | Individual with Id not found
`invalid-type`						            				|53401	 | Not valid customer type
`invalid-name`						            				|53402	 | Name has invalid character(s)
`invalid-last-name`					            				|53403	 | Last name has invalid character(s)
`invalid-middle-name`				            				|53404	 | Middle name has invalid character(s)
`first-name-mandatory`				            				|53405	 | First name is mandatory field
`last-name-mandatory`						            		|53406	 | Last name is mandatory field
`middle-name-mandatory`				            				|53407	 | Middle name is mandatory field
`invalid-PIN`													|53408	 | PIN is invalid
`existing-PIN`													|53409   | PIN already exists
`end-date-before-start-date`									|53410   | Start date has to be before end date

