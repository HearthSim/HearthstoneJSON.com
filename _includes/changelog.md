#### Patch 7.1.0.17720:

- `playerClass` has been renamed `cardClass`. Both properties are still
  available, but the former will be removed in an upcoming patch.
- The cardback API is no longer supported, as almost nobody was using it.
- Support for the `dust` property has been dropped as it is not reliable.
- New property: `referencedTags`. This works exactly like `mechanics`,
  except that it contains tags which are *referenced* rather than directly
  set on the card (for example: Mad Scientist *references* `SECRET`).
- `TREASURE` has been renamed to `DISCOVER`.
- New property: `hideStats` (boolean)

#### Patch 7.0.0.15590:

The game files have greatly changed for the Gadgetzan patch.
Some of the data may have changed in unexpected ways.

- New property: `multiClassGroup`. Currently, this can be `GRIMY_GOONS`,
  `JADE_LOTUS` or `KABAL`.
- New property: `classes`. This is a list of classes, which is only included
  when the card is available for multiple classes. Note that the `playerClass`
  is usually `NEUTRAL` for multi-class cards.
- New property: `collectionText`. Some cards, most notably Jade Golem cards,
  have multiple card texts: A generic one (for the collection) and a formatted
  version, with `{}` placeholders. The `collectionText` property is the generic
  version of the description.
- The `textInPlay` property is no longer supported as it is no longer used.


#### Changes since legacy API

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
