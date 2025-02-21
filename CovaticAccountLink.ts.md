---
id: 4tfjy372vbbqhg265u79zxs
title: 'Covatic Account Link'
desc: 'Refined user data enrichment for Covatic'
updated: 1740073053633
created: 1740073053633
---
## Code Source: 
- Related Files: [Covatic Account Link](/ncu-ad-manager/src/Modules/Covatic/CovaticAccountLink.ts)
- Related Files: [Covatic](/ncu-ad-manager/src/Modules/Covatic/Covatic.ts)

## Summary
This is to link user demographic data to covatic after the lambda has returned the user information. This handles personal data like the age, email, postcode and gender of the user. This sends the data to Covatic for better ad targeting. This helps to build richer user profiles. 

This is separated for single responsibility principle and allows for easy modification to data handling without touching core tracking. Can disbale user data enrichment without affecting basic tracking functionality.

## Key Links
- Related Files: [Config](/ncu-ad-manager/src/Modules/Config/Config.runtime.ts)

## Flow 
- It waits for both user data from the lambda and covatic to be ready before going ahead with this module. [Config adds user data to the config](/ncu-ad-manager/src/Modules/Config/Config.runtime.ts). Then it calls the `sendAdditionalUserInfo` fn. 
- This fn gets the user information from the store that has been retrieved by the lambda. Then sends each piece to the Covatic SDK. 
