---
layout: docs
---
## Cards ([cards.json](https://api.hearthstonejson.com/v1/latest/enUS/cards.json), [cards.collectible.json](https://api.hearthstonejson.com/v1/latest/enUS/cards.collectible.json))

The `cards.json` file contains a list of card objects and includes every single
card in the game. Note that in Hearthstone, everything is a card, even Heroes,
Hero Powers and buffs (Enchantments).

`cards.collectible.json` is a restricted set which contains only collectible
cards (cards which will show up in your collection and the base heroes). Please
use this set if you do not need non-collectible cards in your app.

A card is an array of attributes. With noted exceptions, fields are only shown
if they do not evaluate to `0` or an empty string.

The `id` (String) field identifies the card uniquely. Use it! For more info, see
[Card IDs](https://github.com/jleclanche/fireplace/wiki/Card-IDs).

The following attributes are available as non-localized string representations
of enums (as described in the Enums section below):

* `rarity` (`Rarity` enum). Note that the `FREE` rarity does not determine the
  presence of a rarity gem. Cards without a rarity gem are those in the `CORE` set.
* `faction` (`Faction` enum). Although unused in Hearthstone, faction data for
  cards is (unreliably) stored. `NEUTRAL` cards do not display a faction attribute.
* `set` (`CardSet` enum). Also determines the card's watermark. The collectible
  sets are `CORE` (basic, free cards), `EXPERT1` (expert cards), `NAXX`, `GVG`,
  `BRM`, `TGT`, `LOE`, `PROMO` and `REWARD`.
* `playerClass` (`CardClass` enum). `DEATHKNIGHT` is unused.
* `type` (`CardType` enum). The only used types are `HERO`, `MINION`, `SPELL`,
  `ENCHANTMENT` (buff), `WEAPON` and `HERO_POWER`.
* `race` (`Race` enum). **Usually** only available on minions.

The following attributes are localized strings:

  `name`, `text` (card text), `flavor` (flavor text), `howToEarn` (how to earn
  the card; eg. reward, craft), `howToEarnGolden` (how to earn the golden
  version of the card) and `textInPlay` (old field, now unused by Hearthstone)

The following additional attributes are available:

* `collectible` (bool) determines whether the card is collectible.
* `cost` (int) is the card's mana cost. Always shown, even if 0, except on hero
  and buff cards.
* `attack` (int) is the card's attack value. Always shown on minions and weapons.
* `health` (int) is the health value of the card. Always shown for minions and
  heroes.
* `durability` (int) is the durability value of weapons. Always shown for weapons.


### Enums

Most values in Hearthstone are integer-based. Some of those integers are
available as enumerations. The full list of Hearthstone enums is available in
[python-hearthstone - enums.py](https://github.com/HearthSim/python-hearthstone/blob/master/hearthstone/enums.py).


### Mechanics

The `mechanics` attribute contains a sorted array of `GameTag` boolean enum
string representations which are set on the card.

The following game tags are used in this field:

  `ADJACENT_BUFF`, `AURA`, `BATTLECRY`, `CHARGE`, `COMBO`, `DEATHRATTLE`,
  `DIVINE_SHIELD`, `ENRAGED`, `FORGETFUL`, `FREEZE`, `INSPIRE`, `MORPH`,
  `OVERLOAD`, `POISONOUS`, `SECRET`, `SILENCE`, `STEALTH`, `SPELLPOWER`
  `TAG_ONE_TURN_EFFECT`, `TAUNT`, `TREASURE`, `WINDFURY`, `ImmuneToSpellpower`
  `InvisibleDeathrattle`

Notes:

* The `TREASURE` game tag corresponds to the **Discover** mechanic.
* `ImmuneToSpellpower` is set on cards which do not increase their damage
  with spell damage like other cards (such as Arcane Missiles).
* `InvisibleDeathrattle` is an internal tag, used mostly in boss cards.


### Play Requirements

The `playRequirements` attribute contains an array of `key: param` values which
determine various requirements which have to be met for the card to be played
and what it can target. The key corresponds to a `PlayReq` enum string
representation. Most play requirements ignore the parameter, which is thus `0`.

Some (not all) play requirements are documented in the old
[PlayErrors.xml](https://github.com/HearthSim/hs-data/blob/master/PlayErrors.xml).


### Entourage

The `entourage` attributes contains a sorted array of card IDs which represent
the card's "entourage". Entourage is often used for cards which can create new
cards randomly from a specific pool, such as **Animal Companion** or **Ysera**.
