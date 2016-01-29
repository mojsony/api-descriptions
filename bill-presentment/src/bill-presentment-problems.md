   
Possible problems
=================

When request is valid and no standard status code describes situation, Bill Presentment API will return status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling]()

     Literal                          |  Code | Description                                                            
     -------------------------------- | -----:| -----------------------------------------------------------------------     
     nickname-already-exists          | 50452 | User has already set this nickname for another subscription.
     subscription-already-registered  | 50453 | User has already set bill payment subscription for this issuer.
     subscription-not-active          | 50454 | Bill payment subscription is not active.
     unpaid-bills-exist               | 50455 | There are active bills, subscription cannot be canceled.
     standing-order-scheduled         | 50456 | Subscription cannot be canceled, standing order is scheduled for today.
     debtor-account-not-active        | 50401 | Debtor account number not valid, there is no such active account.
