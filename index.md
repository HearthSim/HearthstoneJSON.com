---
layout: default
---

The API is available at [api.hearthstonejson.com/v1/](https://api.hearthstonejson.com/v1/)
-------

The files are all in JSON format, encoded in UTF-8 and categorized by build,
then by locale.

The `/v1/latest/` endpoint redirects (302) to whichever build is the latest one.

All files are automatically converted from the game files, made available in the
[hs-data repository](https://github.com/HearthSim/hs-data/).


### Card objects

[See full card back documentation](docs/cards.html).

Example card:

<img src="images/leeroy.png" style="float: right;" alt="Leeroy Jenkins"/>

```json
{
    "rarity": "LEGENDARY",
    "cost": 5,
    "text": "<b>Charge</b>. <b>Battlecry:</b> Summon two 1/1 Whelps for your opponent.",
    "health": 2,
    "faction": "ALLIANCE",
    "id": "EX1_116",
    "mechanics": [
        "BATTLECRY",
        "CHARGE"
    ],
    "set": "EXPERT1",
    "name": "Leeroy Jenkins",
    "type": "MINION",
    "collectible": true,
    "flavor": "At least he has Angry Chicken.",
    "attack": 6
}
```

----

### Card Back objects

[See full card back documentation](docs/cardbacks.html).

Example card back:

```json
{
    "description": "A generous gift from the Innkeeper.  He loves to see his guests having a good time together.\\n\\nPlay three matches against players on the same local network as you. (Must have at least 3 players on that network!)",
    "name": "Fireside",
    "prefab_name": "Assets/Game/CardBacks/Launch/Card_Back_Launch",
    "note_desc": "Fireside",
    "source": "achieve",
    "id": 4,
    "enabled": true,
    "source_description": "Special"
}
```

----

### Support

HearthstoneJSON is a [HearthSim](http://hearthsim.info/) project and is
available [on GitHub](https://github.com/hearthsim/hearthstonejson).
