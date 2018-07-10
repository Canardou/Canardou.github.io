---
layout: post
title:  "Nausacii"
date: 2017-12-09
lang: eng
---
<h2>Nausacii</h2>

Since 2015, I have made a lot of trial and error into making a boardgame around the theme of hexes and nausicaa.
This post summarize all the iteration until I came up with a working javascript prototype and more.

<h3>First iteration</h3>

> Back in 2015...

The game require a lot of components and revolves around different mechanics and it is competitive.

As for the tokens, players have 4 outpost (img), 4 towns (img), 4 cities (img) and 4 scouts. At the start of the game a player would have 2 scouts and 2 outposts.

At the start each player would draw 7 research cards, and a draft would occure (take one, give the remaining to the left) until each player would have 7 research cards. Research cards would give advantages when researched (permanent, added to deck or immediate).

Then for the second part of the game, each player would draw a hex tile from a pool which depend of the number of player (7 cards per player : 2 plains, 2 forest, 2 river and 1 swamp).
- **Plain** : <br>produce food, then wood, then gold (max 4 tokens on it, provides 1 more victory point)
- **Forest** : <br>produce wood, then rock, then gold (max 4 tokens on it, provides 1 more defense point)
- **Mountain** : <br>produce rock, then food, then gold (max 4 tokens on it, cost 1 more move to come into)
- **Swamp** : <br>produce nothing, then gold, then gold (max 3 tokens on it)

Player must place the drawn tile adjacente to two already placed tiles. When placing a tile a player could add a scout and an outpost (Mandatory on the two last placed tiles if none have been placed before).

On hexes two ressources are present. Outpost produce the first ressource, then town the second, then city always gold (This would result by adding a ressource card in the deck). Gold can replace any ressource.
Scout has a card in the deck which allows to produce the first ressource at the position of any stading pawn (then the scout is flipped until the next turn)

In a second part, each player would draw cards from his deck, which would allow him to do certain actions. the research action would always be possible (3 same ressources)

<h5>Example of cards :</h5>
**Meeple** (1 Force)
- Produce a ressource at the position of a standing pawn
- Move a meeple
- Transform into an outpost (1 wood)

**Outpost** (1 Force)
- Recruit a meeple (1 food)
- Improve in town (1 rock, 1 wood)

**Town** (2 Force)
- Recruit a meeple (1 food)
- Improve in city (2 rock, 1 wood)

**City** (3 Force)
- Recruit a meeple (1 food)

The deck was dependent of the current state of the game. If you loose a town, you'll need to remove the town and the two ressources cards from your deck.
At the end of his turn, the player would resolve any conflict occured, each player could play one card from his deck to improve their forces.

The way to win was to build 4 cities, or control more than 7 tiles at the end of its turn, or having reached the max research level.

The game was then flavored with differents race and their corresponding powers.

<h4>Flaws</h4>

The start was not a problem, it was interesting to create the map and deciding to place the meeple and outpost.
It was hard to choose research cards, and they would not really change the way you would play.

The game was slow and clunky. The way the game was running with adding and removing cards from your deck was cumbersome.
Combat, an important part of the game, was not well handled and I couldn't figure a way to handle it well.

When playtested, the game showed that you cannot really forsee what makes you win or loose.

Which leaded me to the second iteration of the game in which I kept hexes and buildings.

<h3>Second iteration</h3>

> Back in 2016...

I went from a competitive game to a cooperative one. I changed almost everything.

The theme was changed to Nausicaa. The game was played on a randomly created map of hexes (img) and the goal was to prevent mushrooms overtaking all the tiles. There was random wind each turn thanks to the tool (img) and passive power of races were dependant of the wind direction.

Production was done by drawing cards from decks.

The game slowly revealed itself and was not palyable until...

<h3>Third iteration</h3>

> Back in 2017, first playstests...
> You are the last survivors of earth, besieged by a mushroom forest that you don't understand and kills and destroy everything.

The goal of the game is to search for clues all around the map, by making expedition into the growing forest tiles while slowing the progress of the forest without annoying it too much.

Players and Nausacii start in the center of an hexe map of 4 tiles of radius.

Loosing can come from having too many tiles in turned into mushrooms at the same time, loosing the central tile or annoying the forest too much.

<h3>Actions</h3>

Each player has initially 1 water/turn thanks to the central tile.
Each player start with a pawn. If at a moment of the game a player has no pawn, a new one can be produced at the center tile instead of having a water this turn.

<ul>
    <li>2 food : Recruit a pawn</li>
    <li>1 water : Move a pawn</li>
    <ul>
        <li>If it ends up in a forest tile, without Nausacii on the same tile or an adjacent outpost, it is lost</li>
    </ul>
    <li>1 food : Clean a cube at a pawn position</li>
    <li>1 food & 1 water : Clean a mushroom tile at a pawn position, <em>increase forest irritation by one</em></li>
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

**Lac**, cannot be built on and crossed (except by Nausacii). A mushroom cube which whould be put onto the lac goes through to the next tile in the wind direction.

**Mountain**, can be built on, can contain up to four cubes but the cost for moving onto the tile is 2 actions (except for Nausacii). Produce 1 quartz.

<h3>People</h3>

Up to 6 players can play the game at the same time.

<h5>Example of some people</h5>

**Downwinders**, can move against the wind for free one time each turn.

**Meteorologists**, can predict the next wind direction.

**Warriors**, can use 2 food to clean any mushroom tile on the map.

<h3>Annoying</h3>

It's a ladder going from 0 to 10 with level 2, 4, 6, 7, 8, 9 being special level where player must draw an event card.

<h3>Loosing</h3>

If the number of forest tile is 19 on the board at the end of a turn.

If the forest wrath become 10 or more (it destroys everything).

If the central city is destroyed by becoming a forest tile.

<h3>Winning</h3>

Having completed 6 search.

<h3>Playstests</h3>

A physical board was made and three game were played. The game was shown to be a bit boring and repetitive and the mushrooms were not much of a threat.

Accordingly to these playtests, I made a working prototype in Javascript (with a lot of change in rules) in order to test much more gamedesign ideas. The final prototype game can be played below. At this time I'm no more interested in improving the game and I'm quite happy with the result.

<h2>Javascript Prototype and last iteration</h2>

<button id="new" onclick="startGame();">New game</button><input type="range" style="width:50px" id="number_of_players" value="4" min="1" max="6" oninput="number_of_players_out.value = number_of_players.value"><output id="number_of_players_out">4</output> players
<select id="difficulty">
<option value="easy">Facile</option>
<option value="normal" selected>Normal</option>
<option value="hard">Difficile</option>
<option value="epic">Epique</option>
  </select><button id="next_turn" onclick="nextTurn();" style="position:absolute;left:900px;top:15px"><h3>Tour suivant</h3></button><br><br>
<canvas id="board"  width="500" height="500" style="border:1px solid black;"></canvas><br>
Se deplacer (1 <img src="../images/nausacii/water.png" width="15px">, 2 <img src="../images/nausacii/water.png" width="10px"> pour montagne)<br>
<button id="treat_cube" onclick="treat(false)">Traiter spore</button>(1 <img src="../images/nausacii/seed.png" width="12px">)<br>
<button id="treat_tile" onclick="treat(true)">Traiter champignons</button>(2 <img src="../images/nausacii/seed.png" width="12px">, +1 <img src="../images/nausacii/chitine.png" width="15px">)<br>
<button id="build_wall" onclick="build('wall')">Construire 2 murs</button>(1 <img src="../images/nausacii/rock.png" width="15px">)<br>
<button id="build_town" onclick="build('town')">Construire ville</button>(2 <img src="../images/nausacii/rock.png" width="15px">)<br>
<button id="move_nausacii" onclick="build('nausacii')">Deplacer nausacii 2 fois</button>(1 <img src="../images/nausacii/water.png" width="10px"> montagne/lac)<br>
<button id="produce" onclick="build('produce')">Production forcée</button>(+1 <img src="../images/nausacii/chitine.png" width="15px">)<br>
<span id="current_action_show"></span><br>
<div style="position:absolute;top:30px;left:520px;border:1px solid black">
	Weather <span id="weather_count"></span>
	<div id="weather_content">
	</div>
</div>
<div style="position:absolute;top:100px;left:520px;border:1px solid black">
	Upset <span id="upset_count"></span>
	<div id="upset">
	</div>
	<div id="upset_content">
	</div>
</div>

<div style="position:absolute;top:200px;left:520px;border:1px solid black" id="players">
	
</div>

<div style="position:absolute;top:5px;left:400px;border:1px solid black" id="tuiles_count">
	
</div>

<div style="position:absolute;top:30px;left:400px;border:1px solid black" id="research">
	
