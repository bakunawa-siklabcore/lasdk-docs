# What is LASDK?

**LASDK (Local Agentic Software Delivery Kit) is the governance and proof layer for AI-built software.**

You already have an AI that can write code — Claude Code, Codex, or any coding agent. LASDK is what you put
*around* it so that what the AI produces is delivered like real engineering work: contracted, reviewed by an
independent agent, backed by evidence, and only marked Done when it's earned.

## The one-sentence version
> Your AI builds. LASDK drives it through a real SDLC, checks the work with a second AI, gathers real evidence, and
> refuses "Done" until the evidence proves it.

## What the AI does vs what LASDK does
| The AI (your coding agent) | LASDK |
|---|---|
| Understands the request | Turns it into a **contract** (what "done" means) |
| Designs and writes the code | Bounds the work to a **role + file boundary** |
| Produces the implementation | Runs an **independent AI critic** over it (no self-review) |
| Fixes what the critic finds | Runs **real evidence** — tests, browser render, checks |
| Reports its result | Decides **earned Done**: `ARTIFACT_READY` / `REFUSE_DONE` / `NEEDS_HUMAN` |

The AI is the engine. LASDK is the discipline that makes the engine's output trustworthy — without you having to
babysit every step.

## What it is *not*
- Not a replacement for your AI — it **uses** your AI.
- Not a CI service or a deploy tool — it produces reviewable artifacts + evidence; you ship.
- Not a cloud service — it's **local-first**, runs on your machine, verifies its license offline, and doesn't send
  your code anywhere.

## The core idea: builder ≠ verifier
The thing that wrote the code can't be the only thing that judges it. LASDK enforces separation: an **independent
critic agent** (ideally a *different* model than the builder) reviews the work, and Done is decided from **evidence**
— tests that actually ran, a page that actually rendered — not from the builder's say-so. This is the whole point,
and it's why "the AI said it's done" becomes "here's the proof it's done."

Next: **[Proof-before-Done](proof-before-done.md)** — the mechanism that makes "Done" mean something.
