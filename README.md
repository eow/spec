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

### Chat Message

```json
{
  "target": "player/#channel",
  "message": ""
}