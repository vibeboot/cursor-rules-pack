# Changelog

## 1.1.0 (2026-10-27)
- New `access-control.mdc`: check the session in every Server Action and route handler, take the user id from the session, scope reads and writes to the owner (`{ id, userId }`), return 404 for other users' records, and read roles and plans from the database.
- New `stripe-webhooks.mdc`: raw body with `await req.text()` before `constructEvent`, one `whsec_` secret per endpoint and environment, test and live keys never mixed, duplicate events skipped by a unique `event.id`, out-of-order events handled by re-fetching the object, and a Stripe CLI replay loop (`stripe listen`, `stripe trigger`, `stripe events resend`).
- `stripe.mdc` now points to `stripe-webhooks.mdc` for webhook details instead of repeating them.
- `00-workflow.mdc`: don't change the versions of `next`, `react`, auth, ORM or payment packages unless the task asks for it.
- Suggested by makers who reviewed the pack during our Fazier launch on Oct 26.

## 1.0.0 (2026-10-20)
- First release: 7 Cursor project rules (`00-workflow`, `security`, `nextjs-app-router`, `supabase`, `stripe`, `tailwind-shadcn`, `ai-sdk-chat`), an AGENTS.md template and a CLAUDE.md that imports it.
- Written for Next.js 15/16 (App Router), React 19, Tailwind CSS v4, shadcn/ui, `@supabase/ssr`, the Stripe Node SDK and AI SDK 5+.
