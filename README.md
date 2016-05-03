 Space Opera Design
===================
The design document for Space Opera, an online collaborative storytelling game.

What is it?
===========

It is the first proof of concept of the "Turnstyles" game design principles. 
Principles that I intend to support with an engine and set of phone compatible web components.

The Turnstyles principles focus on games that mix the best features of online play with those of tabletop play.

They are designed for folk with busy lives, but who want to play a game with their friends, 
one that eventually tells a story.

[More](/turnstyles.md) on the "Turnstyles" game design principles 

There is much more to be said and discussed about with turnstyles and I'll eventually put that
 up and link to it, but now on to Space Opera.

Game Design
===========

The game design is broken up into phases, a very minimal first phase and a more complete first prototype.

We'll start with a single game with up to 8 players and 8 npc positions, plus two explicit gm positions. 
Eventually games may be able to reach up to about 40 or 50 players in a single game, 
but more than that would probably require players to keep track of too much even with a month long turn phase.  

The Turnstyle is paralell, as opposed to sequential or realtime which are not long term goals the exception to this
is that military and economic alliances can be negotiated in pseudo-realtime during the player turn phase.

The initial CommunalMode is freestyle as opposed to cooperative or competitive which are long term goals, 
though my assumption is that the initial playtesters will be playing largely cooperatively which is my hope 
for the default style, freestyle allows conflict between players and the engine should support that from the begining
just so that we can test out both cooperative and competitive styles as we wish. Cooperative and Competitive modes
will probably pair with differnt plot elements that encourage the communal style of play that the players have chosen.

There will be two initial map types, a stellar map type and a planetary map type though the stellar map is of 
a much higher priority. 

## Positions consist initially of
1. a ruler 
2. a species
3. 3 other leaders
4. some units (ruler, leaders, ships and robots are identical from a technical standpoint 
where a ship has a hull, a robot has a chassi and a leader or ruler has a suit - each with slots for items)
5. a faction (or independent)
6. a map position
7. a generated or drawn planetary map

	C-Feature: someday the ruler might just be a governance type, 
	allowing for democracies, collectives, hives, packs or other mechanics, 
	for now we'll call this governance_type 'feudal'

## Races 
1. Terran
2. Arachnidia
3. Lupe
4. Sporelon
5. Aurelian
6. Flux

    (there are also ancients and grey to start, but not as pcs)

## Grey Factions 
1. good
2. bad
3. ugly (or chaos/irony)

Grey factions are npc prompts that try to pit players against one another or just cause trouble and interesting story
events in general.

## Maps
Maps are largely how someone determines how they are doing, 
so how big they are and what they display at various zoom levels is key. 	
Score can be based on story, plot points that translate to 'dramatic impact'. 
(fate or karma?) mysteries solved via plot garden story arcs but there are things that a player will always 
guage their progress on via the maps and so what is seen on the map is a sort of scoreboard

Things that a player is trying to determine from the maps are

1. who controls where
2. what you can see at locational privacy levels
    * player positions in general with markers and labels for general direction, but no boundaries?
    * environment and terrain
    * planetary and regional public (see all at once)
    * planetary and regional private (see one at a time)		
3. what you can see at plot levels
    * markers, such as ?
    * mysteries with descriptions (prelude, actions, midstatement, actions, conclusion)
    * story threads as it unfolds (based on transmission devices?)
    * hot spots, special important story threads
4. Trade status and economy
5. Regional Production Values
    * research
    * energy
    * materials
6. environment (habitability and stellar or terrain modifiers)


1. Stellar, one map that maxes out at 2560x1600
        A map like in stars, but with the points as locations in hexes
        each location is a planet or asteroid or space station, etc that is controlled with the hex, 
        when a location is colonized, it produces energy, research or materials
        each position starts off with a home planet, points are seen at the start, 
        but planetary details can be seen after scouting. stellar environmental effects include 
        planet habitability and physics pockets which can change like in vernor vinge's books, 
        the map should have things like invading fleets, solar flare-ups, pirates, and mysteries

2. Planetary, one per planet visited that maxes out initially at 760x480. 
        A hex map like cruenti dei each hex is a region with locations in it         

