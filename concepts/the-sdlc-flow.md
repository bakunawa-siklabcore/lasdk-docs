---
---
# The SDLC flow — how a governed AI build runs

When you run `lasdk build`, your AI doesn't just "write code." LASDK drives it through a real software-delivery
lifecycle, one stage at a time, with each stage's output becoming evidence. Here's what actually happens.

```
Signal → Groundwork → Contract → Architecture → Implementation → Critic → bounded repair → Audit
```

| Stage | Who acts | What it produces |
|---|---|---|
| **Signal** | LASDK | Classifies the request — is this a code ticket, a UI build, a fix? Routes it. |
| **Groundwork** | AI (contract role) | The situation, the success criteria, and — critically — the **open decisions** the requirements leave unanswered. |
| **Contract** | AI (contract role) | *What "done" means* — the requirements, boundaries, and acceptance the work is judged against. |
| **Architecture** | AI (architecture role) | The shape of the change — components, interfaces, the file boundary the build must stay inside. |
| **Implementation** | AI (worker role) | The actual code, written **inside** the contracted boundary. The only stage allowed to write. |
| **Critic** | AI (critic role — *a different agent*) | An independent review of the implementation against the contract. No self-review, and the critic is physically prevented from editing the code it reviews. |
| **bounded repair** | AI (worker role) | One capped round to fix what the critic found — it can't spin forever. |
| **Audit** | LASDK | Summarizes the run + its evidence into an auditable record. |

## Why the order matters
Each stage constrains the next. **Groundwork** surfaces every decision the requirements leave open *before* code
exists — and LASDK won't build past a decision that needs a person until a **named human** answers it (an answer
with nobody's name against it doesn't count). The **contract** is written before any code, so "done" is defined up
front, not rationalized afterward. The **architecture** pins the boundary, so the worker can't quietly sprawl into
unrelated files. The **critic** judges against the contract, so review isn't a vibe check — it's "does this meet
what we agreed?" And the whole chain is recorded, so anyone can see *why* the result was accepted or refused.

## A risk scan that can fail the run
Before the result stands, LASDK runs a **static risk scan** over the code the worker actually delivered, looking for
a floor of well-known defect patterns — things like hardcoded credentials, unsafe database queries, and disabled
transport security. A finding **blocks the run**, and the code being scanned can't wave itself through. It's a
floor, not a full security review, and LASDK says so: it only flags what it checks for, and "nothing examined" is
never recorded as "nothing wrong."

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
