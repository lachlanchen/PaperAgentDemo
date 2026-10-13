[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


[![LazyingArt banner](https://github.com/lachlanchen/lachlanchen/raw/main/figs/banner.png)](https://lazying.art)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

Un socle d’article LaTeX compact et fidèle au dépôt, centré sur `latex/main.tex`, conçu pour valider et étendre un flux de travail de manuscrit avec équations, algorithmes, tableaux, glossaire/acronymes, références et outils de génération PDF.

## 🧩 En un coup d’œil

| Élément | Valeur |
| --- | --- |
| Fichier principal du manuscrit | `latex/main.tex` |
| Style de build actuel | LaTeX local (`latexmk` / `pdflatex`) |
| Statut du dossier i18n | `i18n/` existe (des fichiers de langue peuvent être ajoutés avec le temps) |
| Statut du fichier de licence | Non présent actuellement |

## 📌 Aperçu

Ce dépôt fournit actuellement :

- Un fichier source principal unique : `latex/main.tex`.
- Une structure d’article représentative avec résumé, méthodes, algorithme, résultats, discussion et conclusion.
- Une couverture de paquets LaTeX pour les tâches courantes de rédaction scientifique (mathématiques, citations, glossaire, références croisées).
- Des métadonnées de pipeline dans `.auto-readme-work/` pour la génération multilingue du README.

Remarque importante du dépôt :

- `AGENTS.md` décrit les répertoires prévus (`figures/`, `data/`, `artifacts/`, `code/`), mais certains ne sont pas encore présents dans l’arborescence actuelle. Ce README conserve cette intention et signale explicitement les éléments manquants.

## ✨ Fonctionnalités

- Typographie mathématique via `amsmath`, `amssymb`, `bm`, `mathtools` et `siunitx`.
- Prise en charge des figures et tableaux via `graphicx`, `subcaption`, `booktabs` et `multirow`.
- Environnement d’algorithme via `algorithm` et `algpseudocode`.
- Support des citations via `natbib`.
- Support du glossaire et des acronymes via `glossaries` (`\makeglossaries` activé).
- Références croisées via `hyperref` et `cleveref`.
- Contenu d’exemple déjà inclus : équation de fonction objectif avec régularisation `\ell_1`, équation SNR en dB, pseudo-code de descente de gradient, tableau de comparaison quantitatif et entrées bibliographiques en ligne.

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
├── i18n/                         # actuellement présent ; les fichiers README linguistiques pourront être ajoutés progressivement
└── latex/
    ├── main.tex                  # source principale du manuscrit
    ├── main.acn                  # artefact de glossaire/acronyme généré
    ├── main.glo                  # artefact de glossaire généré
    └── main.ist                  # style de glossaire
```

## ✅ Prérequis

Installez un environnement TeX qui inclut les paquets utilisés par `latex/main.tex`.

Exigences minimales pratiques :

- `latexmk`
- `pdflatex`
- `bibtex` (pour la gestion de la bibliographie dans les flux standard)
- Outils de glossaire requis par les workflows `glossaries` (généralement `makeglossaries` depuis la distribution TeX)

Hypothèse :

- Les noms et versions des paquets ne sont pas figés dans ce dépôt ; utilisez une distribution TeX Live ou MiKTeX récente.

## 📥 Installation

Clonez puis entrez dans le dépôt :

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

Aucune étape d’installation de gestionnaire de paquets supplémentaire n’est actuellement définie dans le dépôt.

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

Flux de travail attendu :

1. Modifiez le contenu du manuscrit dans `latex/main.tex`.
2. Générez le PDF.
3. Vérifiez visuellement la mise en page et les références dans le PDF de sortie.

## ⚙️ Configuration

La configuration actuelle au niveau du document se trouve dans `latex/main.tex` :

- Classe de document : `article` avec `11pt,a4paper`.
- Mise en page : `geometry` avec `margin=1in`.
- Espacement : `\onehalfspacing`.
- Configuration des couleurs de liens via `linkblue` personnalisé et options `hyperref`.
- Acronymes et entrées de glossaire prédéfinis pour `CNN`, `SNR`, `HSI` et `event camera`.

Comportement d’ignorance au niveau du dépôt (`.gitignore`) :

- Ignore la plupart des artefacts de compilation LaTeX (`*.aux`, `*.log`, `*.pdf`, etc.).
- Ignore par défaut les répertoires `artifacts/` et `data/`.

## 🧪 Exemples

Compilez le manuscrit de bout en bout :

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Nettoyer puis reconstruire :

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Compilation rapide pendant la modification d’une section :

```bash
pdflatex latex/main.tex
```

## 🛠 Notes de développement

Recommandations issues de `AGENTS.md` :

- Conserver la source LaTeX sous des sections `\section{}` claires.
- Utiliser des préfixes d’étiquettes cohérents : `eq:` pour les équations, `fig:` pour les figures, `tab:` pour les tableaux et `alg:` pour les algorithmes.
- Préférer les références via `\cref{}`.
- Utiliser des noms de fichiers minuscules avec des tirets (ex. : `figures/snr-comparison.pdf`).
- Indenter les blocs LaTeX imbriqués avec deux espaces lorsque utile.

Approche de validation :

- Il n’existe aucune suite de tests automatisée.
- La validation principale est une compilation LaTeX réussie, suivie d’un contrôle visuel du PDF généré.

## 🧰 Dépannage

Problèmes fréquents et vérifications :

- La compilation échoue à cause d’un paquet manquant : installez le paquet manquant depuis votre distribution TeX.
- Les entrées de glossaire n’apparaissent pas : assurez-vous que les outils de glossaire sont installés et relancez `latexmk` pour exécuter les étapes de glossaire.
- Les avertissements de citation ou de référence persistent : recompilez avec `latexmk` (les passes multiples sont gérées automatiquement).
- Le PDF de sortie n’est pas suivi par git : c’est prévu car `*.pdf` est actuellement ignoré dans `.gitignore`.

## 🗺 Feuille de route

Étapes prévues ou probables suivantes (inférées depuis les fichiers du dépôt et les consignes) :

1. Ajouter `figures/`, `data/`, `artifacts/` et `code/` au fur et à mesure que le projet progresse.
2. Ajouter des README spécifiques à chaque langue dans `i18n/` correspondant aux liens de navigation linguistique.
3. Ajouter des scripts d’assistance optionnels pour la génération reproductible de figures/tableaux dans `code/`.
4. Introduire une CI pour la vérification de build si le projet dépasse un simple modèle local.

## 🤝 Contribuer

Aucun flux de contribution formel n’est défini pour l’instant ; utilisez donc la base suivante :

1. Créez une branche.
2. Réalisez des changements ciblés.
3. Exécutez une compilation LaTeX propre :

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. Incluez dans votre PR un résumé clair des changements du manuscrit ou de l’outillage.

Style de commit suggéré par les consignes du dépôt :

- Utilisez des objets de commit clairs et à l’impératif.
- Exemple : `Add glossary entries for sensor terms`

## ❤️ Support

| Donate | PayPal | Stripe |
| --- | --- | --- |
| [![Donate](https://camo.githubusercontent.com/24a4914f0b42c6f435f9e101621f1e52535b02c225764b2f6cc99416926004b7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f6e6174652d4c617a79696e674172742d3045413545393f7374796c653d666f722d7468652d6261646765266c6f676f3d6b6f2d6669266c6f676f436f6c6f723d7768697465)](https://chat.lazying.art/donate) | [![PayPal](https://camo.githubusercontent.com/d0f57e8b016517a4b06961b24d0ca87d62fdba16e18bbdb6aba28e978dc0ea21/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f50617950616c2d526f6e677a686f754368656e2d3030343537433f7374796c653d666f722d7468652d6261646765266c6f676f3d70617970616c266c6f676f436f6c6f723d7768697465)](https://paypal.me/RongzhouChen) | [![Stripe](https://camo.githubusercontent.com/1152dfe04b6943afe3a8d2953676749603fb9f95e24088c92c97a01a897b4942/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5374726970652d446f6e6174652d3633354246463f7374796c653d666f722d7468652d6261646765266c6f676f3d737472697065266c6f676f436f6c6f723d7768697465)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400) |

## 📄 License

Aucun fichier de licence n’est actuellement présent à la racine du dépôt.

Hypothèse :

- Tous les droits et conditions de réutilisation restent non spécifiés tant qu’un fichier `LICENSE` n’est pas ajouté.

## 📚 Références et remerciements

Le manuscrit d’exemple dans `latex/main.tex` inclut actuellement des entrées bibliographiques en ligne pour :

- Goodfellow, Bengio et Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

Statut des remerciements :

- Aucune section dédiée aux remerciements n’est actuellement présente dans le manuscrit.
- Les liens de parrainage/soutien sont consolidés dans la section **❤️ Support** ci-dessus.
