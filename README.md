# tentosen
Awesome game

# What is it?

* Multiplayer battle game
* For the prototype, JS + Go

# How does client/server communicate?

* Game server inits a game state
* a game state stores a position of each character, with a set of information to determine the velocity.
* Client connects to a server via a websocket (for low latency bi-directional communication), sends and receives following events;
  * heartbeat (client -> server): make sure that the client is capable of receiving a state update from the server.
  * change acceleration (client -> server): updates client acceleration, which leads to change of a player's position
  * change rotation (client -> server): updates client rotation, which leads to change of a player's position

# Game state data model

````
{
  time: <uint64>,
  players: {
    player_id<string>: {
      id: <string>,
      color: <string>,
      position: {
        x: <int>,
        y: <int>
      },
      angle: <int>,
      velocity: {
        x: <int>,
        y: <int>
      },
      acceleration: <int>,
      rotation: <int>
    }
  }
}
````
