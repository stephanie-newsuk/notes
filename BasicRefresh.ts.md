---
id: ntlcjgjtedlzrass9073q1j
title: Basic Refresh
desc: 'Refresh module for ad serving'
updated: 1740183314850
created: 1740183044201
---
## Summary
Basic refresh handles periodic refreshing of ads to keep them fresh and relevant. This also maximises revenue opportunities and only refreshes ads that are visible to the user. 

## Source Code
- [Basic Refresh](/ncu-ad-manager/src/Modules/BasicRefresh/BasicRefresh.ts)


## Related Links
- [File](/ncu-ad-manager/src/)

## Flow 
- This is triggered by the `GPT.IMPRESSION_VIEWABLE` event which means it only starts when ad becomes visible to the user.  

## Relevant Files
