---
---
# Guide: bring your own AI

LASDK doesn't ship a model — it drives **your** AI coding agent. This is the AI-first core: you pick which agent
builds, which reviews, and LASDK enforces that they're separate.

## What LASDK drives
Any supported AI coding CLI you already have — for example Claude Code or Codex. `lasdk doctor` tells you which
agents it found on your PATH:
```bash
lasdk doctor
```
If none are found, `doctor` guides you to install or authenticate one. LASDK runs locally and uses the agent's own
session/credentials — it never asks you to paste keys into LASDK, and it doesn't send your code to a LASDK server.

## Assign AI to roles
A governed build has four roles — **contract**, **architecture**, **worker** (builds) and **critic** (reviews).
Two steps, and they are two different commands:

```bash
lasdk provider scan     # find and register the AI CLIs on this machine (also: list · add <id> --command <cli>)
```

`lasdk provider` registers *what LASDK can drive*; it does not decide which one runs which role. That assignment
lives in the chat, where you can see the current mapping and change it:

```
lasdk                   # open the conversational agent
/role                   # show the current mapping, e.g. contract:claude architecture:claude worker:claude critic:codex
/role critic codex      # assign one role  (…and /role critic reset to go back to auto)
/config                 # the same settings as a panel
```

The key principle: **the critic should be a different model than the worker.** An independent model reviewing the
builder's work catches what a self-review can't. LASDK enforces builder ≠ verifier by *agent*; making them different
*models* too makes the review genuinely independent.

> Example: worker = Claude, critic = Codex. The builder writes; a different model adversarially reviews against the
> contract. That separation is the point.

## Speed vs. thoroughness
You can tune which model does which stage — a strong model to plan and review, a faster one to write the bulk of the
code. LASDK records the requested model + reasoning effort per step as evidence, so the run is auditable.

## What it does *not* do
- It doesn't replace your agent's judgment — it structures and checks it.
- It doesn't need a cloud account for the core loop — local-first.
- It doesn't lock you to one vendor — the roles are provider-agnostic; swap models as you like.

Next: **[The SDLC flow](../concepts/the-sdlc-flow.md)** for what each role does, or **[Running workflows](running-workflows.md)**
to fan work out in parallel.
