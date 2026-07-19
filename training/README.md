# LASDK Training

A structured path from "I have an AI that writes code" to "my AI ships delivery I can trust." Each module is short,
hands-on, and AI-first — you drive your own coding agent through LASDK the whole way.

## Path
| # | Module | You'll be able to… |
|---|---|---|
| 1 | **Foundations** (below) | Explain proof-before-Done; run `doctor`; open the agent |
| 2 | [Your first governed build](02-first-build.md) | Run `lasdk build`, read the SDLC stages + the earned-Done verdict |
| 3 | [Reading evidence](03-reading-evidence.md) | Interpret `ARTIFACT_READY` / `REFUSE_DONE` / `NEEDS_HUMAN`; use `lasdk assess` |
| 4 | [The independent critic](04-independent-critic.md) | Configure a *different* model as the critic; why builder ≠ verifier |
| 5 | [UI Delivery Assurance](05-ui-delivery.md) | Make the AI prove a real interface across viewports + a11y |
| 6 | [Workflows & parallelism](06-workflows.md) | `run --list` / `--plan`; when the AI fans out safely |
| 7 | [Your SDLC pack](07-sdlc-pack.md) | `lasdk sdlc` — fit LASDK to *your* process, tools, and roles |
| 8 | [Team delivery](08-team-delivery.md) | Seats, roles, auditing runs across a team |

---

## Module 1 — Foundations

**Idea (2 min).** Your AI is the builder. On its own, "done" is a *claim*. LASDK adds proof: an independent AI
critic, real evidence (tests that ran, pages that rendered), and an earned-Done verdict. That's the whole product in
one sentence — everything else is how.

**The mental model.**
```
Your coding agent   → builds
An independent agent → reviews (never self-review)
Real evidence        → tests ran, pages rendered, checks executed
Earned Done          → ARTIFACT_READY only when evidence proves it
```

**Do it (5 min).**
1. `lasdk doctor` — confirm your AI coding CLI is detected and your setup is green.
2. `lasdk` — open the agent, ask it "what can you do?"
3. Read [Proof-before-Done](../concepts/proof-before-done.md) and note the three verdicts.

**Check yourself.**
- Why can't the builder be the only judge of its own work? *(Builder ≠ verifier — an independent critic is
  required.)*
- What does `ARTIFACT_READY` mean — and what does it deliberately *not* mean? *(Admissible on the evidence; not
  "production-approved" or "beautiful".)*
- What happens when a claim needs a witness and none exists? *(No pass — `REFUSE_DONE` or `NEEDS_HUMAN`. Absence is
  never a pass.)*

**Next:** Module 2 — Your first governed build. (See the [Quickstart](../guides/quickstart.md) to run it now.)

---

> Modules 2–8 are outlined and will be filled in next. Want a specific one prioritized? It's a quick add.
