---
id: m8fpguplxsdkmepssgrfpdg
title: BrightcovePlayer
desc: 'Handles video ads for Brightcove'
updated: 1740757646065
created: 1740756781240
---
## Summary
Brightcove is a video platfrom that provides video hosting and streaming services. It is being used to handle video ads. This module sets up a listener for video ad impressions, hdnales tracking and uses the IMA3 SDK for managing the video ads. 

## Source Code
- [BrightcovePlayer](/ncu-ad-manager/src/Modules/BrightcovePlayer/BrightcovePlayer.ts)

## Flow 
- We inject the watcher saga and call the `BrightcovePlayerEventListener` function. 
- This function sets up an event listener for the `nuk.brightcovePlayer.adImpression` event and calls the `eventCallback` function. This sets up a listener for video ad impressions. When the event is triggered it calls the `eventCallback` function. 
- `eventCallback` fn takes the custom event and extracts the `ima3` object. It takes a few details from the object. We call `getCreativeId`. 
- `getCreativeId` fn takes the `creativeId` and `wrapperCreativeIds` and returns the first creative id. It checks the wrapper ID and then falls back to regular creative IDs. This returns empty string if no valid ID found. 
- It will return the ID or an empty string and returns back to `eventCallback` fn & then disatches an action with the details. 
