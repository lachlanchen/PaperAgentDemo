[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

Ein kompaktes, repository-genaues LaTeX-Paper-Scaffold mit Fokus auf `latex/main.tex`, entwickelt, um einen Manuskript-Workflow mit Gleichungen, Algorithmen, Tabellen, Glossar/Akronymen, Referenzen und PDF-Build-Tooling zu validieren und zu erweitern.

| Eintrag | Wert |
| --- | --- |
| Primäre Manuskriptdatei | `latex/main.tex` |
| Aktueller Build-Stil | Lokales LaTeX (`latexmk` / `pdflatex`) |
| Status des i18n-Ordners | `i18n/` vorhanden (Sprachdateien können im Laufe der Zeit ergänzt werden) |
| Status der Lizenzdatei | Derzeit nicht vorhanden |

## 📌 Überblick

Dieses Repository bietet aktuell:

- Eine einzelne zentrale Manuskript-Quelldatei: `latex/main.tex`.
- Eine repräsentative Paper-Struktur mit Abstract, Methoden, Algorithmus, Ergebnissen, Diskussion und Fazit.
- LaTeX-Paketabdeckung für typische Aufgaben beim wissenschaftlichen Schreiben (Mathematik, Zitationen, Glossar, Querverweise).
- Pipeline-Metadaten unter `.auto-readme-work/` für die mehrsprachige README-Generierung.

Wichtiger Hinweis zum Repository:

- `AGENTS.md` beschreibt vorgesehene Verzeichnisse (`figures/`, `data/`, `artifacts/`, `code/`), aber einige davon sind im aktuellen Baum noch nicht vorhanden. Diese README bewahrt diese Absicht und kennzeichnet fehlende Teile explizit.

## ✨ Features

- Mathematischer Satz über `amsmath`, `amssymb`, `bm`, `mathtools` und `siunitx`.
- Unterstützung für Abbildungen und Tabellen über `graphicx`, `subcaption`, `booktabs` und `multirow`.
- Algorithmus-Umgebung über `algorithm` und `algpseudocode`.
- Zitationsunterstützung über `natbib`.
- Glossar- und Akronym-Unterstützung über `glossaries` (`\makeglossaries` aktiviert).
- Querverweise über `hyperref` und `cleveref`.
- Beispielinhalt bereits enthalten: Zielfunktionsgleichung mit `\ell_1`-Regularisierung, SNR-Gleichung in dB, Gradient-Descent-Pseudocode, eine quantitative Vergleichstabelle und Inline-Bibliographieeinträge.

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
├── i18n/                         # derzeit vorhanden; sprachspezifische README-Dateien können im Laufe der Zeit ergänzt werden
└── latex/
    ├── main.tex                  # primäre Manuskriptquelle
    ├── main.acn                  # generiertes Glossar-/Akronym-Artefakt
    ├── main.glo                  # generiertes Glossar-Artefakt
    └── main.ist                  # Glossar-Stil-Artefakt
```

## ✅ Voraussetzungen

Installiere eine TeX-Umgebung, die die von `latex/main.tex` verwendeten Pakete enthält.

Praktische Mindestanforderungen:

- `latexmk`
- `pdflatex`
- `bibtex` (für Literaturverarbeitung in Standard-Workflows)
- Glossar-Tooling, das für `glossaries`-Workflows erforderlich ist (typischerweise `makeglossaries` aus der TeX-Distribution)

Annahme:

- Paketnamen und Versionen sind in diesem Repository nicht festgelegt; verwende eine aktuelle TeX-Live- oder MiKTeX-Distribution.

## 📥 Installation

Repository klonen und in das Verzeichnis wechseln:

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

Aktuell ist im Repository kein zusätzlicher Paketmanager-Installationsschritt definiert.

## 🚀 Nutzung

| Aufgabe | Befehl |
| --- | --- |
| Empfohlener Build | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| Schneller Einzel-Durchlauf | `pdflatex latex/main.tex` |
| Aux-Dateien bereinigen | `latexmk -c latex/main.tex` |

Primärer Build-Befehl (empfohlen, aus `AGENTS.md`):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Einzel-Durchlauf-Kompilierung (schnelle Iteration):

```bash
pdflatex latex/main.tex
```

LaTeX-Hilfsdateien bereinigen und PDF behalten:

```bash
latexmk -c latex/main.tex
```

Erwarteter Workflow:

1. Manuskriptinhalt in `latex/main.tex` bearbeiten.
2. Das PDF bauen.
3. Layout und Referenzen im Ausgabe-PDF visuell prüfen.

## ⚙️ Konfiguration

Die aktuelle Konfiguration auf Dokumentebene befindet sich in `latex/main.tex`:

- Dokumentklasse: `article` mit `11pt,a4paper`.
- Seitenlayout: `geometry` mit `margin=1in`.
- Zeilenabstand: `\onehalfspacing`.
- Linkfarb-Setup über benutzerdefiniertes `linkblue` und `hyperref`-Optionen.
- Akronyme und Glossareinträge sind für `CNN`, `SNR`, `HSI` und `event camera` vordefiniert.

Ignore-Verhalten auf Repository-Ebene (`.gitignore`):

- Ignoriert die meisten LaTeX-Build-Artefakte (`*.aux`, `*.log`, `*.pdf` usw.).
- Ignoriert standardmäßig die Verzeichnisse `artifacts/` und `data/`.

## 🧪 Beispiele

Das Manuskript Ende-zu-Ende bauen:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Bereinigen und dann neu bauen:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Schnell kompilieren, während ein Abschnitt bearbeitet wird:

```bash
pdflatex latex/main.tex
```

## 🛠 Entwicklungshinweise

Hinweise aus `AGENTS.md`:

- LaTeX-Quelltext unter klaren `\section{}`-Überschriften halten.
- Label-Präfixe konsistent verwenden: `eq:` für Gleichungen, `fig:` für Abbildungen, `tab:` für Tabellen und `alg:` für Algorithmen.
- Referenzen bevorzugt über `\cref{}` setzen.
- Klein geschriebene, mit Bindestrich getrennte Asset-Namen verwenden (Beispiel: `figures/snr-comparison.pdf`).
- Verschachtelte LaTeX-Blöcke dort mit zwei Leerzeichen einrücken, wo es der Lesbarkeit hilft.

Validierungsansatz:

- Es gibt keine automatisierte Testsuite.
- Die primäre Validierung ist ein erfolgreicher LaTeX-Build plus visuelle Prüfung des erzeugten PDFs.

## 🧰 Fehlerbehebung

Häufige Probleme und Prüfungen:

- Build schlägt wegen fehlendem Paket fehl: fehlende LaTeX-Pakete aus deiner TeX-Distribution installieren.
- Glossareinträge erscheinen nicht: sicherstellen, dass Glossar-Tooling installiert ist, und `latexmk` erneut ausführen, damit die Glossar-Schritte laufen.
- Zitations- oder Referenzwarnungen bleiben bestehen: mit `latexmk` neu bauen (mehrere Durchläufe werden automatisch gehandhabt).
- Ausgabe-PDF wird nicht von Git verfolgt: das ist erwartbar, da `*.pdf` derzeit in `.gitignore` ignoriert wird.

## 🗺 Roadmap

Geplante oder wahrscheinliche nächste Schritte (aus Repository-Dateien und Richtlinien abgeleitet):

1. Verzeichnisse `figures/`, `data/`, `artifacts/` und `code/` hinzufügen, wenn die Arbeit erweitert wird.
2. Sprachspezifische README-Dateien unter `i18n/` ergänzen, passend zu den Sprach-Navigationslinks.
3. Optionale Helferskripte für reproduzierbare Abbildungs-/Tabellengenerierung unter `code/` hinzufügen.
4. CI zur Build-Verifikation einführen, falls das Projekt über ein lokales Template hinauswächst.

## 🤝 Mitwirken

Derzeit ist kein formaler Contribution-Workflow definiert, nutze daher diese Basis:

1. Einen Branch erstellen.
2. Fokussierte Änderungen vornehmen.
3. Einen sauberen LaTeX-Build ausführen:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. Eine klare Zusammenfassung der Manuskript- oder Tooling-Änderungen im PR angeben.

Empfohlener Commit-Stil aus den Repository-Richtlinien:

- Klare, imperative Commit-Betreffzeilen verwenden.
- Beispiel: `Add glossary entries for sensor terms`

## 📄 Lizenz

Im Repository-Root ist derzeit keine Lizenzdatei vorhanden.

Annahme:

- Alle Rechte und Wiederverwendungsbedingungen sind derzeit nicht festgelegt, bis eine `LICENSE`-Datei hinzugefügt wird.

## 📚 Referenzen und Danksagungen

Das Beispielmanuskript in `latex/main.tex` enthält derzeit Inline-Bibliographieeinträge für:

- Goodfellow, Bengio und Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

Status der Danksagungen:

- In den Repository-Dateien ist aktuell kein eigener Abschnitt für Danksagungen, Sponsoren oder Spenden/Support vorhanden.
- Falls Sponsoren-/Support-Informationen extern vorhanden sind, hier ergänzen, ohne technische Inhalte zu entfernen.
