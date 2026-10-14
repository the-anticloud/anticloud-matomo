# Build and Test

**Project:** `MATOMO`
**Upstream:** https://github.com/matomo-org/matomo
**License:** GPL

## Quick Start

```bash
git clone https://github.com/matomo-org/matomo
cd matomo
pip install -r requirements-anticloud.txt
python anticloud_main.py --offline --pax-local
```

## Anticloud Improvements Applied

1. PAX L5 Narrow L2 General 27B local copy generation and A/B variant creation
2. AIOSS campaign audit chain for all content approvals and deployments
3. AES-256 encryption for all customer data and campaign analytics
4. Single-binary marketing suite with no SaaS dependency
5. Zero-cloud: all AI generation and analytics run locally
6. GPU/CPU equalizer: image generation on GPU, text on CPU
7. Zero-telemetry: removes all third-party tracking and retargeting pixels
8. Open export: CSV/JSON analytics data, no vendor lock-in

## Benchmark Targets

| Metric | Target |
| --- | --- |
| Latency | Primary inference task: <5s on CPU, <1s on GPU |
| Throughput | Batch processing: >100 items/hour on single CPU server |
| Memory | <8GB RAM for standard deployment |
| Accuracy | Task-specific accuracy within 5% of cloud-API baseline |

## Build Status

Not yet measured. Run verified build and record actual figures above.
