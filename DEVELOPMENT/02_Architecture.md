# Technical Architecture — MATOMO

**Upstream:** [https://github.com/matomo-org/matomo](https://github.com/matomo-org/matomo)
**License:** GPL
**Category:** MARKETING_TOOLS
**Anticloud Integration:** PAX L5 Narrow L2 General 27B + AIOSS + Offline-First

## Upstream Description

Open-source web analytics

## Anticloud Architectural Changes

1. PAX L5 Narrow L2 General 27B local copy generation and A/B variant creation
2. AIOSS campaign audit chain for all content approvals and deployments
3. AES-256 encryption for all customer data and campaign analytics
4. Single-binary marketing suite with no SaaS dependency
5. Zero-cloud: all AI generation and analytics run locally
6. GPU/CPU equalizer: image generation on GPU, text on CPU
7. Zero-telemetry: removes all third-party tracking and retargeting pixels
8. Open export: CSV/JSON analytics data, no vendor lock-in

## Integration Points

- **PAX Inference Socket:** Local HTTP endpoint at `127.0.0.1:11434/v1/chat` — same OpenAI-compatible API, zero cloud
- **AIOSS Hook:** Every write operation calls `aioss_append(event, payload)` before commit
- **Encryption Layer:** All file I/O routed through `anticloud_crypto.encrypt_at_rest()`
- **Single Binary Build:** `pyinstaller anticloud_matomo.spec` or `go build -o matomo`

## Deployment Modes

| Mode | Hardware | Notes |
| --- | --- | --- |
| Edge CPU | Raspberry Pi 4 / Intel NUC | Full feature set, PAX on CPU |
| Desktop GPU | RTX 3060 / A10 | PAX GPU inference, <1s latency |
| Server | 2× A100 | Full batch throughput |
| Air-gapped | Any x86/ARM | Zero network dependency |