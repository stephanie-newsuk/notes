---
id: xl3wv0uradi2crnifnos4v0
title: Consent
desc: 'All things consent related'
updated: 1740184704294
created: 1740184351562
---
## Summary
This module manages user privacy consent for ads by handling different consent guidelines. There is GDPR (EU consent via TCF API) and US (consent via USP API) and the GPP (Global Privacy Platform consent via GPP API). 

## Source Code
- [Consent](/ncu-ad-manager/src/Modules/Consent/Consent.ts)


## Related Links
- [File](/ncu-ad-manager/src/)

## Flow 
- Once the page is initialised, you have to wait for the APIs to be ready in the `consentReady` function. To do this it uses the `tcfapiAndUSAConsentReady` function. 
- The `tcfapiAndUSAConsentReady` function is a promise that waits for the TCF API and USP API to be ready. 

## Relevant Files
// TODO: Finish Consent notes