# Guide: running workflows (and going parallel)

`lasdk build` runs the standard single-ticket flow. **Workflows** let you run richer, multi-step pipelines — and
where the work is provably independent, LASDK runs your AI agents **concurrently** instead of one-at-a-time.

## See what's available
```bash
lasdk run --list
```
Workflows are flagged by how they parallelize:
- **⚡ inter-step** — independent steps run at the same time (e.g. two disjoint build tracks, or several read-only
  verifiers).
- **🐝 swarm** — a single step fans out into multiple AI reviewers (lenses) that vote.

## Preview before you spend
See the execution plan — which steps run, in what waves, concurrently or serial — **without running anything, no
model calls, no writes**:
```bash
lasdk run <workflow> --plan
```

## Run it
```bash
lasdk run <workflow> --stream          # live progress as each step runs
lasdk run <workflow> --json            # machine-readable result
```
A run writes into its own run directory (`runs/<id>/`) — your project isn't mutated unless you explicitly deliver
the output. You get a reviewed artifact + evidence, same as a build.

## When does it actually go parallel?
Concurrency is **earned, not faked.** LASDK runs steps together only when the dependency graph proves it's safe:
- **read-only** steps (reviews, verifications) fan out by default;
- **writers** run concurrently only when their file boundaries are provably disjoint (e.g. `backend/**` ∥
  `frontend/**`);
- a single cohesive build stays serial — there's nothing to overlap, and LASDK won't pretend otherwise.

So a linear ticket is honestly linear; a decomposable one fans out. Either way you see the real plan with `--plan`.

## Resuming a run
A long run can be continued from its checkpoint:
```bash
lasdk run:resume --run=<id-workflowId> --target=<repo>
```
It reloads completed steps and continues from where it stopped, grounding against your real files via `--target`.

Next: **[The SDLC flow](../concepts/the-sdlc-flow.md)** · **[Bring your own AI](bring-your-own-ai.md)**.
