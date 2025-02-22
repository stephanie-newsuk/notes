---
id: 1zglvjzeb407onbyizmdga6
title: AdIntents
desc: 'AdIntents module for ad serving'
updated: 1740183321333
created: 1740062663635
---
## Summary
Its purpose is to inject a client-specific script for ad targeting. It helps with personalisation of ad targeting, only runs in allowed environments and also waits for consent. 

## Source Code
- [AdIntents](/ncu-ad-manager/src/Modules/AdIntents/AdIntents.ts)


## Related Links
- [Tag](/ncu-ad-manager/src/Modules/Tag/Tag.ts)
- [Consent](/ncu-ad-manager/src/Modules/Consent/Consent.ts)

## Flow 
- After consent is accepted, it injects the AdIntents script. 
- Before injecting it checks for the environment and whether ot not it is allowed to run. 
- the script is tweaked with the client name (grabbed from the store)
