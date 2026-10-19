# OpenPak integration

OpenPak fork of [Xenia-DWServer](https://github.com/wildmaster84/Xenia-DWServer),
under its existing MIT license. OpenPak changes use `main`.

Upstream targets the Xbox 360 build of Call of Duty: Black Ops II on Xenia,
including TU17 protocol behavior. Physical-console compatibility and OpenPak
Live integration require separate testing.

Status: deferred until OpenPak starts Xbox 360 game-server integration.
No build, deployment or active integration is scheduled in the dashboard work.

Later integration work:

- Inventory authentication, encrypted transport, matchmaking and persistence.
- Map game identities to authenticated OpenPak XUIDs; do not accept a claimed
  XUID alone as account authentication.
- Compare transport/task contracts with OpenPak's existing Demonware work
  before extracting shared components or duplicating services.
- Validate one title/update on Wharf, then on each supported hardware path.

This fork has not been built, deployed or tested with OpenPak. Upstream
feature descriptions are not OpenPak compatibility claims. This repository
is a game backend, not a stock-dashboard or Xbox Live replacement.
