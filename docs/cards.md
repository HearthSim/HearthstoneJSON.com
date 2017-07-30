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

### Example

{% include example-card.md %}

### Fields

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
* `cardClass` (`CardClass` enum, previously named `playerClass`). `DEATHKNIGHT` is unused.
* `type` (`CardType` enum). The only used types are `HERO`, `MINION`, `SPELL`,
  `ENCHANTMENT` (buff), `WEAPON` and `HERO_POWER`.
* `race` (`Race` enum). **Usually** only available on minions.

The following attributes are localized strings:

  `name`, `text` (card text), `flavor` (flavor text), `howToEarn` (how to earn
  the card; eg. reward, craft), `howToEarnGolden` (how to earn the golden
  version of the card) and `targetingArrowText` (the text when targeting
  something with the card)

The following additional attributes are available:

* `collectible` (bool) determines whether the card is collectible.
* `cost` (int) is the card's mana cost. Always shown, even if 0, except on hero
  and buff cards.
* `attack` (int) is the card's attack value. Always shown on minions and weapons.
* `health` (int) is the health value of the card. Always shown for minions and
  heroes.
* `durability` (int) is the durability value of weapons. Always shown for weapons.
* `hideStats` (bool) determines whether the card's stats (cost, atk, health) are
  supposed to be hidden.


### Enums

Most values in Hearthstone are integer-based. Some of those integers are
available as enumerations. The full list of Hearthstone enums is available in
[python-hearthstone - enums.py](https://github.com/HearthSim/python-hearthstone/blob/master/hearthstone/enums.py).


### Tags and referenced tags

The `mechanics` attribute contains a sorted array of `GameTag` boolean enum
string representations which are set on the card.

The following game tags are used in this field:

  `ADJACENT_BUFF`, `AI_MUST_PLAY`, `APPEAR_FUNCTIONALLY_DEAD`, `ADAPT`, `AURA`,
  `BATTLECRY`, `CANT_ATTACK`, `CANT_BE_TARGETED_BY_ABILITIES`, `CANT_BE_TARGETED_BY_HERO_POWERS`,
  `CHARGE`, `CHOOSE_ONE`, `COMBO`, `COUNTER`, `DEATHRATTLE`, `DISCOVER`,
  `DIVINE_SHIELD`, `ENRAGED`, `EVIL_GLOW`, `FORGETFUL`, `FREEZE`, `IMMUNE`, `INSPIRE`,
  `JADE_GOLEM`, `MORPH`, `POISONOUS`, `QUEST`, `RECEIVES_DOUBLE_SPELLDAMAGE_BONUS`,
  `RITUAL`, `SECRET`, `SILENCE`, `STEALTH`, `TAG_ONE_TURN_EFFECT`, `TAUNT`, `TOPDECK`,
  `UNTOUCHABLE`, `WINDFURY`, `ImmuneToSpellpower`, `InvisibleDeathrattle`

Notes:

* `ImmuneToSpellpower` is set on cards which do not increase their damage
  with spell damage like other cards (such as Arcane Missiles).
* `InvisibleDeathrattle` is an internal tag, used mostly in boss cards.
* `AI_MUST_PLAY` is set on AI hero powers which are auto-cast.
* `AUTOATTACK` is a mechanic used in the Karazhan Chess scenario.
* `COUNTER` is... essentially just Counterspell.
* `EVIL_GLOW` is set on cards which glow red while in the hand.
* `FORGETFUL` corresponds to "50% chance to attack the wrong target".
* `RITUAL` corresponds to cards which buff C'Thun.
* `UNTOUCHABLE` is used by minions which "do not count as minions".
* `TOPDECK` is set on cards which are revealed to the opponent when drawn.
* For overload and spellpower, look at `overload` and `spellDamage` properties.


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
