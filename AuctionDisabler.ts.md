---
id: x4hkj971vkqyriakyb114zm
title: Auction Disabler
desc: 'Disables auctions for specific paths and regions when GPT is ready.'
updated: 1740756707406
created: 1740147377305
---
## Summary
Provides a way to disable auctions for specific paths and regions when GPT is ready. 
## Source Code
- [Auction Disabler](/ncu-ad-manager/src/Modules/AuctionDisabler/AuctionDisabler.ts)


## Related Links
- [GPT](/ncu-ad-manager/src/Modules/GPT/GPT.ts)

## Flow 
- It waits for the GPT script to be ready and then calls the `disableRefreshByTargetedCampaignDetection` function. 
- `disableRefreshByTargetedCampaignDetection` gets the unit path from the store and gets the disable auction ad unit paths and regions from the store. 
- It then gets the country from the page targeting. If the country is in the regions object then it adds the disable auction ad unit paths to the disable auction ad unit paths array. 
- It then checks if the page path is in the disable auction ad unit paths array. 
- If it is then it dispatches a `TAKEOVER_DETECTED_DISABLE_AUCTIONS` action. 

## Relevant Files
[[GPT]]