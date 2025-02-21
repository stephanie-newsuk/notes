---
id: z21xebgkb5rm4iz6oxt1vfo
title: Config
desc: 'Gathers and sets targeting data'
updated: 1740078198389
created: 1740078198389
---
## Summary
This module primarily sets up kvps for GAM by gathering targeting data. It sets special KVPs. It acts as a data collector and formatter for ad targeting.

## Source Code
- Related Files: [Config](/ncu-ad-manager/src/Modules/Config/Config.ts)

## Related Links
- [Config Runtime](/ncu-ad-manager/src/Modules/Config/Config.runtime.ts)
- [Collector](/ncu-ad-manager/src/Modules/Collector/Collector.ts)

## Flow 
- After it is imported, the root saga will dispatch the `CONFIG.ADD` action. There is also a listener for setting targeting calues. 
- `configLoaded` gets different types of targeting from the store and is called. There is also forward targeting which are values from paths in the window object. There is also cookie based targeting which are values from cookies. There are keys and values that are set based on the content type (registered article or sun club). 
- Calls the `loadRuntimeConfig` from the [Config file](/ncu-ad-manager/src/Modules/Config/Config.runtime.ts) whilst dispatching the `CONFIG.ADDED` action which is picked up by [Collector](/ncu-ad-manager/src/Modules/Collector/Collector.ts) or [Exposed Methods](/ncu-ad-manager/src/Modules/ExposedMethods/ExposedMethods.ts)
[[ConfigRuntime]]

## Relevant Files
[[ConfigRuntime]]
[[Collector]]
[[GAM]]