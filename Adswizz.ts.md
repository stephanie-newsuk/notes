---
id: 9jw9f5vkktcucal0soa18st
title: Adswizz
desc: 'Adswizz - ads for audio'
updated: 1740070233871
created: 1740064777885
---
## Summary
AdsWizz `decorateStreamUrl` is called by [cps-content-render](../../../times/cps-content-render/packages/radio/src/pages/Live/LiveAudioPlayer.tsx). The Times is responsible for passing the parameters to the Ad Library which generates the stream url to be used in the audio element. 

The Ad Library is responsible for: 
- injecting the AdsWizz script onto the page
- dispatching actions on the AdsWizz status
- grabs the permutive and covatic segments (waits for covatic to return segments for 500ms) required for the stream url which has to be appended to the src in the audio element tag on the page. 
- returns the stream ur[[root]]l from the action's payload (that you send) to the cps content render in the form of a resolved promise.

## Source Code:  
- Related files: [Adswizz main file](/ncu-ad-manager/src/Modules/AdsWizz/AdsWizz.ts)
- Related files: [Test file](/ncu-ad-manager/src/Modules/AdsWizz/AdsWizz.test.ts)
- Related files: [Actions](/ncu-ad-manager/src/Modules/AdsWizz/Adswizz.actions.ts)

## Related Links
- [cps](../../../times/cps-content-render/packages/radio/src/pages/Live/LiveAudioPlayer.tsx)
- [Covatic](/ncu-ad-manager/src/Modules/Covatic/Covatic.ts)
- [Permutive](/ncu-ad-manager/src/Modules/Permutive/Permutive.ts)

## Flow 
- Dispatch the `ADSWIZZ.DECORATE_URL` action with the parameters passed into the action payload
- Action triggers the `enhanceStreamUrl` which takes the payload and attempts to wait for SDK by calling the `waitForAdswizzSDK` fn(attempts to find the SDK), if this is errored out, it is handled by dispatching an action with the basic URL and the completed action. Otherwise it continues by calling sdk decorate fn and passing this new url to the `setStreamUrlParams` 
-  `setStreamUrlParams` takes the new url and appends the consent string, platform string, covatic and permutive. 
- In order to validate, the `checkUrlValidity` uses the `newUrl.protocol`, if it does not pass the check it returns the url from the SDK decorated URL. 
- The new url is then sent through the `ADSWIZZ.COMPLETED` action via the payload to resolve the promise.

## Relevant files 
[[cps-content-render]]
[[Covatic]]
[[Permutive]]