</div>


<div style="position:absolute;top:570px;left:450px" id="production">
	
</div>

<div style="position:absolute;top:570px;left:300px" id="directions">
	<button style="position:absolute; left:50px;" id="n" onclick="action('n')">↑</button>
	<button style="position:absolute; top:35px;" id="ne" onclick="action('nw')">↖</button>
	<button style="position:absolute; top:70px;" id="se" onclick="action('sw')">↙</button>
	<button style="position:absolute; top:35px;left:100px;" id="nw" onclick="action('ne')">↗</button>
	<button style="position:absolute; top:70px;left:100px;" id="sw" onclick="action('se')">↘</button>
	<button style="position:absolute; top:100px; left:50px;" id="s" onclick="action('s')">↓</button>
	<button style="position:absolute; top:50px; left:50px;" id="cancel" onclick="action('cancel')">X</button>
</div>

<textarea id="log" rows="20" cols="57" style="position:absolute;top:0px;left:1150px" ></textarea>
<h3>Regles</h3>
<ul>
	<li>Rester sur une case fungi a la fin du tour : +1 <img src="../images/nausacii/chitine.png" width="15px">, perds le jeton recherche sur la tuile si détenu (une seule des deux ressources produites)</li>
	
	<li>Nausacii permet de rester sur une case fungi sans enerver ou perdre le jeton recherche</li>
	
	<li>Nausacii permet de traiter une tuile sans malus de <img src="../images/nausacii/chitine.png" width="15px"></li>
	
	<li>Nausacii et la citadelle (sauf si pouvoirs bloqués) bloquent tous les spores sur leur case, la citadelle ne produit pas mais ne compte pas pour la limite de villes de l'architecte</li>
	
	<li>Nausacii peut aller sur les lacs et pour le même prix dans la montagne</li>
	
	<li>Les montagnes peuvent contenir une spore de plus, mais sont inconstructibles et nécessitent 2 <img src="../images/nausacii/water.png" width="15px"> pour aller dessus (sauf déplacement gratuit)</li>
	
	<li>Facile & Normal : Pas de mycélium</li>
	
	<li>Normal : Cartes météo contiennent enervement de la forêt</li>
	
	<li>Difficile : Mycélium au centre + case champignon, cité placée aléatoirement dans l'anneau extérieur</li>
	
	<li>Epique : mycélium fait apparaitre une spore supplémentaire dans la direction de son déplacement + 2 spores max sur la cité</li>
</ul>
<h3>Victoire</h3>
<ul>
	<li>Aller sur une des tuile contenant <img src="../images/nausacii/search.png" width="15px"> accompagné de nausacii</li>
	
	<li>La tuile ne doit pas être champignons, à la fin du tour le joueur gagne 1 <img src="../images/nausacii/search.png" width="15px">, un joueur ne peut transporter qu'un seul <img src="../images/nausacii/search.png" width="15px"></li>
	
	<li>Il doit ramener ce <img src="../images/nausacii/search.png" width="15px"> à la cité</li>
	
	<li>Une fois son tour terminé dans la cité, augmente la recherche de 1</li>
	
	<li>Si 5 <img src="../images/nausacii/search.png" width="15px"> on été ramenée : Victoire ! </li>
</ul>
<h3>Defaite</h3>
<ul>
	<li>La cité devient champignons</li>
	
	<li>Le nombre de case non champignons est toujours en dessous du min à la fin d'un tour</li>
	
	<li>Le <img src="../images/nausacii/chitine.png" width="15px"> atteint la valeur de 15</li>
</ul>
<script>
function log(string){
	document.getElementById("log").innerHTML += string + "\n";
	document.getElementById("log").scrollTop = document.getElementById("log").scrollHeight;
}

var canvas = document.getElementById("board");
var ctx = canvas.getContext("2d");

var terrains = {"river" : 4, "forest" : 8, "plain" : 8, "hill" : 8, "mountain" : 6, "lac" : 2};

var rules = {"river" : {produce:["water","water"],maxSpores:2,constructible:true,walkable:true,cost:1}, 
				"forest" : {produce:["seed","seed"],maxSpores:2,constructible:true,walkable:true,cost:1}, 
				"plain" : {produce:["water","seed"],maxSpores:2,constructible:true,walkable:true,cost:1}, 
				"hill" : {produce:["seed","rock"],maxSpores:2,constructible:true,walkable:true,cost:1}, 
				"mountain" : {produce:["water","rock"],maxSpores:3,constructible:false,walkable:true,cost:2}, 
				"lac" : {produce:[],maxSpores:-1,constructible:false,walkable:false},
				"city" : {produce:[],maxSpores:3,constructible:false,walkable:true,cost:1},
				"fungi" : {produce:[],maxSpores:0,constructible:false,walkable:true,cost:1},
				"fungi_hidden" : {produce:[],maxSpores:0,constructible:false,walkable:false}};
				
var rulesForNumberPlayer =[
		{ walls:12, towns:2, seed:1, rock:2, water:1},
		{ walls:12, towns:2, seed:1, rock:2, water:1},
		{ walls:12, towns:2, seed:1, rock:2, water:1},
		{ walls:12, towns:2, seed:1, rock:2, water:1},
		{ walls:12, towns:2, seed:1, rock:2, water:1},
		{ walls:12, towns:2, seed:1, rock:2, water:1}
	];
	
var rules_difficulty = {
	easy:6,
	normal:6,
	hard:6,
	epic:6
}

var weather_cards_easy = [
	{id:1,title:"Vent",text:"Vent du nord + Production Plaine", produce:"plain", effect:"n", upset:false},
	{id:2,title:"Vent",text:"Vent du sud + Production Colline", produce:"hill", effect:"s", upset:false},
	{id:3,title:"Vent",text:"Vent du nord-est", produce:"nothing", effect:"ne", upset:false},
	{id:4,title:"Vent",text:"Vent du sud-est", produce:"nothing", effect:"se", upset:false},
	{id:5,title:"Vent",text:"Vent du nord-ouest", produce:"nothing", effect:"nw", upset:false},
	{id:6,title:"Vent",text:"Vent du sud-ouest", produce:"nothing", effect:"sw", upset:false},
	{id:7,title:"Production",text:"Production Plaine", produce:"plain", effect:"n", upset:false},
	{id:8,title:"Production",text:"Production Colline", produce:"hill", effect:"s", upset:false},
	{id:9,title:"Production",text:"Production Forêt", produce:"forest", effect:"ne", upset:false},
	{id:10,title:"Production",text:"Production Rivière", produce:"river", effect:"se", upset:false},
	{id:9,title:"Production",text:"Production Forêt", produce:"forest", effect:"nw", upset:false},
	{id:10,title:"Production",text:"Production Rivière", produce:"river", effect:"sw", upset:false},
	//{id:7,title:"Calme",text:"Rien", produce:"nothing", effect:"n", upset:false},
	//{id:8,title:"Calme",text:"Rien", produce:"nothing", effect:"s", upset:false},
	//{title:"Tempete",text:"Augmente l'enervement dela foret", effect:"upset"}
]

				
var weather_cards_normal = [
	{id:1,title:"Vent",text:"Vent du nord + Production Plaine", produce:"plain", effect:"n", upset:false},
	{id:2,title:"Vent",text:"Vent du sud + Production Colline", produce:"hill", effect:"s", upset:false},
	{id:3,title:"Vent",text:"Vent du nord-est", produce:"nothing", effect:"ne", upset:false},
	{id:4,title:"Vent",text:"Vent du sud-est", produce:"nothing", effect:"se", upset:false},
	{id:5,title:"Vent",text:"Vent du nord-ouest", produce:"nothing", effect:"nw", upset:false},
	{id:6,title:"Vent",text:"Vent du sud-ouest", produce:"nothing", effect:"sw", upset:false},
	{id:7,title:"Production",text:"Production Plaine", produce:"plain", effect:"n", upset:false},
	{id:8,title:"Production",text:"Production Colline", produce:"hill", effect:"s", upset:false},
	{id:9,title:"Production",text:"Production Forêt", produce:"forest", effect:"ne", upset:false},
	{id:10,title:"Production",text:"Production Rivière", produce:"river", effect:"se", upset:false},
	{id:9,title:"Tempete",text:"Enervement forêt + Production Forêt", produce:"forest", effect:"nw", upset:true},
	{id:10,title:"Tempete",text:"Enervement forêt + Production Rivière", produce:"river", effect:"sw", upset:true},
	//{id:7,title:"Tempete",text:"Enervement foret", produce:"nothing", effect:"n", upset:true},
	//{id:8,title:"Tempete",text:"Enervement foret", produce:"nothing", effect:"s", upset:true},
	//{title:"Tempete",text:"Augmente l'enervement dela foret", effect:"upset"}
]


