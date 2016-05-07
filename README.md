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
 
What they are not. They are not realtime. As a game design principle rather than a technical focus, I think realtime 
features are the wrong features to focus on for long term compelling gameplay.

It's ok to have text chat, voice chat would be great, but I think things like skype can take care of that. 

The point is that the actual gameplay should focus on using non-realtime mechanics almost exclusively, specifically 
avoiding anything that can block play waiting for a response.

[More](/turnstyles.md) on the "Turnstyles" game design principles 

There is much more to be said and discussed about with turnstyles and I'll eventually put that
 up and link to it, but now on to Space Opera as a concrete proof of concept.

Game Design
===========

We'll start with a single game of up to 6 players and 6 npc positions, plus two explicit gm positions. 
Eventually games may be able to reach up to about 40 or 50 players in a single game, 
but more than that would probably require players to keep track of too much even with a month long turn phase.  

The Turnstyle is paralell, as opposed to sequential or realtime which are not long term goals. 
The exception to this is that military and economic alliances can be negotiated in pseudo-realtime 
during the player turn phase.

The initial CommunalMode is freestyle as opposed to cooperative or competitive which are long term goals, 
though my assumption is that the initial playtesters will be playing largely cooperatively against the npc positions
which is my hope for the eventual default style, freestyle allows conflict between players and the engine should support 
that from the beginning just so that we can test out both cooperative and competitive styles as we wish. Cooperative and 
Competitive modes will probably pair with different plot device attributes that encourage the particular communal 
style of play that the players have chosen. But to begin with these choices will just be managed by 
convention rather than by mechanics.

There will be two initial map types, a stellar map type and a planetary map type though the stellar map is of 
a much higher priority. Planetary events and combat can be reported via text summaries at first.

## Positions consist initially of
1. a ruler 
2. a species
3. 3 other leaders
4. some units 
    (ruler, leaders, ships and robots are identical from a technical standpoint where a ship has a hull, 
        a robot has a chassi and a leader or ruler has a suit - each with default properties and slots for items)
5. a faction (or can be independent)
6. a map position
7. a generated or drawn planetary map

	C-Feature: someday the ruler might just be a governance type, 
	allowing for democracies, collectives, hives, packs or other mechanics, 
	for now we'll call this governance_type 'feudal'

## Races 
1. Terran
2. Arachnidia
3. Lupe
4. Fungoid
5. Aurelian
6. Vampryei

    (there are also ancients and grey to start, but not as pcs)

## Grey Factions 
1. good
2. bad
3. ugly (chaos/irony)

Grey factions are npc prompts that try to pit players against one another or just cause trouble and interesting story
events in general depending on the group and gm desires.

## Keeping Score

"Keeping score" will be the last set of features to design and will need to be the most customizable aspect 
of the engine. In the end, story based games should focus on personal victory conditions. 

The one part of keeping score that I need to focus on in this early stage is how keeping score relates to maps. 

Maps are just fun and a key part of how folk tend to guage their progress viscerally in this kind of game. 
Whether it's territory ownership or story hotspots or viewing the progression of a plague or a personal journey, 
there are many ways to enhance a story via maps.

The base game has no score, you are telling a story. But it's still good to design each game with goals in mind and
to encode those goals in some way, via a score is an option, A list of unanswerd questions or grudges to address that
would lead to some irony. Story can explicitly or implicitly translate plot points into 'dramatic impact' or things 
like fate or karma, applause is another possible ways to encode story based score.

A likely focus is to emphasize mysteries solved or plots completed via plot garden story arcs. 

There can be military victory badges and points for controlled regions as a simple way for folk that would like 
to focus on that as a basic way to anchor the more abstract story ideas with a simple concrete baseline, but it 
should be easy to remove these for folk who would consider it a bad habit or a distraction.

Essentially Space Opera will use this time honored crutch as I get going, but The Plot Garden won't. 

## Maps
Maps are largely how someone determines how they are doing, so how big they are and what they display at various
zoom levels is key even when there is no explicit score or victory conditions.
 
