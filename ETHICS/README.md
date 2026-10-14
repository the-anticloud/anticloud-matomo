# Ethics — MATOMO

**Project:** MATOMO  
**Category:** MARKETING_TOOLS  
**Upstream:** https://github.com/matomo-org/matomo.git  
**Pinned commit:** `43e5ed4cbd73ac9b318b7bc7502b5bf30e7e6a26`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `6d26da13efd655b11e06b5a57d4a07bada472566131f22faf3232e207424436f`  
**Date:** October 2026

## Position

MATOMO is packaged for offline deployment with a verifiable audit trail. The
ethical questions this raises are answered by making the system's behaviour
checkable rather than by policy statements.

## The four commitments

1. **No hidden egress.** The deployment has no external API dependency; this is
   testable by running it with the network disconnected.
2. **Attributable output.** Every artifact is recorded in a hash chain, so what
   the system produced can be reconstructed.
3. **Operator control.** The institution owns the hardware and the keys.
4. **Refusal to overclaim.** Where a certification is not held, the project says
   so rather than implying it.

## Dual use

This project is packaged for civilian and public-sector deployment. Where an
upstream has dual-use characteristics, the licence gate and the reference-only
marking in `BENCH.json` record that.
