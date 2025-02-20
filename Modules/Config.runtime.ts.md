---
id: 8h7foyd9cqkfyiyxo4h19st
title: ts
desc: ''
updated: 1740073792733
created: 1740073792733
---
## Description: 
- Related Files: [File](/ncu-ad-manager/src/Modules/Covatic/CovaticAccountLink.ts)
- Related Files: [File](/ncu-ad-manager/src/Modules/Config/Config.ts)

## Summary

## Key Links
- [File](/ncu-ad-manager/src/)

## Flow for the Lambda Function 
- Within the `loadRuntimeConfig` there is a check for whether the user is logged in, with an unhashedemail (so we do not make unneeded calls to the lambda) and at least one of the following features should be enabled in the config:
1. linkedaccount is enabled
2. publisher audiences is enabled
3. liveramp is enabled
- calls the AWS endpoint with JSONP. It pushes the lambda into the tasks. 

## Tasks
- [ ] // TODO: Add notes for the rest of the file outside of the lambda function 

## Ideas for Improvement