## Stellar HexMap Properties
* Background
* Position Labels (computed from positions homeRegionId)
* Areas (such as dark matter, radiation or areas of control)
* Height (in rows)
* Width (in cols)
* centerX
* centerY
* Regions

## Stellar Hex Properties
* Name (use stas! star names)
* Environment Type
* Locations (0-3 Planets(colonized and not),  Space Stations, Monoliths)
(Moons, Asteroids, Debris, Plot Triggers)
* Features (Ancient)
* Controling Realm
* Victory Point Value
* Units
* Energy 
* Materials
* Research
* RegionsBorders(wormholes)


## Detail Views
* Stellar Maps
* Transmissions
* Positions 
* Agents 
* Planet Maps

## Actions
* Scout
* Move 
* Build
* Upgrade
* Colonize
* Mine
* Diplomacize
* Research
* Spy
* Story
* Investigate
* Note
* Conditional


## Transmissions Actions

* Send a Message    (continual)
* Propose Trade     (continual)
* Propose Alliance  (continual)
* Broadcast Message
* Research Item
* Upgrade Unit

## Region Actions (requires hex control)

* Colonize
* Terraform
* Upgrade Economy
* Upgrade Resource Mining
* Upgrated Research Facilities

## Unit Actions     Leader(suit) Robot(chassi) Ship(hull)

* Scout - like movement but into unexplored terrain, typically much slower       
* Move
* Investigate
* Mine
* Diplomacize
* Spy

## Items and Upgrades     
       
Suits can allow a leader items like a research team, a minelayer, a misstle weapon, a beam weapon, a research team  
Leaders essentially have their own small ships for free that can support a research team, 
but generally not both. 

Items can be things like bombs or scanners or research tools or any sort of mcguffin

Chassis, the robot version of a suit

Hulls, the ship version of a suit

Unit Level Items - costs?
* Research Gizmo +2 research
* Diplomatic Pouch +2 diplomacy
* Stealth Cloak +2 spycraft
* Colony Pod - colonize one planet in a controled region
* Mine Dispenser 50 - spreads defensive mines throughout a region
* Energy Tap 20 - drains energy from nearby planet- drains energy from nearby planet
* Bat Scanner - scans out one region 
* Dolphin Scanner - scans out two regions, penetration scan out one
* Eagle Scanner - scans out three regions, penetration scan out two
* Nuclear Source +3 energy
* Fusion Source +6 energy
* Tacheon Source +9 energy
* Nuclear Drive - scout 1 moves 2
* Fusion Drive - scout 2 moves 4
* Tacheon Drive - scout 3 moves 6
* Slide Rule Targetron +1 to hit
* TI-83 Targetron +2 to hit
* HAL Targetron +3 to hit
* Mole-Skin Shield  -1 to hit
* Turtle-Shell Shield -2 to hit
* Phase-Barier Shield -3 to hit
* Strobiium Armor +1 hull
* Kelarium Armor +2 hull
* Neutronium Armor +3 hull
* Phase Beam 1 damage at close range
* Disruptor Beam 2 damage at close range
* Anti-Matter Beam 3 damage at close range
* Delta Torpedo 1 damage at long range
* Jihad Missile 2 damage at long range
* Armageddon Spear 3 damage at long range
* Cherry Bomb +2 to destroy colonies
* Neutron Bomb +4 to destroy colonies
* Anti-Matter Bomb +6 to destroy colonies

## Plot Devices
Plot devices should have some properties
these properties might eventually match with game types
to describe it's size and scope 
    the quantity of players it affects
    method of distribution (random, from a direction, manually positioned)
    how it affects certain factions differently than others
    plot points with 
        decisions and effects
        location type(stellar, planetary, region, location)
    possible conclusions and how to trigger them		
    point values for the various conclusions based on 
        faction 
        race
        position
Plot devices are set up with three defaults on creation
A GM can 
    adjust the initial plot devices before the game starts
    add new plot devices as the game progresses 
    choose a path to follow explicitly
    override the results

prototype examples

1. ancient robot releases
2. pirates
3. gravitational flux or dark matter


### Licences 
Code: MIT
Artwork and Design: CC-BY-SA-4.0
