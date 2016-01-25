   
Validation errors
=================

When request is not constructed properly and no standard status code describes situation, Payment Order API will return status code `400` with one of the following validation errors in the payload. To learn more see general guidance on [error handling]()

     Literal                                |  Code | Description                                                                                                                          
     -------------------------------------- | -----:| ----------------------------------------------------------------------------------------------------
     amount-negative-number                 | 50601 | Entered amount must be posistive number.
     debtor-account-or-currency-not-valid   | 50603 | Debtor account number is not valid, there is no such active account/currency.
     creditor-account-or-currency-not-valid | 50604 | Creditor account number is not valid, there is no such active account/currency.
     date-not-valid                         | 50605 | Transfer date is not allowed to be before the current date.
     order-validation-failed                | 50607 | Error during consolidated payment order controll.
     wrong-transaction-amount               | 50609 | You have entered wrong transaction amount.
     transfer-canceled                      | 50610 | You have entered wrong transaction amount three times in a row. Transfer will be canceled.
     transfer-draft-already-exists          | 50611 | Transfer with the same identifier already exists.
     
     currency-not-valid                     | 50612 | Entered currency is not correct.
     
     debtor-account-not-entered             | 50613 | Debtor's account number is not entered.
     creditor-name-not-entered              | 50614 | Creditor's name is not entered.
     creditor-address-not-entered           | 50615 | Creditor's address is not entered.
     creditor-city-not-entered              | 50616 | Creditor's city is not entered.
     creditor-IBAN/account-not-entered      | 50617 | Creditor's IBAN/account is not entered.
     creditor-SWIFT-not-entered             | 50618 | Creditor's SWIFT is not entered.
     creditor-SWIFT-not-valid               | 50619 | Creditor's SWIFT is not valid!
     currency-not-entered                   | 50620 | Currency is not entered.
     purpose-code-not-entered               | 50621 | Payment purpose code is not entered.
     purpose-code-not-valid                 | 50622 | Payment purpose code is not valid.
     amount-not-entered                     | 50623 | Amount for transfer is not entered.
     insufficient-balance                   | 50624 | Amount is greater than available balance.
     creditor-country-code-not-entered      | 50625 | Creditor's country code is not entered.
     creditor-country-code-not-valid        | 50626 | Creditor's country code is not valid.
