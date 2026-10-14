# Students — MATOMO

**Project:** MATOMO  
**Category:** MARKETING_TOOLS  
**Upstream:** https://github.com/matomo-org/matomo.git  
**Pinned commit:** `43e5ed4cbd73ac9b318b7bc7502b5bf30e7e6a26`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `6d26da13efd655b11e06b5a57d4a07bada472566131f22faf3232e207424436f`  
**Date:** October 2026

## What this project gives you

A complete worked example of offline-first packaging with a cryptographic audit
chain: source pinned at `43e5ed4cbd73ac9b318b7bc7502b5bf30e7e6a26`, a 16-check assurance suite, an evidence register
with per-check hashes, and an AIOSS ledger chain ending at `6d26da13efd655b11e06b5a57d4a07bada472566131f22faf3232e207424436f`.

## Learn by verifying

```
python tools/run_bench.py --out BENCH.json
```

Then take any row from `ISOLATED_LAB_RESULTS/03_Result_Register.md`, recompute
the SHA3-256 of its evidence file, and confirm it matches. If it does not match,
the record has been altered — that is the whole point of the chain.

## Licence

Apache 2.0 terms apply to study and teaching use.
