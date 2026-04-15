# Tech substack

Everything needed to build, ship, and monetize a self-serve product as a solo or small founding team, using agentic AI tools as the primary execution environment.

**Last updated:** 2026-04-13

## TL;DR picks

| Job | Pick | Why |
|---|---|---|
| Coding agent | [Claude Code](https://claude.com/claude-code) | Terminal-native, sees the whole repo, runs tools |
| Inline IDE AI | [Cursor](https://cursor.com) | For tight feedback loops on specific files |
| UI generation | [v0](https://v0.dev) | React + Tailwind + shadcn out of the box |
| Framework | Next.js (App Router) + TypeScript | Default for full-stack React; maximum model fluency |
| Styling | Tailwind + [shadcn/ui](https://ui.shadcn.com) | Copy-paste components, agent-friendly |
| Schema / validation | [Zod](https://zod.dev) | One schema shared client/server/LLM |
| Database + auth + storage | [Supabase](https://supabase.com) | Postgres, auth, storage, realtime — one SDK |
| Hosting | [Vercel](https://vercel.com) | Zero-config Next.js, preview URL per push |
| Background jobs | [Trigger.dev](https://trigger.dev) or [Inngest](https://inngest.com) | Durable workflows, agent-friendly |
| Payments — flexible | [Stripe](https://stripe.com) + [Agent Toolkit](https://github.com/stripe/agent-toolkit) | Subscriptions, metered billing, MCP-ready |
| Payments — hands-off tax | [Lemon Squeezy](https://lemonsqueezy.com) | Merchant of Record — they handle VAT/sales tax |
| LLM API | [Anthropic Claude](https://docs.anthropic.com) | Default. Swap per task, not per startup. |
| AI SDK | [Vercel AI SDK](https://sdk.vercel.ai) | Streaming, tool calls, provider-agnostic |
| Error tracking | [Sentry](https://sentry.io) | Free tier covers pre-PMF |
| Product analytics | [PostHog](https://posthog.com) | Events, replays, flags — one tool |
| Uptime | [BetterStack](https://betterstack.com) | Free tier monitoring + status page |
| Domain | [Cloudflare Registrar](https://cloudflare.com) | At-cost pricing, DNS included |

## Phases

### 1. Validate (days 1–2)

Pressure-test the idea before writing code.

- Run mock interviews with Claude playing 3 different customer personas. Steelman objections.
- Use [Perplexity](https://perplexity.ai) for competitor + market sizing research.
- Write findings into a `VALIDATION.md` in the repo root — it becomes the brief for every subsequent prompt.

**Exit criterion:** a one-pager with problem, ICP, top 3 competitors, and a pricing hypothesis.

### 2. Build (days 3–14)

Scaffold with an agent, not a boilerplate.

- Open Claude Code in an empty folder. Paste the `VALIDATION.md`. Have it scaffold Next.js + Supabase + Tailwind + shadcn/ui.
- Use v0 for the landing page and complex UI components; paste outputs into the repo as real files, not an external dependency.
- Keep one agent in the loop for every feature. Context fragmentation across chat tabs is the #1 bootstrapper productivity killer.
- Commit early. Preview URLs on every push via Vercel.

**Shape of the app:**
- Next.js App Router + TypeScript
- Server Actions for mutations; route handlers only for webhooks
- Supabase for Postgres, auth, storage
- Zod schemas shared client/server, also used as LLM tool schemas
- Vercel AI SDK for any LLM-powered features

### 3. Monetize (days 10–14, in parallel with build)

Wire payments before launch — it is the highest-leverage "feature" in the product.

- **Stripe** if you want subscriptions, metered billing, or control. Integrate with the [Stripe Agent Toolkit](https://github.com/stripe/agent-toolkit) so agents (yours and your users') can transact.
- **Lemon Squeezy** if you'd rather not touch global sales tax — they are a Merchant of Record.
- **Auth + billing unified:** [Clerk](https://clerk.com) has built-in billing if you don't want to wire Supabase + Stripe webhooks yourself.

Ship a **pricing page** before you ship a marketing page. It clarifies the product.

### 4. Ship (day 14)

- Deploy to Vercel, custom domain via Cloudflare.
- Wire Sentry + PostHog on the first deploy, not after launch.
- Set up a status page (BetterStack free tier).
- Add a 3-line `SECURITY.md` and a real privacy policy (Claude can draft from your data-handling facts; a lawyer reviews at Series A).

### 5. Observe and iterate

- **Errors:** Sentry. Alert to Slack/Discord, not email.
- **Product analytics:** PostHog. Define 3 north-star events *before* launch (e.g. `signed_up`, `activated`, `paid`). Don't add more until these move.
- **Session replay:** PostHog, built in. Watch the first 20 real sessions personally — no dashboard replaces this.
- **Uptime:** BetterStack.

## Agentic workflow patterns

These patterns matter more than the tool list — they are what makes this stack *agentic* rather than "AI-assisted."

- **One repo, one agent.** Claude Code sees the whole tree. Don't fragment context across browser tabs and half-finished chats.
- **Specs-as-prompts.** Write desired behavior in `specs/<feature>.md`, then have the agent implement it. Diffs stay reviewable, and specs become your real documentation.
- **MCP servers for everything external.** Stripe, Supabase, GitHub, PostHog — connect them as MCP servers so the agent can *act* on real infrastructure, not just generate code that targets it.
- **Tests the agent writes and runs.** The reason you can afford a real test suite now is that an agent is writing and maintaining it. Don't skip tests because "it's fast to prototype" — the speed is exactly why you shouldn't.
- **Shared Zod schemas.** One schema validates HTTP payloads, DB rows, and LLM tool calls. Fewer places to drift.

## What this stack deliberately avoids

- **Kubernetes, Docker Compose, microservices.** You are one person. One Next.js app on Vercel.
- **Rolling your own auth.** Supabase or Clerk. Never.
- **Self-hosting anything** until you have revenue. Managed services are cheaper than your time.
- **More than one LLM provider** at launch. Add a router when you have a specific reason, not "in case."
- **Server frameworks you like but agents don't know well.** Every unusual choice taxes your coding agent.
- **A native mobile app** before the web app has users. React Native later if warranted.

## When to graduate from this stack

- You cross ~$10k MRR → consider dedicated infra, a real data warehouse, and adding a Sales substack.
- You hit Vercel or Supabase limits → usually a good problem; migrate the hottest piece, keep the rest.
- You hire engineers → revisit tools that assumed a solo workflow (particularly the coding agent setup and MCP servers).
- You add a second product surface → split the repo only when the agent actually struggles with the monorepo, not before.
