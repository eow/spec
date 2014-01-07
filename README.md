EOW Specification
=================

* [Basic Concepts](#basic-concepts)
  * [Gameplay](#gameplay)
  * [World](#world)
  * [Implementation](#implementation)
* [Messages](#messages)
  * [Orientation](#orientation-message)
  * [Attack](#attack-message)
  * [Inventory](#inventory-message)
  * [Chat](#chat-message)

Basic Concepts
--------------

### Gameplay

Players control ships, with the aim of moving from one area to another to trade,
gather resources, attack other ships, or simply see the sights.

The following are ideas for gameplay mechanics.

EOW will feature FTL-like gameplay. Players control a (multiple?) ships with a number of subsystems (# TBD) that can be powered.
There will be a crafting system implemented that players can use to create new items for their ships.
There will be some kind of economy that the players can buy and sell items & raw material for a set price.
Ships can be upgraded using raw materials to support more weapon slots, higher hitpoints etc.
Mining asteroids (and planets?) is one of the ways to collect the raw materials.
When a players ship is destroyed (either by another player in P2P combat, or by another means) their items (some/all?) are dropped into open space, which can then be collected by another player.

Questions:

 - AI, should we have AI ships flying around?
 - Leveling system?
 - Player controlled planets? Maybe allow planets to research ship upgrades and automatically mine materials.

### World

The game world is a 2-dimensional infinite arena. Within this arena, there are
various entities. These entities include players and objects. Every entity has a
position, an orientation, and a velocity. If an entity is still, its velocity is
0.

### Implementation

Players connect to servers to interact with the world. They exchange messages
with the server to announce and learn of changes to the world. The server can
accept or reject messages from the player according to its own rules.

Upon connecting to a server, a player receives all the information it needs to
initiate the state of the world that it cares about. The server will, from that
point, only send updates to the player about changes to entities in the world or
other out-of-band events (for example chat messages).

It is expected that the client base will be heterogeneous, and that there will
be various opportunities to exploit oversights in the server's or other clients'
implementations to gain the upper hand.

It is encouraged for players to write or modify their own clients to automate as
much of their gameplay as possible.

Messages
--------

### Orientation Message

```json
{
  "position": {
    "x": 0,
    "y": 0,
  },
  "orientation": 0,
  "trajectory": 0,
  "velocity": 0
}
```

### Attack Message

```json
{
  "power": 0,
  "radius": 0,
  "range": 0
}
```

### Inventory Message

The following message facilitates trading, dropping, using and crafting items.

```json
{
  "action": "actionName",
  "input": [ ],
  "output": [ ],
  "args": { }
}
```

### Chat Message

```json
{
  "target": "player/#channel",
  "message": ""
}
```
