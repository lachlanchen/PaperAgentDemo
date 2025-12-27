# Repository Guidelines

## Project Structure & Module Organization

- `latex/` holds the main manuscript source (`latex/main.tex`) and build artifacts such as `main.pdf` and auxiliary files.
- `figures/` is the intended home for images referenced by the paper (e.g., `figures/experiment-setup.pdf`).
- `data/` is reserved for datasets or tables used to generate results.
- `artifacts/` can store generated outputs (plots, logs, or compiled assets).
- `code/` is currently empty and can be used for scripts that support experiments or figure generation.

## Build, Test, and Development Commands

Run these from the repository root unless noted.

- `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` builds the PDF with continuous dependency tracking.
- `pdflatex latex/main.tex` provides a single-pass compile when you are iterating quickly.
- `latexmk -c latex/main.tex` cleans auxiliary LaTeX files while keeping `main.pdf`.

## Coding Style & Naming Conventions

- LaTeX source lives in `latex/main.tex`; keep new sections grouped under clear `\section{}` headings.
- Use consistent label prefixes (`eq:`, `fig:`, `tab:`, `alg:`) and reference with `\cref{}`.
- Keep file names lowercase with hyphens (e.g., `figures/snr-comparison.pdf`).
- Indent LaTeX blocks with two spaces where nesting helps readability (algorithms, lists).

## Testing Guidelines

- There are no automated tests in this repository.
- The primary validation step is a clean LaTeX build and a visual scan of `latex/main.pdf` for layout issues.

## Commit & Pull Request Guidelines

- No commit history exists yet, so there is no established message convention.
- Use clear, imperative subject lines (e.g., "Add glossary entries for sensor terms").
- Pull requests should include a short summary, the LaTeX build command used, and any notable PDF changes (screenshots optional for major layout updates).

## Security & Configuration Tips

- Keep large data files out of version control unless required for reproducibility.
- If you add scripts under `code/`, document dependencies and expected output paths in the script header or a short README.
