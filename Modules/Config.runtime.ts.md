---
id: 8h7foyd9cqkfyiyxo4h19st
title: ts
desc: ''
updated: 1740073792733
created: 1740073792733
---
## Summary
This handles dynamic configuration loading after the initial config is set up. 

## Key Links
- Related Files: [Config Reducer](/ncu-ad-manager/src/Modules/Config/Config.reducer.ts)
- Related Files: [Covatic](/ncu-ad-manager/src/Modules/Covatic/CovaticAccountLink.ts)
- Related Files: [Config](/ncu-ad-manager/src/Modules/Config/Config.ts)


## General Flow
- From `loadRuntimeConfig` you grab a number of config from the store.
- If the user is not logged in, there is an action that removes sensitive info which is removed via a [reducer](/ncu-ad-manager/src/Modules/Config/Config.reducer.ts) 
- Tasks that are pushed into the `runtimeConfigTasks` are based on enabled features: 
1. loadAutoKPI - Gets Ad Manager data 
2. loadIPCheck - Checks user's IP
3. Dynamic floor pricing
4. Grab user data for targeting dependent on logic [Go to Flow for the Lmabda Function]

## Flow for the Lambda Function 
- Within the `loadRuntimeConfig` there is a check for whether the user is logged in, with an unhashedemail (so we do not make unneeded calls to the lambda) and at least one of the following features should be enabled in the config:
1. linkedaccount is enabled
2. publisher audiences is enabled
3. liveramp is enabled
- calls the AWS endpoint with JSONP. It pushes the lambda into the tasks.
- `loadUserIntoLamdbda` gets the id from the cookie and calls the lambda with the ID to fetch data. 
- The fn first gets the src attribute from the script tag that loads the ad manager and the creates the new URL object from it with /covatic appended onto it. This ensures the lambda calls the same domain as the ad manager script. 
- `const: brandCookie && const: userCookie` the brand specific cookie name from the store ad retrieves it from the window. If they exist it is added as query params to the lambda url. The cookie contains user unique identifier to the brand and uses the ID to look up user information in the backend and return personalised data. 
- `const: UserInfo` makes the JSONP call to the lambda which passes the cookie ID to get their data. 
- the cookie (ID card) allows you to get your user data (personal file) from the lambda (the secure office)

## Tasks

## Ideas for Improvement
