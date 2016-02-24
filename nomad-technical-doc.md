# Nomad - Technical Design Document
This document provides a technical overview for Nomad.


----
## Overview
The engine for Nomad can be broken down into three main layers:
- Interface Layer
- Game Layer
- net Layer

These modules form an interesting circle of read-write data access.
```
.-- Iface Layer <-- Game Layer <-- Net Layer <-.
'----------------------------------------------'
```
Data passed between layers follows the direction of the arrows.

----
## Interface Layer
The interface layer has read only access to the world state and write only
access to the event relay.  The interface layer provides a platform for
implementing players, be they human or computer controlled.

For a human player, the interface layer renders the game state to the screen and
sends events to the relay server based on the players input.

A computer controlled player implementation will analyse the game state, and
directly send messages to the relay server.

An interface Layer is strongly tied to a player UUID.  Each player may have one
or more interface layers working on their behalf.  This allows one or more
humans to cooperate and control the same team, or to provide a computer
assistant for the player.


----
## Game layer
The game layer consumes events received from the event relay.  These events are
interpreted by the game layer in a deterministic manner, thus advancing the game
state.  All other layers and modules have read only access to the game state.

The primary player (uuid 0), is responsible for sending regular e_event_frame
packets to the relay server.  When these are received by the game layer they
will trigger a simulation step of the game.

The game layer is responsible for shrouding information that should not be
directly visible to a certain player.  For instance a player should not be able
to make spatial queries and discover units that are covered by that players fog
of war.


----
## Net layer
The net layer manages the routing of events, produced by the interface layer,
collected and serialised by the event relay, and then consumed by the game
layer.

A detailed description of the net layer is covered in the netcode document.
