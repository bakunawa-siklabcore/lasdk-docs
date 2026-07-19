# Quickstart — your first governed AI build

Goal: install LASDK, point it at your AI, and get your first **proof-before-Done** build in about 10 minutes.

> **Requirements.** LASDK drives your own AI — it doesn't include a model. You'll need: (1) an active **LLM
> subscription or API access** (e.g. Claude or OpenAI/Codex), and (2) a supported **AI coding CLI installed**
> (Claude Code, Codex, …). Everything runs locally with your CLI's own login — `lasdk doctor` checks both.

## 1. Install
Run the installer from the LASDK kit you downloaded:
```bash
./install.sh
```
It installs the `lasdk` binary + its data (`lasdk-home`) and prints the `lasdk` command location. LASDK is a single
self-contained binary — no Node, no dependencies to manage.

## 2. Check your setup
```bash
lasdk doctor
```
`doctor` verifies you're ready: an **AI coding CLI** on your PATH (Claude Code, Codex, or another supported agent),
your license (Community is free), and a workspace. It **guides any gaps** — follow what it says.

> LASDK doesn't ship an AI. It drives *your* coding agent. `doctor` tells you which ones it found.

## 3. Meet the agent
Run `lasdk` with no arguments to open the conversational agent (works from any directory):
```bash
lasdk
```
Ask it what it can do, or describe a task. Prefer a menu? `lasdk studio`.

## 4. Your first governed build
From your project, describe a small, real task:
```bash
lasdk build "add a slugify() helper with tests"
```
Watch the AI-first SDLC run: **Signal → Contract → Architecture → Implementation → Critic → Audit.** The builder
agent writes the code; an **independent critic agent** reviews it; tests run as **evidence**; and LASDK decides
**earned Done** — you'll see `ARTIFACT_READY`, or `REFUSE_DONE` with the reason.

Nothing is force-pushed or auto-merged — you get a reviewed artifact you choose to ship.

## 5. Judge any AI's work
Already have output from another agent or workflow? Assess it:
```bash
lasdk assess <run-dir>
```
LASDK reads the evidence and returns `ARTIFACT_READY` / `REFUSE_DONE` / `NEEDS_HUMAN` — proof-before-Done over
whatever produced the work.

## Next
- [UI Delivery Assurance](ui-delivery.md) — make the AI ship a *real* interface, not a generic template.
- [Cheatsheet](../cheatsheet.md) — every command on one page.
- [Training path](../training/README.md) — learn it properly.
