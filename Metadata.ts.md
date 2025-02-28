---
id: 59srk3rd23aeu12ywadg5lq
title: Metadata
desc: 'This is a utility file that contains functions to get metadata from the page'
updated: 1740756201108
created: 1740752930175
---
## Summary

## Source Code
- [Metadata.ts](/ncu-ad-manager/src/Utils/Page/Metadata.ts)


## Related Links
- [Page](/ncu-ad-manager/src/Utils/Page/Page.ts)

## Explanation 
- `getProperty` - generic function that looks up properties from the specified namespace that is passed in as an argument. 
  - Arguments: 
    - `names` - an array of property names to look up
    - `defaultValue` - a default value to return if the property is not found on the page
    - `namespaces` - an array of namespaces to look up the property in
  - Returns: 
    - Returns the first found value or the default value. 
  - It checks for the property names to check for, if it empty then it logs a warning and returns the default value. 
  - Grabs the validnamespaces and then returns a value if it is found with the `getPath` function. 
  - Use: 
    - Use this to get metadata from the page. 

- `getPageType` - determines whether the page is an article, video or a page. 
  - Returns: 
    - `art` - article
    - `video` - video
    - `page` - page
  - It checks if the `page_type` from metadata and uses the isMetaArticle function to check if it is an article. 
  - Uses: 
    - Used to determine the page type for ad targeting. 
  
- `isMetaArticle` - determines if current page is an article through 3 methods.
  - checks all the typical namespaces for an article and returns true if any condition is met. 

- `getMetadata` - this is a function that returns various metadata about the page. 
  - Uses `MetadataTypes` enum to determine what metadata to return. 
  - Each case has specific logic for retrieving and formatting the data.

- `getUserStatus` - returns the user status from the metadata.
  - Determines whether or not the user is logged in or not based on the brand the property is being retrieved from. 

## Relevant Files
[[Page]]