var peuples = [
	{id:0,nom:"Architecte",
	actif:"4 <img src='../images/nausacii/rock.png' width='15px'> Construire/Déplacer la citadelle",
	passif:"Les villes permettent aux tuiles de contenir une spore de plus"},
	{id:1,nom:"Sourcier",
	actif:"3 <img src='../images/nausacii/water.png' width='15px'> Déplacer un pion joueur n'importe où",
	passif:"Au lieu du mouvement gratuit, +1 <img src='../images/nausacii/water.png' width='15px'>/tour et déplacement sur la montagne côute 1"},
	{id:2,nom:"Météorologiste",
	actif:"3 <img src='../images/nausacii/water.png' width='15px'> Pas d'effet météo prochain tour",
	passif:"Lorsque tir le prochain effet du vent, lance deux dés"},
	{id:3,nom:"Explorateur",
	actif:"3 <img src='../images/nausacii/seed.png' width='15px'> Faire reculer l'enervement de 1",
	passif:"Peut rester sur les champignons et produire les deux ressources"},
	{id:4,nom:"Exterminateur",
	actif:"3 <img src='../images/nausacii/seed.png' width='15px'> Traiter une tuile champignons au choix sur la carte (+1 <img src='../images/nausacii/chitine.png' width='15px'>)",
	passif:"Traite tous les spores d'une tuile quand effectue l'action traiter"},
	{id:5,nom:"Marchand",
	actif:"Peut échanger 3 ressources identiques contre 2 au choix",
	passif:"Peut traverser le lac"},
	/*{id:6,nom:"Ingénieur",
	actif:"Construire une route entre deux tuiles (déplacement gratuit, coûte une route)",
	passif:"Peut avoir jusqu'à 8 graines et eau"},
	{id:7,nom:"Chercheur",
	actif:"Peut utiliser 2 chitines pour une action coûtant 1 eau ou 1 graine, peut utiliser 6 chitines pour une action coûtant 2 eaux, 2 graines ou 1 pierre",
	passif:"Lorsque traite une spore, gagne 1 chitine et 6 chitine max"}*/
]

var upsetting_cards = [
	//Tuiles
	{title:"Souche aquatique",text:"Une spore sur chaque riviere", effect:"river"},
	{title:"Proliferation",text:"Une spore sur chaque foret collee au champignon", effect:"forest"},
	{title:"Concentration urbaine",text:"Une spore sur chaque plaine avec une ville", effect:"plain"},
	{title:"Concentration urbaine",text:"Une spore sur chaque colline avec une ville", effect:"hill"},
	{title:"Souche d'altitude",text:"Une spore sur chaque montagne en ayant deja au moins une", effect:"mountain"},
	//Autres
	{title:"Tremblement de terre",text:"Détruire tous les murs", effect:"walls"},
	{title:"Mise en quarantaine",text:"Detruire deux villes au choix", effect:"town"},
	{title:"Rafales",text:"Tirez deux cartes meteo la prochaine fois", effect:"weather"},
	{title:"Secheresse",text:"Chaque joueur defausse tout son eau", effect:"water"},
	{title:"Silos infectés",text:"Chaque joueur defausse la totalité de ses graines", effect:"seed"},
	{title:"Blessure",text:"Nausacii ne se déplace que d'une tuile pendant 6 tours", effect:"nausacii"},
	{title:"Fatigue",text:"Les pouvoirs actifs ne peuvent plus être utilisés pendant 6 tours", effect:"power"}
]

var search_indexes_base = [4,4,3,3,2,2];
var search_positions = [{x:0,y:-3},{x:1,y:-3},{x:2,y:-3},{x:3,y:-3},{x:3,y:-2},{x:3,y:-1},{x:3,y:0},{x:2,y:1},{x:1,y:2},
						{x:0,y:3},{x:-1,y:3},{x:-2,y:3},{x:-3,y:3},{x:-3,y:2},{x:-3,y:1},{x:-3,y:0},{x:-2,y:-1},{x:-1,y:-2}];

var direction_array = ["se","s","sw","nw","n","ne"];
var hex_directions = {
			s:{x:0, y:1},
			n:{x:0, y:-1},
			sw:{x:-1, y:1},
			nw:{x:-1, y:0}, 
			se:{x:1, y:0}, 
			ne:{x:1, y:-1}
	};

function moveCoord(coord,dir){
	return {x:coord.x+hex_directions[dir].x,y:coord.y+hex_directions[dir].y};
}
	
function pickRandomWind() {
    var result;
    var count = 0;
    for (var prop in hex_directions)
        if (Math.random() < 1/++count)
           result = prop;
    return result;
}
	
function hexToPixels(coord){
	return {x:250+coord.x*60,y:250+coord.y*70+coord.x*35};
}

function pixelsToHex(coord){
	var x = coord.x-250;
	var y = coord.y-250;
	return {x:Math.round(x * 2/3 / 40),y:Math.round((-x / 3 + Math.sqrt(3)/3 * y) / 40)};
}

class Player{
	constructor(id, towns, peuple){
		this.position = city;
		this.buildings = [];
		this.seed = rulesForNumberPlayer[numberPlayers-1].seed;
		this.rock = rulesForNumberPlayer[numberPlayers-1].rock;
		this.chitine = 0;
		this.water = rulesForNumberPlayer[numberPlayers-1].water;
		this.id = id;
		this.free_move = true;
		
		this.maxBuildings = towns;
		this.search = false;
		this.peuple = peuple;
		if(peuple.id == 1){
			this.free_move = false;
		}
	}
	
	show(current){
		var result = "<div style='" + ((this.id == current)?"border:2px solid red":"border:1px solid black") + "'>" + this.peuple.nom + " " + '<img src="../images/nausacii/pion_'+this.id+'.png" width="15px"><br>'
		result += 'Passif: ' + this.peuple.passif + '<br>';
		result += 'Actif : ' + this.peuple.actif + ' ';
		if(this.peuple.id == 0){
			result += "<button id='build_citadel' onclick='build(\"citadel\")'>Construire/Déplacer</button>";
		}
		if(this.peuple.id == 1){
			for(var k in players){
				result += "<button id='move_"+k+"' onclick='moveGlobal("+k+")'><img src='../images/nausacii/pion_"+players[k].id+".png' height='15px'></button>";
			}
			//result += "<button id='move_7' onclick='moveGlobal(7)'><img src='pion_nausicaa.png' height='15px'></button>";
		}
		if(this.peuple.id == 2){
			result += "<button id='shuffle_deck' onclick='dontDraw()'>Ne pas tirer</button>";
		}
		if(this.peuple.id == 3){
			result += "<button id='reduce_upset' onclick='reduceUpset()'>Reduire upset</button>";
		}
		if(this.peuple.id == 4){
			result += "<button id='treat_select' onclick='treatSelected()'>Traiter tuile au choix</button>";
		}
		if(this.peuple.id == 5){
			result += "<button id='exchange_seed' onclick='exchange(\"water\")'><img src='../images/nausacii/water.png' width='15px'></button>";
			result += "<button id='exchange_seed' onclick='exchange(\"seed\")'><img src='../images/nausacii/seed.png' height='15px'></button>";
			result += "<button id='exchange_rock' onclick='exchange(\"rock\")'><img src='../images/nausacii/rock.png' height='15px'></button>";
		}
		result += '<br>';
		result += this.water + '/6 <img src="../images/nausacii/water.png" width="15px"> - '
		result += this.seed + '/6 <img src="../images/nausacii/seed.png" width="15px"> - '
		result += this.rock + '/4 <img src="../images/nausacii/rock.png" width="15px"> - '
		result += this.buildings.length + "/" + this.maxBuildings + ' <img src="../images/nausacii/building_'+this.id+'.png" width="15px"> '
		result += (this.search?"1":"0") + '/1 <img src="../images/nausacii/search.png" width="15px">';
		if(this.peuple.id != 1)
			result += ' dplct gratuit : ' + (this.free_move?"1":"0") + '/1';
		result += "</div>";
		return result;
	}
}

class hexTile{
	constructor(x, y){
		this.x = x;
		this.y = y;
		this.type = "blank";
		this.fungi = false;
		this.currentSpores = 0;
		this.maxSpores = 0;
		this.pawns = [];
		this.buildings = [];
		this.built = false;
	}
	
