# DoEmailInvoiceBatchTruckRechargeTruckVersion  

Email processor for Truck Recharge invoices

## Frequency  
**Minutely**  

## Execution  
Processes Pending emails
````bash 
AppInvoiceBatchTruckRechargess where IsFullyProcessed is false and SendEmails is true
````

 
