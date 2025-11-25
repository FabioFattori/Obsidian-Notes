# Project Proposal: DrawGheter

## Vision
DrawGheter is a multiplayer party game designed for small groups of around six players (\*). Players first join a lobby, and one player at a time is randomly selected to draw on a shared board while the others try to guess what is being drawn.

Each painter has approximately one and a half minutes to draw (\*). During this time, the other players submit their predictions. When the timer expires, the drawing role passes to the next player.

Players who guess the correct word earn points based on a multiplier that starts at x4 and decreases each time someone guesses correctly, down to a minimum of x1. A leaderboard is displayed throughout the match.

### Legend
- *: To be evaluated further; final values may differ in the deployed version.

---
## Key Functionalities
- **Private matches**: Players can create or join a private game room via a shareable link.
- **Quick matches**: Players can join a random public match with unknown players.
- **Real-time game flow**: The server manages the complete game lifecycle and state transitions.
- **Game state synchronization**: All clients maintain a consistent view of the drawing board and game state.
- **Fault tolerance**: Player data is preserved if they disconnect, allowing seamless reconnection.
- **Global Leaderboard**: Displays top players based on public match wins (private matches excluded).

---
## Learning Goals
- **Real-time communication**: Implementing WebSockets for low-latency interactions.
- **Scalability & fault tolerance**: Running multiple backend nodes and maintaining consistent state across them via Kubernetes.
- **Containerization & orchestration**: Using Docker and Kubernetes for modular deployment.
- **Data consistency & synchronization**: Managing shared game state and ensuring atomic updates.

---
## Technology Stack

### Backend
- **.NET Web API (C#)**: REST services and WebSocket support.
- **Redis**: Pub/Sub system for inter-service communication and fast access to:
  1. login sessions  
  2. global leaderboard  
  3. lobby-to-websocket routing  
- **MinIO / S3**: Object storage used for:
  1. action logs  
  2. game-board image history  
  3. game-state snapshots for fault tolerance and recovery  
- **Postgres**: Database for users, match history, and statistics.
### Frontend
- **React**: For building a responsive interface.
- **TailwindCSS + Flowbite**: Styling and UI components.
- **Socket.IO Client**: For real-time communication.
- **Konva**: Simplified canvas handling for the drawing board.
### Infrastructure
- **Docker & Docker Compose**: Local development setup.
- **Kubernetes**: Distributed deployment and autoscaling.
- **NGINX**: Reverse proxy and load balancer supporting WebSockets.

---
## Team Members
- **Fabio Fattori** – fabio.fattori3@studio.unibo.it