	draw(ctx){
		var coord = hexToPixels(this);
		switch(this.type){
			case "river":
				ctx.fillStyle = "DarkTurquoise";
				break;
			case "forest":
				ctx.fillStyle = "DarkSeaGreen";
				break;
			case "plain":
				ctx.fillStyle = "Wheat";
				break;
			case "hill":
				ctx.fillStyle = "LightCoral";
				break;
			case "mountain":
				ctx.fillStyle = "SlateGray";
				break;
			case "city":
				ctx.fillStyle = "LightBlue";
				break;
			case "lac":
				ctx.fillStyle = "Blue";
				break;
			default:
				ctx.fillStyle = "Gray";
				break;
		}
		if(board.distance_hex(this.coord(), mouseCoord) == 0){
			ctx.lineWidth=2;
			ctx.strokeStyle = "red";
		}
		else{
			ctx.lineWidth=1;
			ctx.strokeStyle = "black";
		}
		ctx.translate(coord.x,coord.y);
		ctx.translate(40,0);
		ctx.rotate(60*Math.PI/180);
		ctx.beginPath();
		ctx.moveTo(0,0);
		for(var i=0; i<6; i++){
			ctx.rotate(60*Math.PI/180);
			ctx.lineTo(40,0);
			ctx.translate(40,0);
		}
		ctx.fill();
		ctx.stroke();
		//Draw walls
		if(this.fungi){
			ctx.globalAlpha = 0.5;
			ctx.fillStyle = "Purple";
			ctx.fill();
		}
		ctx.globalAlpha = 1.0;
		this.drawWalls();
		//
		ctx.rotate(-60*Math.PI/180);
		ctx.translate(-60,-35);
		
		ctx.globalAlpha = 0.5;
		if(this.type == "mountain"){
			ctx.drawImage(imagesArray.mountain,-5,15,30,30)
		}
		ctx.fillStyle = "Black";
		ctx.font = "8px Arial";
		ctx.fillText(this.x + ":" + this.y,18,67);
		ctx.globalAlpha = 1.0;
		//0,0 to 40,70
		if(this.fungi == false){
			this.drawSpores(ctx, this.maxSpores, this.currentSpores);
		}
		this.drawProduce(ctx);
		ctx.globalAlpha = 1.0;
		this.drawOthers(ctx);
		ctx.setTransform(1, 0, 0, 1, 0, 0);
	}
	
	drawWalls(){
		for(var i=0; i<6; i++){
			if(walls[getWallKey(this,moveCoord(this, direction_array[i]))]){
				ctx.beginPath();
			}
			ctx.moveTo(0,0);
			ctx.rotate(60*Math.PI/180);
			if(walls[getWallKey(this,moveCoord(this, direction_array[i]))]){
				ctx.lineTo(40,0);
				ctx.lineWidth=5;
				ctx.strokeStyle = "black";
				ctx.stroke();
				ctx.lineWidth=2;
				ctx.strokeStyle = "LightBlue";
				ctx.stroke();
			}
			ctx.translate(40,0);
		}
		ctx.lineWidth=1;
	}
	
	drawSpores(ctx, max, current){
		ctx.lineWidth=1;
		ctx.strokeStyle = "black";
		ctx.fillStyle = "purple";
		ctx.globalAlpha = 0.35;
		for(var i = 0; i < max; i++){
			ctx.fillRect(25+i*12-max*5,50,8,8);
			ctx.strokeRect(25+i*12-max*5,50,8,8);
		}
		ctx.globalAlpha = 1.0;
		for(var i = 0; i < current; i++){
			ctx.drawImage(imagesArray.spore,24+i*12-max*5,49,10,10)
		}
	}
	
	drawProduce(ctx){
		for(var i = 0; i < rules[this.type].produce.length; i++){
			drawImageProp(ctx, imagesArray[rules[this.type].produce[i]], 0.15, 10+i*12, 5);
		}
	}
	
	drawOthers(ctx){
		for(var i = 0; i < players.length; i++){
			if(this.equal(players[i].position)){
				if(i<3)
					drawImageProp(ctx, imagesArray["pion_"+i], 0.15, 28+i%3*6, 14);
				else
					drawImageProp(ctx, imagesArray["pion_"+i], 0.15, 28+i%3*6+3, 19);
			}
			for(var k in players[i].buildings){
				if(this.equal(players[i].buildings[k]))
					drawImageProp(ctx, imagesArray["building_"+i], 0.1, -7, 22);
			}
			if(this.equal(city)){
				drawImageProp(ctx, imagesArray["building_citadel"], 0.1, -7, 22);
				drawImageProp(ctx, imagesArray["building_citadel"], 0.07, -12, 28);
				drawImageProp(ctx, imagesArray["building_citadel"], 0.05, -2, 32);
			}
			if(this.equal(citadel) && power_stuck == 0){
				drawImageProp(ctx, imagesArray["building_citadel"], 0.1, -7, 22);
			}
		}
		if(mycelium && this.equal(mycelium)){
			drawImageProp(ctx, imagesArray["fungi"], 0.15, 10, 17);
		}
		if(this.equal(nausacii)){
			drawImageProp(ctx, imagesArray["pion_nausacii"], 0.15, 15, 19);
		}
		var count_search = 0;
		for(var i in searchs){
			if(this.equal(searchs[i])){
				drawImageProp(ctx, imagesArray["search_token"], 0.22, -7+count_search*3, 45);
				count_search++;
			}
		}
	}
	
	getNeighbor(direction){
		return {x:this.x+direction.x,y:this.y+direction.y}
	}
	
	coord(){
		return {x:this.x,y:this.y}
	}
	
	addSporeWithoutDir(){
		if(!this.equal(nausacii) && !(this.equal(citadel) && power_stuck == 0) && !this.fungi){
			if(this.currentSpores < this.maxSpores){
				this.currentSpores++;
			}
			else if(this.currentSpores >= this.maxSpores){
				if(this.type == "city"){
					lost = true;
					log("PERDU : Cite champignons !");
				}
				this.fungi = true;
				this.maxSpores = rules[this.type].maxSpores;
				this.built = false;
				if(this.equal(citadel)){
					citadel = {x:Infinity,y:Infinity};
				}
				for(var i = 0; i < players.length; i++){
					for(var k in players[i].buildings){
						if(this.equal(players[i].buildings[k])){
							players[i].buildings.splice(k, 1);
							break;
						}
					}
				}
				for(var i = 0; i < 6; i++){
					var dir = hex_directions[direction_array[i]];
					var other = board.get(this.getNeighbor(dir));
					var key = getWallKey(this,other);
					if(other.fungi && walls[key]){
						walls_count--;
						walls[key] = false;
					}
				}
			}
		}
	}
	
	addSpore(direction){
		if(!this.fungi && !this.equal(nausacii)){
			if(this.maxSpores>0){
				this.addSporeWithoutDir();
			}
			else{
				var hex = board.get(this.getNeighbor(direction));
				if(hex && !hex.equal(nausacii) && !(hex.equal(citadel) && power_stuck ==0)){
					var key = getWallKey(this,this.getNeighbor(direction));
					if(walls[key]){
						walls_count--;
						walls[key] = false;
					}
					else {
						var hex = board.get(this.getNeighbor(direction));
						if(hex)
							hex.addSpore(direction);
					}
				}
			}
		}
	}
	
	equal(other){
		return this.x == other.x && this.y == other.y;
	}
}

function drawImageProp(ctx, image, prop, x, y){
	var width = image.width;
	var height = image.height;
	ctx.drawImage(image,x,y,width*prop,height*prop);
}

class hexMap{
	constructor(radius){
		this.hexes_table = [[]];
		this.hexes = [];
		
		for(var y=-radius; y<=radius; y++){
			for(var x=-radius; x<=radius; x++){
				if(this.distance_hex({x:x,y:y},{x:0,y:0})<=radius){
					this.hexes_table[x + ":" + y] = new hexTile(x,y);
					this.hexes.push(this.hexes_table[x + ":" + y]);
				}
			}
		}
	}
	
	countNotFungi(){
		var result = 0;
		for(var i in this.hexes){
			if(!this.hexes[i].fungi && this.distance_hex(this.hexes[i],{x:0,y:0})<=3){
				result++;
			}
		}
		return result;
	}
	
	get(coord){
		return this.hexes_table[coord.x + ":" + coord.y];
	}
	
	isCorner(coord){
		for(var k in hex_directions){
			var tmp = {x:hex_directions[k].x*3,y:hex_directions[k].y*3};
			if(this.distance_hex(tmp,coord) == 0){
				return true;
			}
		}
		return false;
	}
	
	isFungiCorner(coord){
		for(var k in hex_directions){
			var tmp = {x:hex_directions[k].x*4,y:hex_directions[k].y*4};
			if(this.distance_hex(tmp,coord) == 0){
				return true;
			}
		}
		return false;
	}
	
