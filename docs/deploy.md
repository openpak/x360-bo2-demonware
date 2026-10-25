# Deploy: x360-bo2-demonware

## Getting started

```bash
# Install
npm install

# Build
npm run build

# Run
npm start
```

Server listens on **port 30003**.

### Requirements

- Node.js 18+
- MongoDB instance
- Xenia with BO2 configured to point at this server

### Environment

Set your MongoDB connection string in `src/app.module.ts` (or use environment variables).

## Code check

- TCP listener: `0.0.0.0:30003`, set in `src/core/tcp-server.ts`. `src/main.ts` calls `app.listen(0)`, so no HTTP port is opened. Its startup log line also says port 30003.
- Environment variables: none are read from `process.env` in `src/`. The MongoDB URI is hard-coded in `src/app.module.ts` as `mongodb+srv://120.0.0.1:12345/xenia-dw`. An SRV URI does not take a port or an IP, so this string must be edited in source before a real deployment.
- MongoDB collections: `user_files`, `dw_sessions` and `clips` (schemas in `src/infrastructure/persistance/models/`).
- Outbound HTTPS: `src/infrastructure/xboxpres-client.ts` calls `https://xenia-netplay-2a0298c0e3f4.herokuapp.com` (POST, DELETE and GET on session routes). This host is hard-coded in the upstream code, not OpenPak infrastructure.
- Image: none. The repository has no Dockerfile and no CI configuration.
