---
layout: default
title: An API for Hearthstone
---

The API is available at [api.hearthstonejson.com/v1/](https://api.hearthstonejson.com/v1/)
-------

The files are all in JSON format, encoded in UTF-8 and categorized by build,
then by locale.

The `/v1/latest/` endpoint redirects (302) to whichever build is the latest one.

All files are automatically converted from the game files, made available in the
[hs-data repository](https://github.com/HearthSim/hs-data/).

----

## Card objects

[See full card documentation](docs/cards.html).

Example card:

{% include example-card.md %}

----

## Changelog

{% include changelog.md %}

----

## Support

HearthstoneJSON is a [HearthSim](https://hearthsim.info/) project and is
available [on GitHub](https://github.com/HearthSim/HearthstoneJSON/).
