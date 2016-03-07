   
Possible problems
=================

When request is valid and no standard status code describes situation, Payment API will return status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling]()

     Literal                                |  Code | Description                                                                                                                          
     -------------------------------------- | -----:| -------------------------------------------------------------------------------------------------------------------------------------                                          
     allowed-amount-exceeded                | 50650 | This amount exceeds the amount allowed for this currency in your sight accounts!           
     blocked-account                        | 50651 | Current account is blocked, you cannot perform the payment.                                                                          
     debtor-account-blocked                 | 50687 | Selected ordering account is blocked, you cannot perform the payment. Please select another account.
     transfer-not-allowed-accounts-types    | 50652 | You cannot make internal transfer between chosen accounts because of their types.                                                                                                    
     debtor-card-not-active                 | 50654 | Debtor's card is expired or not active.                                                                                              
     frequency-limit-exceeded               | 50655 | Withdrawal frequency limit is exceeded.                                                                                              
     amount-above-limit                     | 50656 | The amount is above predefined limit for this type of payment. Please contact our Contact center to request temporary limit increase.
     transfer-not-allowed                   | 50657 | Debtor account status does not allow person to person payment.                                                                       
     account-deposited                      | 50658 | Account of creditor or debtor is deposited. It can not be used for this transaction.                                                 
     insufficient-available-balance         | 50659 | Debtor's account does not have sufficient available balance.                                                                         
     transaction-currency-not-allowed       | 50660 | To this currency transactions are not allowed.                                                                                       
     creditor-aml-check-failed              | 50661 | Creditor failed AML check procedure.                                                                                                 
     debtor-aml-check-failed                | 50662 | Debtor failed AML check procedure.                                                                                                   
     work-date-not-set                      | 50663 | Work date for National Payments System is not set.                                                                                   
     payment-date-not-set                   | 50664 | Date of the payment order execution is not determined.                                                                               
     put-order-on-wait-error                | 50665 | Error while putting payment order on wait.                                                                                           
     immediate-executing-order-error        | 50666 | Error during immediate executing payment order.                                                                                      
     debtor-account-deposited               | 50667 | Account of debtor is deposited. It can not be used for this transaction.                                                             
     authorization-code-error               | 50668 | Generating authorisation code failed.                                                                                                
     reservation-error                      | 50669 | Error during processing reservation.                                                                                                 
     transfer-not-allowed-for-nonresident   | 50670 | Payment for nonresident is not allowed!                                                                                              
     reservation-not-exists                 | 50671 | There is no active reservation with this authorization code.                                                                         
     obligation-type-not-defined            | 50672 | The type of obligation is not defined for account debit.                                                                             
     event-not-defined                      | 50673 | The event of obligation is not defined for account debit.                                                                            
     creditor-account-deposited             | 50674 | Creditor Account is deposited. It can not be used for this transaction.                                                              
     obligation-type-credit-not-defined     | 50675 | The type of obligation is not defined for account credit.                                                                            
     credit-event-not-defined               | 50676 | The event of obligation is not defined for account credit.                                                                           
     cancel-reservation-error               | 50677 | Error ocured while canceling reservation.                                                                                            
     transfer-not-allowed                   | 50678 | Not allowed transfer to the account of another owner.
     transaction-already-canceled           | 50679 | Transaction was already canceled.
     transaction-already-in-processing      | 50680 | Transaction is already in processing.
     order-reference-not-created            | 50681 | Order reference is not created.
     wrong-order-statistics                 | 50682 | Order statistics is enetered wrong.
     pairing-reservations-error             | 50683 | Error while pairing reservations.
     account-not-active                     | 50684 | Account is not active.
     not-marked-for-verification            | 50685 | Bill is not marked for verification.
     funds-reservation-error                | 50686 | Error ocured while defering payment.
     