# MATOMO

![license](https://img.shields.io/badge/license-MIT-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-marketing_tools-lightgrey)

> Anticloud-hardened packaging of the upstream project `MATOMO` in category **MARKETING TOOLS**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** MARKETING TOOLS · **Upstream:** https://github.com/matomo-org/matomo-sdk-ios · **Upstream pin:** `f140afcb7cedebdcbf8b8230fdd822b4b61e3685` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

# MatomoTracker (former PiwikTracker) iOS SDK

The MatomoTracker is an iOS, tvOS and macOS SDK for sending app analytics to a Matomo server. MatomoTracker can be used from Swift and [Objective-C](https://github.com/matomo-org/matomo-sdk-ios/wiki/FAQ#how-to-use-the-matomotracker-from-objective-c).

**Fancy help improve this SDK? Check [this list](https://github.com/matomo-org/matomo-sdk-ios/issues?utf8=✓&q=is%3Aopen+is%3Aissue) to see what is left and can be improved.**

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

and in your dependencies:

`.product(name: "MatomoTracker", package: "matomo-sdk-ios")`

</details>

## Usage
### Matomo Instance

The Matomo iOS SDK doesn't provide a instance of the PiwikTracker. In order to be able to track data you have to create an instance first.

```Swift
let matomoTracker = MatomoTracker(siteId: "23", baseURL: URL(string: "https://demo2.matomo.org/piwik.php")!)
```

The `siteId` is the ID that you can get if you [add a website](https://matomo.org/faq/how-to/create-and-manage-websites/) within the Matomo web interface. The `baseURL` it the URL to your Matomo web instance and has to include the "piwik.php" or "matomo.php" string.

You can either pass around this instance, or add an extension to the `MatomoTracker` class and add a shared instance property.

```Swift
extension MatomoTracker {
    static let shared: MatomoTracker = MatomoTracker(siteId: "1", baseURL: URL(string: "https://example.com/piwik.php")!)
}
```

The `siteId` is the ID that you can get if you [add a website](https://matomo.org/faq/how-to/create-and-manage-websites/) within the Matomo web interface. The `baseURL` is the URL to your Matomo web instance and has to include the "piwik.php" or "matomo.php" string.

You can use multiple instances within one application.

#### Opting Out

The MatomoTracker SDK supports opting out of tracking. Please use the `isOptedOut` property of the MatomoTracker to define if the user opted out of tracking.

```Swift
matomoTracker.isOptedOut = true
```

### Tracking Page Views

The MatomoTracker can track hierarchical screen names, e.g. screen/settings/register. Use this to create a hierarchical and logical grouping of screen views in the Matomo web interface.

```Swift
matomoTracker.track(view: ["path","to","your","page"])
```

You can also set the url of the page.
```Swift
let url = URL(string: "https://matomo.org/get-involved/")
matomoTracker.track(view: ["community","get-involved"], url: url)
```

### Tracking Events

Events can be used to track user interactions such as taps on a button. An event consists of four parts:

- Category
- Action
- Name (optional, recommended)
- Value (optional)

```Swift
matomoTracker.track(eventWithCategory: "player", action: "slide", name: "volume", value: 35.1)
```

This will log that the user slid the volume slider on the player to 35.1%.

### Tracking search

The `MatomoTracker` can track how users use your app internal search. You can track what keywords were searched for, what categories they use, the number of results for a certain search and what searches resulted in no results.

```Swift
matomoTracker.trackSearch(query: "Best mobile tracking", category: "Technology", resultCount: 15)
```

### Custom Dimension

The Matomo SDK currently supports Custom Dimensions for the Visit Scope. Using Custom Dimensions you can add properties to the whole visit, such as "Did the user finish the tutorial?", "Is the user a paying user?" or "Which version of the Application is being used?" and such. Before sending custom dimensions please make sure Custom Dimensions are [properly installed and configured](https://matomo.org/docs/custom-dimensions/). You will need the `ID` of your configured Dimension.

After that you can set a new Dimension,

```Swift
matomoTracker.set(value: "1.0.0-beta2", forIndex: 1)
```

or remove an already set dimension.

```Swift
matomoTracker.remove(dimensionAtIndex: 1)
```

Dimensions in the Visit Scope will be sent along every Page View or Event. Custom Dimensions are not persisted by the SDK and have to be re-configured upon application startup.

### Custom User ID

To add a [custom User ID](https://matomo.org/docs/user-id/), simply set the value you'd like to use on the `userId` field of the tracker:

```Swift
matomoTracker.userId = "coolUsername123"
```

All future events being tracked by the SDK will be associated with this userID, as opposed to the default UUID created for each Visitor.

### Custom Visitor ID persisted on app starts

MatomoTracker will generate an `_id` upon first usage and will use this value to recognize the current visitor. This `_id` is persisted over app starts.

If you want to set your own visitor id, you can set your own visitor id with the `forcedVisitorId` field. Make sure you use a 16 character long hexadecimal string. The `forcedVisitorId` is persisted over app starts.

```Swift
matomoTracker.forcedVisitorId = "0123456789abcdef"
```

Because the SDK persists this visitor id on app start, then

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Ruby / Bundler** (manifests: Gemfile, Gemfile.lock; scanned in UPSTREAM_CLONE)
- Top-level source layout: `Example/`, `MatomoTracker/`, `MatomoTracker.xcodeproj/`, `MatomoTracker.xcworkspace/`, `MatomoTrackerTests/`
- Snapshot size: **131 files**, **3194 lines of code** (measured; see Benchmarks)
- Primary languages: `.swift` (54), `.json` (20), `.h` (8), `(none)` (7), `.m` (7), `.plist` (6)
- Upstream commit pinned for this packaging: `f140afcb7cedebdcbf8b8230fdd822b4b61e3685`

---

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

and in your dependencies:

`.product(name: "MatomoTracker", package: "matomo-sdk-ios")`

</details>

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

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

and in your dependencies:

`.product(name: "MatomoTracker", package: "matomo-sdk-ios")`

</details>

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

You can either pass around this instance, or add an extension to the `MatomoTracker` class and add a shared instance property.

```Swift
extension MatomoTracker {
    static let shared: MatomoTracker = MatomoTracker(siteId: "1", baseURL: URL(string: "https://example.com/piwik.php")!)
}
```

The `siteId` is the ID that you can get if you [add a website](https://matomo.org/faq/how-to/create-and-manage-websites/) within the Matomo web interface. The `baseURL` is the URL to your Matomo web instance and has to include the "piwik.php" or "matomo.php" string.

You can use multiple instances within one application.

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Ruby / Bundler |
| Manifests detected | Gemfile, Gemfile.lock |
| Files in snapshot | 131 |
| Lines of code | 3194 |
| Dependency references | 0 |
| Upstream license | MIT |
| Overlay license | Anticommons 0.1.0 |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

```Swift
matomoTracker.track(view: ["path","to","your","page"])
```

You can also set the url of the page.
```Swift
let url = URL(string: "https://matomo.org/get-involved/")
matomoTracker.track(view: ["community","get-involved"], url: url)
```

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

*Excerpt from upstream `CONTRIBUTING.md`:*

# How can I contribute?

Welcome! We are very happy to have you here. There are always too many things to do and not enough volunteers to help. So please join! This document collect things we need help with and act as a guideline.

## Reporting bugs

Did you find a bug? Bummer! Please help us find the reason and fix them.

* Search on GitHub under [Issues](https://github.com/matomo-org/matomo-sdk-ios/issues) if it was already reported. Maybe you can add information to it?
* If you're unable to find an open issue addressing the problem, please [open a new one](https://github.com/matomo-org/matomo-sdk-ios/issues/new). Please explain your problem and include as much detail as you can as they might help the maintainers to reproduce it:
  * A clear and descriptive title.
  * Describe your issue and add exact steps to reproduce the issue. You found a crash? Please attach a symbolicated crash report.
  * If possible add a few lines of code or possibly even an example project.

## Discussing

We love to discuss changes and improvements. If there is functionality you want to add or improve please [open an issue](https://github.com/matomo-org/matomo-sdk-ios/issues/new) and describe what you want to do, why and how. Maybe the feature already exists but is hidden? Maybe somebody wants to add ideas on how to implement it.

You are always welcome to add your thoughts to an existing [issue in discussion](https://github.com/matomo-org/matomo-sdk-ios/labels/discussion).

## Submitting changes

When contributing to this project, please first discuss the change you wish to make via an issue before making a change.

If you implemented a change please send a [Pull Request](https://github.com/matomo-org/matomo-sdk-ios/compare?expand=1) with a clear list of what you have done. Try to only tackle one thing a time. This will lead to smaller pull requests that are easier to review.

## Contributing Code

You want to contribute code? Awesome. Here are some tips that should get you started.

1. Check out the project
2. Install the CocoaPods by running `pod install` from the checked out folder
3. Open the Workspace in Xcode

### Adding code to the SDK

In the Workspace you will find the *MatomoTracker* Project. Inside of it there is a folder for the SDK code and one for the Tests. Tests can be run from the *MatomoTracker* scheme.

### Adding example code

All the example code can be found in the Workspace, in the *Examples* folder. There is a scheme for every example application

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: MIT** (evidence: `LICENSE.md` in the upstream snapshot).

License file excerpt:

```text
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original MIT terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `MIT` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `MATOMO` (category: MARKETING TOOLS)
- **Upstream URL:** https://github.com/matomo-org/matomo-sdk-ios
- **Pinned commit (SHA):** `f140afcb7cedebdcbf8b8230fdd822b4b61e3685`
- **Branch:** develop
- **Pin provenance:** GitHub API commits/develop. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`3db611c71a7a53353070251c2e60f1009f36cf7a66af7c6ffc7bfee3147b0cc1`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

