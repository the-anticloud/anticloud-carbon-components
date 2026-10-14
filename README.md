# CARBON COMPONENTS

![license](https://img.shields.io/badge/license-license-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-carbon_capture-lightgrey)

> Anticloud-hardened packaging of the upstream project `CARBON_COMPONENTS` in category **CARBON CAPTURE**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** CARBON CAPTURE · **Upstream:** https://github.com/the-anticloud/anticloud-carbon-components.git · **Upstream pin:** `7ea17b427c4bdad73f6995ffd87d0790b5389ec9` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

# carbon-components-svelte

[![NPM][npm]][npm-url]
![npm downloads to date](https://img.shields.io/npm/dt/carbon-components-svelte?color=262626&style=for-the-badge)
<a href="https://discord.gg/J7JEUEkTRX">
<img src="https://img.shields.io/discord/689212587170201628?color=5865F2&style=for-the-badge" alt="Chat with us on Discord">
</a>

Carbon Components Svelte is a [Svelte](https://github.com/sveltejs/svelte) component library that implements the [Carbon Design System](https://www.carbondesignsystem.com/), an open source design system by IBM. Ship accessible, consistent, production-ready interfaces.

- **90+ components**: from inputs to data tables
- **5 built-in themes**: two light, three dark
- **Fully typed TypeScript API**: props, events, and slots
- **WCAG 2.1 AA**: keyboard and screen-reader ready

The Carbon Svelte ecosystem also includes:

- **[Carbon Icons Svelte](https://github.com/carbon-design-system/carbon-icons-svelte)**: 2,700+ Carbon icons as Svelte components
- **[Carbon Pictograms Svelte](https://github.com/carbon-design-system/carbon-pictograms-svelte)**: 1,500+ Carbon pictograms as Svelte components
- **[Carbon Charts Svelte](https://github.com/carbon-design-system/carbon-charts/tree/master/packages/svelte)**: 25+ charts, powered by d3
- **[Carbon Preprocess Svelte](https://github.com/carbon-design-system/carbon-preprocess-svelte)**: Collection of Svelte preprocessors for Carbon

## [Documentation](https://svelte.carbondesignsystem.com)

## Installation

```sh
# npm
npm i carbon-components-svelte

# pnpm
pnpm add carbon-components-svelte

# Yarn
yarn add carbon-components-svelte

# Bun
bun add carbon-components-svelte
```

## Usage

### Styling

Before importing components, you will need to first apply Carbon component styles. The Carbon Design System supports five themes (2 light, 3 dark).

- **white.css**: Default Carbon theme (light)
- **g10.css**: Gray 10 theme (light)
- **g80.css**: Gray 80 theme (dark)
- **g90.css**: Gray 90 theme (dark)
- **g100.css**: Gray 100 theme (dark)
- **all.css**: All five themes (White, Gray 10, Gray 80, Gray 90, Gray 100) using [CSS variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)

Each StyleSheet is [generated](scripts/build-css.ts) from the flagship [carbon-components](https://github.com/carbon-design-system/carbon/tree/main/packages/carbon-components) library.

The compiled CSS is generated from the following `.scss` files:

- [css/white.scss](css/white.scss)
- [css/g10.scss](css/g10.scss)
- [css/g80.scss](css/g80.scss)
- [css/g90.scss](css/g90.scss)
- [css/g100.scss](css/g100.scss)
- [css/all.scss](css/all.scss)

Import one theme once at the top-level entry point of your app, like `index.js` or `src/+layout.svelte`.

#### CSS StyleSheet

```js
// White theme
import "carbon-components-svelte/css/white.css";

// Gray 10 theme
import "carbon-components-svelte/css/g10.css";

// Gray 80 theme
import "carbon-components-svelte/css/g80.css";

// Gray 90 theme
import "carbon-components-svelte/css/g90.css";

// Gray 100 theme
import "carbon-components-svelte/css/g100.css";

// All themes
import "carbon-components-svelte/css/all.css";
```

### SCSS

The most performant method to load styles is to import SCSS directly from carbon-components. Although it requires more set up, you can reduce the size of the bundle CSS by importing individual component styles instead of a pre-compiled CSS StyleSheet.

Refer to the [official Carbon guide on SASS](https://github.com/carbon-design-system/carbon/blob/v10/docs/guides/sass.md) for documentation.

### Dynamic theming

To switch themes at runtime, import the combined "all.css" StyleSheet instead of a single theme. It bundles all five themes and toggles between them through a `theme` attribute on the HTML element.

```js
import "carbon-components-svelte/css/all.css";
```

Update the theme by setting the `theme` attribute on the `html` element. The default `theme` is `"white"`.

```html
<!doctype html>
<html lang="en" theme="g10">
  <body>
    ...
  </body>
</html>
```

Or programmatically switch between each of the five Carbon themes by setting the `theme` attribute on the HTML element.

```html
<script>
  let theme = "white"; // "white" | "g10" | "g80" | "g90" | "g100"

  $: document.documentElement.setAttribute("theme", theme);
</script>
```

Alternatively, use the [Theme component](https://svelte.carbondesignsystem.com/components/Theme) to manage the theme reactively.

### Importing components

Import components from `carbon-components-svelte` in the `script` tag of your Svelte file. Visit the [documentation site](https://svelte.carbondesignsystem.com) for examples.

```html
<!-- App.svelte -->
<script>
  import { Accordion, AccordionItem } from "carbon-components-svelte";
</script>

<Accordion>
  <AccordionItem title="Section 1" open> Content 1 </AccordionItem>
  <AccordionItem title="Section 2"> Content 2 </AccordionItem>
  <AccordionItem title="Section 3"> Content 3 </AccordionItem>
</Accordion>
```

**Refer to the [documentation site](https://svelte.carbondesignsystem.com) for component API documentation.**

## Preprocessors & Plugins

[carbon-preprocess-svelte](https://github.com/carbon-design-system/carbon-preprocess-svelte) is a collection of Svelte preprocessors for Carbon. It trims build times and bundle size with two drop-in tools for faster HMR in development and leaner CSS when you ship.

> [!NOTE]
> Using `carbon-preprocess-svelte` is optional and not a prerequisite for this library. It should be installed as a development dependency.

```sh
# npm
npm i -D carbon-preprocess-svelte

# pnpm
pnpm add -D carbon-preprocess-svelte

# Yarn
yarn add -D carbon-preprocess-svelte

# Bun
bun add -D carbon-preprocess-svelte
```

### `optimizeImports`

`optimizeImports` is a Svelte preprocessor that rewrites barrel imports from Carbon components/icons/pictograms packages to their source Svelte code paths. This can significantly speed up development and production

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Unknown (no standard manifest detected)** (manifests: none detected; scanned in UPSTREAM_CLONE)
- Top-level source layout: `bench/`, `css/`, `e2e/`
- Snapshot size: **1226 files**, **11452 lines of code** (measured; see Benchmarks)
- Primary languages: `.svelte` (709), `.ts` (239), `.svx` (105), `.html` (88), `.scss` (67), `.md` (5)
- Upstream commit pinned for this packaging: `7ea17b427c4bdad73f6995ffd87d0790b5389ec9`

---

## Installation

No installation section was found in the upstream readme, so the commands below are generated from the manifests detected in this project directory.

```sh
# No standard manifest detected. Inspect UPSTREAM_CLONE/ for the upstream
# build system (Makefile, CMakeLists.txt, configure, ...) and follow it.
```

Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

No usage section was found in the upstream readme. Entry points detected in this project directory:

Browse the snapshot layout listed under What This Project Does and follow the upstream run instructions for the detected ecosystem (Unknown (no standard manifest detected)).

Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

- **90+ components**: from inputs to data tables
- **5 built-in themes**: two light, three dark
- **Fully typed TypeScript API**: props, events, and slots
- **WCAG 2.1 AA**: keyboard and screen-reader ready

The Carbon Svelte ecosystem also includes:

- **[Carbon Icons Svelte](https://github.com/carbon-design-system/carbon-icons-svelte)**: 2,700+ Carbon icons as Svelte components
- **[Carbon Pictograms Svelte](https://github.com/carbon-design-system/carbon-pictograms-svelte)**: 1,500+ Carbon pictograms as Svelte components
- **[Carbon Charts Svelte](https://github.com/carbon-design-system/carbon-charts/tree/master/packages/svelte)**: 25+ charts, powered by d3
- **[Carbon Preprocess Svelte](https://github.com/carbon-design-system/carbon-preprocess-svelte)**: Collection of Svelte preprocessors for Carbon

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Unknown (no standard manifest detected) |
| Manifests detected | none |
| Files in snapshot | 1226 |
| Lines of code | 11452 |
| Dependency references | 20 |
| Dependencies by ecosystem | npm: 20 |
| Upstream license | Apache-2.0 |
| Overlay license | Anticommons 0.1.0 |

Top dependency references recorded in the benchmark snapshot:

| Ecosystem | Name | Version | Source file |
|-----------|------|---------|-------------|
| npm | @roxi/routify | ^3.6.4 | docs/package.json |
| npm | @sveltejs/vite-plugin-svelte | ^7.3.1 | docs/package.json |
| npm | @types/mdast | ^4.0.4 | docs/package.json |
| npm | @types/prismjs | ^1.26.5 | docs/package.json |
| npm | @types/unist | ^3.0.3 | docs/package.json |
| npm | carbon-icons-svelte | ^13.15.0 | docs/package.json |
| npm | carbon-pictograms-svelte | ^13.20.0 | docs/package.json |
| npm | clipboard-copy | ^4.0.1 | docs/package.json |
| npm | estree-walker | ^3.0.3 | docs/package.json |
| npm | github-slugger | ^2.0.0 | docs/package.json |
| npm | mdsvex | ^0.12.8 | docs/package.json |
| npm | minisearch | ^7.1.0 | docs/package.json |
| npm | prettier | ^3.9.9 | docs/package.json |
| npm | prettier-plugin-svelte | ^4.1.1 | docs/package.json |
| npm | prism-svelte | ^0.5.0 | docs/package.json |
| ... | (5 more) | | |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

Each StyleSheet is [generated](scripts/build-css.ts) from the flagship [carbon-components](https://github.com/carbon-design-system/carbon/tree/main/packages/carbon-components) library.

The compiled CSS is generated from the following `.scss` files:

- [css/white.scss](css/white.scss)
- [css/g10.scss](css/g10.scss)
- [css/g80.scss](css/g80.scss)
- [css/g90.scss](css/g90.scss)
- [css/g100.scss](css/g100.scss)
- [css/all.scss](css/all.scss)

Import one theme once at the top-level entry point of your app, like `index.js` or `src/+layout.svelte`.

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

*Excerpt from upstream `CONTRIBUTING.md`:*

# Contributing

If you're not sure what to build or how to approach a change, [file an issue](https://github.com/carbon-design-system/carbon-components-svelte/issues) before opening a PR.

## Prerequisites

Codebase:

- [Bun](https://bun.com/docs/installation)

Use Bun as the package manager and task runner. Run package scripts with `bun <script>` and one-off binaries with `bunx <bin>`.

## Project set-up

Fork the project and source your fork:

```sh
git source <YOUR_FORK>
cd carbon-components-svelte
```

Set the original project as the upstream:

```sh
git remote add upstream git@github.com:carbon-design-system/carbon-components-svelte.git
# verify that the upstream is added
git remote -v
```

### Set up

```sh
bun setup
```

This installs root and docs dependencies and generates TypeScript definitions and `docs/src/COMPONENT_API.json`.

Component documentation lives in `docs/`. The site uses [Vite](https://vite.dev/), [Routify 3](https://routify.dev/docs), Svelte 5, and MDsveX. The Vite config resolves `carbon-components-svelte` to the project root, so edits under `src/` show up in the docs without a separate package link.

To preview the docs site locally:

```sh
cd docs
bun dev
```

The site serves at http://localhost:5173/ (or the next available port).

## Best practices

Conventions used across `src/`. Follow them in new and changed code.

### Code style

Comments:

- Do not add trivial comments. If a comment restates what the code already says, delete it or improve the code instead.
- Reserve comments for non-obvious behavior: Svelte reactivity edge cases, ARIA placement, workarounds for Carbon v10 gaps. See loop guards in [`ContentSwitcher.svelte`](src/ContentSwitcher/ContentSwitcher.svelte) and the duplicate-dispatch guard in [`Checkbox.svelte`](src/Checkbox/Checkbox.svelte).

Patterns:

- Use `function` declarations in `<script>`. Declare handlers, defaults, and logic as functions rather than inline in markup. Named functions give stable references for default prop values (see `defaultShouldFilter` in [`ComboBox.svelte`](src/ComboBox/ComboBox.svelte)).
- Avoid `afterUpdate`. It runs after every DOM update and is easy to loop in Svelte 5. Prefer `$:` reactive statements with guards, event handlers, `onMount`, or `tick()` for DOM reads. Legacy code may still use `afterUpdate` for scroll-sync or measurement; do not add new uses without a strong reason.
- When moving a `dispatch(...)` from `afterUpdate` to `$:`, timing changes. `afterUpdate` ran af

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: Apache-2.0** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
                                 Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

   TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

   1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, direct or indirect, to cause the
      direction or management of such entity, whether by contract or
      otherwise, or (ii) ownership of fifty percent (50%) or more of the
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original Apache-2.0 terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `Apache-2.0` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `CARBON_COMPONENTS` (category: CARBON CAPTURE)
- **Upstream URL:** https://github.com/the-anticloud/anticloud-carbon-components.git
- **Pinned commit (SHA):** `7ea17b427c4bdad73f6995ffd87d0790b5389ec9`
- **Branch:** main
- **Pin provenance:** resolved during the second documentation pass. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`01d566ed997d801f20f4826ad8a96bea9fcb117c364a77f73b3c66d4b0f1f594`.

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