Things that a player is trying to determine from the maps in Space Opera are

1. who controls where
2. what you can see at locational privacy levels
    * player positions in general with markers and labels for general direction, but no boundaries at first?
    * environment and terrain
    * planetary and regional public (visibility all or none)
    * planetary and regional private (visibility one at a time)		
3. what you can see at plot levels
    * markers, such as ?
    * mysteries with descriptions (prelude, actions, choices, midstatement, actions, choices, conclusion)
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
        when a location is teraformed it produces another unit of energy research or materials 
        each position starts off with a home planet, points are seen at the start, 
        but planetary details can be seen after scouting and scanning. stellar environmental effects include 
        planet habitability and physics pockets which can change like in vernor vinge's books, 
        the map should have things like invading fleets, solar flare-ups, pirates, and mysteries

2. Planetary, one per planet visited that maxes out initially at 760x480. 
        A hex map like cruenti dei each hex is a region with locations in it         

## Stellar HexMap Properties
* Background
* Position Labels (computed from each positions homeRegionId)
* Areas (such as dark matter, radiation or areas of control)
* Height (in rows)
* Width (in cols)
* centerX
* centerY
* Regions

## Stellar Hex Properties
* Name (use stars! star names)
* Environment Type
* Locations (0-3 Planets(colonized and not),  Space Stations, Monoliths)
(Moons, Asteroids, Debris, Plot Triggers)
* Features (Ancient)
* Controlling Realm
* Inhabiting Species
* Victory Point Value
* Units
* Features
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

## Transmission Actions

* Broadcast Message
* Send a Personal Diplomatic Message (continual)
* Propose/Accept/Cancel Trade        (continual) - requires adjacent regions, gives 1 resource of any type
* Propose/Accept/Cancel Alliance     (continual) - doesn't require adjacency, allows movement without default combat
* Share Research
* Share Story or Plot Element 
* Share Scanner Data

{  Todo: if a player attacks another player or bombs their planet without canceling first they become a traitor 
  a number of story specific repercussions can result. For now by default the victem just gets extra resources 
  and the traitor gets negative victory points or a badge of shame} 

## Position Actions
* Research Item
* Upgrade Unit

## Stellar Map Actions (requires hex control)

* Move
* Scout - like movement but into unexplored terrain, typically half speed       
* Colonize
* Terraform - gives a second resource
    * Energy
    * Materials
    * Research 

## Unit Actions - Leader(suit) Robot(chassi) Ship(hull)

* Move
* Scout - like movement but into unexplored terrain, typically much slower       
* Investigate +X Mv Pt Cost
* Diplomacize +X Mv Pt Cost
* Spy +X Mv Pt Cost
* Attack +X Mv Pt Cost
* Bomb +X Mv Pt Cost
* Lay Minefield +X Mv Pt Cost
* Note 
* Conditional 
* Set Stance (aggressive, defensive, ...)

## Items and Upgrades     
       
Suits can allow a leader items like a research team, a minelayer, a misstle weapon, a beam weapon, a research team  
Leaders essentially have their own small ships for free that can support a research team, 
but generally not both. 

Items can be things like bombs or scanners or research tools or any sort of mcguffin

Chassis, the robot version of a suit

Hulls, the ship version of a suit

( Clicking on a hull, suit or chassi from the Unit Detail View sends you to the Position View 
    with that Unit scrolled into the viewport )

Unit Level Items - costs?
* Research Gizmo +2 research
* Diplomatic Pouch +2 diplomacy
* Stealth Cloak +2 spycraft
* Colony Pod - colonize one planet in a controled region
* Mine Dispenser 50 - spreads defensive mines throughout a region
* Energy Tap 20 - drains energy from nearby planet
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
* Aligator-Hide Shield  -1 to hit
* Turtle-Shell Shield -2 to hit
* Phase-Barier Shield -3 to hit
* Strobiium Armor +1 hull
* Kelarium Armor +2 hull
* Neutronium Armor +3 hull
* Phaser Beam 1 damage at close range
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
