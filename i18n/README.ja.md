[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


[![LazyingArt banner — apps and four buddies](https://github.com/lachlanchen/LazyingArtWebsite/raw/main/media/brand/lazyingart-intro.gif)](https://lazying.art)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

`latex/main.tex` を中核に据えた、リポジトリ実態に沿ったコンパクトな LaTeX 論文スケルトンです。数式、アルゴリズム、表、用語集／略語、参考文献、PDF ビルド支援を備え、原稿ワークフローの検証と拡張を想定しています。

## 🧩 At a Glance

| 項目 | 値 |
| --- | --- |
| 主原稿ファイル | `latex/main.tex` |
| 現在のビルド方式 | ローカル LaTeX (`latexmk` / `pdflatex`) |
| i18n フォルダの状態 | `i18n/` が存在（言語ファイルは順次追加予定） |
| ライセンスファイルの状態 | 現時点では未配置 |

## 📌 概要

このリポジトリは現在以下を提供します。

- 単一の主原稿ソース `latex/main.tex`。
- 摘要、手法、アルゴリズム、結果、議論、結論を含む代表的な論文構成。
- 共通的な研究執筆タスク（数式、引用、用語集、相互参照）に対応する LaTeX パッケージ群。
- 多言語 README 生成用のパイプラインメタデータ (`.auto-readme-work/`)。

重要なリポジトリ注記:

- `AGENTS.md` には想定ディレクトリ（`figures/`, `data/`, `artifacts/`, `code/`）が記載されていますが、現時点のツリーには未作成のものがあります。本 README ではその意図を維持し、未整備項目を明示します。

## ✨ 特徴

- `amsmath`, `amssymb`, `bm`, `mathtools`, `siunitx` による数式組版。
- `graphicx`, `subcaption`, `booktabs`, `multirow` による図表サポート。
- `algorithm` と `algpseudocode` によるアルゴリズム環境。
- `natbib` による引用支援。
- `glossaries` (`\makeglossaries` 有効) による用語集／略語サポート。
- `hyperref` と `cleveref` による相互参照。
- 既存サンプル内容: `\ell_1` 正則化付き目的関数、dB 単位の SNR 式、勾配降下法の疑似コード、定量比較表、インライン参考文献エントリ。

## 🧭 プロジェクト構成

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
├── i18n/                         # 現在存在; 必要に応じて言語別 README を追加
└── latex/
    ├── main.tex                  # 主原稿ソース
    ├── main.acn                  # 生成された用語集／略語アーティファクト
    ├── main.glo                  # 生成された用語集アーティファクト
    └── main.ist                  # 用語集スタイルアーティファクト
```

## ✅ 前提条件

`latex/main.tex` で用いられているパッケージを含む TeX 環境をインストールします。

最小限の実用要件:

- `latexmk`
- `pdflatex`
- `bibtex`（標準的な参照文献フロー向け）
- `glossaries` ワークフローに必要な用語集ツール（通常は TeX 配布物付属の `makeglossaries`）

前提:

- パッケージ名やバージョンはこのリポジトリでは固定されていないため、最新の TeX Live または MiKTeX 環境を想定します。

## 📥 インストール

リポジトリをクローンしてディレクトリへ移動します。

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

現時点で追加のパッケージマネージャーインストール手順はリポジトリ内で定義されていません。

## 🚀 使い方

| タスク | コマンド |
| --- | --- |
| 推奨ビルド | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| 簡易単発ビルド | `pdflatex latex/main.tex` |
| 補助ファイルの削除 | `latexmk -c latex/main.tex` |

主要なビルドコマンド（`AGENTS.md` 推奨）:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

編集中の単発コンパイル:

```bash
pdflatex latex/main.tex
```

PDF を保持したまま LaTeX 補助ファイルをクリーン:

```bash
latexmk -c latex/main.tex
```

期待されるワークフロー:

1. `latex/main.tex` で原稿内容を編集する。
2. PDF をビルドする。
3. 出力 PDF のレイアウトと参照情報を目視で確認する。

## ⚙️ 設定

現在の文書レベル設定は `latex/main.tex` に記載されています。

- 文書クラス: `article`（`11pt,a4paper`）
- ページレイアウト: `geometry`（`margin=1in`）
- 行間: `\onehalfspacing`
- カスタム `linkblue` と `hyperref` オプションによるリンク色設定
- `CNN`, `SNR`, `HSI`, `event camera` の用語・略語エントリを事前定義

リポジトリレベルの無視設定（`.gitignore`）:

- ほとんどの LaTeX 生成物（`*.aux`, `*.log`, `*.pdf` など）を除外
- `artifacts/` および `data/` を既定で除外

## 🧪 例

原稿を最後までビルドする:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

クリーン後に再ビルド:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

セクションを編集しながら素早くコンパイル:

```bash
pdflatex latex/main.tex
```

## 🛠 開発ノート

`AGENTS.md` からのガイダンス:

- LaTeX ソースは明確な `\section{}` 見出しごとに整理する。
- ラベルのプレフィックスを一貫して使用: 数式は `eq:`、図は `fig:`、表は `tab:`、アルゴリズムは `alg:`。
- `\cref{}` を優先して参照する。
- 資産名は小文字・ハイフン区切りを使用（例: `figures/snr-comparison.pdf`）。
- 必要に応じて、ネストした LaTeX ブロックを 2 スペースでインデント。

検証方針:

- 自動テストスイートはありません。
- 主要な検証は LaTeX ビルド成功と生成 PDF の目視確認です。

## 🧰 トラブルシューティング

よくある問題と確認項目:

- パッケージ不足でビルド失敗: 使用している TeX ディストリビューションから不足パッケージをインストール
- 用語集エントリが表示されない: 用語集ツールがインストール済みか確認し、`latexmk` を再実行して用語集工程を走らせる
- 引用または参照警告が解消しない: `latexmk` で再ビルド（複数パスが自動的に処理されます）
- 出力 PDF が git で追跡されない: `.gitignore` が `*.pdf` を除外しているため、想定通りの挙動です。

## 🗺 ロードマップ

リポジトリ内のファイルとガイドラインから推測される次のステップ:

1. `figures/`, `data/`, `artifacts/`, `code/` ディレクトリを作業拡大に合わせて追加
2. 言語ナビゲーションリンクに対応する言語別 README を `i18n/` に追加
3. 再現性のある図表生成のための補助スクリプトを `code/` 下に追加
4. ローカルテンプレートを越えて拡張した場合、CI でビルド検証を導入

## 🤝 コントリビュート

現時点で正式なコントリビューション手順は未定義のため、以下を基本とします。

1. ブランチを作成する。
2. 集中的に変更を加える。
3. クリーンな LaTeX ビルドを実行:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. PR に、原稿またはツール変更内容の明確な要約を含める。

リポジトリガイダンスに基づく推奨コミット方針:

- 明確で命令形の件名を使う。
- 例: `Add glossary entries for sensor terms`

## 📄 ライセンス

現時点でリポジトリルートにライセンスファイルはありません。

前提:

- `LICENSE` ファイルが追加されるまでは、権利・再利用条件は未設定です。

## 📚 参考文献と謝辞

`latex/main.tex` のサンプル原稿には、現在インラインの参考文献エントリとして以下が含まれます。

- Goodfellow, Bengio, and Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

謝辞の状況:

- リポジトリ内には、原稿に専用の謝辞セクションはまだありません。
- スポンサー／サポートリンクは上記 **❤️ Support** セクションに集約されています。


## ❤️ Support

| Donate | PayPal | Stripe |
| --- | --- | --- |
| [![Donate](https://camo.githubusercontent.com/24a4914f0b42c6f435f9e101621f1e52535b02c225764b2f6cc99416926004b7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f6e6174652d4c617a79696e674172742d3045413545393f7374796c653d666f722d7468652d6261646765266c6f676f3d6b6f2d6669266c6f676f436f6c6f723d7768697465)](https://chat.lazying.art/donate) | [![PayPal](https://camo.githubusercontent.com/d0f57e8b016517a4b06961b24d0ca87d62fdba16e18bbdb6aba28e978dc0ea21/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f50617950616c2d526f6e677a686f754368656e2d3030343537433f7374796c653d666f722d7468652d6261646765266c6f676f3d70617970616c266c6f676f436f6c6f723d7768697465)](https://paypal.me/RongzhouChen) | [![Stripe](https://camo.githubusercontent.com/1152dfe04b6943afe3a8d2953676749603fb9f95e24088c92c97a01a897b4942/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5374726970652d446f6e6174652d3633354246463f7374796c653d666f722d7468652d6261646765266c6f676f3d737472697065266c6f676f436f6c6f723d7768697465)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400) |
