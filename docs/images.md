---
layout: docs
title: Hearthstone Card Art and Render API
---

## art.hearthstonejson.com - Image API

HearthstoneJSON includes a full image API for all the cards in the game.

You are free to use this API without restrictions, but we ask that you
avoid direct embedding on high-traffic websites, and instead re-host the
images. You may also generate them yourself with the game files; the scripts
[are available here](https://github.com/HearthSim/HearthstoneJSON.com).

If you intend to use HearthstoneJSON for commercial purposes, please contact us
at <contact@hearthsim.net>, we'd love to hear from you.


### Card art

Cards are indexed by [CardID](https://hearthsim.info/docs/cards/) (eg. `EX1_001`).


**Base URLs**:

- `https://art.hearthstonejson.com/v1/orig/` ([Example](https://art.hearthstonejson.com/v1/orig/EX1_001.png))
- `https://art.hearthstonejson.com/v1/256x/` ([Example](https://art.hearthstonejson.com/v1/256x/EX1_001.jpg))
- `https://art.hearthstonejson.com/v1/512x/` ([Example](https://art.hearthstonejson.com/v1/512x/EX1_001.jpg))


#### orig/

The `orig` section provides the original, lossless image in PNG format
Note that although most card art is 512x512 resolution, that is not always
consistent and some cards have even been known not to be square at times
(eg. [512x256](https://art.hearthstonejson.com/v1/orig/AT_035.png)).
Using `orig` is not recommended unless you absolutely need lossless images.


#### 256x/, 512x/

The `256x` and `512x` paths offer the full card art, guaranteed to be in
256x256 or 512x512 resolution, respectively.
Art files are available in JPG (`.jpg`) and WebP (`.webp`) formats. Examples:

- <https://art.hearthstonejson.com/v1/256x/EX1_001.jpg>
- <https://art.hearthstonejson.com/v1/256x/EX1_001.webp>


### Card tiles

When a card is placed in a deck, Hearthstone displays a special rectangular
thumbnail of the image. The coordinates for the cut are not consistent across
different cards, but are instead embedded in the Unity assets.

HearthstoneJSON includes a pre-cut repository of card tiles available in 256x59
PNG (`.png`), JPG (`.jpg`) and WebP (`.webp`) formats. Examples:

- <https://art.hearthstonejson.com/v1/tiles/CS2_235.png>
- <https://art.hearthstonejson.com/v1/tiles/CS2_235.jpg>
- <https://art.hearthstonejson.com/v1/tiles/CS2_235.webp>


### Card renders

Rendering a Hearthstone card is not a simple process.
This is why we have [Sunwell](https://github.com/HearthSim/Sunwell), a library
that renders Hearthstone cards to Canvas.

Using Sunwell in the browser however is overkill if all you need is an simple
in-collection render. HearthstoneJSON includes in-collection prerenders for all
renderable cards (Minions, Spells, Weapons, Heroes), in all available Hearthstone
languages.

URL structure:

`https://art.hearthstonejson.com/v1/render/latest/{LOCALE}/{RESOLUTION}/{CARD_ID}.{EXT}`

Legend:

- `LOCALE`: The Hearthstone locale (eg. `enUS`, `frFR`, ...).
  A full list of locales is available in [enums.json](https://api.hearthstonejson.com/v1/enums.json)
- `RESOLUTION`: 256x or 512x for 256px or 512px in width. Height is currently
  1.5x the width, but that may change in future patches if cards gain new assets.
- `CARD_ID`: The card's cardId, as with the other APIs
- `EXT`: The format extension. Only `png` is currently available, but `webp` is
  on the wishlist.

Examples:

- <https://art.hearthstonejson.com/v1/render/latest/enUS/512x/EX1_001.png>
- <https://art.hearthstonejson.com/v1/render/latest/enUS/256x/EX1_001.png>
- <https://art.hearthstonejson.com/v1/render/latest/frFR/512x/EX1_001.png>
- <https://art.hearthstonejson.com/v1/render/latest/thTH/256x/EX1_001.png>
