---
id: 4tfjy372vbbqhg265u79zxs
title: 'Covatic Account Link'
desc: ''
updated: 1740073053633
created: 1740073053633
---
## Description: 
- Related Files: [Covatic Account Link](/ncu-ad-manager/src/Modules/Covatic/CovaticAccountLink.ts)
- Related Files: [Covatic](/ncu-ad-manager/src/Modules/Covatic/Covatic.ts)
- Related Files: [Config](/ncu-ad-manager/src/Modules/Config/Config.runtime.ts)

## Summary
This is to link user demographic data to covatic's tracking system. This handles personal data like the age, email, postcode and gender of the user. 

## Key Links
- [File](/ncu-ad-manager/src/)

## Flow 
- It waits for both user and covatic to be ready before going ahead with this module. [Config adds user data to the config](/ncu-ad-manager/src/Modules/Config/Config.runtime.ts). Then it calls the `sendAdditionalUserInfo` fn. 
- This fn gets the user information from the store 
- 

## Tasks
- //TODO: [ ] This is linked into Config.runtime doc - limk to the config_fetched_useR_info from there - grabs data from a lambda?


## Ideas for Improvement
