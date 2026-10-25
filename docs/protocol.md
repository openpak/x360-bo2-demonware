# Protocol: x360-bo2-demonware

## Protocol

The server speaks the original DemonWare binary protocol over TCP. No modifications to the game or Xenia are needed — the server implements the same wire format the official servers used.

- Bit-packed authentication (XUID + gamertag + title ID)
- Tagged binary serialization for request/response bodies
- Per-service routing (stats, storage, matchmaking, etc.)
- Keepalive heartbeat

## What it does

- **Stats** — Parses and serves MP and Zombies stats (kills, deaths, score, rank, prestige, etc.)
- **Leaderboards** — Global and per-map leaderboards for both MP and ZM
- **Matchmaking** — Session creation, group management, and player matching
- **File Storage** — User stats files and publisher files with MongoDB persistence
- **Profiles** — Player profile read/write
- **Anticheat** — Heartbeat and validation checks
- **Rich Presence** — Player status broadcasting
- **League** — League season data
- **Content Streaming** — Theater/clip support
- **Tags** — Player tags

## Service IDs

From `onModuleInit()` in `src/app.module.ts`. Each ID is the service type the dispatcher routes to a handler.

| Service ID | Handler |
| --- | --- |
| 3 | `simple.handlers.ts` (`handleTeams`) |
| 4 | `stats.handler.ts` |
| 8 | `profile.handler.ts` |
| 10 | `storage.handler.ts` |
| 12 | `simple.handlers.ts` (`handleTitleUtilities`) |
| 15 | `simple.handlers.ts` (`handleKeyArchive`) |
| 21 | `matchmaking.handler.ts` |
| 23 | `simple.handlers.ts` (`handleCounter`) |
| 27 | `simple.handlers.ts` (`handleDml`) |
| 28 | `simple.handlers.ts` (`handleGroup`) |
| 38 | `anticheat.handler.ts` |
| 50 | `content-streaming.handler.ts` |
| 52 | `tags.handler.ts` |
| 58 | `pooled-storage.handler.ts` |
| 67 | `simple.handlers.ts` (`handleEventLog`) |
| 68 | `simple.handlers.ts` (`handleRichPresence`) |
| 81 | `simple.handlers.ts` (`handleLeague`) |

All handlers live in `src/application/handlers/`. On disconnect, the matchmaking session is cleaned up and the player's stats cache is flushed.
