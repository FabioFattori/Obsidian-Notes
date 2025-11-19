# Project Proposal: Drawgheter 
## Vision
DrawGheter is a game that consists in a small number of players, like 6(\*), that are in a lobby, each player, when they are extracted from a random pull (but all players will be drawing eventually), will be drawing on to a board and the others are asked to predict what the painter is drawing.
Each painter has about one minutes and a half to paint(\*), and in the mean time the other players need to predict, when the time is over the paint is passed to an another player. 
If a player gets the correct prediction obtains points based on a multiplier which starts at x4 and gets reduced when a player gets the right word until it reaches x1.
For all the duration of the game a leaderboard is shown.
### Leggend
- \* : to consider further, can be different from the deployed version of the software. 
### Key Functionalities 
- **Lobby system**: Players can create or join a game room via a shareable link.
- **Quick matches**: Players can join a random match with unknown players.
- **⁠Real-time game flow**: The server manages the game state and game flow of each session.
- **Game state synchronization**: All clients maintain a consistent view of the current phase and player states.
- **Fault tolerance**: If a player disconnects, the server keeps their state and allows reconnection.