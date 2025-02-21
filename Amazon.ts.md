---
id: zbo8hkd2urkwiaw5ka5qhmb
title: Amazon
desc: 'Handles bid requests and responses for Amazon'
updated: 1740103404560
created: 1740101016775
---
## Summary
Amazon is a bid adapter for Amazon. It is used to request bids from Amazon and set them in GPT.

## Code Source
- [Amazon](/ncu-ad-manager/src/Modules/Amazon/Amazon.ts)
- [Amazon Reducer](/ncu-ad-manager/src/Modules/Amazon/Amazon.reducer.ts)
- [Amazon Actions](/ncu-ad-manager/src/Modules/Amazon/Amazon.actions.ts)
- [Amazon Videos](/ncu-ad-manager/src/Modules/Amazon/Amazon.videos.ts)

## Related Links
- [Consent](/ncu-ad-manager/src/Modules/Consent/Consent.ts)
- [Prebid](/ncu-ad-manager/src/Modules/Prebid/Prebid.ts)
- [GPT](/ncu-ad-manager/src/Modules/GPT/GPT.ts)
- [Gumgum](/ncu-ad-manager/src/Modules/Prebid/Adapters/gumgumBidAdapter.ts)

## Flow 
- NOTE: `prepareBid` and `prepareBids` are two different functions. 
- The `waitForThings` fn which waits for consent, the slots defined and that GPT is ready. It also checks if the user is in school, injects the  script and sets up the Amazon Global config. 
- `pauseIfSchool` checks if IP is enabled and if it is enabled it enters a loop that checks the IP type from the state. If it is school then signals that services are ready to start via a `SERVICES.READY` action. The purpose -> this pauses the ad services and resumes when the IP changes to a non-school. It waits for the not school action. 
- `injectAmazonScript` this fn injects the script and dispatches the `AMAZON.INJECTED` action. 
- `globalConfig` this grabs config and constructs it, we intiialise Amazon with publisher settings. 
- From an `AMAZON.READY` action you trigger `prepareBid`. This gets the slot sizes for the current breakpoint. It filters invalid sizes, creates bid object with slot details and handles multi-format when configured - [Gumgum](/ncu-ad-manager/src/Modules/Prebid/Adapters/gumgumBidAdapter.ts). The function returns the bid and is sent in the payload. 
- `gatherPreparedBids` grabs the bids from the store and if there are any bids it will dispatch a `REQUEST_BIDS` action. 
- the `requestBids` fn will checks the apstag objetc in the window exists so it can go ahead with amazon. It calls the amazon apstag `fetchBids` method and passes in the timeout and slots.
- This then triggers the `bidsBackHandler` fn. This logs which slots had bid responses and then for each response, if the slot exists, you prepate the targeting data and set it at slot level in GPT
- Lastly, the `setDisplayBids` fn is called. This calls the setDisplayBids method on the apstag object. If the payload has slots then it will dispatch an `AUCTION_COMPLETED` action with the slot names joined together. 

## Relevant Files
[[GPT]]
[[Prebid]]
[[Gumgum]]
[[AmazonVideos]]
