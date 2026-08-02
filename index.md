# LASDK — ship what your AI builds, with proof

**Your AI writes the code. LASDK makes sure it's actually done.**

AI coding agents are fast, and they'll happily tell you a task is "complete." A green checkmark from an agent is a
*claim*, not proof. LASDK is the layer that turns AI-built software into **delivery you can trust** — it drives your
AI through a real SDLC, has an independent AI critic review the work, gathers **real evidence**, and **refuses to
call it Done** until the evidence backs the claim.

> **A completed workflow is not completed work.** LASDK is proof-before-Done for the AI-SDLC.

## Why it exists
Point an AI at a ticket and you get output. What you *don't* get is a guarantee it meets the requirement, that the
build was reviewed by something other than the thing that wrote it, or that anyone can audit *why* it was accepted.
LASDK adds exactly that, without slowing your AI down:

- **AI-first delivery** — the AI does contract → architecture → implementation → review. LASDK orchestrates it.
- **Independent AI critic** — a separate agent (ideally a different model) reviews the build. No self-review.
- **Real evidence** — tests run, browsers render, checks execute. Claims are backed by artifacts, not vibes.
- **Earned Done** — `ARTIFACT_READY`, `REFUSE_DONE`, or `NEEDS_HUMAN`, decided from the evidence — never
  self-stamped.
- **Local-first** — runs on your machine, uses *your* AI coding CLI, and doesn't phone home.

## Start here
| I want to… | Go to |
|---|---|
| Understand the idea | [What is LASDK](concepts/what-is-lasdk.md) · [Proof-before-Done](concepts/proof-before-done.md) · [The SDLC flow](concepts/the-sdlc-flow.md) |
| Install and run my first build | [Quickstart](guides/quickstart.md) |
| Use my own AI (which model builds vs reviews) | [Bring your own AI](guides/bring-your-own-ai.md) |
| Run it on my existing project | [Using LASDK on your repo](guides/using-on-another-repo.md) |
| Run richer / parallel pipelines | [Running workflows](guides/running-workflows.md) |
| Ship a real UI, not a generic template | [UI Delivery Assurance](guides/ui-delivery.md) |
| Fit it to my team's process | [Your SDLC pack](guides/your-sdlc-pack.md) |
| Fix a problem | [Troubleshooting](guides/troubleshooting.md) |
| Learn it properly | [Training path](training/README.md) |
| Just the commands | [Cheatsheet](cheatsheet.md) |

## Editions
LASDK sells two paid tiers: **Pro** and **Team**. There is no Business or Enterprise tier — if you read about one
here previously, it did not exist.

**Community (free, no licence needed)** — `lasdk assess` and `lasdk certify`, the two judgement commands, plus
diagnostics (`lasdk doctor`, `--help`, `version`, provider preflight), evidence verification, recovery and export.
You can check any run's evidence and gate your own repository without paying.

**Pro** — the full governed SDLC: Signal → Contract → Architecture → Implementation → Critic → Audit, earned Done,
signed evidence, all production roles, commercial use, two activated devices. Bring your own model; no token
markup.

**Team** — everything in Pro plus an organization policy authority: signed, versioned SDLC profiles with a floor
individuals cannot weaken, hosted independently-verifiable acceptance records, a CI/PR acceptance gate, and
named-seat management. Starts at one seat.

Reading a verdict is free; producing the governed work it judges is not. Current pricing is on
[the pricing page](https://lasdk.siklabcore.com/#pricing) — this page deliberately does not repeat the numbers,
because a price in two places is a price that goes stale in one of them.
