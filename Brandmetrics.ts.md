---
id: 082m8n18t3coyow7qs0j7yy
title: Brandmetrics
desc: 'Handles survey or polling functionality'
updated: 1740184270620
created: 1740183774986
---
## Summary
Brandmetrics manages survey/polling functionality by controlling poll presence on pages. This coordinated with GPT for ad targeting. It is independent of consent and detects existing polls, prevents multiple polls and sets targeting for GPT. 

## Source Code
- [Brandmetrics](/ncu-ad-manager/src/Modules/Brandmetrics/Brandmetrics.ts)


## Related Links
- [GPT](/ncu-ad-manager/src/Modules/GPT/GPT.ts)

## Flow 
- The `injectBrandmetricsWatcher` is a watcher that forks two other watchers. 
- The `injectBrandmetricsScriptWatcher` is a watcher that waits for consent to be accepted or rejected. 
  - `injectBrandmetricsScript` function injects the Brandmetrics script into the page regardless of consent. 
- The `brandmetricsTargetingWatcher` is a watcher that waits for the GPT to be ready. 
  - Once GPT is ready, the `setBrandmetricsTargeting` function is called. This checks if the poll widget is in page. When it does exist it sets brandmetrics targeting to 0. 
  - If it does not, it sets the brandmetrics targeting to 1. 

## Context
Brandmetrics is a polling widget that is used to collect feedback from users. The targeting helps GPT to decide whether to show an ad or not and also avoids multiple polls on the same page.
