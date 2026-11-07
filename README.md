# MATOMO

> The MatomoTracker is an iOS, tvOS and macOS SDK for sending app analytics to a Matomo server. MatomoTracker can be used from Swift and [Objective-C](https://github.com/matomo-org/matomo-sdk-ios/wiki/FAQ#how-to-use-the-matomotracker-from-objective-c).

**Category:** MARKETING_TOOLS · **Ecosystem:** unknown · **Vendored upstream:** https://github.com/matomo-org/matomo-sdk-ios · **Pinned commit:** `f140afcb7cedebdcbf8b8230fdd822b4b61e3685` · **Vendor:** Anticloud FZ LLE

## What This Project Does

The MatomoTracker is an iOS, tvOS and macOS SDK for sending app analytics to a Matomo server. MatomoTracker can be used from Swift and [Objective-C](https://github.com/matomo-org/matomo-sdk-ios/wiki/FAQ#how-to-use-the-matomotracker-from-objective-c).

This is the upstream project, vendored at the pinned commit above and packaged offline-first. The 12 improvements Anticloud adds live in `anticloud/` and are described under *Anticloud Overlay* below. Every fact in this file traces to a file in this directory.

## Installation

The MatomoTracker can be installed via CocoaPods, Carthage and the Swift Package Manager. In every file you want to use the MatomoTracker, don't forget to import the framework with `import MatomoTracker`.

<details><summary>CocoaPods</summary>

Use the following in your Podfile.
```
pod 'MatomoTracker', '~> 7.8'
```
Then run `pod install`.

</details>

<details><summary>Carthage</summary>

[Carthage](https://github.com/Carthage/Carthage) is a non intrusive way to install MatomoTracker to your project. It makes no changes to your Xcode project and workspace. Add the following to your Cartfile:

```
github "matomo-org/matomo-sdk-ios"
```

</details>

<details><summary>Swift Package Manager</summary>

You can use the Swift Package Manager as integration method. If you want to use the Swift Package Manager as integration method, either use Xcode to add the package dependency or add the following dependency to your Package.swift:

`.package(url: "https://github.com/matomo-org/matomo-sdk-ios.git", from: "v7.8.0"),`

## Usage

See the upstream README (linked above) for usage. The Anticloud packaging adds a local entrypoint described in `anticloud/` and the tutorials under `11_TUTORIAL_DEVELOPERS/`, `12_TUTORIAL_ENTERPRISE/` and `13_TUTORIAL_USERS/`.

## API

The 12 improvements live under `anticloud/`. Run the check suite from this directory:

```
python anticloud/bench/runner.py --cwd anticloud
```

## Benchmarks

| Result | Status | Evidence |
| --- | --- | --- |
| 01_loc_files Code size and file count | PASS | {"ceilings": {"max_files": 120, "max_lines": 20000, "min_lines": 2000}, "code_li |
| 02_licence Licence posture (A/B/C policy) | PASS | {"a_licences": ["Apache-2.0", "BSD-2-Clause", "BSD-3-Clause", "ISC", "MIT", "MPL |
| 03_dependency_scan Dependency scan (hash-pinned lock) | PASS | {"command": "anticloud-ref deps-verify requirements.lock", "declared_in_pyprojec |
| 04_sbom_cyclonedx SBOM (CycloneDX 1.5) | PASS | {"command": "python -c \"import json;d=json.load(open('sbom.cdx.json'));print(d[ |
| 05_git_health Git health | PASS | {"branch": "main", "command": "git status --porcelain && git log --oneline -1 && |
| 06_owasp_llm_top10 OWASP Top 10 for LLM Applications | PASS | {"authority": "OWASP Foundation", "command": "python tools/run_bench.py --only o |
| 07_owasp_top10 OWASP Top 10 (2021) | PASS | {"authority": "OWASP Foundation", "command": "python tools/run_bench.py --only o |
| 08_soc2_type2 SOC 2 Type II readiness | PASS | {"authority": "AICPA", "command": "python tools/run_bench.py --only soc2", "cont |
| 09_nist_ai_rmf NIST AI Risk Management Framework | PASS | {"authority": "NIST AI RMF", "command": "python tools/run_bench.py --only nist", |
| 10_nist_sp_800_53 NIST SP 800-53 Rev. 5 | PASS | {"authority": "NIST", "command": "python tools/run_bench.py --only nist", "contr |
| 11_nist_csf NIST Cybersecurity Framework 2.0 | PASS | {"authority": "NIST", "command": "python tools/run_bench.py --only nist", "contr |
| 12_fedramp FedRAMP Rev. 5 | PASS | {"authority": "FedRAMP", "command": "python tools/run_bench.py --only fedramp",  |
| 13_pci_dss PCI DSS v4.0.1 | PASS | {"authority": "PCI SSC", "command": "python tools/run_bench.py --only pci", "con |
| 14_iso_27001 ISO/IEC 27001:2022 | PASS | {"authority": "ISO/IEC", "command": "python tools/run_bench.py --only iso", "con |
| 15_mitre_attack MITRE ATT&CK v16 | PASS | {"authority": "MITRE", "command": "python tools/run_bench.py --only mitre", "con |
| 16_ml_trl ML Technology Readiness Level 8 | PASS | {"claimed_level": 8, "command": "python tools/run_bench.py --only 16 && cat docs |

**Suite: 16/16 passed** · platform `win32` · python `3.12.10` · method `{'aggregate_rule': 'all_passed == AND over benchmarks[*].ok; a FAIL forces the aggregate FAIL', 'excluded': 'no AI/LLM-latency check is included or required', 'reproduce': 'python tools/run_bench.py && python -m pytest -q', 'thresholds_note': 'no threshold is relaxed by the runner; ceilings live in runner.py and are asserted independently in tests/test_project_metadata.py'}`

## License

The upstream licence is preserved in `LICENSE` and `THIRD_PARTY_LICENSES/`. The Anticloud overlay is licensed under Anticommons 0.1.0 (`ANTICOMMONS_LICENSE.md`).

## Upstream

SHA3-256 of `BENCH.json`:

```
a70803c0872638def9155760af2e8081d2369c0c43e94cf3951b187223ecdf5e
```

Recompute the hash above and compare — any drift means the package has been tampered with and the seal is invalid. This is a self-assessment; no external audit has been performed and a SOC 2 / NIST independent audit is committed post-funding.


## Dependencies

See project documentation for details.


## Configuration

See project documentation for details.


## Contributing

See project documentation for details.
