# DoOrderProcessing  

Regular job to maintain orders.

## Frequency  
**Minutely**  

## Execution  
WorkerOrdersAppService: 
````bash 
	await _orderRepository.AppProductionDaysProcessing();  
	await _orderRepository.AppCompletedOrders();
````



## AppProductionDaysProcessing  
Job to maintain totals on the Production Calendar
 

 ## AppCompletedOrders  
Job to auto complete orders:
````bash 
 Where
	    IsOrderComplete = 0
		and
		(
	        (o.MeasureRequired = 0
	        AND ISNULL(os.SentUnits,-1) >= o.Units
	        AND (ISNULL(t.OrderCount,0) = 0)	 
	        )
	        OR 
	o.DeliveryDateTime < DATEADD(hour,-36, GETDATE())
	) 
````