	loadDeck(deck){
		for(var i in this.hexes){
			if(this.hexes[i].type == "blank"){
				var type = deck.splice(Math.floor(Math.random()*deck.length), 1)[0];
				if(mycelium && this.hexes[i].equal(mycelium)){
					do{
						if(type == "lac"){
							deck.push(type);
							type = deck.splice(Math.floor(Math.random()*deck.length), 1)[0];
						}
						else {
							this.hexes[i].type = type;
							this.hexes[i].maxSpores = rules[this.hexes[i].type].maxSpores;
							break;
						}
					}while(true);
				}
				else {
					this.hexes[i].type = type;
					this.hexes[i].maxSpores = rules[this.hexes[i].type].maxSpores;
				}
			}
		}
		//We don't want lac at the border
		var result = [];
		for(var k in this.hexes){
			var hex = this.hexes[k];
			var tmp = {x:hex.x,y:hex.y};
			//var tmp = {x:hex_directions[k].x*3,y:hex_directions[k].y*3};
			
			if(hex.type == "lac" && this.distance_hex(hex,{x:0,y:0}) == 3){
				//try to swap with random non city and non-lac tile
				do{
				var tile = this.hexes[Math.floor(this.hexes.length*Math.random())];
				if(tile.type == "city" || tile.type == "lac")
					continue;
				if(mycelium && tile.equal(mycelium))
					continue;
				if(this.distance_hex({x:0,y:0},tile) > 2)
					continue;
				//console.log("swap " + tile.x + ":" + tile.y + " and " + tmp.x + ":" + tmp.y);
				this.hexes_table[tile.x + ":" + tile.y] = this.get(tmp);
				this.hexes_table[tmp.x + ":" + tmp.y] = tile;
				
				this.hexes_table[tile.x + ":" + tile.y].x = tile.x;
				this.hexes_table[tile.x + ":" + tile.y].y = tile.y;
				
				this.hexes_table[tmp.x + ":" + tmp.y].x = tmp.x;
				this.hexes_table[tmp.x + ":" + tmp.y].y = tmp.y;
				
					break;
				}while(true);
			}
		}
		return result;
		
	}
	
	distance_hex(first,second){
		return (Math.abs(first.x-second.x)+Math.abs(first.x+first.y-second.x-second.y)+Math.abs(first.y-second.y))/2;
	}
	
	draw(ctx){
		for(var i in this.hexes){
			this.hexes[i].draw(ctx);
		}
		if(lost){
			ctx.fillStyle = "red";
			ctx.font = "50px Arial";
			ctx.textAlign = "center";
			ctx.fillText("PERDU!",250,250);
		}
		if(won){
			ctx.fillStyle = "green";
			ctx.font = "50px Arial";
			ctx.textAlign = "center";
			ctx.fillText("GAGNE!",250,250);
		}
	}
	
	setFungiDistance(radius){
		for(var i in this.hexes){
			if(this.distance_hex(this.hexes[i],{x:0,y:0})==radius){
				this.hexes[i].fungi = true;
				this.hexes[i].type = "fungi_hidden";
				this.hexes[i].maxSpores = -1;
			}
		}
	}
	
	getSearchs(){
		var result = [];
		/*for(var k in hex_directions){
			var tmp = {x:hex_directions[k].x*3,y:hex_directions[k].y*3};
			if(this.get(tmp).type != "lac"){
				result.push(tmp);
				
				//this.get(tmp).currentSpores = 1;
				//this.get(tmp).fungi = true;
			}
		}*/
		var search_indexes = createDeckFrom(search_indexes_base);
		//var current = Math.floor(search_positions.length*Math.random()); can't be easly done in real life
		var current = 0;
		result.push(search_positions[current]);
		board.get(search_positions[current]).fungi = true;
		for(var i = 0; i < 5; i++){
			var decalage = search_indexes.splice(Math.floor(Math.random()*search_indexes.length),1)[0];
			current = (current+decalage)%search_positions.length;
			result.push(search_positions[current]);
			board.get(search_positions[current]).fungi = true;
		}
		return result;
	}
	
	addMycelium(){
		mycelium = {x:0,y:0};
		do{
			var tile = this.hexes[Math.floor(this.hexes.length*Math.random())];
			var tmp = {x:tile.x,y:tile.y};
			if(tile.equal(mycelium))
				continue;
			if(board.distance_hex({x:0,y:0},tile) != 2)
				continue;
			//console.log("swap " + tile.x + ":" + tile.y + " and " + tmp.x + ":" + tmp.y);
			this.hexes_table[tile.x + ":" + tile.y] = this.get(mycelium);
			this.hexes_table[mycelium.x + ":" + mycelium.y] = tile;
			
			this.hexes_table[tile.x + ":" + tile.y].x = tile.x;
			this.hexes_table[tile.x + ":" + tile.y].y = tile.y;
			
			this.hexes_table[mycelium.x + ":" + mycelium.y].x = mycelium.x;
			this.hexes_table[mycelium.x + ":" + mycelium.y].y = mycelium.y;
			
			city = tmp;
			
			break;
		}while(true);
	}
	
	wind(direction){
		var before_fungi = [];
		for(var i in this.hexes){
			if(this.hexes[i].fungi)
				before_fungi.push(this.hexes[i]);
		}
		if(mycelium && current_difficulty == "epic"){
			before_fungi.push(this.get(board.get(mycelium)));
		}
		for(var i in before_fungi){
			if(before_fungi[i].fungi){
				var hex = this.get(before_fungi[i].getNeighbor(hex_directions[direction]));
				if(hex && !hex.equal(nausacii) && !(hex.equal(citadel) && power_stuck == 0)){
					var key = getWallKey(before_fungi[i].coord(),before_fungi[i].getNeighbor(hex_directions[direction]));
					if(walls[key]){
						walls_count--;
						walls[key] = false;
					}
					else {
						if(hex)
							hex.addSpore(hex_directions[direction]);
					}
				}
			}
		}
	}
}

function getMousePos(canvas, evt) {
	var rect = canvas.getBoundingClientRect();
	return {
	  x: evt.clientX - rect.left,
	  y: evt.clientY - rect.top
	};
}

var imagesArray = {
	building_0:"building_0.png",
	building_1:"building_1.png",
	building_2:"building_2.png",
	building_3:"building_3.png",
	building_4:"building_4.png",
	building_5:"building_5.png",
	pion_0:"pion_0.png",
	pion_1:"pion_1.png",
	pion_2:"pion_2.png",
	pion_3:"pion_3.png",
	pion_4:"pion_4.png",
	pion_5:"pion_5.png",
	building_neutral:"city.png",
	building_citadel:"citadel.png",
	pion_nausacii:"pion_nausicaa.png",
	fungi:"pion_fungi.png",
	water:"water.png",
	spore:"fungi.png",
	seed:"seed.png",
	rock:"rock.png",
	chitine:"chitine.png",
	mountain:"mountain.png",
	search_token:"search.png"
};
function imageHelper(array){
	for(var i in array){
		var tmp = new Image();
		tmp.src = "../images/nausacii/"+array[i];
		this[i] = tmp;
	}
	return this;
}
imagesArray = imageHelper(imagesArray);

function createDeckFrom(array){
	var result = [];
	for(var i in array){
		result.splice(Math.random()*result.length,0,array[i]);
	}
	return result;
}


/*var upsetting_cards = [
	//Tuiles
	{title:"Souche aquatique",text:"Une spore sur chaque riviere", effect:"river"},
	{title:"Proliferation",text:"Une spore sur chaque foret collee au champignon", effect:"forest"},
	{title:"Concentration urbaine",text:"Une spore sur chaque plaine avec une ville", effect:"plain"},
	{title:"Concentration urbaine",text:"Une spore sur chaque colline avec une ville", effect:"hill"},
	{title:"Souche d'altitude",text:"Une spore sur chaque montagne en ayant deja au moins une", effect:"mountain"},
	//Autres
	{title:"Echantillons dangereux",text:"Une spore sur chaque jeton recherche (tuile ou joueur)", effect:"search"},
	{title:"Mise en quarantaine",text:"Detruire une ville au choix", effect:"town"},
	{title:"Rafales",text:"Tirez deux cartes meteo la prochaine fois", effect:"weather"},
	{title:"Secheresse",text:"Chaque joueur defausse la moitié de son eau et peut immédiatement se déplacer", effect:"water"},
	{title:"Silos infectés",text:"Chaque joueur defausse la totalité de ses graines mais choisi une spore à enlever sur le plateau", effect:"seed"}
]*/

