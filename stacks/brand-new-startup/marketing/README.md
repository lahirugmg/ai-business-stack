# Marketing substack

Everything needed to get a self-serve product in front of the right people and convert them, run by a solo founder with agents doing most of the work.

**Last updated:** 2026-04-13

## TL;DR picks

| Job | Pick | Why |
|---|---|---|
| Naming + brand voice | [Claude](https://claude.ai) | Better at hard constraints than dedicated naming tools |
| Logo | [Looka](https://looka.com) or Claude-generated SVG | Good enough pre-PMF; redo at Series A |
| Landing page (in-repo) | [v0](https://v0.dev) | Outputs React + Tailwind you can commit |
| Landing page (no-code) | [Framer](https://framer.com) | If you want to iterate outside the codebase |
| Copywriting | Claude | Default for long-form and conversion copy |
| Blog / docs | MDX in your Next.js repo | Own your content, ship with the product |
| SEO research | [Ahrefs](https://ahrefs.com) | Paid but worth it once |
| Trend-spotting | [Exploding Topics](https://explodingtopics.com) | For pre-keyword signals |
| Programmatic SEO | Claude + your DB | Generate pages from structured data |
| Transactional email | [Resend](https://resend.com) + [React Email](https://react.email) | Dev-friendly, renders from your repo |
| Lifecycle email | [Loops](https://loops.so) | Built for SaaS, integrates with PostHog |
| Newsletter | [Beehiiv](https://beehiiv.com) | Only if newsletter is a primary channel |
| Social — Twitter/X | [Typefully](https://typefully.com) | Scheduling + analytics + AI drafts |
| Video — short-form | [Opus Clip](https://opus.pro) | Long-form → shorts pipeline |
| Voiceover / dubbing | [ElevenLabs](https://elevenlabs.io) | Best quality, multilingual |
| Ad creative (if running paid) | [AdCreative.ai](https://adcreative.ai) | Variation generation for Meta/Google |
| Web analytics | [Plausible](https://plausible.io) | Privacy-friendly, simple |
| Product analytics | [PostHog](https://posthog.com) | Shared with the Tech substack |

## Phases

### 1. Brand (day 1)

Fast and reversible. Do not over-invest pre-PMF.

- **Name:** Claude with hard constraints — .com available, ≤12 characters, pronounceable, no trademark conflicts in your category. Verify at [Namecheap](https://namecheap.com) and the USPTO TESS search.
- **Logo:** Looka (one-time ~$20) or have Claude output an SVG. Plan to redo it once you have revenue.
- **Voice:** write a one-page `BRAND.md` — tone, words you use, words you don't, example sentences. Feed it into every copy prompt. This single file is the highest-leverage brand asset you'll make.

### 2. Landing page (days 2–4)

Goal: one page that explains the product and captures either signups or payments.

- **Copy:** Claude, using `BRAND.md` + a proven framework (Problem → Solution → Proof → CTA). Write the copy *before* the design.
- **Design:** v0 if it lives in your repo; Framer if you want non-technical iteration.
- **Must-haves:** hero, 3 benefit blocks, social proof placeholder, FAQ, single clear CTA.
- **Optional:** comparison table if there are competitors worth naming.

Ship the pricing page at the same time — it's part of the landing page experience, not a separate project.

### 3. Content engine (ongoing, starts day 5)

Pick **one** primary channel and go deep. Solo founders lose by trying to be everywhere.

| ICP | Primary channel | Tooling |
|---|---|---|
| Developers | Twitter/X + technical blog | Typefully, MDX blog, Claude for drafts |
| SMB / prosumer | YouTube + SEO blog | Descript, Opus Clip, Claude, Ahrefs |
| Consumer | TikTok / Instagram Reels | CapCut AI, Opus Clip, ElevenLabs |
| Enterprise / ops | LinkedIn + long-form | Claude, scheduling in Typefully alt |

**Cadence:** minimum 3 posts/week on the primary channel. Claude drafts, you edit for voice, ship. The edit pass is non-negotiable — raw model output reads like raw model output.

### 4. SEO foundations (days 5–10)

Most bootstrappers skip this and regret it a quarter later.

- **Technical:** sitemap, robots.txt, OG tags, structured data. Next.js handles most of it — verify with [ahrefs.com/webmaster-tools](https://ahrefs.com/webmaster-tools).
- **Keyword list:** 20 long-tail terms with real intent and weak competition. Ahrefs free tier or Exploding Topics is enough to start.
- **Programmatic SEO:** if your product has structured data (directories, comparisons, templates, calculators), generate pages from the DB with Claude. This is the single highest-leverage marketing tactic available to bootstrappers in the agentic era — nothing else scales as cheaply.
- **Backlinks:** guest posts, HN, niche newsletters, Product Hunt. Never pay for links.

### 5. Email (days 10–14)

- **Transactional** (receipts, password resets, notifications): Resend + React Email. The emails live in your repo.
- **Lifecycle** (welcome, onboarding, trial-end, winback): Loops. Trigger from PostHog events; do not build your own state machine.
- **Broadcast / newsletter:** only if you committed to newsletter as a primary channel. Beehiiv if so. Otherwise, skip entirely.

### 6. Launch (day 14)

- **Product Hunt** — schedule for Tue/Wed at 12:01am PT. Build a hunter list and notify list the week before.
- **Hacker News** — `Show HN` only if you have a live demo and a technical angle. Post Tue–Thu morning US time. Don't ask for upvotes.
- **Niche communities** — subreddits, Discords, Slack groups your ICP actually uses. Give value for 2 weeks before you post about yourself.
- **Personal network** — founder's list, soft launch, a simple "hey, I made this" email.

### 7. Measure

Three numbers, nothing else, until they move:

1. **Visitors** — Plausible or PostHog.
2. **Signups** — PostHog event.
3. **Paying users** — Stripe or Lemon Squeezy dashboard.

Every other metric is a distraction at this stage. Do not build dashboards; read the numbers once a day.

## Agentic workflow patterns

These are what make marketing *feasible* for a solo founder:

- **Content factory.** One long-form piece → Claude repurposes into 5 tweets, 1 LinkedIn post, 1 newsletter, 1 short-form video script. One input, five outputs, you edit each for voice.
- **SEO writing loop.** Claude reads the top-ranking pages for a target keyword, drafts a better one to your `BRAND.md`, you edit, publish, monitor rank weekly, revise.
- **Inbox triage.** An agent drafts replies in your support/sales inbox; you approve. Claude with a Gmail MCP server or [Missive](https://missiveapp.com) + AI.
- **Analytics Q&A.** PostHog's natural-language query replaces most dashboards. Ask questions; don't build charts.
- **Landing page A/B via agent.** Ask Claude to propose 3 hero variants grounded in your `BRAND.md` and your top-performing content; ship via PostHog feature flags.

## What this substack deliberately avoids

- **Paid ads** until organic proves the funnel converts. Paid amplifies the funnel; it does not fix it.
- **Marketing automation suites** (HubSpot, Marketo). Too heavy pre-PMF; you'll outgrow the config before you outgrow the tool.
- **SEO content farms.** One high-quality programmatic template beats 100 generic AI-slop articles and won't get you penalized.
- **Being on every social channel.** Pick one. The second one comes after the first one is working.
- **Custom email designs.** React Email defaults. Agents can generate prettier ones than you'll have time to review anyway.

## When to graduate from this substack

- Organic converts reliably → add paid acquisition, likely AdCreative.ai + Meta Advantage+ or Google's AI-driven campaigns.
- You hire a marketer → revisit tools built around solo workflows (especially Typefully, Loops, and the content factory pattern).
- Content volume justifies a real CMS → you probably still want MDX, but add a preview/staging workflow.
- You need attribution beyond "where did the signup come from" → then, and only then, look at the paid analytics tier.
