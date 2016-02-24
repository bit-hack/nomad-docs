# Nomad - Computer opponents (AI) Document
This document specifies the design for the computer controlled players in Nomad.


----
## Requirements
Nomad will provide a single player experience along with multiplayer game play.
Since nomad is a symmetric Real Time Strategy game, a key feature of the single
player experience is a strong and challenging computer opponent to play against.
The computer player must be capable of playing from game start to end against
one or more opponents.  The computer opponent must also understand the different
game modes provided by Nomad, and adapt its play style to match the objective
accordingly.


----
## Technical Overview
The first thing to note is that a computer player uses exactly the same game
interface as the human player.

When Nomad is launched, it loads all the shared libraries in the modules folder.
Some of these modules may provide game types, player interfaces or new computer
players.  This would allow Nomad to provide multiple different computer
opponents, perhaps each with their own strengths, weaknesses, play styles etc.
For the base version however only one computer opponent is planned.
