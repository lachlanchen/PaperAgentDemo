[English](README.md) · [العربية](i18n/README.ar.md) · [Español](i18n/README.es.md) · [Français](i18n/README.fr.md) · [日本語](i18n/README.ja.md) · [한국어](i18n/README.ko.md) · [Tiếng Việt](i18n/README.vi.md) · [中文 (简体)](i18n/README.zh-Hans.md) · [中文（繁體）](i18n/README.zh-Hant.md) · [Deutsch](i18n/README.de.md) · [Русский](i18n/README.ru.md)


[![LazyingArt banner — apps and four buddies](https://github.com/lachlanchen/LazyingArtWebsite/raw/main/media/brand/lazyingart-intro.gif)](https://lazying.art)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

A compact, repository-accurate LaTeX paper scaffold centered on `latex/main.tex`, designed to validate and extend a manuscript workflow with equations, algorithms, tables, glossary/acronyms, references, and PDF build tooling.

## 🧩 At a Glance

| Item | Value |
| --- | --- |
| Primary manuscript file | `latex/main.tex` |
| Current build style | Local LaTeX (`latexmk` / `pdflatex`) |
| i18n folder status | `i18n/` exists (language files may be added over time) |
| License file status | Not currently present |

## 📌 Overview

This repository currently provides:

- A single main manuscript source file: `latex/main.tex`.
- A representative paper structure with abstract, methods, algorithm, results, discussion, and conclusion.
- LaTeX package coverage for common research writing tasks (math, citations, glossary, cross-references).
- Pipeline metadata under `.auto-readme-work/` for multilingual README generation.

Important repository note:

- `AGENTS.md` describes intended directories (`figures/`, `data/`, `artifacts/`, `code/`), but some of these are not yet present in the current tree. This README preserves that intent and marks missing pieces explicitly.

## ✨ Features

- Mathematical typesetting via `amsmath`, `amssymb`, `bm`, `mathtools`, and `siunitx`.
- Figures and tables support via `graphicx`, `subcaption`, `booktabs`, and `multirow`.
- Algorithm environment via `algorithm` and `algpseudocode`.
- Citation support via `natbib`.
- Glossary and acronym support via `glossaries` (`\makeglossaries` enabled).
- Cross-referencing via `hyperref` and `cleveref`.
- Example content already included: objective function equation with `\ell_1` regularization, SNR equation in dB, gradient descent pseudocode, a quantitative comparison table, and inline bibliography entries.

## 🧭 Project Structure

```text
PaperAgentDemo/
├── .auto-readme-work/
│   └── 20260228_200112/
│       ├── pipeline-context.md
│       ├── language-nav-root.md
│       ├── language-nav-i18n.md
│       └── translation-plan.txt
├── .gitignore
├── AGENTS.md
├── README.md
├── i18n/                         # currently present; language README files may be added over time
└── latex/
    ├── main.tex                  # primary manuscript source
    ├── main.acn                  # generated glossary/acronym artifact
    ├── main.glo                  # generated glossary artifact
    └── main.ist                  # glossary style artifact
```

## ✅ Prerequisites

Install a TeX environment that includes the packages used by `latex/main.tex`.

Minimum practical requirements:

- `latexmk`
- `pdflatex`
- `bibtex` (for bibliography handling in standard flows)
- Glossary tooling required by `glossaries` workflows (typically `makeglossaries` from TeX distribution)

Assumption:

- Package names and versions are not pinned in this repository; use a recent TeX Live or MiKTeX distribution.

## 📥 Installation

Clone and enter the repository:

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

No additional package manager install step is currently defined in-repo.

## 🚀 Usage

| Task | Command |
| --- | --- |
| Recommended build | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| Quick single pass | `pdflatex latex/main.tex` |
| Clean aux files | `latexmk -c latex/main.tex` |

Primary build command (recommended, from `AGENTS.md`):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Single-pass compile (quick iteration):

```bash
pdflatex latex/main.tex
```

Clean LaTeX auxiliary files while keeping PDF:

```bash
latexmk -c latex/main.tex
```

Expected workflow:

1. Edit manuscript content in `latex/main.tex`.
2. Build the PDF.
3. Visually inspect layout and references in the output PDF.

## ⚙️ Configuration

Current document-level configuration is in `latex/main.tex`:

- Document class: `article` with `11pt,a4paper`.
- Page layout: `geometry` with `margin=1in`.
- Spacing: `\onehalfspacing`.
- Link color setup via custom `linkblue` and `hyperref` options.
- Acronyms and glossary entries pre-defined for `CNN`, `SNR`, `HSI`, and `event camera`.

Repository-level ignore behavior (`.gitignore`):

- Ignores most LaTeX build artifacts (`*.aux`, `*.log`, `*.pdf`, etc.).
- Ignores `artifacts/` and `data/` directories by default.

## 🧪 Examples

Build the manuscript end-to-end:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Clean then rebuild:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Quick compile while editing one section:

```bash
pdflatex latex/main.tex
```

## 🛠 Development Notes

Guidance from `AGENTS.md`:

- Keep LaTeX source under clear `\section{}` headings.
- Use label prefixes consistently: `eq:` for equations, `fig:` for figures, `tab:` for tables, and `alg:` for algorithms.
- Prefer references via `\cref{}`.
- Use lowercase, hyphenated asset names (example: `figures/snr-comparison.pdf`).
- Indent nested LaTeX blocks with two spaces where helpful.

Validation approach:

- There is no automated test suite.
- Primary validation is successful LaTeX build plus visual inspection of the generated PDF.

## 🧰 Troubleshooting

Common issues and checks:

- Build fails with missing package: install missing LaTeX packages from your TeX distribution.
- Glossary entries do not appear: ensure glossary tooling is installed and rerun `latexmk` so glossary steps execute.
- Citation or reference warnings persist: rebuild with `latexmk` (multiple passes handled automatically).
- Output PDF is not tracked by git: this is expected because `*.pdf` is currently ignored in `.gitignore`.

## 🗺 Roadmap

Planned or likely next steps (inferred from repository files and guidelines):

1. Add `figures/`, `data/`, `artifacts/`, and `code/` directories as work expands.
2. Add language-specific README files under `i18n/` matching the language navigation links.
3. Add optional helper scripts for reproducible figure/table generation under `code/`.
4. Introduce CI for build verification if the project grows beyond a local template.

## 🤝 Contributing

No formal contribution workflow is currently defined, so use the following baseline:

1. Create a branch.
2. Make focused changes.
3. Run a clean LaTeX build:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. Include a clear summary of manuscript or tooling changes in your PR.

Suggested commit style from repository guidance:

- Use clear, imperative commit subjects.
- Example: `Add glossary entries for sensor terms`

## ❤️ Support

| Donate | PayPal | Stripe |
| --- | --- | --- |
| [![Donate](https://camo.githubusercontent.com/24a4914f0b42c6f435f9e101621f1e52535b02c225764b2f6cc99416926004b7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f6e6174652d4c617a79696e674172742d3045413545393f7374796c653d666f722d7468652d6261646765266c6f676f3d6b6f2d6669266c6f676f436f6c6f723d7768697465)](https://chat.lazying.art/donate) | [![PayPal](https://camo.githubusercontent.com/d0f57e8b016517a4b06961b24d0ca87d62fdba16e18bbdb6aba28e978dc0ea21/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f50617950616c2d526f6e677a686f754368656e2d3030343537433f7374796c653d666f722d7468652d6261646765266c6f676f3d70617970616c266c6f676f436f6c6f723d7768697465)](https://paypal.me/RongzhouChen) | [![Stripe](https://camo.githubusercontent.com/1152dfe04b6943afe3a8d2953676749603fb9f95e24088c92c97a01a897b4942/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5374726970652d446f6e6174652d3633354246463f7374796c653d666f722d7468652d6261646765266c6f676f3d737472697065266c6f676f436f6c6f723d7768697465)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400) |

## 📄 License

No license file is currently present in the repository root.

Assumption:

- All rights and reuse terms are currently unspecified until a `LICENSE` file is added.

## 📚 References and Acknowledgements

The sample manuscript in `latex/main.tex` currently includes inline bibliography entries for:

- Goodfellow, Bengio, and Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

Acknowledgement status:

- No dedicated acknowledgements section is currently present in the manuscript.
- Sponsorship/support links are consolidated in the **❤️ Support** section above.
