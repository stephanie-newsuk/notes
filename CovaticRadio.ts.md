---
id: dl73hpl659n9px8bj5nxbpp
title: Covatic Radio
desc: 'Covatic for radio stations'
updated: 1740084235923
created: 1740079141073
---
## Summary
This is a special version of Covatic for tracking audio consumption. Covatic tracks article and page views, general user behaviour, works on any page and tracks text based content consumption. Whereas Covatic Radio tracks audio instead, tracks play/pause events, duration and playhead position on only radio pages. 

## Source code: 
- Related Files: [Covatic Radio](/ncu-ad-manager/src/Modules/Covatic/CovaticRadio.ts)

## Related Links
- [Covatic](/ncu-ad-manager/src/Modules/Covatic/Covatic.ts)

## Flow 
- When `COVATIC.INITIATED` action is dispatched in the [Covatic Module](/ncu-ad-manager/src/Modules/Covatic/Covatic.ts) this triggers the `initRadioEvents` fn. The same occurs with `COVATIC.SEND_RADIO_CONSUMPTION`. This only occurs to sites that have the Covatic Radio Module imported. 
- `initRadioEvents` checks if the page is a radio page and adds event listeners to the play and pause event with an radio consumption action. 
- `sendRadioConsumptionData` fn checks it is a Covatic enabled player and grabs metadata from the window for covatic. This is then sent to Covatic SDK with the SDK `notifyEvent` method. 
- When the user interacts with play/pause triggers event and gets the current state. This is then sent to Covatic for traffic. 
- Covatic helps build user profiles based on what audio content they consume and how they consume it (duration, completion etc).

## Relevant Files
[[Covatic]]
[[Config]]