function increaseUpset(){
	upset++;
	if(upset_spots[0] == upset){
		upset_spots.splice(0,1);
		let card = upset_deck.splice(0,1)[0];
		log("Carte " + card.text + " tiree");
		document.getElementById("upset_content").innerHTML = "<b style='color:red'>" + card.title + "</b><br>" + card.text;
		upset_effect = card.effect;
		var tmp_effect = card.effect;
		for(var k in board.hexes){
			var hex = board.hexes[k];
			switch(tmp_effect){
				case "river":
					if(hex.type == "river")
						hex.addSporeWithoutDir();
					upset_effect = "";
					break;
				case "forest":
					if(hex.type == "forest"){
						for(var i = 0; i < 6; i++){
							var dir = hex_directions[direction_array[i]];
							var other = board.get(hex.getNeighbor(dir));
							if(other.fungi){
								hex.addSporeWithoutDir();
								break;
							}
						}
					}
					upset_effect = "";
					break;
				case "plain":
					if(hex.type == "plain" && hex.built)
						hex.addSporeWithoutDir();
					upset_effect = "";
					break;
				case "hill":
					if(hex.type == "hill" && hex.built)
						hex.addSporeWithoutDir();
					upset_effect = "";
					break;
				case "mountain":
					if(hex.type == "mountain" && hex.currentSpores>0)
						hex.addSporeWithoutDir();
					upset_effect = "";
					break;
			}
		}
		if(upset_effect == "search"){
			for(var k in searchs){
				board.get(searchs[k]).addSporeWithoutDir();
			}
			for(var k in players){
				if(players[k].search){
					board.get(players[k].position).addSporeWithoutDir();
				}
			}
			upset_effect = "";
		}
		if(upset_effect == "town"){
			var count_town = 0;
			for(var k in players){
				count_town += players[k].buildings.length;
			}
			if(count_town == 0)
				upset_effect = "";
			else
				custom_number = Math.min(count_town,2);
			log("Destroy " + custom_number + " towns");
		}
		if(upset_effect == "walls"){
			walls_count = 0;
			for(var k in walls){
				walls[k] = false;
			}
			upset_effect = "";
		}
		if(upset_effect == "nausacii"){
			nausacii_stuck = 6;
			upset_effect = "";
		}
		if(upset_effect == "weather"){
			weather_upset = true;
			upset_effect = "";
		}
		if(upset_effect == "power"){
			power_stuck = 6;
			upset_effect = "";
		}
		if(upset_effect == "water"){
			upset_effect = "";
			for(var k in players){
				players[k].water = 0;
			}
		}
		if(upset_effect == "seed"){
			upset_effect = "";
			for(var k in players){
				players[k].seed = 0;
			}
		}
	}
	refresh();
}

function reduceUpset(){
	if(current_player.peuple.id == 3 && current_player.seed >= 3 && upset > 0 && power_stuck == 0){
		current_player.seed-=3;
		log("Recule upset de 1")
		upset--;
		refresh();
	}
}

function showUpset(){
	let result = "<table><tr>";
	for(let i = 0; i <= upset_max; i++){
		result += "<td style='border:1px solid black;width:10px;text-align:center'>";
		if(i == upset)
			result += '<img src="../images/nausacii/chitine.png" width="15px">';
		else{
			if(upset_spots.includes(i)){
				result += "!";
			}
			else if (i == upset_max){
				result += "Perdu";
			}
			else
				result += i;
		}
		result += "</td>";
	}
	result += "</tr></table>";
	return result;
}


var walls_count;
var board;
var weather_deck;
var turn;
var mousePos;
var mouseCoord;
var upset;
var upset_deck;
var upset_spots;
var players;
var current_player_index;
var current_player;
var current_action;
var weather_card;
var nausacii;
var searchs;
var numberPlayers;
var upset_max;
var min_tiles;
var current_research;
var current_difficulty;
var upset_effect;
var custom_number;
var current_exchange;
var nausacii_stuck;
var power_stuck;
var weather_upset;
var remaining_walls;
var citadel;
var city;
var mycelium;
var nausacii_remaining;
var lost;
var won;
var current_weathers_cards;
var noDraw;
startGame();

function startGame(){
	won = false;
	lost = false;
	noDraw = false;
	nausacii_remaining = 0;
	citadel = {x:Infinity,y:Infinity};
	weather_upset = false;
	nausacii_stuck = 0;
	power_stuck = 0;
	current_exchange = 0;
	document.getElementById("weather_content").innerHTML = "";
	upset_effect = "";
	current_research = 0;
	walls_count=0;
	walls = {};
	document.getElementById("log").innerHTML = "";
	document.getElementById("upset_content").innerHTML = "";
	current_difficulty = document.getElementById("difficulty").value;
	turn = 1;
	log("---------------------------------------------");
	log("Tour " + turn);
	current_action = "move";
	current_player_index = 0;
	players =[];
	weather_card = undefined;
	numberPlayers = document.getElementById("number_of_players").value;
	upset = 0;
	upset_max = 15;
	upset_deck = createDeckFrom(upsetting_cards);
	current_weathers_cards = createDeckFrom(weather_cards_normal);
	
	board = new hexMap(4);
	var deck = []
		for(var k in terrains){
		for(var i = 0; i < terrains[k]; i++ ){
			deck.push(k);
		}
	}
	city = {x:0,y:0};
	if(current_difficulty != "easy" && current_difficulty != "normal"){
		board.addMycelium();
	}
	else{
		mycelium = false;
	}
	if(current_difficulty == "easy"){//25 rounds ~ 30 needed to gather 6 searchs
		board.get(city).maxSpores = 3;
		min_tiles = 15;
		upset_spots = [3,5,7,9,11,13];
		current_weathers_cards = createDeckFrom(weather_cards_easy);
	}
	else if(current_difficulty == "normal"){//22 rounds
		board.get(city).maxSpores = 3;
		min_tiles = 15;
		upset_spots = [3,5,7,9,11,13];
	}
	else if(current_difficulty == "hard"){//21 rounds
		board.get(city).maxSpores = 3;
		min_tiles = 15;
		upset_spots = [3,5,7,9,11,13];
	}
	else {//18 rounds
		board.get(city).maxSpores = 2;
		min_tiles = 15;
		upset_max = 12;
		upset_spots = [3,5,7,9,10,11];
	}
	
	weather_deck = createDeckFrom(current_weathers_cards);
	
	board.get(city).type = "city";
	board.get(city).buildings.push({image:"nausicaa"});
	board.setFungiDistance(4);
	board.loadDeck(deck);
	
	nausacii = city;
	var deck_races = createDeckFrom(peuples);
	for(let i = 0; i < numberPlayers; i++){
		players.push(new Player(i,rulesForNumberPlayer[numberPlayers-1].towns, deck_races.splice(Math.floor(deck_races.length*Math.random()),1)[0]));
	}
	current_player = players[current_player_index];
	if(current_player.peuple.id == 1){
		current_player.water++;
	}
	
	if(mycelium)
		board.get(mycelium).fungi = true;
	searchs = board.getSearchs();
	mousePos = {x:0,y:0};
	mouseCoord = {x:0,y:0};
	
	var production = rules[board.get(current_player.position).type].produce;
	for(var i in production){
		log("Joueur " + current_player.id + " produit " + production[i]);
		current_player[production[i]]++;
	}
	
	refresh();
}

canvas.addEventListener('mousemove', function(evt) {
mousePos = getMousePos(canvas, evt);
mouseCoord = pixelsToHex(mousePos);
}, false);

function draw(){
	ctx.fillStyle = "black";
	ctx.fillRect(0,0,500,500);
	board.draw(ctx);
}

var loopTimer = setInterval(function() {
	 draw();
},100);

function moveGlobal(int){
	if(current_player.peuple.id == 1 && current_player.water >= 3 && power_stuck == 0){
		current_action = "move_global";
		custom_number = int;
		current_player.water -= 3;
		log("Global move " + int + " awaiting for location (click)");
	}
	refresh();
}

function treatSelected(){
	if(current_player.peuple.id == 4 && current_player.seed >= 3 && power_stuck == 0){
		current_action = "treat_global";
		log("Global treat awaiting for location (click)");
	}
	refresh();
}

canvas.addEventListener('mouseup', function(evt) {
	var hex = board.get(mouseCoord);
	if(upset_effect == "town"){
		if(hex.built){
			hex.maxSpores = rules[hex.type].maxSpores;
			hex.built = false;
			for(var i = 0; i < players.length; i++){
				for(var k in players[i].buildings){
					if(hex.equal(players[i].buildings[k])){
						custom_number--;
						players[i].buildings.splice(k, 1);
						log("--Destroyed town reste " + custom_number)
						break;
					}
				}
			}
			if(custom_number == 0)
				upset_effect = "";
		}
	}
	if(current_action == "move_global"){
		if(rules[hex.type].walkable){
			players[custom_number].position = hex.coord();
			log("--Moved selected player");
			current_action = "move";
		}
	}
	if(current_action == "treat_global"){
		if(hex.fungi && (!hex.equal(mycelium))){
			log("treated global")
			hex.currentSpores = 0;
			hex.fungi = false;
			current_player.seed -= 3;
			if(!hex.equal(nausacii))
				increaseUpset();
		}
		else{
			log("invalid treated global")
		}
		current_action = "move";
	}
	refresh();
});

