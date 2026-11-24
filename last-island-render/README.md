# LAST ISLAND Survival Online v2.0 — Render Edition

A mobile browser multiplayer survival game with building, boars, wolves, gathering, crafting, hunger, health, chat, and room codes. Node.js + Express + Socket.IO.

## Deploy

Push the contents of this directory to the root of a GitHub repository. On Render, create a Node Web Service from the repository:
- Build command: `npm install`
- Start command: `npm start`
- Health check: `/health`
- Root directory: empty

Or use Render Blueprint (`render.yaml`) from the repository; inspect the plan before confirming.

Read `RENDER-SETUP-TH.md` for Thai step-by-step instructions.

## Notes

- Multiplayer requires a running server and an internet connection.
- The server listens on `0.0.0.0` and `process.env.PORT`.
- Game state is held in RAM and is lost on restart, redeploy or instance sleep.
- A single instance is needed for consistent multiplayer rooms.
- This is a prototype, not a security-hardened public game.
