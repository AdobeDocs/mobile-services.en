---
description: An example of the products variable with Merchandising eVars and product-specific events.
seo-description: An example of the products variable with Merchandising eVars and product-specific events.
seo-title: Products Variable with Merchandising eVars and Product-Specific Events
solution: Experience Cloud,Analytics
title: Products Variable with Merchandising eVars and Product-Specific Events
topic: Developer and implementation
uuid: 94e882e4-b19d-4c48-9dfb-331465490347
exl-id: 3a90f624-da13-4c26-9e4c-3a4af33bc5ee
---
# Products variable with merchandising eVars and product-specific events{#products-variable-with-merchandising-evars-and-product-specific-events}

An example of the products variable with Merchandising eVars and product-specific events.

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>If you trigger a product-specific event using the *`&&products`* variable, you must also set that event in the *`&&events`* variable, otherwise the event is filtered out during processing.