function refresh(){
	var player_show = "";
	for(var i = 0; i < players.length; i++){
		players[i].seed = Math.min(6,players[i].seed);
		players[i].water = Math.min(6,players[i].water);
		players[i].rock = Math.min(4,players[i].rock);
		player_show += players[i].show(current_player_index);
	}
	document.getElementById("players").innerHTML = player_show;
	document.getElementById("weather_count").innerHTML = weather_deck.length + "/" + current_weathers_cards.length;
	if(weather_card)
		document.getElementById("weather_content").innerHTML = "<b style='color:blue'>" + weather_card.title + "</b><br>" + weather_card.text;
	document.getElementById("upset_count").innerHTML = upset_deck.length + "/" + upsetting_cards.length;
	document.getElementById("upset").innerHTML = showUpset();
	document.getElementById("players").innerHTML = "Murs " + walls_count + "/" + rulesForNumberPlayer[players.length-1].walls + "<br>";
	document.getElementById("players").innerHTML += player_show;
	document.getElementById("tuiles_count").innerHTML = "Tuiles : " + (board.countNotFungi()-2) + "/" + min_tiles;
	document.getElementById("research").innerHTML = "Recherche : " + current_research + "/" + rules_difficulty[current_difficulty];
	document.getElementById("current_action_show").innerHTML = "Action courante : " + current_action;
}

function handleWeatherCard(){
	
	var production;
	log("Production des " + weather_card.produce);
	if(weather_card.produce == "pawn"){
		var production = rules[board.get(current_player.position).type].produce;
		for(var i in production){
			log("Joueur " + current_player.id + " produit " + production[i]);
			current_player[production[i]]++;
		}
	}
	else {
		for(var i = 0; i < players.length; i++){
			for(var k in players[i].buildings){
				var building = players[i].buildings[k];
				if(board.get(building).type == weather_card.produce){
					production = rules[board.get(building).type].produce;
					log("- Joueur " + players[i].id + " production :");
					for(var j in production){
						log("-- +1 " + production[j]);
						players[i][production[j]]++;
					}
				}
			}
		}
	}

	if(weather_card.title == "Vent"){
		board.wind(weather_card.effect);
		if(mycelium){
			var dir = weather_card.effect;
			log("Mycelium bouge vers " + dir);
			var new_mycelium = moveCoord(mycelium, dir);
			var hex = board.get(new_mycelium);
			if(rules[hex.type].walkable && hex.fungi){
				mycelium = new_mycelium;
			}
				/*if(mycelium && current_difficulty == "hard"){
					hex = board.get(board.get(mycelium).getNeighbor(hex_directions[dir]));
					if(hex && !hex.equal(nausacii) && !(hex.equal(citadel) && power_stuck == 0)){
						var key = getWallKey(hex,board.get(mycelium));
						if(walls[key]){
							walls_count--;
							walls[key] = false;
						}
						else {
							if(hex)
								hex.addSpore(hex_directions[dir]);
						}
					}
				}*/
		}
	}
	
	if(weather_card.upset)
		increaseUpset();
	
	log("====");
		
	refresh();
}

function drawWeather(bool){
	
	log("==Card==");
	if(noDraw){
		noDraw = false;
		log("No draw");
		return;
	}
	
	if(current_player.peuple.id == 2 && bool){
		weather_card = undefined;
		custom_number = [];
		if(weather_deck.length == 0){
			log("Deck meteo vide remelange");
			weather_deck = createDeckFrom(current_weathers_cards);
		}
		for(var i = 0; i < 2; i++){
			if(weather_deck.length == 0){
				log("Deck meteo vide remelange sauf carte deja tiree");
				weather_deck = createDeckFrom(current_weathers_cards);
				for(var k in weather_deck){
					if(weather_deck[k].id == custom_number[0].id)
						weather_deck.splice(k,1);
				}
			}
			var tmp_card = weather_deck.splice(0,1)[0];
			log("Carte " + tmp_card.text + " tiree en attente choix");
			custom_number.push(tmp_card);
		}
		document.getElementById("weather_content").innerHTML = "<button onclick='selectWeather(0)'>"+custom_number[0].text+"("+custom_number[0].produce+")</button><br><button onclick='selectWeather(1)'>"+custom_number[1].text+"("+custom_number[1].produce+")</button>";
	}
	else {
		if(weather_deck.length == 0){
			log("Deck meteo vide remelange");
			weather_deck = createDeckFrom(current_weathers_cards);
		}
		weather_card = weather_deck.splice(0,1)[0];
		log("Carte " + weather_card.text + " tiree");
		
		handleWeatherCard();
	}
}

function selectWeather(int){
	weather_card = custom_number[int];
	log("Carte " + weather_card.text + " selectionnee " + weather_card.id);
	weather_deck.push(custom_number[(int+1)%2]);
	handleWeatherCard();
	refresh();
}

function dontDraw(){
	if(current_player.peuple.id == 2 && noDraw == false && current_player.water >= 3 && power_stuck == 0){
		current_player.water-=3;
		noDraw=true;
		log("No draw next turn");
		refresh();
	}
}

function shuffleDeck(){
	if(current_player.peuple.id == 2 && current_player.water >= 3 && power_stuck == 0){
		current_player.water-=3;
		log("Deck meteo re-melange");
		weather_deck = createDeckFrom(current_weathers_cards);
		refresh();
	}
}

function exchange(type){
	if(power_stuck == 0){
		if(current_exchange == 0 && current_player.peuple.id == 5 && current_player[type] >= 3){
			current_player[type] -= 3;
			current_action = "exchange";
			current_exchange = 2;
			log("Commence echange avec 3 " + type)
		}
		else if(current_exchange > 0){
			current_player[type] ++;
			current_exchange--;
			log("-- Player " + current_player.id + " prends 1 " + type + ", reste " + current_exchange)
		}
		if(current_exchange == 0){
			current_action = "move";
			log("-- Fin echange")
		}
		refresh();
	}
}

function nextTurn(){
	if(upset_effect != ""){
		log("You must resolve upset effect before continuing");
		return;
	}
	
	document.getElementById("upset_content").innerHTML = "";
	
	//If player in fungi (and no nausacii) at the end of his turn, dead + upset
	if(!(current_player.peuple.id == 3) && board.get(current_player.position).fungi && !board.get(nausacii).equal(current_player.position)){
		log("Joueur " + current_player.id + " a termine son tour dans le fungi sans etre accompagne, perd recherche si détenue et +1 Upset");
		if(current_player.search){
			current_player.search = false;
			searchs.push(current_player.position);
		}
		//current_player.position = city;
		increaseUpset();
	}
	
	//Search token !
	for(var i = 0; i < searchs.length; i++){
		if(!board.get(current_player.position).fungi && board.get(current_player.position).equal(searchs[i]) && !current_player.search && board.get(nausacii).equal(current_player.position)){
			current_player.search = true;
			searchs.splice(i,1);
			break;
		}
	}
	
	//To victory
	if(board.get(current_player.position).equal(city) && current_player.search){
		current_player.search = false;
		current_research++;
		if(current_research == rules_difficulty[current_difficulty]){
			won = true;
			log("VICTORY !");
		}
	}
	
	
	if((board.countNotFungi()-2) < min_tiles){
		lost = true;
		log("PERDU : Trop de champignons sur la carte !");
	}
	
	
	
	turn++;
	log("---------------------------------------------");
	log("Tour " + turn);
	if(nausacii_stuck > 0){
		nausacii_stuck--;
		log("Nausacii stuck for " + nausacii_stuck + "turns")
	}
	if(power_stuck > 0){
		power_stuck--;
		log("Active powers disables for " + power_stuck + "turns")
	}
	
	if(weather_upset){
		drawWeather(false);
		weather_upset = false;
	}
	drawWeather(true);//true for player who can choose
	
	
	current_action = "move";
	current_player_index++;
	current_player_index = current_player_index%players.length;
	current_player = players[current_player_index];
	current_player.free_move = true;
	if(current_player.peuple.id == 1){
		current_player.free_move = false;
		current_player.water++;
	}
	
	//Production of the pawn
	var production = rules[board.get(current_player.position).type].produce;
	if(board.get(current_player.position).fungi && !(current_player.peuple.id == 3)){
		document.getElementById("production").innerHTML = "";
		for(var i in production){
			document.getElementById("production").innerHTML += "<button onclick='produce("+i+")'><img src='"+production[i]+".png' height='15px'></button>";
		}
		log("Joueur " + current_player.id + " commence dans fungi et doit choisir 1 production");
	}
	else{
		for(var i in production){
			log("Joueur " + current_player.id + " produit " + production[i]);
			current_player[production[i]]++;
		}
	}
		
	var player_show = "";
	for(var i = 0; i < players.length; i++){
		player_show += players[i].show(current_player_index);
	}
	
	if(upset == upset_max){
		lost = true;
		log("PERDU : Upset max !");
	}
	
	refresh();
}

