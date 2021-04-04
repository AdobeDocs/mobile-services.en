---
description: You can deliver targeted content in Android applications.
keywords: android;library;mobile;sdk
seo-description: You can deliver targeted content in Android applications.
seo-title: Target configuration
solution: Experience Cloud,Analytics
title: Target configuration
topic: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
---
# Target configuration {#target-configuration}

You can deliver targeted content in Android applications.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Required)** The `setContext()` method must be called once in the `onCreate()` method of your main activity.

For example:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

If you already added this method call when you implemented Analytics or Audience Management, you do not need to add it again.
