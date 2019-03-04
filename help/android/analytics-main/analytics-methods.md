---
description: Here is a list of Adobe Analytics methods that are provided by the Android library.
keywords: android;library;mobile;sdk
seo-description: Here is a list of Adobe Analytics methods that are provided by the Android library.
seo-title: Analytics Methods
solution: Marketing Cloud,Analytics
title: Analytics Methods
topic: Developer and implementation
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
---

# Analytics methods {#analytics-methods}

Here is a list of Adobe Analytics methods that are provided by the Android library.

The SDK currently supports multiple [!DNL Adobe Experience Cloud Solutions], including [!DNL Analytics], [!DNL Target], [!DNL Audience Manager], and the [!DNL Experience Cloud ID Service]. Methods are prefixed according to the solution, for example, Experience Cloud ID methods are prefixed with `analytics`.

Each of the following methods is used to send data to your Adobe Analytics report suite: 

* **trackState**

  Tracks an app state with optional context data. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. These states are similar to pages on a website, and `trackState` calls increment page views. 
  
  If `state` is empty, `app name app version (build)` is displayed in reports. If you see this value in reports, ensure that you set `state` in each `trackState` call. 
  
  >[!TIP]
  >
  >This is the only tracking call that increments page views.

  * Here is the syntax for this method:

    ```java
    public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
    ```

  * Here is the code sample for this method:

    ```java
    Analytics.trackState("loginScreen",null);
    ```

* **trackAction**
  Tracks an action in your app.
  
  Actions that you want to measure, such as `logons`, `banner taps`, `feed subscriptions`, and other metrics, that occur in your app. 

  * Here is the syntax for this method:

    ```java
    publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
    ```

  * Here is the code sample for this method:

    ```java
    Analytics.trackAction("heroBannerTouched",null);
    ```

* **getTrackingIdentifier**
  Returns the automatically generated visitor identifier for Analytics. 
  
  This is an app-specific, unique visitor ID that is generated at the initial launch and is stored and used from that point forward. The ID is preserved between app upgrades and is removed when the app is uninstalled. 

  * Here is the syntax for this method:

    ```java
    public static String getTrackingIdentifier(); 
    ```

  * Here is the code sample for this method:

    ```java
    String trackingId = Analytics.getTrackingIdentifier(); 
    ```
  
* **trackLocation**

  Sends the current latitude, longitude, and location in a defined point of interest. For more information, see [Geo-location and Points of Interest](/help/android/location/geo-poi.md).

  * Here is the syntax for this method:

    ```java
    public static void trackLocation(Location location, Map<String,Object> contextData); 
    ```

  * Here is the code sample for this method:

    ```java
    Analytics.trackLocation(userLocation, null);
    ```

* **trackLifetime​ValueIncrease**

  Adds `amount` to the user's lifetime value. 

  * Here is the syntax for this method:

    ```java
    publicstaticvoidtrackLifetimeValueIncrease(BigDecimalamount,Map&lt;String,Object&gt;contextData);
    ```

  * Here is the code sample for this method:

    ```java
    Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
    ```

* **trackTimed​ActionStart**

  Start a timed action with name `action`.
  
  If you call this method for an action that has already started, the previous timed action is overwritten. 
  
  >[!TIP]
  >
  >This call does not send a hit. 

  * Here is the syntax for this method:

   ```java
   publicstaticvoidtrackTimedActionStart(Stringaction,Map&lt;String,Object&gt;contextData);
   ```

  * Here is the code sample for this method:

    ```java
    Analytics.trackTimedActionStart("cartToCheckout",null)
    ```

* **trackTimed​ActionUpdate**

  Pass in `contextData` to update the context data that is associated with the `action`. The `data` that is passed in is appended to the existing data for the action, and if the same key is already defined for `action`, overwrites the data. 
  
   >[!TIP]
   >
   >This call does not send a hit. 

  * Here is the syntax for this method:

    ```java
    public static void trackTimedActionUpdate(Stringaction,Map <String,Object> contextData); 
    ```

  * Here is a code sample for this method:

    ```java
    HashMap cdata = new HashMap<String Object> (); 
    cdata.put("quantity",3); 
    Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
     ```

* **trackTimed​ActionEnd**

  End a timed action. If you provide `block`, you can access the final time values and can manipulate `data` before sending the final hit. 

   >[!TIP]
   >
   >If you provide `block`, you must return `true` to send a hit. Passing `null` for `block` sends the final hit.

  * Here is the syntax for this method:

    ```java
    public static void trackTimedActionEnd(Stringaction,TimedActionBlock<Boolean> logic); 
    ```

  * Here is the code sample for this method:

    ```java
    Analytics.trackTimedActionEnd("cartToCheckout",new
    Analytics.TimedActionBlock&lt;Boolean&gt;(){
      @Override
      public Booleancall(long inAppDuration,long totalDuration, Map<String,
    Object> contextData) {
            contextData.put("price", 49.95);
            return true;
       }
    });
    ```

* **sendQueuedHits**

  **Requires SDK 4.1.** 
  
  Regardless of how many hits are queued, this method forces the library to send all hits in the offline queue. 

  * Here is the syntax for this method:

    ```java
    voidsendQueuedHits()
    ```

  * Here is the code sample for this method:

    ```java
    Analytics.sendQueuedHits();
    ```

* **getQueueSize**

  Returns the number of stored tracking calls in the offline queue. 

  * Here is the syntax for this method:

    ```java
    long getQueueSize()
    ```

  * Here is the code sample for this method:

    ```java
    long queueSize = Analytics.getQueueSize(); 
    ```

* **clearQueue**
  
  Clears all of the hits from the offline queue.

  * Here is the syntax for this method:

    ```java
    voidclearQueue()
    ```

  * Here is the code sample for this method:

    ```java
    Analytics.clearQueue();
    ```

    >[!WARNING]
    >
    > Use caution when manually clearing the queue. This process cannot be reversed.