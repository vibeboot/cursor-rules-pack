# AGENTS.md

<!--
  VibeBoot Cursor Rules Pack v1.0.0 (https://vibeboot.dev/tools/cursor-rules-pack)
  Replace every <placeholder>, delete lines that don't apply, and keep this file short.
  Agents read it on every task, so only write down what they can't figure out from the code.
-->

Instructions for AI coding agents (Cursor, Claude Code, Codex, Copilot and others) working in this repo.

## Project
<One or two sentences: what the app does, who uses it, and what matters most (e.g. "billing must never break").>

## Stack
- Next.js <15 | 16> App Router, React 19, TypeScript (strict). Code lives in <`src/` | the repo root>.
- Styling: Tailwind CSS v4 <+ shadcn/ui>
- Auth: <Supabase Auth | Auth.js v5 | Clerk | Better Auth>
- Database: <Supabase Postgres | Prisma + Postgres | Drizzle + Postgres>
- Payments: <Stripe Checkout + Customer Portal | none>
- AI: <Vercel AI SDK v<x> with <provider> | none>
- Package manager: <npm | pnpm | bun>, Node <20 | 22>

## Commands
- `<pm> run dev`: dev server on http://localhost:3000
- `<pm> run build`: production build. Must pass before a task is done.
- `<pm> run lint`, `<pm> run typecheck`, `<pm> test`
- <Database: `supabase migration new <name>` | `npx prisma migrate dev --name <change>` | `npx drizzle-kit generate`>
- <Stripe: `stripe listen --forward-to localhost:3000/api/stripe/webhook`>

## Where things live
- `app/`: routes (`page.tsx`), layouts, and route handlers in `app/api/**/route.ts`
- `components/`: shared UI. `components/ui/`: shadcn/ui primitives.
- `lib/`: server helpers such as `lib/db.ts`, `lib/auth.ts`, `lib/stripe.ts`
- <The 3 to 6 files an agent should read before touching each feature, e.g. "billing: lib/billing.ts and app/api/stripe/webhook/route.ts">

## Conventions
- Server Components by default. `"use client"` only on small interactive leaves.
- Mutations go through Server Actions that authenticate, authorize and validate input (Zod) before writing.
- Every query for user data is scoped to the signed-in user.
- Secrets stay on the server. New env vars go in `.env.example` with a comment.
- Named exports, except Next.js special files (`page`, `layout`, `route`, `loading`, `error`).
- <Your real conventions: naming, folder layout, error handling, how you write tests.>

## Done means
1. Typecheck, lint, tests and build pass, and you say which ones you ran.
2. New env vars, migrations and dashboard steps are listed in your summary.
3. The diff contains nothing unrelated to the task.

## Don't
- Don't swap core libraries (auth, database, payments, UI kit) unless asked.
- Don't hand-edit generated files (`.next/`, `node_modules/`, generated database types) or migrations that already ran.
- Don't commit `.env*` files or real keys.
- <Project-specific landmines, e.g. "never grant Pro access outside the Stripe webhook".>

## Scoped rules
Detailed rules live in `.cursor/rules/*.mdc`: workflow, security, Next.js, Supabase, Stripe, Tailwind + shadcn/ui and AI SDK. Cursor attaches them automatically. Other agents: read the matching file before working in that area (for example `stripe.mdc` before touching billing).