function produce(int){
	var production = rules[board.get(current_player.position).type].produce;
	current_player[production[int]]++;
	document.getElementById("production").innerHTML = "";
	log("Joueur " + current_player.id + " selection production " + production[int])
	refresh();
}

var walls = {};
function getWallKey( coordA, coordB ) {

	var xmin = Math.min( coordA.x, coordB.x );
	var xmax = Math.max( coordA.x, coordB.x );
	var ymin = Math.min( coordA.y, coordB.y );
	var ymax = Math.max( coordA.y, coordB.y );

	var key = xmin + "_" + ymin + "_" + xmax + "_" + ymax;

	return key;
}

function build(type){
	switch(type){
		case 'nausacii':
			if(current_action!='nausacii'){
				if(current_player.water >= 1){
					current_player.water--;
					if(nausacii_stuck > 0)
						nausacii_remaining = 1;
					else
						nausacii_remaining = 2;
					current_action = "nausacii"
					log("Player " + current_player.id + " direction nausacii en attente (1 ou 2 fois)...");
				}
				else
					log("Player " + current_player.id + " nausacii invalid (water)");
			}
			else{
				nausacii_remaining = 0;
				log("nausacii annule");
				current_action = "move";
			}
			break;
		case 'wall':
			if(current_action!='wall'){
				if(!board.get(current_player.position).fungi && walls_count < rulesForNumberPlayer[players.length-1].walls && current_player.rock >= 1){
					log("Player " + current_player.id + " mur direction en attente...");
					current_action = "wall"
					remaining_walls = Math.min(rulesForNumberPlayer[players.length-1].walls-walls_count,2);
					log("--Reste " + remaining_walls + " murs...");
					current_player.rock--;
				}
				else
					log("Player " + current_player.id + " mur invalide");
			}
			else{
				log("mur annule");
				current_action = "move";
			}
			break;
		case 'town':
			if(!board.get(current_player.position).built && current_player.buildings.length < current_player.maxBuildings && current_player.rock >= 2 && rules[board.get(current_player.position).type].constructible){
				board.get(current_player.position).built = true;
				current_player.buildings.push(current_player.position);
				current_player.rock -= 2;
				if(current_player.peuple.id == 0){
					board.get(current_player.position).maxSpores++;
				}
				log("Player " + current_player.id + " ville construite");
			}
			else
				log("Player " + current_player.id + " ville invalide");
			break;
		case 'produce':
			var production = rules[board.get(current_player.position).type].produce;
			if(board.get(current_player.position).fungi && !(current_player.peuple.id == 3)){
				document.getElementById("production").innerHTML = "";
				for(var i in production){
					document.getElementById("production").innerHTML += "<button onclick='produce("+i+")'><img src='"+production[i]+".png' height='15px'></button>";
				}
				log("Joueur " + current_player.id + " commence dans fungi et doit choisir 1 production");
			}
			else{
				for(var i in production){
					log("Joueur " + current_player.id + " produit " + production[i]);
					current_player[production[i]]++;
				}
			}
			increaseUpset();
			break;
		case 'citadel':
			if(!board.get(current_player.position).built && current_player.peuple.id == 0 && current_player.rock >= 4 && rules[board.get(current_player.position).type].constructible && power_stuck == 0){
				if(citadel.x != Infinity){
					board.get(citadel).built = false;
				}
				board.get(current_player.position).built = true;
				citadel = current_player.position;
				current_player.rock -= 4;
				log("Player " + current_player.id + " citadelle construite");
			}
			else
				log("Player " + current_player.id + " citadelle invalide");
			break;
	}
	refresh();
}

function treat(bool){
	var position = current_player.position;
	if(board.get(position).currentSpores > 0 && !board.get(position).fungi){
		if(current_player.seed >= 1){
			log("Joueur " + current_player.id + " traitement spore");
			if(current_player.peuple.id == 4)
				board.get(position).currentSpores = 0;
			else
				board.get(position).currentSpores--;
			current_player.seed --;
			current_player.chitine ++;
		}
		else
			log("Joueur " + current_player.id + " traitement a echoue");
	}
	else if(board.get(position).fungi && (!board.get(position).equal(mycelium)) && bool){
		if(current_player.seed >= 2){
			log("Joueur " + current_player.id + " traitement tuile");
			board.get(position).currentSpores = 0;
			board.get(position).fungi = false;
			current_player.seed -= 2;
			current_player.chitine ++;
			nausacii_remaining == 0
			if(!board.get(position).equal(nausacii))
				increaseUpset();
		}
		else
			log("Joueur " + current_player.id + " traitement a echoue");
	}
	else
		log("Joueur " + current_player.id + " traitement a echoue");
	refresh();
}

function action(string){
	if(string == "cancel"){
		log("Action courante annulee");
		current_action = "move"
		refresh();
		return;
	}
	switch(current_action){
		case "wall":
			var coordA = current_player.position;
			var coordB = moveCoord(coordA,string);
			var key = getWallKey(coordA, coordB);
			if(remaining_walls > 0 && !walls[key]){
				walls_count++;
				remaining_walls--;
				log("--mur construit reste " + remaining_walls);
				walls[key] = true;
				if(remaining_walls == 0){
					log("Fin mur multiple");
					current_action = "move"
				}
			}
			else
				log("--mur invalid reste " + custom_number);
			break;
		case "nausacii":
			var old_position = nausacii;
			var newPosition = moveCoord(nausacii,string);
			if(walls[getWallKey(old_position, newPosition)]){
				log("--Joueur " + current_player.id + " mouvement nausacii a echoue (mur) reste " + nausacii_remaining);
			}
			else if(board.get(newPosition).type != "fungi_hidden" && nausacii_remaining>0){
				nausacii_remaining--;
				log("--Joueur " + current_player.id + " mouvement nausacii reste " + nausacii_remaining);
				nausacii = newPosition;
				if(nausacii_remaining == 0){
					log("--Joueur " + current_player.id + " fin mouvement nausacii");
					current_action = "move"
				}
			}
			else {
				log("--Joueur " + current_player.id + " mouvement nausacii a echoue reste " + nausacii_remaining);
			}
			break;
		case "move":
			var old_position = current_player.position;
			var newPosition = moveCoord(old_position,string);
			if(walls[getWallKey(old_position, newPosition)]){
				log("Joueur " + current_player.id + " mouvement a echoue (mur) " + string);
				break;
			}
			while(current_player.peuple.id == 5 && board.get(newPosition).type == "lac"){
				newPosition = moveCoord(newPosition,string);
				if(walls[getWallKey(old_position, newPosition)]){
					log("Joueur " + current_player.id + " mouvement a echoue (mur) " + string);
					break;
				}
			}
			if(board.get(newPosition) && rules[board.get(newPosition).type].walkable){
				current_player.position = newPosition;
				if(current_player.free_move){
					log("Joueur " + current_player.id + " dplct gratuit " + string);
					current_player.free_move = false;
				}
				else if(board.get(newPosition).fungi && current_player.water >= rules["fungi"].cost){
					log("Joueur " + current_player.id + " dplct cout " + rules["fungi"].cost + " " + string);
					current_player.water -= rules["fungi"].cost;
				}
				else if(current_player.peuple.id == 1 && current_player.water >= 1){
					log("Joueur " + current_player.id + " dplct (sourcier) coute 1 " + string);
					current_player.water -= 1;
				}
				else if(current_player.water >= rules[board.get(newPosition).type].cost){
					log("Joueur " + current_player.id + " dplct cout " + rules[board.get(newPosition).type].cost + " " + string);
					current_player.water -= rules[board.get(newPosition).type].cost;
				}
				else{
					log("Joueur " + current_player.id + " mouvement a echoue " + string);
					current_player.position = old_position;
				}
			}
			else
				log("Joueur " + current_player.id + " mouvement a echoue " + string);
			break;
	}
	refresh();
}
</script>