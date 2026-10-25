# Call of Duty: Black Ops II

OpenPak's Call of Duty: Black Ops II Server.

| | |
| --- | --- |
| Game | [Call of Duty: Black Ops II](https://openpak.org/titles) |
| Network | Xbox 360 |
| Title ID | `0x415608C3` |
| Licence | MIT |

## What it serves

| Endpoint | What | Served by |
| --- | --- | --- |
| `0.0.0.0:30003` (TCP) | DemonWare binary protocol: stats, storage, matchmaking, profiles, anticheat, rich presence, league, content streaming, tags | `src/core/tcp-server.ts` |

## Run

```sh
npm install
npm run build
npm start
```

Requires Node.js 18+ and a MongoDB instance. Details are in [docs/deploy.md](docs/deploy.md).

## Docs

- [Protocol](docs/protocol.md)
- [Evidence](docs/evidence.md)
- [Deploy](docs/deploy.md)
- [Notes](docs/notes.md)

Live compatibility status: [openpak.org/titles](https://openpak.org/titles).

## Licence

MIT. See [LICENSE](LICENSE).
