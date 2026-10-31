# Guide: use LASDK on your existing project

LASDK governs delivery **into** your project without living inside it. Your repo is the **target**; LASDK is the
harness. Nothing about your codebase has to change to start.

## The boundary
- **LASDK** — the installed `lasdk` binary + its data. Where the governance lives.
- **Your project (the target)** — the repo you're delivering into. LASDK reads it for grounding and writes only
  what you allow.

Your AI builds against a snapshot of the real files, but by default a run writes into its **own** run directory —
your working tree isn't touched until you choose to apply the result. That's the safety model: propose + prove
first, apply on your say-so.

## Point a build at your repo
From inside your project:
```bash
cd ~/code/my-app
lasdk build "add rate-limiting to the login endpoint"
```
LASDK reads your code for context (grounding), the worker builds against it, the critic reviews, evidence runs.

## Ground the AI in the right files
For a focused change, tell LASDK which files matter so the AI isn't guessing:
- LASDK collects a bounded **target context** (capped by size/count, so it stays fast and relevant).
- The contract + architecture pin the **file boundary** — the worker can't sprawl outside it, and a stray change
  outside the boundary is flagged.

## Artifact-only vs. applied
- **Artifact-only** (default for safety) — the AI runs in a sandbox; LASDK applies only the allow-listed outputs
  afterward. The provider never gets write access to your target.
- You review the produced artifact/diff and apply it yourself. LASDK does **not** push to main or auto-merge.

## Assess work that didn't come from LASDK
Already have a change an agent made elsewhere? Judge it on the evidence:
```bash
lasdk assess <run-dir>
```
Proof-before-Done works over any harness — not just LASDK's own builds.

Next: **[Running workflows](running-workflows.md)** · **[Your SDLC pack](your-sdlc-pack.md)**.
