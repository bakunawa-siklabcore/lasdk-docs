# Boundaries and governance

Proof-before-Done answers "is it done?" This page is about the other half: **what each agent is allowed to do while
getting there** — and why those boundaries hold even when an agent is confidently wrong.

## Roles have powers, and the powers are enforced
Every stage runs under a role with a defined boundary, not on trust:

- **read-only** roles (like Signal) read the workspace and produce their reply — no writes.
- **document** roles (Contract, Architecture, Audit) produce exactly one artifact — no code.
- the **worker** is the *only* role that can write code and run builds and tests.
- the **critic** can run tests, but **cannot change the code it's reviewing** — an independent review that could
  quietly "fix" the thing it's grading wouldn't be independent.

These are local boundaries LASDK enforces around each role — not an operating-system sandbox, and LASDK is explicit
about that distinction.

## The builder can't grade itself
LASDK refuses to call work "Done" when the agent that closes it is the same agent that built it. Independence isn't
a promise in a prompt — it's a condition of the verdict. (Running the critic on a *different model* than the builder
is good practice and easy to configure, too.)

## Decisions the requirements leave open go to a person
If the groundwork turns up an unanswered question — a contradiction, an unconfirmed assumption, a default nobody
authorized — LASDK stops and waits for a **named human** to answer it. An answer with nobody's name against it
doesn't count. The agent is not allowed to quietly pick a sensible default and tell you about it afterward.

Some findings are **human-only, always**: anything irreversible, externally visible, a risk taken on your behalf, or
an escape from the agreed boundary. On those, LASDK raises it to you with options and stops — no autonomy setting
overrides that floor.

## It learns without silently changing itself
LASDK can study real runs and *suggest* improvements — but it **applies nothing on its own**. A named person
applies each suggestion, reversibly. Nothing about how LASDK governs your work changes without a human's hand on it.

## Where the boundaries stop (stated plainly)
- The role boundaries are **local**, not an operating-system sandbox.
- LASDK is **not** a hardened security boundary against a hostile program running as your own user.
- The governance is **local to your machine** — not a central, multi-tenant policy server.

The product ships a full, honest **Known Limitations** document — read it before you rely on LASDK heavily.
