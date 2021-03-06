RunescapeHighscores
===================
[![Latest Stable Version](https://poser.pugx.org/that-chris-r/runescape-highscores/v/stable.svg)](https://packagist.org/packages/that-chris-r/runescape-highscores) [![Total Downloads](https://poser.pugx.org/that-chris-r/runescape-highscores/downloads.svg)](https://packagist.org/packages/that-chris-r/runescape-highscores) [![Latest Unstable Version](https://poser.pugx.org/that-chris-r/runescape-highscores/v/unstable.svg)](https://packagist.org/packages/that-chris-r/runescape-highscores) [![License](https://poser.pugx.org/that-chris-r/runescape-highscores/license.svg)](https://packagist.org/packages/that-chris-r/runescape-highscores)

A PHP layer on top of the RuneScape Highscores.

## Install

### Installing via composer

If you run this command with composer it'll require it into your project

`composer require that-chris-r/runescape-highscores`

Or add this to your composer.json

```javascript
{
	"require": {
		"that-chris-r/runescape-highscores": "2.*"
	}
}
```

### Installing via git

Alternatively you can clone this repository and use the files in lib.

## Retrieving a player

In order to access a player you need to create a new highscores object and use that to query the RuneScape API, `$client = new RunescapeHighscores();`.

Once you have a client you can retrieve a single player using the `get_player` method, `$player = $client->get_player('Das Wanderer');`.

You can also retrive multiple players at one time using the `get_players` method, `$players = $client->get_players(["Das Wanderer", "Bexs"]);`.

This will return an indexed array with the indexes being the RuneScape usernames, E.G. `$players["Das Wanderer"]` will give you access to a player object.

## Using a player object

### Properties

Player objects use magic methods to access the properties for a player.

Each attribute holds its values in a `PlayerValue` class, when treated like a string it will return the level for skills and rank for anything else.

So to access a players attack level you do:

```
// Short syntax
echo $player->attack;
// Longer syntax
echo $player->attack->level;
```

Each `PlayerValue` object holds other values, for skills it holds
* Rank
* Xp
* Level

For minigames it holds:
* Rank
* Score

Minigames are access as they are named in the api documentation and spaces are replaced with underscores, so to access the information for a player on Dominion Tower you use `$player->dominion_tower->rank`.

### Combat levels

You can access both the standard combat level and the legacy combat level on a player object with the following methods, `get_legacy_combat_level` and `get_combat_level`.

### Converting to Array

You can convert the player object to an array if you need to by calling the `to_array` method.

## Issues
If you have any issues please raise them via github
