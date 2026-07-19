# Module 5 — UI Delivery Assurance

**Idea (2 min).** AI produces UI that *looks* done. The trap: it's functional and polished but ships a generic
template — the exact thing you said to avoid — and the tests pass, so nothing catches it. LASDK treats visual and
experiential intent as a real delivery obligation, proven against what you asked for.

**Do it (5 min).** Run a UI build with explicit intent:
```bash
lasdk build "landing page for a jewelry brand — modern, NOT a conventional luxury template"
```
Or gather browser evidence on any page directly:
```bash
lasdk verify-web --file dist/index.html --viewports --screenshot --a11y
```

**What gets proven.**
- **Real multi-viewport render** — desktop / laptop / tablet / mobile (~390px), with console errors + overflow
  captured. An actual render, not a pasted screenshot.
- **Accessibility oracle** — reduced-motion honored, controls keyboard-reachable with a visible focus indicator.
- **Independent visual critic** — a separate AI reviews the rendered result against your intent and can
  **REFUSE_DONE** on an unmet look, not just broken code.

**Honest scope.** The a11y oracle machine-checks reduced-motion + keyboard today; contrast, ARIA, and JS-parallax
are declared obligations the critic/human check — it's not a full WCAG audit. LASDK reports what it proved and what
it didn't.

**Check yourself.**
- Why can passing tests still mean a bad UI delivery? *(Tests don't check "is this the *right* interface" — intent
  does.)*
- What makes the visual critic trustworthy? *(It's independent and judges the real render against your declared
  intent.)*

**Next:** Module 6 — [Workflows & parallelism](06-workflows.md). See also **[UI Delivery guide](../guides/ui-delivery.md)**.
