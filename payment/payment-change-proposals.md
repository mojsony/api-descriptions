
2016-04-13
----------

Changes proposed by Risto Krulj

###Indicate whether funds for future dated transfer should be reserved immediately
We need **new field** in `credit-transfer` instruction that indicates that customer 
wants to reserve funds for transfer scheduled with date in future. This indicator may be applicable for other forms of future dated transfers such as cross-border transfers.
> Rationale: Such feature is already offered by Raiffeisen bank and is now requested by MTS bank.


###Provide actual value data in cross-border transfer instruction
We need **new field** in `cross-border-transfer` instruction that would show actual value date changed by agent of the bank 
if value date originally set by customer could not be executed (holiday or similar reason). 

