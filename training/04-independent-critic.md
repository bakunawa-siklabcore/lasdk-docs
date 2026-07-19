# Module 4 — The independent critic

**Idea (2 min).** The thing that wrote the code can't be the only thing that judges it. LASDK enforces **builder ≠
verifier** — a separate agent reviews the work. Make that agent a *different model* and the review becomes genuinely
independent.

**Do it (5 min).** Configure who reviews:
```bash
lasdk provider          # assign worker and critic to providers
```
Set the **critic to a different model than the worker** (e.g. worker = Claude, critic = Codex). Run a build and read
the critic's review — notice it argues *against* the contract, not "looks good".

**Why it works.** A model reviewing another model's output doesn't share its blind spots. It re-derives the verdict
from the evidence rather than trusting the builder's framing. That's what stops an AI from grading its own homework —
and it's why a same-agent "review" doesn't discharge the gate.

**Deeper: review swarms.** A critic step can fan out into several **lenses** — e.g. correctness, security,
performance — each a separate reviewer that must agree. More independent perspectives, less chance a real problem
slips through.

**Check yourself.**
- Why isn't "the worker reviewed its own code" acceptable? *(No independence — same blind spots, self-justification.)*
- What does making the critic a *different model* add on top of it being a different agent? *(It removes shared
  model blind spots — genuinely independent judgment.)*

**Next:** Module 5 — [UI Delivery Assurance](05-ui-delivery.md). See also **[Bring your own AI](../guides/bring-your-own-ai.md)**.
