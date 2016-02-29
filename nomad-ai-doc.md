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


----
# Basic architecture
The first AI will use some fairly tried and tested techniques to get up and
running.  A blackboard architecture will be implemented with various knowledge
sources informing the backboard of opportunity.  An arbiter will score these
opportunities and undertake them as an action.

Knowledge sources can be inserted or removed with little disruption to the main
blackboard system.


----
## Areas of research
##### Neural Net
Since the game state can be recorded, A neural network could be trained on
recordings of real players.  An application area would be to have a neural net
analyze a players influence map, and make predictions about future game states.

##### Genetics
In the basic AI architecture, the blackboard and arbiter system will rely on
various hand tuned scoring systems.  An interesting idea is to adjust these
values using a genetic algorithm, similar to John Van Wavren's seminal work on
Quake 3.  Different AI personalities could be extracted.
