# VibeBoot Cursor Rules Pack

A free set of Cursor project rules, plus an `AGENTS.md` template and a `CLAUDE.md`, for Next.js apps built with AI coding agents (Cursor, Claude Code, and other agents that read `AGENTS.md`).

Written for Next.js 15/16 (App Router), React 19, Tailwind CSS v4, shadcn/ui, `@supabase/ssr`, the Stripe Node SDK and AI SDK 5+.

Project page: https://vibeboot.dev/tools/cursor-rules-pack

## Install

1. Copy the rules into your project:
   ```bash
   mkdir -p .cursor/rules
   cp rules/*.mdc /path/to/your-project/.cursor/rules/
   ```
2. Optionally copy `AGENTS.md` and `CLAUDE.md` to your project root and edit them for your stack and commands.
3. Restart Cursor (or reload the window). Rules with `alwaysApply: true` load on every request; the others attach when files matching their `globs` are in context.

## Rules

| File | What it covers |
| --- | --- |
| `rules/00-workflow.mdc` | How the agent plans, edits and verifies changes (always applied). |
| `rules/security.mdc` | Guardrails for secrets, untrusted input, authorization, logging and redirects (always applied). |
| `rules/nextjs-app-router.mdc` | App Router conventions: Server Components, Server Actions, caching, proxy and metadata. |
| `rules/supabase.mdc` | `@supabase/ssr` clients, server-side auth checks, Row Level Security, migrations and generated types. |
| `rules/stripe.mdc` | Stripe Checkout, verified idempotent webhooks, access gating and the Customer Portal. |
| `rules/tailwind-shadcn.mdc` | Tailwind CSS v4 and shadcn/ui: CSS-first theme, v4 class renames, semantic tokens and `cn()`. |
| `rules/ai-sdk-chat.mdc` | Vercel AI SDK chat: `streamText` route handlers, `useChat`, tools, structured output, cost limits and abuse protection. |

Also included: `AGENTS.md` (agent instructions template) and `CLAUDE.md` (imports `AGENTS.md` for Claude Code).

## More from VibeBoot

Free tools:
- Auth.js error fixer: https://vibeboot.dev/tools/authjs-error-fixer
- Stripe webhook fixer: https://vibeboot.dev/tools/stripe-webhook-fixer

Paid Next.js starters at https://vibeboot.dev: SaaS Starter ($49) and AI Chatbot Starter ($59).

## License

MIT, see [LICENSE](LICENSE).
