---
layout: docs
---
## Card Backs ([cardbacks.json](https://api.hearthstonejson.com/v1/latest/enUS/cardbacks.json))

Card Back objects all have the following attributes:

* `id` (int): Unique ID.
* `name` (locstr): Localized name of the card back
* `description` (locstr): Localized description of the card back
* `note_desc` (str): Internal description.
* `source` (str): How the card back is obtained. Can be one of `achieve`,
  `fixed_reward` or `season`.
* `source_description`: Internal note on the source.
* `enabled`: Whether the card back is usable.
* `prefab_name`: Path to the card back's image in the game files.
