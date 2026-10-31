# Module 8 — Team delivery

**Idea (2 min).** Everything so far works solo. On a team, the same proof-before-Done loop scales — seats, roles,
and an auditable record of *why* each result was accepted.

**Do it (5 min).**
```bash
lasdk edition          # your edition + entitlements
lasdk team             # team + seats (paid tiers)
lasdk runs             # every past run
lasdk audit <run-id>   # the evidence chain for a run
```
Claim a license, add teammates by email, and each governed build leaves an audit trail anyone on the team can
inspect.

**What scales well.**
- **Roles** — different teammates (and their AIs) own different roles; the builder ≠ verifier separation holds
  across people, not just agents.
- **Auditability** — `lasdk audit` + the run record show the contract, the review, and the evidence behind every
  accepted result. No "trust me, it's done."
- **Your pack** — shared in the repo, so the whole team's AI builds follow the same contracts and standards.

**The team payoff.** When an AI-built change lands, anyone can answer "was this actually reviewed, tested, and
within scope?" from the evidence — not from whoever ran it. That's the difference between AI velocity and AI you can
put your name on.

**Check yourself.**
- How does a teammate verify a change they didn't build? *(`lasdk audit <run-id>` — the contract, review, and
  evidence are recorded.)*
- What keeps everyone's AI builds consistent? *(The shared SDLC pack in the repo.)*

**You've finished the path.** Back to the [Training index](README.md) · the [Cheatsheet](../cheatsheet.md).
