# Military Asset Management System

React/Vite frontend, Express API, PostgreSQL inventory ledger. This is a demonstration framework, not certified for real military use.

## Setup
1. Create PostgreSQL database `military_assets`.
2. Run `psql -d military_assets -f database/schema.sql`.
3. In `backend`, run `npm install`, copy `.env.example` to `.env`, edit database credentials and JWT secret, then `npm run seed` and `npm run dev`.
4. In `frontend`, run `npm install`, copy `.env.example` to `.env`, set `VITE_API_URL`, then `npm run dev`.
5. Open http://localhost:5173.

## Demo accounts (seed only)
- admin@demo.local / DemoPass123!
- commander@demo.local / DemoPass123!
- logistics@demo.local / DemoPass123!

## Deployment
- Render: Node web service rooted at `backend`, build `npm install`, start `npm start`; configure DATABASE_URL, JWT_SECRET, FRONTEND_URL and SSL for your provider.
- Vercel: project root `frontend`, build `npm run build`, output `dist`, env VITE_API_URL to Render API URL.
- PostgreSQL: run schema.sql and seed script on hosted database.
- Do not deploy demo passwords to a public system.

## Limitations
- Opening balances are derived from all prior ledger movements, assuming initial stock zero.
- Global dashboard excludes internal transfers from net totals but shows gross transfers in detail.
- Assigned totals are current active assignments, not date-range snapshots.
- Logistics access is scoped to their base for outgoing transfers; incoming transfers to other bases are allowed.
- Real production requires refresh-token strategy, MFA, immutable audit store, pagination, input schema validation, automated tests, TLS, backup/restore and hardened deployment.
