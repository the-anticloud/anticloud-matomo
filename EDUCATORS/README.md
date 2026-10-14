# Educators — MATOMO

**Project:** MATOMO  
**Category:** MARKETING_TOOLS  
**Upstream:** https://github.com/matomo-org/matomo.git  
**Pinned commit:** `43e5ed4cbd73ac9b318b7bc7502b5bf30e7e6a26`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `6d26da13efd655b11e06b5a57d4a07bada472566131f22faf3232e207424436f`  
**Date:** October 2026

## Teaching with MATOMO

The project is usable as a worked example of offline-first packaging with a
cryptographic audit chain. It ships with the assurance suite, the evidence
register and the ledger, so students can verify claims rather than take them on
faith.

## Suggested exercises

1. Run `python tools/run_bench.py --out BENCH.json` and read the 16 results.
2. Recompute the SHA3-256 of a row's evidence file and compare to the register.
3. Walk the AIOSS chain from genesis to head `6d26da13efd655b11e06b5a57d4a07bada472566131f22faf3232e207424436f` and confirm every link.
4. Break one artifact and observe the chain fail to verify.

## Licence for teaching

Apache 2.0 terms apply to academic and teaching use. See `24_ANTICOMMONS_LICENSE`.
