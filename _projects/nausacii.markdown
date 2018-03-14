---
layout: post
title:  "Nausacii"
date: 2017-12-09
lang: eng
---
<h2>Nausacii</h2>

I tried to make a boardgame in 2015. This post summarize all the iteration until I came up with a working prototype and more.

<h3>First iteration</h3>

Cards + Hex Tiles in a competitive game.
The game revolved around a lot of differents mechanics, which was interesting but not really a good idea.

Players have 4 outpost, 4 towns, 4 cities and 4 meeples. Initially a player would have 2 meeples and 2 outpost.
At the start each player would draw 7 research cards, and a draft would occure (take one, give the remaining) until each player would have 7 research cards.
Research cards would give advantages (permanent, added to deck or immediate).

First part of the game, each player draw a tile from a pool which depend of the number of player (7 cards per player : 2 plains, 2 forest, 2 river and 1 swamp).
Outpost produce the first ressource, then town the second, then city the last one (This would result by adding a ressource card in the deck). Gold can replace any ressource.
Meeple was a card in the deck which allows to produce the first ressource at the position of any stading pawn (by turning it)
Plain : produce food, then wood, then gold (max 4 pawns)
Forest : produce wood, then rock, then gold (max 4 pawns)
Mountain : produce rock, then food, then gold (max 4 pawns)
Swamp : produce nothing, then gold, then gold and cannot be occupied by more than 3 pawns
Player must place the drawn tile adjacente to two already placed tiles (except first and second one obviously). When placing a tile a player could add a meeple and an outpost.
(Mandatory on the two last placed tiles if none have been placed before)

In a second part, each player would draw cards from his deck, which would allow him to do certain actions. the research action would always be possible (3 same ressources)
For example :
Meeple (1 Force)
- Produce a ressource at the position of a standing pawn
- Move a meeple
- Transform into an outpost (1 wood)

Outpost (1 Force)
- Recruit a meeple (1 food)
- Improve in town (1 rock, 1 wood)

Town (2 Force)
- Recruit a meeple (1 food)
- Improve in city (2 rock, 1 wood)

City (3 Force)
- Recruit a meeple (1 food)

The deck was dependent of the current state of the game. If you loose a town, you'll need to remove the town and the two ressources cards from your deck.
At the end of his turn, the player would resolve any conflict occured, each player could play one card from his deck to improve their forces.

The way to win was to build 4 cities, or control more than 7 tiles at the end of its turn, or having reached the max research level.

The game was then flavored with differents raceand their power.

<h4>Flaws</h4>

The start was not a problem, it was interesting to create the map and deciding to place the meeple and outpost.
It was hard to choose research cards, and they would not really change the way you would play.

Clunky. The way the game was running with adding and removing cards from your deck was slow.
Combat, an important part of the game, was not well handled and I couldn't figure a way to handle it well.

When playtested, the game showed that you cannot really forsee what makes you win or loose.

<h4>Fine point</h4>

Hexagonale tiles are cools. Buildings are also cool.

<h3>Second iteration</h3>

I'm more of a cooperative boardgame fan. So I changed almost everything for a cooperative game keeping only some ideas.

Random wind each turn with a dice (or rotating arrow). Passive power of race are dependant of the wind.

Production is done by drawing cards from decks.

<h3>Third iteration</h3>

<h4>First playtest</h4>

<h3>Fourth iteration</h3>

Inspired from Nausicaa...

> You are the last survivor of earth, beseiged by a forest you don't understand but it kills human.

```javascript
var base = new Bone(0,0,0,0,null,0xffffff);
var torso = new Bone(0,12,0,2,base,0xffff00);
var shoulder_lf = new Bone(2,12,0,1.5,torso,0xff0000);
var shoulder_rg = new Bone(-2,12,0,1.5,torso,0x00ff00);
var elbow_lf = new Bone(4.5,10,0,2.5,shoulder_lf,0xff00ff);
var hand_lf = new Bone(6,8,0,2.5,elbow_lf,0x0000ff);
    var elbow_rg = new Bone(-4.5,10,0,2.5,shoulder_rg,0x00ffff);
```

The goal of the game is too search the solution, by making expedition into the growing forest tiles.

Players and Nausacii start in the center of an hexe map of 4 tiles of radius.

Loosing can come from having too many tiles in forest at the same time, annoying too much the forest

<h3>Actions</h3>

Each player has initially 1 water/turn thanks to the central tile.
Each player start with a pawn. If at a moment of the game a player has no pawn, a new one can be produced at the center tile instead of having a water this turn.

<ul>
    <li>2 food : Recruit a pawn</li>
    <li>1 water : Move a pawn</li>
    <ul>
        <li>If it ends up in a forest tile, without Nausacii on the same tile or an adjacent outpost, its lost</li>
    </ul>
    <li>1 food : Clean a cube at a pawn position</li>
    <li>1 food & 1 water : Clean a forest at a pawn position, <em>increase forest irritation by one</em></li>
    <li>1 brick : Build an outpost</li>
    <ul>
        <li>An outpost is lost if the tile turn into a forest</li>
    </ul>
    <li>Build a wall</li>
    <ul>
        <li>A wall has a direction, it cannot sustain the wind if there is no pawn on the tile and it cannot be crossed (either by pawns or forest cube)</li>
    </ul>
</ul>

Some special action which require some conditions

<ul>
    <li>Move Nausacii</li>
    <ul>
        <li>Nausacii prevent forest iritation from action taken on the same tile of her and can protect pawn in the forest</li>
    </ul>
    <li>Search for a clue</li>
    <ul>
        <li>Only possible by a pawn in a forest tile with a cube on it, only the first 7 forest tiles have a cube on them</li>
        <li>The cube is put ontop of the pawn, and must me brought back to the central tile in order to advance research (and draw a research card)</li>
    </ul>
</ul>

<h3>Tiles</h3>

**Plain**, can be built on and can contain up to two forest cube. Produce 1 food.

**River**, can be built on and can contain up to two forest cube. Produce 1 water.

**Hills**, can be built on and can contain up to two forest cube. Produce 1 brick.

**Lac**, cannot be built on and crossed (except by Nausacii). A cube which whould be put onto the lac goes through to the next tile in the wind direction.

**Mountain**, can be built on, can contain up to four cubes but the cost for moving onto the tile is 2 actions (except for Nausacii). Produce 1 quartz.

<h3>People</h3>

Up to 6 persone can play the game at the same time, I'm not sure right now how to handle turns in order to make all peope active at the same time.
Either ressource management which you gain at the end of your turn or another thing.

**Downwinders**, can move against the wind for free one time each turn.

**???**, can predict the next wind direction.

<h3>Irritation</h3>

It's a ladder going from 0 to 10 with level 2, 4, 6, 7, 8, 9 being special level where player must draw an irritation card.

The game is lost if it reaches 10.

<h3>Cards</h3>

<table>
    <tr>
        <td>
            5x
        </td>
        <td>
            5x
        </td>
        <td>
            5x
        </td>
    </tr>
</table>

<h3>Loosing</h3>

If the number of forest tile is 19 on the board at the end of a turn.

If the forest wrath become 10 or more (it destroys everything).

If the central city is destroyed by becoming a forest tile.

<h3>Winning</h3>

Having completed 6 search.