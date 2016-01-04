   
Possible problems
=================

When request is valid and no standard status code describes situation, Currency Exchange API will return status code `440` with one of the following problems in the payload. 
To learn more see general guidance on [error handling]()

     Literal                              |  Code | Description                                                                           
     ------------------------------------ | -----:| -------------------------------------------------------------------------------------- 
     temporary-unavailable                | 51201 | Exchange job can not be done now. Please try again later.                             
     negative-amount                      | 51202 | Entered amount must be positive.                                                      
     same-currencies                      | 51203 | Source currency must be different from destination currency.                          
     currency-mismatch                    | 51204 | Source or destination currency of account must match foreign currency of transaction. 
     unsuficient-balance                  | 51205 | Source account does not have sufficient available balance.                            
     night-exchanges-closed               | 51250 | The transactions of exchange for this night are closed.                               
     source-account-check-failed          | 51251 | Check of source account failed.                                                       
     destination-account-check-failed     | 51252 | Check of destination account failed.                                                  
     account-deposit-type-not-appropriate | 51253 | Source and destination accounts have to be either current account or saving on demand.
     local-currency-missing               | 51254 | Source or destination currency must be domestic.                                      
     amount-limit-exceeded                | 51255 | This amount exceeds limit for this currency in sight accounts.                        
     frequency-limit-exceeded             | 51256 | Number of withdrawals for the time period is exceeded.                                
     source-amount-limit-exceeded         | 51257 | This amount exceeds withdrawal limit on source account.                                                   
