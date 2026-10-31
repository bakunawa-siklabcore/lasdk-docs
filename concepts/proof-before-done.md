# Proof-before-Done

The single idea LASDK is built on: **a completion claim is not completion.** When an AI agent says "done," LASDK
treats that as a hypothesis to be proven — and it either produces the proof or refuses the claim.

## The three verdicts
Every LASDK build (and any run you point `lasdk assess` at) resolves to one of three honest outcomes:

| Verdict | Meaning |
|---|---|
| **`ARTIFACT_READY`** | The evidence backs the claim. The work is admissible — reviewed, tested, boundary-respected. |
| **`REFUSE_DONE`** | A required obligation is unmet, or the evidence is missing/contradicted. Not done. |
| **`NEEDS_HUMAN`** | The machine can't decide with confidence — a human should look (e.g. tooling wasn't available to verify). |

`ARTIFACT_READY` means *admissible*, not "production-approved" and not "beautiful" — it means the claim is backed by
evidence a reviewer can trust. That honesty is deliberate.

## What counts as evidence
Not a filename. Not the builder's assertion. LASDK looks for **witnesses** — things that actually happened:
- Tests that **ran** (with counts), not just test files that exist.
- A page that **rendered** in a real browser (across viewports), not a screenshot someone pasted.
- Security/accessibility checks that **executed**, with results.
- A review written by an agent that is **not** the builder.

If a claim needs a witness and none exists, LASDK doesn't guess — it refuses, or asks for a human. **Absence is never
a pass.**

## Why "independent" matters
LASDK enforces **builder ≠ verifier**. The critic is a separate agent, and its review is retained as evidence. A
review "written" by the same agent that built the code — or one that just echoes "looks good" — doesn't discharge
the gate. This is what stops an AI from grading its own homework.

## It works over *any* harness
`lasdk assess <run-dir>` judges a completion claim from **any** AI workflow's output — not just LASDK's own builds.
Point it at what another agent produced and it tells you, on the evidence, whether the "done" is real.

> A green checkmark is a claim. Proof-before-Done is the difference between a claim and delivery.
