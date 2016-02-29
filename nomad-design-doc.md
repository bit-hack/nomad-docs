# Nomad - Game Design Document
This document contains details of the game design for Nomad.

## Contents
* Overview
* Story
* Setting
* Game Play
* Village Building
* Unit Control
* Unit Classes
* Spells
* Progression
* Level Design
* Building Classes
* Battle Mechanics
* User Interface


----
## Overview
Nomad is a real time strategy game and god game, inspired by Age of Empires,
Populous and Dungeon Keeper.  The game supports single player and multi-player
(LAN) game modes.  The game centers around skirmish mode, where players battle
against each other and computer AI on a procedurally generated or hand-crafted
map.


----
## Story
The thousand year storm has ended providing safe passage north.  Many have set
sail, hoping for new lands and in search of wealth and prosperity, drawn by the
tales and myths handed down through generations before them.

Many didn't make the long and perilous journey, but where they failed, some
explorers have succeeded. Their boats landing on a strange and unfamiliar shore.

As they set foot on your island, you reawaken once more...  however the others
will too...


----
## Setting
The world of nomad is set in a fictional medieval time period.  The game follows
different populations that have settled in close proximity and are competing
with each other and struggling to survive and colonize a new land.  Each
population is controlled by one of the islands demigods, rivaling for total
control.

Each villager must take on different roles and responsibilities to aid in the
survival of their village.

Resources must be collected to help the village grow.  As new houses are
constructed, so too, new villagers are born.  These new villagers must train
in a discipline to help construct and defend the village, and explore the
surrounding lands.

Your source of power is the mana you receive from the land and the devotion of
your population.


----
## Game play
At the start of a match, all players enter the same map, and are each given
control of a different population, which they must lead to total domination over
the map, by wiping out the other players' population (skirmish mode).

A player's interactions with the world center around giving their team's units
orders to carry out. You act as an invisible god over the land and your
population.

##### Resources
Four resources must be collected, managed and spent by each player:
- Wood
  - Areas of the land are often covered by dense regions of forest.  villagers
    may chop down trees, and stock pile them for wood.  Wood can be used when
    constructing weaker buildings.
- Stone
  - Deposits of stone are scattered over the land. Stone may be mined by
    villagers to be used when constructing strong buildings.
- Iron
  - Iron deposits are scattered over the land and may be mined by villagers.
    Stockpiles of iron can be used when constructing swords, armour and arrows
    for military use.
- Food
  - Food may be gathered from the land by hunting animals or fishing via boats.  
    Villagers may also construct farms which produce food at a constant rate.  
    ???Food is required to produce new villagers???
- Mana
  - Casting spells costs you mana which regenerates automatically, at a rate
    influenced by various game factors.

Some implicit, less obvious resources are also:
- Population
- Strategic positioning
- Technological process

Gathering resources will enable you to build new buildings, train your villagers
and research new technologies.

##### Expansion
Buildings generate a field of influence in their immediate surroundings.  New
buildings can only be placed within the radius of another building.  In this
way, players must slowly spread and expand across the map.

##### Fog of war
Land that has not yet entered the field of view of a player's unit is shrouded
from view by 'Fog of War', a mechanic shared by many RTS games.  As land becomes
visible to a player's unit the fog of war is lifted and any activity in that
region is directly shown.

##### Skirmish game
In a skirmish match, the objective is total control of the land.  Your opponents
must be conquered and wiped out.


----
## Village Building
Village building will be an important focal point of the game.  The player will
be able to place blueprints down on the map for new buildings, at which point a
villager in the construction role, will start to fabricate the building.

Placing blueprints may only be done in the radius of influence of other
buildings in your village.  This limits extremely sparse and rapid expansion, to
keep the game pace in a more narrow range.

Blueprint placement is free, however resources will be consumed while a villager
fabricates the building.

Buildings can be dismantled to release some of the resources that were sank into
its construction.  Buildings may also be repaired, at the cost of some
resources, proportional to the cost of a new build.


