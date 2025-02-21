---
id: cd8okkqj0ba40o0k6dgllnn
title: Image Count
desc: 'Sends image count to GAM'
updated: 1740104304594
created: 1740103545541
---
## Code Source
- [Image Count](/ncu-ad-manager/src/Modules/ImageCount/ImageCount.ts)

## Summary
Grabs the image kvp from the window and send it to GAM via slot level targeting. 

## Key Links
- [Page Builder](../../nu-sun-titan/packages/nu-sun-helios/src/page-builder/page-builder.js)
- [GPT](/ncu-ad-manager/src/Modules/GPT/GPT.ts)
- [PR Link for Image KVP](https://github.com/newsuk/nu-sun-titan/pull/11040/files)

## Flow 
- This is linked to `Titan` which provides the image KVP by exposing it on the window. 
- A GPT action triggers the `sendImageKVPtoGAM` fn which ensures the page is an article before proceeding. The image count is picked from the window and then set to the slots with the `GPT.SET_SLOT_LEVEL_TARGETING` action.