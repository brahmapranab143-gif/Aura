# Aura Shop

A simple clothing shop website with an admin panel. It has no dependencies: it needs only Node.js 18 or newer.

- Shop: `/`
- Admin panel: `/admin`

## Run locally

```bash
node server.js
```

Open http://localhost:3000. On the very first run the admin password is printed **once** in the terminal (user: `owner`). Change it in Admin > Settings.

## Environment variables

| Variable | Purpose |
|---|---|
| `PORT` | Port to listen on (hosting services set this automatically) |
| `DATA_DIR` | Where `db.json` and uploaded photos are stored. Must be a persistent disk when hosted |
| `ADMIN_PASSWORD` | Admin password for the very first start |
| `FAST2SMS_KEY` | Enables real OTP SMS (otherwise the OTP is shown on screen, test mode) |

## Deploying publicly

GitHub only stores the code. To make the site live, connect this repository to a host that runs Node.js (for example Render, Railway or Fly.io).

1. Start command: `node server.js` (or use the included `Dockerfile`). No `npm install` is needed.
2. Attach a persistent volume and point `DATA_DIR` at it. Without it, products, orders and photos are lost on every restart or redeploy.
3. HTTPS is required for the GPS location button (most hosts provide it for free).
4. Set `ADMIN_PASSWORD`, and `FAST2SMS_KEY` for real SMS.
5. Run only ONE instance (the data is stored in a local file).
6. Back up the `DATA_DIR` folder regularly.
