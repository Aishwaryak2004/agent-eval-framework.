# Agent Evaluation Framework — Take-home Assignment (Assignment A)

## Overview
This project is a complete local-ready scaffold for the Agent Evaluation Framework take-home assignment.
It uses Next.js (Pages router), Supabase (Auth + Postgres + RLS), Tailwind CSS, and Recharts.

## What is included
- Full Next.js app (pages) with Auth (email/password), Config page, Dashboard, Evals list/detail.
- Server API `POST /api/evals/ingest` (uses SUPABASE_SERVICE_ROLE_KEY)
- Seed script: `npm run seed` to generate ~20,000 synthetic eval rows.
- DB schema with indexes + RLS (db/schema.sql)

## Quick start (local)
1. Install dependencies:
   ```
   npm install
   ```

2. Create a Supabase project and run `db/schema.sql` in the SQL editor to create tables and RLS.

3. Create a user in Supabase Auth (Email/password). Copy the `id` for TEST_USER_ID.

4. Create a `.env.local` in the project root with:
   ```
   NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
   SUPABASE_URL=${NEXT_PUBLIC_SUPABASE_URL}
   SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
   INGEST_SECRET=a-secret-for-ingest
   TEST_USER_ID=the-user-uuid
   ```

5. Seed data:
   ```
   npm run seed
   ```

6. Start dev server:
   ```
   npm run dev
   # open http://localhost:3000
   ```

## Notes
- Do NOT commit your service role key or any secrets to GitHub.
- For performance, create DB RPCs for heavy aggregates as needed.
- The UI masks PII in eval detail if `obfuscate_pii` is enabled in configs.

## What to submit (for your assignment)
- Deploy to Vercel and paste URL in submission.
- Public GitHub repo with this code + README.
- Test login credentials (create a demo user in Supabase).
- `npm run seed` script is included to generate demo data.
- Optional Loom demo script: show login, config, dashboard, sample eval.

## Troubleshooting
If you see auth errors, confirm your environment variables are set and RLS policies applied.

