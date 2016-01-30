Changes since legacy API:

- Website:
  - New website style and theme!
  - API now has its own subdomain and is served with HTTPS
  - API is now versioned (/v1/)
  - Separate output for each build. /v1/latest/ will always give you the latest build.
  - Locales are now generated into their own directory
  - Zip support has been removed in favour of server compression
- Cards:
  - CardSet separation has been removed as it was largely unused
  - Tags are not localized anymore (mostly this just means uppercased)
  - Created separate "collectible" set
  - Added individual `set` and `targetingArrowText` properties
  - Added some more mechanics (forgetful, treasure...)
  - Added `entourage` property
  - Added `playRequirements` property
  - Added `dust property
- Card backs:
  - Added more properties from the DBF
