OPTOUT 
==========

Traditionally, SMS campaigns are targeted to those customers who are registered subscribers to your SMS
services. You can block the customer's number using our optout feature.Once the customer's number is blocked, meanwhile if you try to trigger Sms to the  customer's number then our system will automatically reject the Sms triggered and the customer will not recieve the sms.

API 
-------

Adding numbers to your optout list can also be proccessed using our API.

API URL:
-----

http://portal.mobtexting.co/api/v2/optout?token=a19eb34810exxxxxxxxx&number=74114xxxxx,707856xxxx  
  
  Kindly replace the token with your respective token and you can specify multiple mobile numbers by seperating it with ','(comma).
  
  On triggering the above API the specified numbers will be added to your optout list.