# CLAUDE.md

## Critical rules (read first)
1. **Security:** secrets stay on the server; only `NEXT_PUBLIC_*` vars reach the browser. Never commit `.env*` files or real keys.
2. **Never invent env vars.** Use only those in `.env.example`; add any new one there with a comment. No placeholder secrets.
3. **Auth checks:** authenticate and authorize on the server in every route handler and Server Action. Scope every user-data query to the signed-in user.
4. **Stripe webhooks:** always verify the signature (`stripe.webhooks.constructEvent` with the raw body and the webhook secret) before handling an event. Grant paid access only from the webhook.
5. **Done means tested:** typecheck, lint, tests and build pass before you say you're done, and you say which ones you ran.

@AGENTS.md

AGENTS.md (imported above) is the source of truth for this repo. Area-specific rules live in `rules/*.mdc` (copy into `.cursor/rules/`). Before editing billing, auth, database, styling or AI code, read the matching file there (stripe.mdc, stripe-webhooks.mdc, access-control.mdc, supabase.mdc, nextjs-app-router.mdc, tailwind-shadcn.mdc, ai-sdk-chat.mdc).
