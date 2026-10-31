# Troubleshooting

Start with `lasdk doctor` — it checks your setup and guides most issues. Common ones below.

## "No AI coding CLI found"
LASDK drives your agent; it needs one on your PATH. Install or authenticate a supported coding CLI (e.g. Claude
Code or Codex), then re-run `lasdk doctor`. LASDK uses the agent's own session — you don't paste keys into LASDK.

## The build ran but produced no change / says "mock"
The run used the **mock** provider (no real AI), so nothing was built. Configure a real provider for the role:
```bash
lasdk provider          # assign a real AI to worker/critic
```
Then re-run. If you're driving a workflow directly, make sure the role has a provider assigned — an unassigned role
falls back to mock by design (fail-closed), so you notice instead of getting fake output.

## "REFUSE_DONE" — my build didn't pass
That's the system working. Read the reason it prints — a missing witness (a test that didn't run, a page that
didn't render), an unmet contract obligation, or a critic finding. Fix the gap and re-run, or use the refinement
loop. A refusal means the evidence didn't back the claim — not that LASDK is broken.

## "NEEDS_HUMAN"
The machine couldn't verify with confidence — often because the tool it needed wasn't available (e.g. no browser
for a UI check). Install the missing tool, or review it yourself. Absence of a check is never treated as a pass.

## A long build looks stuck
Long generations are normal — one big file can take minutes. Builds stream a heartbeat so a working run isn't
mistaken for a hang, and there's no default per-call timeout (large work runs to completion). If it's truly stuck,
the process will surface it; a healthy long run just keeps going.

## Resuming a run fails with "requires an explicit --deliverable / --allow-output"
Resume with the output declaration:
```bash
lasdk run:resume --run=<id-workflowId> --target=<repo> --capture-all-outputs
```
New runs carry this automatically; older runs may need the flag. (`--deliverable`/`--allow-output` also work.)

## License / edition questions
```bash
lasdk edition          # see your current edition + entitlements
lasdk doctor           # confirms your license state
```
The Community edition is free and never paywalls the core loop. Drop your license file into your LASDK home to
unlock a paid tier.

Still stuck? Contact support (see the site footer).
