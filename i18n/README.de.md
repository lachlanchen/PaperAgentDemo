[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


[![LazyingArt banner — apps and four buddies](https://github.com/lachlanchen/LazyingArtWebsite/raw/main/media/brand/lazyingart-intro.gif)](https://lazying.art)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

Ein kompaktes, repository-genaues LaTeX-Paper-Scaffold, das auf `latex/main.tex` basiert und darauf ausgelegt ist, einen Manuskript-Workflow mit Formeln, Algorithmen, Tabellen, Glossar/Akronymen, Referenzen und PDF-Build-Werkzeugen zu validieren und zu erweitern.

## 🧩 Auf einen Blick

| Element | Wert |
| --- | --- |
| Zentrale Manuskriptdatei | `latex/main.tex` |
| Aktueller Build-Stil | Lokales LaTeX (`latexmk` / `pdflatex`) |
| Status des i18n-Ordners | `i18n/` ist vorhanden (Sprachdateien können im Laufe der Zeit ergänzt werden) |
| Status der Lizenzdatei | Derzeit nicht vorhanden |

## 📌 Übersicht

Dieses Repository enthält aktuell:

- Eine einzelne Haupt-Manuskriptquelle: `latex/main.tex`.
- Eine repräsentative Paper-Struktur mit Abstract, Methoden, Algorithmus, Ergebnissen, Diskussion und Schlussfolgerung.
- LaTeX-Paketabdeckung für gängige wissenschaftliche Schreibaufgaben (Mathematik, Zitationen, Glossar, Querverweise).
- Pipeline-Metadaten unter `.auto-readme-work/` für die mehrsprachige README-Generierung.

Wichtiger Repository-Hinweis:

- `AGENTS.md` beschreibt die vorgesehenen Verzeichnisse (`figures/`, `data/`, `artifacts/`, `code/`), aber einige sind im aktuellen Baum noch nicht vorhanden. Dieses README bewahrt diese Intention und weist fehlende Bestandteile explizit aus.

## ✨ Funktionen

- Mathematische Satzunterstützung via `amsmath`, `amssymb`, `bm`, `mathtools` und `siunitx`.
- Unterstützt Abbildungen und Tabellen über `graphicx`, `subcaption`, `booktabs` und `multirow`.
- Algorithmus-Umgebung via `algorithm` und `algpseudocode`.
- Zitationsunterstützung via `natbib`.
- Glossar- und Akronym-Unterstützung über `glossaries` (`\makeglossaries` aktiviert).
- Querverweise via `hyperref` und `cleveref`.
- Beispielinhalt bereits enthalten: Zielfunktionsgleichung mit `\ell_1`-Regularisierung, SNR-Gleichung in dB, Pseudocode für Gradientenabstieg, eine quantitative Vergleichstabelle und Inline-Bibliographieeinträge.

## 🧭 Projektstruktur

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
├── i18n/                         # derzeit vorhanden; Sprach-README-Dateien können schrittweise ergänzt werden
└── latex/
    ├── main.tex                  # zentrale Manuskriptquelle
    ├── main.acn                  # generiertes Glossar/Akronym-Artefakt
    ├── main.glo                  # generiertes Glossar-Artefakt
    └── main.ist                  # Glossar-Style-Artefakt
```

## ✅ Voraussetzungen

Installiere eine TeX-Umgebung, die die Pakete enthält, die in `latex/main.tex` verwendet werden.

Praktische Mindestanforderungen:

- `latexmk`
- `pdflatex`
- `bibtex` (für den Bibliographie-Handling in Standardabläufen)
- Glossar-Werkzeuge, die von `glossaries`-Workflows benötigt werden (typischerweise `makeglossaries` aus der TeX-Distribution)

Annahme:

- Paketnamen und -versionen sind in diesem Repository nicht festgelegt; verwende eine aktuelle TeX Live- oder MiKTeX-Distribution.

## 📥 Installation

Repository klonen und wechseln:

```bash
 git clone <your-fork-or-repo-url>
 cd PaperAgentDemo
```

Aktuell ist kein zusätzlicher Paketmanager-Installationsschritt im Repository definiert.

## 🚀 Nutzung

| Aufgabe | Befehl |
| --- | --- |
| Empfohlener Build | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| Schnelle Einzeldurchlauf-Kompilierung | `pdflatex latex/main.tex` |
| Hilfsdateien bereinigen | `latexmk -c latex/main.tex` |

Primärer Build-Befehl (empfohlen, laut `AGENTS.md`):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Einzel-Durchlauf-Kompilierung (schnelle Iteration):

```bash
pdflatex latex/main.tex
```

LaTeX-Hilfsdateien bereinigen, PDF behalten:

```bash
latexmk -c latex/main.tex
```

Erwarteter Ablauf:

1. Manuskriptinhalt in `latex/main.tex` bearbeiten.
2. Das PDF bauen.
3. Layout und Referenzen im erzeugten PDF visuell prüfen.

## ⚙️ Konfiguration

Die aktuelle Dokumentkonfiguration befindet sich in `latex/main.tex`:

- Dokumentklasse: `article` mit `11pt,a4paper`.
- Seitenlayout: `geometry` mit `margin=1in`.
- Zeilenabstand: `\onehalfspacing`.
- Link-Farbkonfiguration über benutzerdefiniertes `linkblue` und `hyperref`-Optionen.
- Vorab definierte Akronyme und Glossar-Einträge für `CNN`, `SNR`, `HSI` und `event camera`.

Repository-weites Ignore-Verhalten (`.gitignore`):

- Ignoriert die meisten LaTeX-Build-Artefakte (`*.aux`, `*.log`, `*.pdf` etc.).
- Ignoriert standardmäßig die Verzeichnisse `artifacts/` und `data/`.

## 🧪 Beispiele

Das Manuskript durchgängig bauen:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Bereinigen und neu bauen:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Schnellkompilierung während der Bearbeitung eines Abschnitts:

```bash
pdflatex latex/main.tex
```

## 🛠 Entwicklungsnotizen

Richtlinien aus `AGENTS.md`:

- Halte die LaTeX-Quelle unter klaren `\section{}`-Überschriften.
- Nutze konsistente Label-Präfixe: `eq:` für Gleichungen, `fig:` für Abbildungen, `tab:` für Tabellen und `alg:` für Algorithmen.
- Bevorzuge Verweise via `\cref{}`.
- Verwende kleingeschriebene, mit Bindestrichen verbundene Dateinamen (z. B. `figures/snr-comparison.pdf`).
- Rüste verschachtelte LaTeX-Blöcke mit zwei Leerzeichen ein, wenn es die Lesbarkeit verbessert.

Validierungsansatz:

- Es gibt keine automatisierte Test-Suite.
- Die Hauptvalidierung ist ein erfolgreicher LaTeX-Build plus visuelle Prüfung des generierten PDFs.

## 🧰 Fehlerbehebung

Häufige Probleme und Prüfungen:

- Build schlägt fehl wegen fehlendem Paket: fehlende LaTeX-Pakete aus der TeX-Distribution installieren.
- Glossar-Einträge erscheinen nicht: stelle sicher, dass Glossar-Tools installiert sind und führe `latexmk` erneut aus, damit Glossar-Schritte ausgeführt werden.
- Zitations- oder Referenzwarnungen bleiben bestehen: erneut mit `latexmk` bauen (mehrere Durchläufe werden automatisch gehandhabt).
- Das Ausgabe-PDF ist nicht im Git-Index: das ist erwartbar, da `*.pdf` derzeit in `.gitignore` ignoriert wird.

## 🗺️ Roadmap

Vorgesehene oder wahrscheinliche nächste Schritte (abgeleitet aus Repository-Dateien und Richtlinien):

1. Verzeichnisse `figures/`, `data/`, `artifacts/` und `code/` ergänzen, wenn die Arbeit wächst.
2. Sprachspezifische README-Dateien unter `i18n/` entsprechend den Sprach-Navigationslinks hinzufügen.
3. Optional Hilfsskripte für reproduzierbare Erzeugung von Abbildungen/Tabellen unter `code/` ergänzen.
4. CI für Build-Validierung einführen, falls das Projekt über eine lokale Vorlage hinaus wächst.

## 🤝 Beitragen

Ein formaler Beitrags-Workflow ist derzeit nicht definiert; nutze daher diese Baseline:

1. Einen Branch erstellen.
2. Fokussierte Änderungen vornehmen.
3. Einen sauberen LaTeX-Build ausführen:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. Eine klare Zusammenfassung von Manuskript- oder Tooling-Änderungen in der PR aufnehmen.

Vorgeschlagener Commit-Stil aus Repository-Hinweisen:

- Verwende klare, imperative Commit-Betreffzeilen.
- Beispiel: `Add glossary entries for sensor terms`

## 📄 Lizenz

Eine Lizenzdatei ist derzeit nicht im Repository-Root vorhanden.

Annahme:

- Alle Rechte- und Wiederverwendungsbedingungen sind derzeit ungeklärt, bis eine `LICENSE`-Datei hinzugefügt wird.

## 📚 Referenzen und Danksagungen

Das Beispielmanuskript in `latex/main.tex` enthält derzeit Inline-Bibliographieeinträge für:

- Goodfellow, Bengio und Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

Danksagungsstatus:

- Im Manuskript ist derzeit kein dedizierter Danksagungsabschnitt vorhanden.
- Sponsoring-/Support-Links sind in der **❤️ Support**-Sektion oben zusammengefasst.


## ❤️ Support

| Donate | PayPal | Stripe |
| --- | --- | --- |
| [![Donate](https://camo.githubusercontent.com/24a4914f0b42c6f435f9e101621f1e52535b02c225764b2f6cc99416926004b7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f6e6174652d4c617a79696e674172742d3045413545393f7374796c653d666f722d7468652d6261646765266c6f676f3d6b6f2d6669266c6f676f436f6c6f723d7768697465)](https://chat.lazying.art/donate) | [![PayPal](https://camo.githubusercontent.com/d0f57e8b016517a4b06961b24d0ca87d62fdba16e18bbdb6aba28e978dc0ea21/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f50617950616c2d526f6e677a686f754368656e2d3030343537433f7374796c653d666f722d7468652d6261646765266c6f676f3d70617970616c266c6f676f436f6c6f723d7768697465)](https://paypal.me/RongzhouChen) | [![Stripe](https://camo.githubusercontent.com/1152dfe04b6943afe3a8d2953676749603fb9f95e24088c92c97a01a897b4942/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5374726970652d446f6e6174652d3633354246463f7374796c653d666f722d7468652d6261646765266c6f676f3d737472697065266c6f676f436f6c6f723d7768697465)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400) |
