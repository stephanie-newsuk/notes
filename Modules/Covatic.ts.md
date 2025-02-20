---
id: hctbaiur38yhwqhe3ejtb7x
title: ts
desc: ''
updated: 1740073033601
created: 1740070162239
---
## Description: 
- Related Files: [File](/ncu-ad-manager/src/)

## Summary
Covatic is a user behaviour tracking and audience segmentation SDK that tracks article and media consumption on the page. This assigns users to audience segments for targeted advertisig. It handles anonymous and authenticated users differently and does require user consent. It helps us to better understand what content users consume to better target ads and is in line with privacy regulations. 

## Key Links
- [File](/ncu-ad-manager/src/)

## Flow 
- Calls the `injectCovaticScript` which injects the covatic script with the `TAG` action.
- This this cals the `initCovatic` function which attempts to wait for the SDK to load (will wait for at least 15 times). If it can initiate then it will get the secret from the store and make a call to the SDK via the window with the secret and signal it is ready. This initialises the SDK with a client secret. `COVATIC.INITIATED` is dispatched. 
- When initiated the `sendArticleOnPageLoadConsumption` fn is called. This creates the consumption event. This is then passed into the SDK and an action dispatched. 
- `getSegments` is called which calls `isLoggedIn` from [Page module](/ncu-ad-manager/src/Utils/Page/Page.ts). 
- It then grabs the segments via `getLinkedAudiences` if the user is logged in, if not then it grabs the segments via `getAudiences`, they return the segments if successful. 

## Tasks
// TODO: [ ] Find out what EXACTLY a consumption event is and why it is required for covatic

## Ideas for Improvement