# Module 6 — Workflows & parallelism

**Idea (2 min).** `lasdk build` is one flow. **Workflows** are richer pipelines, and where the work is provably
independent, LASDK runs your AI agents **concurrently** — faster, without faking it.

**Do it (5 min).**
```bash
lasdk run --list                 # ⚡ = inter-step parallel, 🐝 = swarm
lasdk run <workflow> --plan      # preview the wave plan — NO run, no model calls, no writes
lasdk run <workflow> --stream    # run with live progress
```
Read the `--plan` output: which steps run together (a "wave") and which wait. That's the real schedule.

**The honesty rule.** Concurrency is **earned**: read-only steps fan out by default; writers overlap only when their
file boundaries are provably disjoint; a single cohesive build stays serial because there's nothing to overlap.
LASDK won't claim parallelism it can't prove safe.

**Resuming.** A long run continues from its checkpoint:
```bash
lasdk run:resume --run=<id-workflowId> --target=<repo>
```

**Check yourself.**
- What does `--plan` let you do before spending anything? *(See exactly which steps run, and whether they overlap —
  no model calls.)*
- When will two writer steps run at the same time? *(Only when their write boundaries are provably disjoint.)*

**Next:** Module 7 — [Your SDLC pack](07-sdlc-pack.md). See also **[Running workflows](../guides/running-workflows.md)**.
