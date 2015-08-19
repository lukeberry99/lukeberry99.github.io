---
layout: post
title: Using GoogleMaps and Alamofire on Swift
---

One of the requirements on an iOS app I've been working on recently is the need to load locations from an external API and plot them onto a Google map. This is rather simple in theory however I was running into an issue where the app would crash when trying to load the Google Map after I added the Alamofire cocoapod to my Podfile and throw the following error.

`2015-08-19 16:09:56.303 cew-display-prototypes[16820:1347718] CoreData: warning: Unable to load class named 'GMSCachedTile' for entity 'GMSCachedTile'.  Class not found, using default NSManagedObject instead.`

`2015-08-19 16:09:56.303 cew-display-prototypes[16820:1347716] CoreData: warning: Unable to load class named 'GMSCachedObject' for entity 'GMSCachedObject'.  Class not found, using default NSManagedObject instead.`

`2015-08-19 16:09:56.307 cew-display-prototypes[16820:1347718] *** Terminating app due to uncaught exception 'NSInvalidArgumentException', reason: '-[NSManagedObject tileCoords]: unrecognized selector sent to instance'`


After some debugging I realised that the issue arose when attempting to use both ObjectiveC pods (such as `GoogleMapsSDK`) and Swift libraries such as `Alamofire`. 

A really simple solution is to add `-ObjC` to your linkers in XCode which will it to compile the ObjectiveC pods.

After adding the linker everything compiles and I'm able to use the two pods in unison. 
