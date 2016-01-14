   
Validation errors
=================

When request is not constructed properly and no standard status code describes situation, Currency Exchange API will return status code `400` with one of the following validation errors in the payload. 
To learn more see general guidance on [error handling]()

     Literal                              |  Code | Description                                                                           
     ------------------------------------ | -----:| ------------------------------------------------------------------------------------------------------- 
     entry-parameters-not-valid           | 51401 | Entry parameters SwitchOff and ResetToDefault are both turned on (set to 1). Incorect input parameters.
     not-only-one-limit                   | 51402 | Not only one limit exists. At least SwitchOff or ResetToDefault parameter must be turned on (set to 1).
