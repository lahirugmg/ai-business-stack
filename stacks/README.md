# Stacks

Each folder here is one opinionated stack targeted at a specific kind of business.

## Available stacks

- [brand-new-startup/](brand-new-startup/) — zero-to-paying-users for self-serve businesses (SaaS, PLG, DTC, creator, light marketplace).

## Anatomy of a stack

```
<stack-name>/
  README.md          overview, target archetype, go-to-market assumptions
  tech/
    README.md        build, ship, monetize
  marketing/
    README.md        brand, traffic, conversion, measurement
  <other-substack>/  sales, ops, support — added when the archetype needs them
    README.md
```

A substack is a self-contained README that covers:

1. **TL;DR picks** — a table of job → tool → one-line reason.
2. **Phases** — what you do in week 1, week 2, ongoing.
3. **Agentic workflow patterns** — the patterns matter more than the tools.
4. **What this substack avoids** — equally important as what it picks.
5. **When to graduate** — signs you've outgrown the stack.
6. **Last updated** — date. If older than ~3 months, verify before trusting.

## Adding a new stack

1. Create `<stack-name>/` with a `README.md` that names the target archetype, business model, and team size.
2. Add substack folders. Start with `tech/` and `marketing/`; add `sales/`, `ops/`, `support/` only when the archetype genuinely needs them.
3. Link the new stack from the root [README.md](../README.md) table.
