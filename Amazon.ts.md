---
id: zbo8hkd2urkwiaw5ka5qhmb
title: Amazon
desc: ''
updated: 1740103404560
created: 1740101016775
---
## Code Source
- [Amazon](/ncu-ad-manager/src/Modules/AdsWizz/AdsWizz.ts)

## Summary

## Related Links
- [Consent](/ncu-ad-manager/src/Modules/Consent/Consent.ts)

## Flow 
- NOTE: `prepareBid` and `prepareBids` are two different functions. 
- The `waitForThings` fn which waits for consent, the slots defined and that GPT is ready. It also checks if the user is in school, injects the  script and sets up the Amazon Global config. 
- `pauseIfSchool` checks if IP is enabled and if it is enabled it enters a loop that checks the IP type from the state. If it is school then signals that services are ready to start via a `SERVICES.READY` action. The purpose -> this pauses the ad services and resumes when the IP changes to a non-school. It waits for the not school action. 
- `injectAmazonScript` this fn injects the script and dispatches the `AMAZON.INJECTED` action. 
- `globalConfig` this grabs config and constructs it, we intiialise Amazon with publisher settings. 
- From an `AMAZON.READY` action you trigger `prepareBid`. This gets the slot sizes for the current breakpoint. It filters invalid sizes, creates bid object with slot details and handles multi-format when configured - [Gumgum](/ncu-ad-manager/src/Modules/Prebid/Adapters/gumgumBidAdapter.ts). The function returns the bid and is sent in the payload. 
- `gatherPreparedBids` is 

## Tasks
- [ ] // TODO: Finish Amazon Notes

## Ideas for Improvement
