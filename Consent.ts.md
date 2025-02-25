---
id: xl3wv0uradi2crnifnos4v0
title: Consent
desc: 'All things consent related'
updated: 1740494167575
created: 1740184351562
---
## Summary
This module manages user privacy consent for ads by handling different consent guidelines. There is GDPR (EU consent via TCF API) and US (consent via USP API) and the GPP (Global Privacy Platform consent via GPP API). 

## Source Code
- [Consent](/ncu-ad-manager/src/Modules/Consent/Consent.ts)

## Flow 
- Once the page is initialised, you have to wait for the APIs to be ready in the `consentReady` function. To do this it uses the `tcfapiAndUSAConsentReady` function. 
- The `tcfapiAndUSAConsentReady` function is a promise that waits for the TCF API and USP API to be ready. 
- `addEventListener` then `tcDataResolver` is called which is a fork based on GDPR applicability.
1. If GDPR does not apply 
- calls `getUSAconsent()` which returns a promise along with the consent. This sends the consent payload along with the `CONSENT.DONE` action. 

2. If GDPR does apply
- calls `checkConsentStringValid` which validates that it is GDPR jurisdiction and not GPP.Within this function it will dispatch `CONSENT.DONE or CONSENT.REJECTED`. Either way consent resolves. 

3. GPP Fall back
- if _gpp is a function that exists on the window then we call `getGPPConsent` which is another promise that resolves with the data. 

For cleanup, you call `removeEventListener` which removes the TCF event listener and logs completion. 

## Relevant Files
[[Covatic]]
[[Adswizz]]
[[Amazon]]
[[GPT]]