[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

`latex/main.tex` を中心に構成された、リポジトリ実態に即したコンパクトな LaTeX 論文スキャフォールドです。数式・アルゴリズム・表・用語集/略語・参考文献・PDF ビルドツールを含む原稿ワークフローの検証と拡張を目的としています。

| 項目 | 値 |
| --- | --- |
| 主原稿ファイル | `latex/main.tex` |
| 現在のビルド方式 | ローカル LaTeX (`latexmk` / `pdflatex`) |
| i18n フォルダの状態 | `i18n/` は存在（各言語ファイルは今後追加される場合があります） |
| ライセンスファイルの状態 | 現時点では未配置 |

## 📌 概要

このリポジトリは現在、以下を提供しています。

- 単一の主原稿ソースファイル: `latex/main.tex`。
- アブストラクト、手法、アルゴリズム、結果、考察、結論を含む代表的な論文構成。
- 研究執筆で一般的なタスク（数式、引用、用語集、相互参照）をカバーする LaTeX パッケージ構成。
- 多言語 README 生成のためのパイプラインメタデータ（`.auto-readme-work/`）。

重要なリポジトリ注記:

- `AGENTS.md` には想定ディレクトリ（`figures/`, `data/`, `artifacts/`, `code/`）が記載されていますが、現在のツリーには未作成のものがあります。本 README はその意図を維持し、未存在項目を明示しています。

## ✨ 特徴

- `amsmath`, `amssymb`, `bm`, `mathtools`, `siunitx` による数式組版。
- `graphicx`, `subcaption`, `booktabs`, `multirow` による図表サポート。
- `algorithm` と `algpseudocode` によるアルゴリズム環境。
- `natbib` による引用サポート。
- `glossaries` による用語集・略語サポート（`\makeglossaries` 有効）。
- `hyperref` と `cleveref` による相互参照。
- 既存のサンプル内容: `\ell_1` 正則化付き目的関数、dB 表記の SNR 方程式、勾配降下法の疑似コード、定量比較表、インライン参考文献エントリ。

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
├── i18n/                         # 現在存在; 各言語 README は今後追加される場合があります
└── latex/
    ├── main.tex                  # 主原稿ソース
    ├── main.acn                  # 生成される用語集/略語アーティファクト
    ├── main.glo                  # 生成される用語集アーティファクト
    └── main.ist                  # 用語集スタイルアーティファクト
```

## ✅ 前提条件

`latex/main.tex` で使用しているパッケージを含む TeX 環境をインストールしてください。

実用上の最小要件:

- `latexmk`
- `pdflatex`
- `bibtex`（標準フローでの参考文献処理向け）
- `glossaries` ワークフローに必要な用語集ツール（通常は TeX ディストリビューションに含まれる `makeglossaries`）

前提:

- このリポジトリではパッケージ名・バージョンを固定していません。比較的新しい TeX Live または MiKTeX を使用してください。

## 📥 インストール

リポジトリをクローンして移動します。

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

現在、リポジトリ内に追加のパッケージマネージャー導入手順は定義されていません。

## 🚀 使い方

| タスク | コマンド |
| --- | --- |
| 推奨ビルド | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| 単発クイックコンパイル | `pdflatex latex/main.tex` |
| 補助ファイル削除 | `latexmk -c latex/main.tex` |

主ビルドコマンド（`AGENTS.md` 推奨）:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

単発コンパイル（高速反復向け）:

```bash
pdflatex latex/main.tex
```

PDF を残したまま LaTeX の補助ファイルを削除:

```bash
latexmk -c latex/main.tex
```

想定ワークフロー:

1. `latex/main.tex` の原稿内容を編集する。
2. PDF をビルドする。
3. 出力 PDF のレイアウトと参照を目視確認する。

## ⚙️ 設定

現在の文書レベル設定は `latex/main.tex` にあります。

- 文書クラス: `article`（`11pt,a4paper`）。
- ページレイアウト: `geometry`（`margin=1in`）。
- 行間: `\onehalfspacing`。
- カスタム `linkblue` と `hyperref` オプションによるリンク色設定。
- `CNN`, `SNR`, `HSI`, `event camera` の略語・用語集エントリを事前定義。

リポジトリレベルの無視設定（`.gitignore`）:

- 多くの LaTeX ビルド成果物（`*.aux`, `*.log`, `*.pdf` など）を無視。
- `artifacts/` と `data/` ディレクトリを既定で無視。

## 🧪 例

原稿をエンドツーエンドでビルド:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

クリーン後に再ビルド:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

1セクションを編集中に素早くコンパイル:

```bash
pdflatex latex/main.tex
```

## 🛠 開発メモ

`AGENTS.md` に基づくガイダンス:

- LaTeX ソースは明確な `\section{}` 見出し配下に整理する。
- ラベル接頭辞を一貫させる: 数式は `eq:`, 図は `fig:`, 表は `tab:`, アルゴリズムは `alg:`。
- 参照は `\cref{}` を優先。
- アセット名は小文字・ハイフン区切りを使用（例: `figures/snr-comparison.pdf`）。
- ネストした LaTeX ブロックは必要に応じて 2 スペースでインデントする。

検証方針:

- 自動テストスイートはありません。
- 主な検証は LaTeX ビルド成功と生成 PDF の目視確認です。

## 🧰 トラブルシューティング

よくある問題と確認事項:

- パッケージ不足でビルド失敗: 使用中の TeX ディストリビューションから不足 LaTeX パッケージを追加してください。
- 用語集が表示されない: 用語集ツールが導入済みか確認し、`latexmk` を再実行して用語集処理を走らせてください。
- 引用や参照の警告が残る: `latexmk` で再ビルドしてください（複数パスは自動処理されます）。
- 出力 PDF が git で追跡されない: `.gitignore` で現在 `*.pdf` が無視されるため、これは想定動作です。

## 🗺 ロードマップ

計画中または想定される次のステップ（リポジトリファイルとガイドラインから推定）:

1. 作業拡大に合わせて `figures/`, `data/`, `artifacts/`, `code/` ディレクトリを追加する。
2. 言語ナビゲーションリンクに対応する言語別 README を `i18n/` に追加する。
3. 再現可能な図表生成のため、任意の補助スクリプトを `code/` 配下に追加する。
4. プロジェクトがローカルテンプレートを超えて拡大した場合、ビルド検証 CI を導入する。

## 🤝 コントリビュート

現時点で正式なコントリビューションフローは定義されていないため、以下を基本としてください。

1. ブランチを作成する。
2. 変更を焦点化して実施する。
3. クリーンな LaTeX ビルドを実行する。

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. PR に原稿またはツール変更の明確な要約を含める。

リポジトリガイダンスに基づく推奨コミットスタイル:

- 命令形で明確なコミット件名を使う。
- 例: `Add glossary entries for sensor terms`

## 📄 ライセンス

現時点でリポジトリルートにライセンスファイルはありません。

前提:

- `LICENSE` ファイルが追加されるまでは、権利および再利用条件は未定義です。

## 📚 参考文献と謝辞

`latex/main.tex` のサンプル原稿には現在、以下のインライン参考文献エントリが含まれています。

- Goodfellow, Bengio, and Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

謝辞ステータス:

- リポジトリファイル上には、専用の謝辞・スポンサー・寄付/サポートセクションは現在ありません。
- スポンサー/サポート情報が外部に存在する場合は、技術的内容を削除せずここに追加してください。