----
## Unit Control
A slightly indirect control method puts the player in a more passive role where
they influence and guide their units, reminiscent of the controls in Dungeon
Keeper.  Units have a certain level of autonomy and will of their own.  They
must be encouraged and guided to perform the tasks you want them to.

A player can pick up their units, and drop them back onto the map, upon which
the context of their location will inform their actions.  If you drop a
villagers besides a tree they will take on the lumberjack role and collect wood.
Drop a villager beside an unfinished house and they will try to construct it.

Limitations must be placed on where units can be dropped however, as it would
be game breaking to allow a player to drop military units directly into a
opposition players base.

Units may only be dropped inside your villages radius of influence.  With this
rule in place border skirmishes will become an important aspect of game play.

> How will units be guided outside of of your villages radius?  Perhaps the only
  limitation is that units cant be directly picked up by their owning player.
  Interestingly this may give a small advantage to the defender which might be
  good for gameplay.


----
## Unit Classes

All units on the map have a health value associated with them and they will die
if it reaches zero.  Each class of unit maintains the following stats:
- Health
  - The current health of a unit.  They will die if this reaches zero.  Injured
    units will be less effective in battle.  Injured units may retreat in battle
    and refuse to fight until they are healed.
- Offense
  - The offense rating of a unit details how much damage they can inflict with
    a single attack.
- Defense
  - The defense rating is a measure of how resistant this unit is to damage.
- Attack Rate
  - The attack rate statistic defines how much time passes by between attacks.
- Skill Level
  - The level rating denotes the skill level to which this unit has been trained
    to.  Units gain skill during combat, and also gain skill during repeated
    training.  A unit with a high skill level can be placed in either the
    Archery Range or the Barracks where their skill level will then be passed
    on to new graduates.

All units start off life as a villager produced by a house.  These villagers can
take on different roles and be trained to different classes.  The following list
details the possible units that can be created:

##### Villager
All units start out as villagers and can be guided into different roles.  Some
roles require now special training and are listed immediately below.  With
special training at the Barracks or Archery range villagers can become Archers
or Swordsmen.

  - Lumberjack
    - The lumberjack carries an axe, and will chop down trees to provide you
      with the wood resource.
  - Stone Miner
    - A stone miner carries a pickaxe and will mine stone deposits to provide
      their player with the stone resource.
  - Iron Miner
    - An iron miner carries a pickaxe and will mine iron deposits to provide
      their player with the iron resource.

##### Archer
An Archer carries a bow and arrow bolts and is restricted to ranged attacks
against enemy units.

##### Swordsman
Swordsmen carry short swords and shields and have good defense and cause melee
damage.

##### Farmer
A villager assigned to a farm becomes a farmer and will provide the food
resource over time.

##### Instructor
A unit with a high skill level may be placed in the Barracks or Archery range
as an instructor.  When this is done all graduates will have a skill level of
(instructor-1).


----
## Spells
The player can cast numerous spell provided they have enough mana.  Mana is
generated at a constant rate and can be increased by having villagers build and
worship in a temple building.  Spells offer a range of passive, offensive and
defensive effects.

Possible spells that can be cast are:
* Heal
  * It must be hard having corporeal form, there are just so many ways to get
    hurt.  Fix your subjects boo boo in the blink of an eye (if you even have
    eyes that is).
* Disease
  * Slow down your foe with this amazingly infectious plague, I just hope it
    doesnt find its way back to your village somehow...
* Speed
  * Why are your subjects so damn slow.  If only there were some way to make
    them faster...
* Terraform
  * The land is your canvas, build that mountain or valley you have always
    wanted.
* Lightning
  * Cast a bolt of lightning down from the heavens to kill enemy villagers,
    burn their buildings and start forest fires.
* Reseed
  * As a god you have the power to shape the forest.  Reseed any grassland and
    watch it turn into dense forest before your very eyes.
* Earthquake
  * Cause a harsh earthquake in a small radius damaging buildings and delaying
    all activity for a period of time.
