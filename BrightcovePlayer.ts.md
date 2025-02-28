---
id: m8fpguplxsdkmepssgrfpdg
title: BrightcovePlayer
desc: 'Handles video ads for Brightcove'
updated: 1740757244420
created: 1740756781240
---
## Summary
Brightcove is a video platfrom that provides video hosting and streaming services. It is being used to handle video ads. This module sets up a listener for video ad impressions, hdnales tracking and uses the IMA3 SDK for managing the video ads. 

## Source Code
- [BrightcovePlayer](/ncu-ad-manager/src/Modules/BrightcovePlayer/BrightcovePlayer.ts)


## Related Links
- [File](/ncu-ad-manager/src/)

## Flow 
- We inject the watcher saga and call the `BrightcovePlayerEventListener` function. 
- This function sets up an event listener for the `nuk.brightcovePlayer.adImpression` event and calls the `eventCallback` function. This sets up a listener for video ad impressions. When the event is triggered it calls the `eventCallback` function. 
- `eventCallback` fn is

## Relevant Filess
