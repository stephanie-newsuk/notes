---
id: z9yx4tzorhokwigss7fy3vh
title: GPT
desc: 'test'
updated: 1740176963298
created: 1740149636114
updated1: <%- new Date(1740176934293).toDateString() %>  # Will show as "Fri Feb 21 2025"
created2: <%- new Date(1740149636114).toDateString() %>
up: {{date.now}}
create: {{date.created}}
create1: date.created:YYYY-MM-DD:
---
## Summary
Google's GPT manages ad delivery and rendering, slot deifntions, targeting and auction processes. This integrates with GAM to serve ads. 

## Source code
- [GPT](/ncu-ad-manager/src/Modules/GPT/GPT.ts)

## Key Links
- [File](/ncu-ad-manager/src/Modules/Slots/Slots.ts)

## Flow 
There are a number of steps to the GPT flow that are triggered by actions asynchronously. This flow will not be in order. 
- It waits for consent and the GPT script to be ready before proceeding. This is the `waitForConsentAndGPTScript` function. It checks for consent, the slots are completed, auction has been explicitly enabled before it injects the script. It sends the `GPT.INITIALISED` action.
- The function triggered is `waitForGPTReady` which waits for the Google API to be ready and sends a signal. 
- `handleGPT` sets up the core functionality by adding event listenters (`addSlotRenderEventListener`, `addSlotRequestEventListener`, `addImpressionViewableEventListener`), setting up presets and detects private sandbox labels. 
- `detectPrivateSandboxLabel` detects if the private sandbox label is set and if it is it will dispatch the `GPT.DETECT_PRIVATE_SANDBOX_LABEL` action. 
  - It is part of Google's privacy sandbox initiative (solution to phasing out third party cookies). It detects if the user's browser is in the cookie deprecation trial. Checks if the label API is available in the browser and grabs the value from the browser. This is set as targeting data with `cft` cookie. This is how infor is used by GAM to serve appropriate ads. 

-  `onSlotRender` is triggered by `addSlotRenderEventListener` and is triggered when a slot is rendered. It logs the slot details and the GAM link. 
- `addImpressionViewableEventListener` is triggered by `addImpressionViewableEventListener` and is triggered when a slot is rendered. It logs the slot details and the GAM link. 

- `gptPresets` disables initial load and enables single request with the `enableSingleRequest` fn on googletag. It also collapses empty divs. 
  - Collapsing divs - When `collapseEmptyDivs()` is called, any ad slot that receives no ad (empty response) will be collapsed to 0x0 pixels. This prevents empty white spaces on the page where ads failed to load This then improves user experience by not showing blank spaces.
  - GPT Single Request Architecture - instead of maning separate HTTP requests for each ad slot, all ad slots are requested in a single HTTP request to the Google ad server. This reduces overhead and latency. This lets Google see all ad slots at once which lets them make better decisions on which ads to serve. You can then optimise overall page revenue than individual slot revenue. 
- `gptAddPageTargeting` adds page targeting. It sets page level targeting for  testmode pages. It grabs page targeting from the store and adds it to the GPT page targeting. 
- `gptPrepareSlots` prepares the slots. It grabs the slots from the store and adds them to the GPT slots. This is responsible for triggering prep for each slot. 
- `gptEnableServices` calls the function from google and it is required before the ads are displayed. Service completion is signalled by the action. 
- `requestAds` waits for service completion and then requests ads. It grabs the slots from the store and adds them to the GPT slots. Then refresh is triggered. 
- `gptRefresh` is triggered by the `gptRefresh` action. It waits for the slots to be displayed and then refreshes the ads. 

- It then adds page targeting. 
- It then enables services. 
- It then prepares slots. 
- It then completes page level targeting. 

## TODO: Finish GPT flow