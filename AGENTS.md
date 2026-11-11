# AGENTS.md

Rules for coding agents in this learning repo. They apply to the whole tree. `event-signup/AGENTS.md` comes from the Nest CLI; when the two differ, follow this file.

## Rules

- Synthetic data only.
- Local only. Bind `127.0.0.1`. No public deploy, no real emails, no payments, and do not commit real secrets.
- The human writes negative tests. Agents only hint or review them.
- Do not add frameworks, microservices, or Python unless the task needs them.

## Commands

These commands exist after this init. Run them from `event-signup/`.

```bash
docker compose up -d
npm run build
npm test
npm run test:e2e
npm run start
npm run start:dev
```

`npm run start` listens on `127.0.0.1`. The port is `PORT` from the environment, default `3000`. This app does not load a `.env` file on its own; export the variables before starting.

### TODO

Not set up yet. The owner will fill these in.

- `npx prisma migrate dev`
- `npx prisma db seed`
- prisma / application test command
