   
Possible problems
=================

When request is valid and no standard status code describes situation, Customer Account API will return status code `440` with one of the following problems in the payload. 
To learn more see general guidance on [error handling]()

     Literal                              |  Code | Description                                                                           
     ------------------------------------ | -----:| --------------------------------------------------------------------------------------                          
     default-limit-not-allowed            | 51450 | One or more default limits exceeds maximum allowed value!
     sent-value-not-allowed               | 51451 | One or more sent values (max_count or max_amount) exceeds maximum allowed level!
