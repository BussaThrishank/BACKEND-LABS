# Lab 1: Node.js and Express server

**Name:** Thrishank · **Section:** CSE-GEN-AI-2A-304

**Live link:** https://backend-labs-511l.onrender.com/
## How to run

```bash
cd lab-01
npm install
npm start          # Express server (server.js) on port 3000
npm run plain      # plain http server (plain-server.js) on port 3000
```

Environment variables: `PORT` (optional, defaults to 3000). No `.env` file is needed.

## Endpoints

| Method | Path     | Description                                   | Status |
| ------ | -------- | --------------------------------------------- | ------ |
| GET    | `/`      | Welcome text                                  | 200    |
| GET    | `/about` | JSON with name and section                    | 200    |
| GET    | `/time`  | Current date and time from `new Date()`       | 200    |
| ANY    | others   | 404 message for any unknown path              | 404    |

Status codes logged by opening each route: `/` → 200, `/about` → 200, `/time` → 200, `/nope` → 404.

## Screenshots

![Route /](screenshots/root.png)
![Route /about](screenshots/about.png)
![Route /time](screenshots/time.png)
![404 for unknown path](screenshots/not-found.png)

## package.json fields (from `npm init -y`)

- **name**: package name (here, `lab-01`), taken from the folder name.
- **version**: current version of the project, `1.0.0` by default.
- **description**: short text about the project.
- **main**: entry file of the package (`server.js`).
- **scripts**: named commands run with `npm run`; `start` runs the server.
- **keywords**: search terms if the package is published.
- **author**: who wrote it.
- **license**: license of the code (`ISC` by default).
- **dependencies**: packages needed at runtime (`express`), added by `npm install`.

Express was installed with `npm install express` and lives in `node_modules/express`.

## Notes: viva answers

- **package.json vs node_modules:** `package.json` is the small manifest listing project details and dependencies; `node_modules` is the folder with the actual downloaded packages. It can be rebuilt with `npm install`, so it is never committed.
- **What `app.listen` does:** starts the server, binds it to a port and begins accepting requests; the callback runs once it is ready.
- **Request and response:** `req` holds what the client sent (method, URL, headers, params); `res` is used to send back the status, headers and body.

## Notes: problems faced

- The 404 handler must be placed after all routes, otherwise it catches valid paths too.
- Port 3000 was already in use when both servers ran together; stop one before starting the other.
# backendlabs
