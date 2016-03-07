   
Possible problems
=================

When request is valid and no standard status code describes situation, Currency Exchange API will return status code `440` with one of the following problems in the payload. 
To learn more see general guidance on [error handling]()

     Literal                              |  Code | Description                                                                           
     ------------------------------------ | -----:| --------------------------------------------------------------------------------------                          
     night-exchange-closed                | 51250 | The transactions of exchange for this night are closed.
     source-account-check-failed          | 51251 | Check of source account failed.
     destination-account-check-failed     | 51252 | Check of destination account failed.
     account-type-not-appropriate         | 51253 | Source and destination accounts have to be either current account or saving on demand.
     amount-limit-exceeded                | 51254 | This amount exceeds withdrawal limit on source account.
     frequency-limit-exceeded             | 51255 | Number of withdrawals for the time period is exceeded.
     temporary-unavailable                | 51256 | Exchange job can not be done now. Please try again later.
     insufficient-balance                 | 51257 | Source account does not have sufficient available balance.