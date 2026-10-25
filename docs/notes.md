# Notes: x360-bo2-demonware

## Overview (from the previous README)

**Call of Duty: Black Ops 2 DemonWare server emulator for Xenia (Xbox 360 emulator).**

Restores online functionality for BO2 on Xenia. Handles stats, leaderboards, matchmaking, file storage, profiles, anticheat, and more over the original binary protocol.

The previous README was titled `Xenia-DWServer`.

## Upstream credit

This repository is a fork of [Xenia-DWServer](https://github.com/wildmaster84/Xenia-DWServer) by wildmaster84, kept as the `upstream` git remote. OpenPak changes are on `main`. Upstream feature descriptions are not OpenPak compatibility claims.

## Licence as found

The `LICENSE` file is the MIT License, Copyright (c) 2026 wildmaster84. `package.json` also declares `"license": "MIT"` and `"private": true`. The licence file is kept as found.

## Status snapshot

From [OPENPAK.md](../OPENPAK.md): the fork is deferred until OpenPak starts Xbox 360 game-server integration. It has not been built, deployed or tested with OpenPak, and no integration is scheduled. Later integration work listed there: inventory authentication, encrypted transport, matchmaking and persistence; mapping game identities to authenticated OpenPak XUIDs (a claimed XUID alone is not account authentication); and validating one title/update on Wharf before each hardware path.

## License

This project is for educational and preservation purposes. Not affiliated with Activision or Treyarch.

## Tech stack

- **NestJS** + **TypeScript** — Application framework
- **MongoDB** — Data storage (stats files, sessions, clips)
- **Custom TCP server** — Binary protocol handler (not HTTP)
- **Stats parser** — Bit-level DDL parser for BO2's stats format

## Performance

- Write-back stats cache (5-min flush to MongoDB, instant replies to game)
- Pre-allocated receive buffers with zero-copy compaction
- Single-buffer frame construction
- Batch session queries for matchmaking
- Async file I/O for publisher files

## Project structure

```
src/
├── core/                    # TCP server, connection, protocol, binary read/write
├── application/
│   ├── handlers/            # Service handlers (stats, storage, matchmaking, etc.)
│   ├── services/            # Stats parser, stats cache
│   └── schemas/             # DDL stat definitions (JSON)
├── infrastructure/          # MongoDB repositories, Xbox presence client
└── app.module.ts            # Module wiring + service registration
```

## Keywords

Black Ops 2, BO2, DemonWare, DWServer, Xenia, Xbox 360, emulator, server emulator, Call of Duty, Black Ops 2 online, BO2 multiplayer, BO2 zombies, leaderboards, stats, NestJS, TypeScript, MongoDB, reverse engineering, game server, private server, TU17, title update 17, Xbox Live, online play, preservation
