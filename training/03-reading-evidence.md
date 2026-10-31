# Module 3 — Reading evidence

**Idea (2 min).** LASDK's verdicts aren't opinions — they're read off **evidence**. Learn to read the evidence and
the three verdicts, and you can trust (or challenge) any AI's "done."

**The three verdicts.**
- `ARTIFACT_READY` — the evidence backs the claim. Admissible (not "perfect", not "production-approved").
- `REFUSE_DONE` — a required obligation is unmet, or evidence is missing/contradicted.
- `NEEDS_HUMAN` — can't decide with confidence; a human should look.

**Do it (5 min).** Point the assessor at a run — one of your own, or output from any other AI workflow:
```bash
lasdk assess <run-dir>
```
Read what it reports: which obligations were covered, whether the review was independent (builder ≠ author), which
claims had a **witness** (a test that ran, a page that rendered), and which didn't.

**The rule to internalize.** *Absence is never a pass.* A test *file* is not a test *run*. A screenshot is not a
render. If a claim needs a witness and none exists, LASDK refuses or asks for a human — it never assumes.

**Check yourself.**
- What's the difference between a test file existing and a test having run? *(Only the second is evidence.)*
- Why is `ARTIFACT_READY` deliberately *not* "production-approved"? *(It means admissible on the evidence — a
  reviewer can trust the claim; shipping is still your call.)*

**Next:** Module 4 — [The independent critic](04-independent-critic.md). See also **[Proof-before-Done](../concepts/proof-before-done.md)**.
