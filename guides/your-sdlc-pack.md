# Guide: fit LASDK to your process (the SDLC pack)

LASDK ships generic rails. Your team has its own process, tools, and roles. The **SDLC pack** is how you fit LASDK
to *your* SDLC without editing the core — so the AI works the way your team works.

## What a pack defines
A single, editable pack describes your delivery reality:
- **Roles** — who does what (worker, critic, and your own role names/families).
- **Providers** — which AI runs which role.
- **Workflow** — your default flow and any custom steps.
- **Team instructions** — your conventions, guardrails, and "how we do things here", injected into the AI's prompts.

## Commands
```bash
lasdk sdlc init       # create a pack (interview-style; can be AI-assisted)
lasdk sdlc show       # view the current pack
lasdk sdlc validate   # check it's well-formed before you rely on it
lasdk sdlc sync       # apply it so builds pick it up
```

## Why this matters for AI-first delivery
Without a pack, the AI uses sensible defaults. With one, it inherits **your** contracts, your role separation, and
your conventions — so a governed build reflects how your team actually ships, not a generic template. The pack is
the "bring your own SDLC" hook: LASDK is the rails; your pack is the route.

## Team instructions = your standards, enforced
The `team-instructions` in your pack are the place to put the things you'd otherwise repeat in every prompt — coding
standards, security rules, definition-of-done specifics. They travel into every role's prompt automatically, so the
AI applies them without you re-stating them each time.

## Keep it in your repo
A pack is config, not code — keep it with your project so it's versioned and shared. Creds live once at your team's
`.env` (pulled, never typed into prompts).

Next: **[Bring your own AI](bring-your-own-ai.md)** · **[Using LASDK on your project](using-on-another-repo.md)**.
