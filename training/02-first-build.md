# Module 2 — Your first governed build

**Idea (2 min).** You describe a task; your AI builds it; LASDK drives the whole SDLC and proves the result. One
command starts it — the discipline is automatic.

**Do it (5 min).** From a real project:
```bash
lasdk build "add a slugify() helper with tests"
```
Watch the stages go by: **Signal → Contract → Architecture → Implementation → Critic → Audit**. The worker agent
writes the code; a *different* critic agent reviews it; tests run as evidence; LASDK issues a verdict.

**What you're looking at.**
- The **contract** — what "done" means, written before any code.
- The **implementation** — the worker's code, inside the contracted boundary.
- The **critic's review** — an independent agent's judgment against the contract.
- The **verdict** — `ARTIFACT_READY` (proven) or `REFUSE_DONE` (with the reason).

**Check yourself.**
- What gets written *before* the code, and why? *(The contract — so "done" is defined up front.)*
- Who reviews the worker's code? *(An independent critic agent — never the worker itself.)*
- Did your run pass or refuse? Read the reason either way — that's the evidence talking.

**Next:** Module 3 — [Reading evidence](03-reading-evidence.md). See also **[The SDLC flow](../concepts/the-sdlc-flow.md)**.
