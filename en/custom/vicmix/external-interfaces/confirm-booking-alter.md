# Confirm Booking Alert
Automatically identifies unconfirmed orders and sends an SMS notification to customers, prompting them to confirm their orders proactively.

## Triggered by
Stored Procedure:  
App_ScheduledTask_Minutely_010_Confirm_Booking_Alert


## Criteria
- only sends after 9am
- fires every minute
- only sends maximum 1 message per plant per cycle
- only send once per order 
- only for up coming orders
- only if the order has a number in the contact phone

## Format
SMS via redcoal system

## Destination
Contact Number on Order:  
![image](../images/ordercontact.png)  
 

The number in the Contact Phone + @redcoal.net is the address used when sending the email

## Output Construction
The following sql is used for the message construction:  
````bash
	,'Plz confirm Order: ' + cast(o.OrderNumber as varchar(16)) 
		+ ' for: ' + case when ISNULL(o.CashSaleName,'') >'' then o.CashSaleName else c.Name end
		+ ' qty: ' + CAST(o.Units as varchar(16))
		+ ' mix: ' + m.Code
		+ ' booked for: ' + FORMAT(o.DeliveryDateTime, 'hh:mm tt')
		+ ' on: ' + FORMAT(o.DeliveryDateTime, 'DDD dd MMM')
		+ ' to: ' +  o.DeliveryAddressLine1 
		+ '. Avoid loosing your slot, confirm by 1pm today. Call: VicMix '  + p.Name 
		+ ' tap: ' + p.Phone
		+ ' Reply STOP to opt out'  
````  


