---
description: The products variable cannot be set using processing rules. In the mobile SDK, you must use a special syntax within the context data parameter to set products directly on the server call.
seo-description: The products variable cannot be set using processing rules. In the mobile SDK, you must use a special syntax within the context data parameter to set products directly on the server call.
seo-title: Products variable
solution: Marketing Cloud,Analytics
title: Products variable
topic: Developer and implementation
uuid: 607983d6-48ac-4274-bfc8-b1ca4e5dad1b
index: y
internal: n
snippet: y
---

# Products variable{#products-variable}

The products variable cannot be set using processing rules. In the mobile SDK, you must use a special syntax within the context data parameter to set products directly on the server call.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the [products](http://microsite.omniture.com/t2/help/en_US/sc/implement/?f=c_products) variable:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

For example:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

Note that *`products`* is set directly on the image request, and the other variables are set as context data: 

![](assets/products-bloodhound.png)

All context data variables must be mapped using processing rules: 

![](assets/products-procrules.png){width="672px"}

You do not need to map the *`products`* variable using processing rules since it is set directly on the image request by the SDK.

## Products Variable with Merchandising eVars and Product-Specific Events {#section_685D53AD3D064F9A8E225F995A9BA545}

An example of the *`products`* variable with Merchandising eVars and product-specific events.

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

>[!NOTE]
>
>If you trigger a product-specific event using the *`&&products`* variable, you must also set that event in the *`&&events`* variable, otherwise the event is filtered out during processing.

