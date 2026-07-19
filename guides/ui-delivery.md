# Guide: ship a real UI, not a generic template

AI is great at producing UI that *looks* finished. The failure mode: it's functional and polished but ships a
conventional template — the exact thing you told it to avoid — and nothing catches it because the tests pass. LASDK
**UI Delivery Assurance** treats visual and experiential intent as a real delivery obligation, so the AI's UI is
proven against what you actually asked for.

## What it does
When a build is UI work, LASDK routes it through a UI-aware flow and holds it to real evidence:

1. **UI intent contract** — what the interface must be and must *not* be (e.g. "not a generic luxury template"),
   stated as checkable intent.
2. **Real multi-viewport evidence** — the page is rendered in a real browser at desktop / laptop / tablet / mobile
   (~390px), capturing console errors, overflow, and screenshots. Not a pasted image — an actual render.
3. **Accessibility oracle** — machine checks that `prefers-reduced-motion` is honored and that controls are
   keyboard-reachable with a visible focus indicator.
4. **Independent visual critic** — a separate AI reviews the rendered result against the intent contract and can
   **REFUSE_DONE** on unmet visual intent — not just on broken code.

## Run it
UI work is detected and routed automatically from a normal build:
```bash
lasdk build "landing page for a jewelry brand — modern, NOT a conventional luxury template"
```
Or gather the browser evidence directly on any page:
```bash
lasdk verify-web --file dist/index.html --viewports --screenshot --a11y
```

## The verdicts you'll see
- **`ARTIFACT_READY`** — renders cleanly across viewports, honors the intent, critic approves.
- **`REFUSE_DONE`** — a generic-template collapse, a broken breakpoint, or the critic finds the intent unmet.
- **`NEEDS_HUMAN`** — the browser tooling wasn't available to verify (door-first: absence isn't a pass).

## Honest scope
The a11y oracle machine-checks **reduced-motion and keyboard** today; contrast, ARIA, labels, and JS-driven
parallax are declared obligations the critic/human check — it is **not** a full WCAG/axe-core audit. The
anti-template judgment is the critic's, reinforced by declared content checks. LASDK tells you what it proved and
what it didn't — it never claims more than the evidence supports.
