---
id: 9jw9f5vkktcucal0soa18st
title: Adswizz
desc: ''
updated: 1740065740895
created: 1740064777885
---
- Description:  
- Related files: [File](/ncu-ad-manager/src/Modules/AdsWizz/AdsWizz.ts)
- Related files: [File](/ncu-ad-manager/src/Modules/AdsWizz/AdsWizz.test.ts)
- Related files: [File](/ncu-ad-manager/src/Modules/AdsWizz/Adswizz.actions.ts)

## Summary
AdsWizz `decorateStreamUrl` is called by [cps-content-render](../../../times/cps-content-render/packages/radio/src/pages/Live/LiveAudioPlayer.tsx). The Times is responsible for passing the parameters to the Ad Library. 

The Ad Library is responsible for: 
- injecting the AdsWizz script onto the page
- dispatching actions on the AdsWizz status
- grabs the permutive and covatic segments (waits for covatic to return segments for 500ms) required for the stream url which has to be appended to the src in the audio element tag on the page. 
- 
## Key Links

## Tasks
- [ ] Check logic at line X
- [ ] Write unit test for function Y

## Ideas for Improvement
