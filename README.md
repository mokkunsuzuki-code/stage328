# Stage328: QSP Evidence Match Gate

Stage328 adds the core REMEDA trust decision layer:

**AI Claim vs Reproduction Evidence**

This stage does not reproduce vulnerabilities.  
Instead, it determines whether the reproduction evidence can be trusted as evidence.

## What Stage328 Checks

- `same_target`
- `evidence_files_present`
- `sha256_bound`
- `signature_present`

## Decision

The gate returns:

- `accept`
- `pending`
- `reject`

## Why This Matters

Stage328 turns REMEDA from a proof viewer into a trust decision engine.

It answers the important question:

> Does this reproduction evidence actually match the AI claim?

## Safety Model

Stage328 does not include exploit code.  
Stage328 does not reproduce attacks.  
Stage328 only checks evidence binding.

## Private Core Protection

The private REMEDA core is excluded from GitHub.

Ignored private areas:

- `private_core/`
- `core/`
- `internal_engine/`
- `billing/`
- `rate_limit/`
- `secrets/`

## Demo

Run:

```bash
python3 qsp_public/evidence_match_gate.py \
  --claim samples/ai_claim.json \
  --reproduction samples/reproduction_evidence.json \
  --base-dir . \
  --output stage328_decision.json

Expected result:

{
  "decision": "accept"
}
Positioning

Stage328 is the QSP Evidence Match Gate.

It verifies whether AI security claims and reproduction evidence are bound together by target, files, hashes, and signatures.

Stop trusting AI claims.
Start verifying evidence.

License

MIT License

Copyright (c) 2025 Motohiro Suzuki
