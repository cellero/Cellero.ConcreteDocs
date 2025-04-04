# DoTruckProcessing  

Regular job for truck `GPS` processing.

## Frequency  
**Minutely**  

## Execution  
WorkerTruckGPSAppService: 
````bash 
  await DoDigitalMattersCurrentStateProcessing();                                      
````



 
 ## DoDigitalMattersCurrentStateProcessing  
Gets latest GPS data from Cellero Cloud Services:
````bash 
 https://cellerocloudservices2025-f0c6f0bgbcgkangj.australiaeast-01.azurewebsites.net/api/app/ext-digital-matters-vehicles/recent-updates
````

