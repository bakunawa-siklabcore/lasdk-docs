---
---
# Evidence you can verify

Proof-before-Done produces a verdict. But a verdict is only as trustworthy as the evidence under it — so LASDK lets
you **check that evidence yourself**, rather than taking the machine's word for it.

## From a recorded run to a verifiable bundle
Every run records its evidence as it goes. When a run finishes, you can export it into a self-contained bundle —
a complete, redacted record of what happened, with host paths removed and secret-class files left out by design.

That bundle can be **cryptographically signed**, and anyone can verify it with one command:

```bash
lasdk evidence:verify <bundle>
```

Verification confirms the bundle is intact and tells you, honestly, which of three things is true:

| Verdict | Meaning |
|---|---|
| **`SIGNED_VALID`** | The bundle is unmodified **and** signed by a key you trust. |
| **`SIGNED_UNTRUSTED_KEY`** | The bundle is unmodified, but the signer isn't one you've anchored as trusted. |
| **`SIGNED_INVALID`** | The bundle doesn't hold up — treat it as untrusted. |

The whole bundle is checked, not just a headline file — so a verified `SIGNED_VALID` means the evidence you're
looking at is the evidence the run actually produced.

## Why this matters
You can hand a signed bundle to a teammate, a reviewer, or a CI job and say **"verify this yourself."** They don't
have to trust your screen, your word, or even your machine — they run one command and the math answers.

## What a signature does — and does not — prove
LASDK is deliberately honest about the limits of its guarantee. A valid signature proves that the holder of **that
key** signed an **unmodified** bundle. It does **not**, by itself, establish *who* that key belongs to, *when* they
signed, or how the key is kept safe — those come from your organization's own controls, not from LASDK. And the
bundle is a record of the delivery evidence, not a copy of your repository.

That honesty is the point: LASDK gives you something you can independently verify, and tells you exactly where your
trust still has to come from somewhere else.

> A green checkmark asks you to trust the agent. A verifiable bundle asks you to trust the math — and is honest
> about the rest.
