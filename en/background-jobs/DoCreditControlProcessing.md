# DoCreditControlProcessing  

An interface to the accounting system that retrieves up-to-date debtor details.  

## Frequency  
**Hourly**  

## Execution  
Calls stored procedures with pattern: 
````bash 
App_CustomerDebtorTransactions% 
````



## Stored Procedures
### App_CustomerDebtorTransactions_100_Processing  
### Logic Summary  

1. **Opening Balances**  Retrieves initial debtor balances.  
2. **Processed Transactions**  Imports processed transactions (Spend, Payment, Credit, Refund, Journal) from EXO.  
3. **Unprocessed Transactions**  Captures unprocessed transactions (Spend by Docket) from Cellero.  
