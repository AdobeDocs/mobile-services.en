---
description: The Adobe Target prefetch feature uses the iOS Mobile SDKs to fetch offer content as few times as possible by caching the server responses.
seo-description: The Adobe Target prefetch feature uses the iOS Mobile SDKs to fetch offer content as few times as possible by caching the server responses.
seo-title: Prefetch offer content in iOS
title: Prefetch offer content in iOS
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
exl-id: 64d43be7-6bd1-4657-8154-5b2c1cbbf42b
---
# Prefetch offer content in iOS {#prefetch-offer-content-in-ios}

The Adobe Target prefetch feature uses the iOS Mobile SDKs to fetch offer content as few times as possible by caching the server responses.

>[!IMPORTANT]
>
>Prefetch functionality in the Mobile SDKs for iOS is not supported for Auto Target, Auto Allocate, and Automated Personalization activity types in Adobe Target.

This process reduces the load time, prevents multiple network calls, and allows Adobe Target to be notified which mbox was visited by the mobile app user. All content will be retrieved and cached during the prefetch call, and this content will be retrieved from the cache for all future calls that contain cached content for the specified mbox name.

Prefetch content does not persist across launches. The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

In SDK version 4.14 or later, if specified, the `environmentId` is picked from the `ADBMobileConfig.json` file when initiating a v2 batch mbox TnT call. If no `environmentId` is specified in this file, no environment parameter is sent in TNT batch mbox call, and offer is delivered for the default environment.

For example:

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Prefetch methods {#section_05967F1F3A554B0FBC2C08A954554BDE}

Here are the methods that you can use for prefetch in iOS:

* **targetPrefetchContent**

  Sends a prefetch request with an array of locations to the configured Target server and returns the request status in the provided callback. 

  * Here is the syntax for this method:

    ```objective-c
    (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                   withProfileParameters:(nullable NSDictionary*)profileParameters 
                          callback:(nullable void(^)(BOOL success))callback;
    ```

  * Here are the parameters for this method:

    * **`targetPrefetchArray`**

      Array of `TargetPrefetchObjects` that contains the name and mboxParameters for each Target location to prefetch.

    * **`profileParameters`**

      Contains the keys and values of profile parameters to be used with every location prefetch in this request.

    * **`callback`**

      Invoked when the prefetch is complete. Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **targetLoadRequests**

  Executes a batch request for multiple mbox locations that are specified in the requests array. Each object in the array contains a callback function, which will be invoked when content is available for its given mbox location. 
  
  >[!IMPORTANT]
  >
  >If the content for the requested locations is already cached, it will be returned immediately in the provided callback. Otherwise, the SDK will send a network request to the Target servers to retrieve the content. 

  * Here is the syntax for this method:

    ```objective-c
    (void)targetLoadRequests:(nonnullNSArray*)requests 
             withProfileParameters:(nullableNSDictionary*)profileParameters;
    ```

  * Here are the parameters for this method:

    * **`requests`**

      Array of `TargetRequestObjects` that contains the name, default content, parameters, and callback function per location to retrieve.

    * **`profileParameters`**

      Contains keys and values of profile parameters to be used with every location prefetch in this request.

* **targetPrefetchClearCache**

  Clears the data that was cached by Target Prefetch.

  * Here is the syntax for this method:

    ```objective-c
    (void) targetPrefetchClearCache; 
    ```

  * There are no parameters for this method.

* **targetRequestObjectWithName**

  Creates and returns an instance of `TargetRequestObject` with the provided data. 

  * Here is the syntax for this method:

    ```objective-c
    +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
    defaultContent:(nonnullNSString*)defaultContent
    mboxParameters:(nullableNSDictionary*)mboxParameters
    callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
    ```

  * There are no parameters for this method.

* **createTargetPrefetchObject**

  Creates and returns an instance of `TargetPrefetchObject` with the provided data. 

  * Here is the syntax for this method:

    ```objective-c
    +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
    mboxParameters:(nullableNSDictionary *)mboxParameters;
    ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

Here are the public classes that support pre-fetch in iOS :

### Class reference: TargetPreFetchObject

Encapsulates the mbox name and the parameters that are used for mbox prefetch.

* **`name`**

  Name for the location/mbox you want to retrieve.

  * **Type**: NSString*

* **`mboxParameters`**

  An optional dictionary that contains the key-value pairs of mbox parameters.

  * **Type**: NSDictionary*

* **`orderParameters`**

  Dictionary that contains the key-value pairs of order parameters.

  * **Type**: NSDictionary*

* **`productParameters`**

  Dictionary that contains the key-value pairs of product parameters.

  * **Type**: NSDictionary*

### Class reference: TargetRequestObject

This class encapsulates the mbox name, default content, mbox parameters and the return callback used for Target location requests.

* **`name`**

  Name of the requested location.

  * **Type**: NSString*

* **`mboxParameters`**

  The NSString value that represents the name for the location/mbox you want to retrieve.

  * **Type**: NSString*

* **`defaultContent`**

  The default content that will be returned if Target servers are unreachable.

  * **Type**: NSString*

* **`callback`**

  When the batch requests Target locations, callback will be invoked when content is available for this location.

  * **Type**: Function

## Code sample {#section_BF7F49763D254371B4656E17953D520C}

Here is an example of how to prefetch content by using the iOS SDKs:

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

Here is an example of the batch `loadRequest` by using the iOS SDKs: 

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
```

## Additional information {#section_A454BAD1CD49423E86C71BAEE06125FD}

Here is some additional information about these samples:

* `ProductParameters` only allows the following keys:

  * `id` 
  * `categoryId`

* `OrderParameters` only allows the following keys:

  * `id` 
  * `total` 
  * `purchasedProductIds`

* `purchasedProducts` accepts an array of strings.
