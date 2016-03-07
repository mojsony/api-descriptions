   
Possible problems
=================

When request is valid and no standard status code describes situation, Action Authorization API will return status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling]()

Literal               |  Code | Description                        
--------------------- | -----:| ----------------------------------- 
locked-out            | 50250 | Locked out                         
max-attempts-reached  | 50251 | Max login attempts has been reached
authorization-expired | 50252 | Authorization expired   

