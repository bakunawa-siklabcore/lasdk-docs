# LASDK Cheatsheet

One page. Your AI builds; these commands govern it and prove the result. Run `lasdk help` for the full list.

## Start here
| Command | What it does |
|---|---|
| `lasdk` | Open the conversational AI agent (any directory) |
| `lasdk doctor` | Check setup: AI coding CLI, license, workspace — guides gaps |
| `lasdk setup` / `lasdk onboard` | First-time setup / onboard a workspace |
| `lasdk studio` · `lasdk tui` | Menu interface |

## Build & prove (the core loop)
| Command | What it does |
|---|---|
| `lasdk build "<task>"` | Governed AI build: Signal → Contract → Architecture → Implementation → Critic → Audit |
| `lasdk assess <run-dir>` | Proof-before-Done over ANY run → `ARTIFACT_READY` / `REFUSE_DONE` / `NEEDS_HUMAN` |
| `lasdk assess <run-dir> --obligations=<file>` | Assess against explicit obligations |
| `lasdk review` | Run an independent critic review |
| `lasdk run --list` | List workflows (⚡ parallel, 🐝 swarm) |
| `lasdk run <workflow> --plan` | Preview the execution plan (no run, no writes) |
| `lasdk run <workflow> --stream` | Run a workflow with live progress |

## Verify (real evidence)
| Command | What it does |
|---|---|
| `lasdk verify-web --file <page> --viewports --screenshot` | Real multi-viewport browser render evidence |
| `lasdk verify-web --file <page> --a11y` | Accessibility oracle: reduced-motion + keyboard |
| `lasdk verify-web --file <page> --scroll` | Motion/animation evidence (a still can't fake it) |
| `lasdk owasp:api` · `lasdk owasp:mobile` | Security review passes |

## Configure your AI & workspace
| Command | What it does |
|---|---|
| `lasdk provider` | Configure which AI runs which role (worker, critic, …) |
| `lasdk sdlc` | Your SDLC pack: `init` / `show` / `validate` / `sync` |
| `lasdk roles` / role bundles | What each kind of teammate can do |
| `lasdk edition` · `lasdk team` | License edition + team/seats |

## Track & audit
| Command | What it does |
|---|---|
| `lasdk runs` | List past runs |
| `lasdk audit <run-id>` | Audit a run's evidence chain |
| `lasdk dashboard` | Status dashboard |
| `lasdk next` | Suggest the next task |
| `lasdk ledger` · `lasdk export:evidence` | Task ledger / export the evidence bundle |

## The AI-first model in 4 lines
```
Your AI coding agent   = the builder (writes the code)
An independent AI      = the critic  (reviews it — never self-review)
Real evidence          = tests ran, pages rendered, checks executed
Earned Done            = ARTIFACT_READY only when the evidence proves it
```