* Resurrect
  * You wield the power of life and death with the ability to bring back the
    dead.  It unfortunate that they are not quite the same (zombified) ...
* Clone
  * That villager is amazing, if only there were more of them...
* Invulnerability
  * Your puny subjects are just too weak, with this spell you can make them
    stronger for a period of time.  It comes at a price however (death) ...
* Reveal
  * Wouldn't it be nice to see what your foe is up to, or what treasure lies
    just around the corner.  Lift that pesky Fog of War in a small radius for
    a limited time.

----
## Progression
Progression occurs by each player expanding their territory across the map,
while trying to cut off the expansion of their enemies.  Enemy buildings may be
captured by wiping out all enemy units in their radius and defending it for a
period of time where the bigger the building the longer it takes to capture.

Enemy buildings have limited health and will be destroyed by persistent attacks
when their health reaches zero.


----
## Level Design
Levels may be hand-crafted or generated automatically via one of many different
procedural level generators.  Some basic level layout ideas follow:

- Dense forest map:
  - Mostly tree covered map.
- Islands:
  - One team per island.
  - No direct land links between islands.
- Cliff and valley:
  - Direct paths over the land are blocked by a large number of cliffs and
    valleys.
- River map:
  - Rivers split the map into distinct regions with few passing places.
- Archipelago:
  - Many small and big islands are loosely connected by narrow strips of land.


----
## Building Classes
Many different kinds of buildings may be constructed as part of a village:
- Houses
  - Each house standing in a player's village, increases their population limit
    by five units.  While there is enough food, and the population is below the
    limit, houses will produce new villagers.
- Barracks
  - Villagers may be sent into the barracks to be trained in the art of melee
    combat with a sword.  Training can occur while there is enough iron
    collected to produce armour and swords for each unit.  An instructor unit
    may be placed in the barracks where their skill level will set the skill
    level of graduate units. (instructor level -1)
- Archery range
  - Villagers may be sent into the archery range to be trained in the art of
    archery.  Training can occur while there is enough iron and wood to produce
    bows and arrows for each unit. An instructor unit may be placed in the
    barracks where their skill level will set the skill level of graduate units.
    (instructor level -1)
- Farm
  - Villagers may be sent into a farm to become farmers.  While a farm has a
    resident farmer it will produce constant food at the expense of some wood.
- Watchtower
  - Watch towers can be constructed on a village's borders.  Military units may
    be sent into a watchtower where they will defend the land in its radius.
- Store hut
  - As wood, stone and iron resources are gathered they may be deposited in a
    store hut where they will then count towards a player's total resources.
- Temple
  - Villagers worshiping you in a temple increase the rate at which your mana
    accumulates.

> - Docks
    - Villagers may be sent into the docks to produce boats.


----
## Battle Mechanics
Battles are initiated when one player brings their units into range of an
opposition's units.  Battles are indirectly controlled by the player, and are
mostly directed by the simplistic rules that units follow:

- If an enemy unit is within range it will attempt to engage and attack.
- A completely outmatched or heavily outnumbered unit may retreat.
- A unit that is injured and has very low health may retreat from battle.
- Units that are unhappy will refuse to fight for their player.

Units can be encouraged to fight when they are dropped close to a nearby enemy
unit or settlement.

Rally points can also be placed on the map which will cause all units in their
circle of influence to move to their location.

Another import aspect of any battle is each players arsenal of spells and their
offensive and defensive capabilities.

> Rally points should have some kind of associated cost perhaps


----
## User Interface
Users will interact with the game using a keyboard and mouse.  The game will be
fully playable with the mouse alone, with hot-keys provided by the keyboard.

Players can pick up their units by left clicking on them with the mouse.  Units
that have been picked up may be dropped at the current mouse location using the
right mouse button.

User interface layer:
- Mini map
- Blueprint menu
- Current resources
- Message stream
- Currently picked up units
- Rally point menu
- Spell menu

User input interactions:
- Pickup/Drop unit
- Place/Remove blueprint
- Destroy building
- Scroll view port
- Place/Remove rally point
- Cast Spell
