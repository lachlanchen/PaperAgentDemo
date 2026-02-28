[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

Un squelette d’article LaTeX compact et fidèle au dépôt, centré sur `latex/main.tex`, conçu pour valider et étendre un flux de travail de manuscrit avec équations, algorithmes, tableaux, glossaire/acronymes, références et outillage de compilation PDF.

| Élément | Valeur |
| --- | --- |
| Fichier principal du manuscrit | `latex/main.tex` |
| Style de build actuel | LaTeX local (`latexmk` / `pdflatex`) |
| Statut du dossier i18n | `i18n/` existe (des fichiers de langue peuvent être ajoutés au fil du temps) |
| Statut du fichier de licence | Non présent actuellement |

## 📌 Vue d’ensemble

Ce dépôt fournit actuellement :

- Un unique fichier source principal de manuscrit : `latex/main.tex`.
- Une structure d’article représentative avec résumé, méthodes, algorithme, résultats, discussion et conclusion.
- Une couverture de packages LaTeX pour les tâches courantes de rédaction scientifique (maths, citations, glossaire, références croisées).
- Des métadonnées de pipeline sous `.auto-readme-work/` pour la génération multilingue du README.

Note importante sur le dépôt :

- `AGENTS.md` décrit les répertoires visés (`figures/`, `data/`, `artifacts/`, `code/`), mais certains ne sont pas encore présents dans l’arborescence actuelle. Ce README conserve cette intention et signale explicitement les éléments manquants.

## ✨ Fonctionnalités

- Composition mathématique via `amsmath`, `amssymb`, `bm`, `mathtools` et `siunitx`.
- Prise en charge des figures et tableaux via `graphicx`, `subcaption`, `booktabs` et `multirow`.
- Environnement d’algorithme via `algorithm` et `algpseudocode`.
- Prise en charge des citations via `natbib`.
- Prise en charge du glossaire et des acronymes via `glossaries` (`\makeglossaries` activé).
- Références croisées via `hyperref` et `cleveref`.
- Contenu d’exemple déjà inclus : équation de fonction objectif avec régularisation `\ell_1`, équation SNR en dB, pseudocode de descente de gradient, tableau de comparaison quantitative et entrées bibliographiques inline.

## 🧭 Structure du projet

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
├── i18n/                         # actuellement présent ; des README de langue peuvent être ajoutés au fil du temps
└── latex/
    ├── main.tex                  # source principale du manuscrit
    ├── main.acn                  # artefact généré du glossaire/acronymes
    ├── main.glo                  # artefact généré du glossaire
    └── main.ist                  # artefact de style du glossaire
```

## ✅ Prérequis

Installez un environnement TeX qui inclut les packages utilisés par `latex/main.tex`.

Exigences pratiques minimales :

- `latexmk`
- `pdflatex`
- `bibtex` (pour la gestion de la bibliographie dans les flux standard)
- Outils de glossaire requis par les workflows `glossaries` (généralement `makeglossaries` depuis la distribution TeX)

Hypothèse :

- Les noms et versions des packages ne sont pas verrouillés dans ce dépôt ; utilisez une distribution TeX Live ou MiKTeX récente.

## 📥 Installation

Clonez puis entrez dans le dépôt :

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

Aucune étape d’installation supplémentaire via gestionnaire de paquets n’est actuellement définie dans le dépôt.

## 🚀 Utilisation

| Tâche | Commande |
| --- | --- |
| Build recommandé | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| Passe unique rapide | `pdflatex latex/main.tex` |
| Nettoyer les fichiers auxiliaires | `latexmk -c latex/main.tex` |

Commande de build principale (recommandée, d’après `AGENTS.md`) :

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Compilation en passe unique (itération rapide) :

```bash
pdflatex latex/main.tex
```

Nettoyer les fichiers auxiliaires LaTeX tout en conservant le PDF :

```bash
latexmk -c latex/main.tex
```

Workflow attendu :

1. Modifiez le contenu du manuscrit dans `latex/main.tex`.
2. Compilez le PDF.
3. Inspectez visuellement la mise en page et les références dans le PDF de sortie.

## ⚙️ Configuration

La configuration actuelle au niveau du document se trouve dans `latex/main.tex` :

- Classe de document : `article` avec `11pt,a4paper`.
- Mise en page : `geometry` avec `margin=1in`.
- Espacement : `\onehalfspacing`.
- Configuration des couleurs de liens via `linkblue` personnalisé et options `hyperref`.
- Acronymes et entrées de glossaire prédéfinis pour `CNN`, `SNR`, `HSI` et `event camera`.

Comportement d’ignore au niveau dépôt (`.gitignore`) :

- Ignore la plupart des artefacts de build LaTeX (`*.aux`, `*.log`, `*.pdf`, etc.).
- Ignore les répertoires `artifacts/` et `data/` par défaut.

## 🧪 Exemples

Compiler le manuscrit de bout en bout :

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Nettoyer puis recompiler :

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Compilation rapide pendant l’édition d’une section :

```bash
pdflatex latex/main.tex
```

## 🛠 Notes de développement

Recommandations issues de `AGENTS.md` :

- Garder la source LaTeX sous des titres `\section{}` clairs.
- Utiliser les préfixes d’étiquettes de manière cohérente : `eq:` pour les équations, `fig:` pour les figures, `tab:` pour les tableaux et `alg:` pour les algorithmes.
- Préférer les références via `\cref{}`.
- Utiliser des noms de ressources en minuscules avec tirets (exemple : `figures/snr-comparison.pdf`).
- Indenter les blocs LaTeX imbriqués avec deux espaces lorsque cela aide.

Approche de validation :

- Il n’existe pas de suite de tests automatisés.
- La validation principale est une compilation LaTeX réussie suivie d’une inspection visuelle du PDF généré.

## 🧰 Dépannage

Problèmes fréquents et vérifications :

- La compilation échoue à cause d’un package manquant : installez les packages LaTeX manquants depuis votre distribution TeX.
- Les entrées de glossaire n’apparaissent pas : vérifiez que les outils de glossaire sont installés puis relancez `latexmk` pour exécuter les étapes de glossaire.
- Les avertissements de citation ou de référence persistent : recompilez avec `latexmk` (les passes multiples sont gérées automatiquement).
- Le PDF de sortie n’est pas suivi par git : c’est attendu car `*.pdf` est actuellement ignoré dans `.gitignore`.

## 🗺 Feuille de route

Étapes prévues ou probables (inférées à partir des fichiers du dépôt et des consignes) :

1. Ajouter les répertoires `figures/`, `data/`, `artifacts/` et `code/` à mesure que le travail s’étend.
2. Ajouter des README spécifiques à chaque langue sous `i18n/` en correspondant aux liens de navigation linguistique.
3. Ajouter des scripts d’aide optionnels pour une génération reproductible des figures/tableaux sous `code/`.
4. Introduire une CI pour la vérification de build si le projet dépasse le stade du template local.

## 🤝 Contribuer

Aucun workflow de contribution formel n’est défini actuellement, utilisez donc cette base :

1. Créez une branche.
2. Faites des modifications ciblées.
3. Exécutez une compilation LaTeX propre :

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. Incluez dans votre PR un résumé clair des changements de manuscrit ou d’outillage.

Style de commit suggéré d’après les consignes du dépôt :

- Utiliser des sujets de commit clairs et à l’impératif.
- Exemple : `Add glossary entries for sensor terms`

## 📄 Licence

Aucun fichier de licence n’est actuellement présent à la racine du dépôt.

Hypothèse :

- Tous les droits et conditions de réutilisation sont actuellement non spécifiés jusqu’à l’ajout d’un fichier `LICENSE`.

## 📚 Références et remerciements

Le manuscrit d’exemple dans `latex/main.tex` inclut actuellement des entrées bibliographiques inline pour :

- Goodfellow, Bengio et Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

Statut des remerciements :

- Aucune section dédiée aux remerciements, sponsors, dons ou support n’est actuellement présente dans les fichiers du dépôt.
- Si des informations de sponsor/support existent en dehors du dépôt, ajoutez-les ici sans supprimer le contenu technique.
