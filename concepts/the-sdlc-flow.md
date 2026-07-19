# The SDLC flow — how a governed AI build runs

When you run `lasdk build`, your AI doesn't just "write code." LASDK drives it through a real software-delivery
lifecycle, one stage at a time, with each stage's output becoming evidence. Here's what actually happens.

```
Signal → Contract → Architecture → Implementation → Critic → Audit
```

| Stage | Who acts | What it produces |
|---|---|---|
| **Signal** | LASDK | Classifies the request — is this a code ticket, a UI build, a fix? Routes it. |
| **Contract** | AI (contract role) | *What "done" means* — the requirements, boundaries, and acceptance the work is judged against. |
| **Architecture** | AI (architecture role) | The shape of the change — components, interfaces, the file boundary the build must stay inside. |
| **Implementation** | AI (worker role) | The actual code, written **inside** the contracted boundary. |
| **Critic** | AI (critic role — *a different agent*) | An independent review of the implementation against the contract. No self-review. |
| **Audit** | LASDK | Summarizes the run + its evidence into an auditable record. |

## Why the order matters
Each stage constrains the next. The **contract** is written before any code, so "done" is defined up front, not
rationalized afterward. The **architecture** pins the boundary, so the worker can't quietly sprawl into unrelated
files. The **critic** judges against the contract, so review isn't a vibe check — it's "does this meet what we
agreed?" And the whole chain is recorded, so anyone can see *why* the result was accepted or refused.

## The refinement loop
If the critic finds problems, LASDK can send the work back to the worker to fix — a bounded **refinement loop**
(capped, so it can't spin forever). The worker addresses the findings; the critic re-reviews. This is how AI output
gets *iterated to correct*, not just accepted or rejected once.

## Earned Done
Only after the critic is satisfied and the evidence backs the claim does LASDK issue a verdict —
`ARTIFACT_READY`, `REFUSE_DONE`, or `NEEDS_HUMAN`. See **[Proof-before-Done](proof-before-done.md)**.

## It's your AI at every builder stage
Contract, architecture, implementation, and critic are all done by **AI agents you configure** — ideally with a
*different* model as the critic than the builder. LASDK orchestrates the flow; your AI does the thinking. See
**[Bring your own AI](../guides/bring-your-own-ai.md)**.
