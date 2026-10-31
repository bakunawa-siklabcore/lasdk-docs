# Module 7 — Your SDLC pack

**Idea (2 min).** LASDK ships generic rails. Your team has its own process, roles, and standards. The **SDLC pack**
fits LASDK to *your* SDLC — so a governed AI build reflects how your team actually ships, not a default.

**Do it (5 min).**
```bash
lasdk sdlc init        # create a pack (interview-style; can be AI-assisted)
lasdk sdlc show        # review it
lasdk sdlc validate    # confirm it's well-formed
lasdk sdlc sync        # apply it so builds use it
```

**What a pack carries.**
- **Roles** — your role names/families and who does what.
- **Providers** — which AI runs which role.
- **Workflow** — your default flow + custom steps.
- **Team instructions** — your standards, conventions, and definition-of-done, injected into every role's prompt so
  the AI applies them without you re-stating them each time.

**Why it matters.** The pack is the "bring your own SDLC" hook. Without it the AI uses defaults; with it, the AI
inherits your contracts and guardrails. It's config, not code — keep it in your repo, versioned and shared.

**Check yourself.**
- Where do you put standards you'd otherwise repeat in every prompt? *(Team instructions in the pack — they travel
  into every role automatically.)*
- Is a pack code or config, and where should it live? *(Config — in your project repo, versioned.)*

**Next:** Module 8 — [Team delivery](08-team-delivery.md). See also **[Your SDLC pack guide](../guides/your-sdlc-pack.md)**.
