[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


[![LazyingArt banner — apps and four buddies](https://lazying.art/media/brand/lazyingart-intro.gif)](https://lazying.art)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

一個精簡、與倉庫內容一致的 LaTeX 論文骨架，以 `latex/main.tex` 為核心，旨在以公式、演算法、表格、詞彙表/縮寫、參考文獻與 PDF 建置工具來驗證並延伸論文工作流程。

## 🧩 概覽

| 項目 | 值 |
| --- | --- |
| 主要論文檔案 | `latex/main.tex` |
| 目前建置方式 | 本機 LaTeX（`latexmk` / `pdflatex`） |
| i18n 資料夾狀態 | `i18n/` 已存在，語言檔案可持續補上 |
| 授權檔案狀態 | 目前尚未提供 |

## 📌 概述

目前本倉庫提供：

- 一個單一的主要論文來源檔：`latex/main.tex`。
- 一個具代表性的論文架構，包含摘要、方法、演算法、結果、討論與結論。
- 支援常見研究寫作任務的 LaTeX 套件組合（數學、引文、詞彙表、交叉參照）。
- `.auto-readme-work/` 目錄下的多語 README 生成流程中繼資料。

重要的倉庫說明：

- `AGENTS.md` 描述了預期目錄（`figures/`、`data/`、`artifacts/`、`code/`），但目前部分目錄尚未在實際目錄樹中出現。本 README 保留這些設計意圖並明確標示缺漏。

## ✨ 功能

- 透過 `amsmath`、`amssymb`、`bm`、`mathtools` 與 `siunitx` 提供數學排版能力。
- 透過 `graphicx`、`subcaption`、`booktabs` 與 `multirow` 支援圖表。
- 透過 `algorithm` 與 `algpseudocode` 提供演算法環境。
- 透過 `natbib` 提供文獻引用支援。
- 透過 `glossaries` 提供詞彙表與縮寫支援（已啟用 `\makeglossaries`）。
- 透過 `hyperref` 與 `cleveref` 提供交叉參照。
- 已內建示例內容：含 `\ell_1` 正則化的目標函式方程式、以 dB 表示的 SNR 方程式、梯度下降偽代碼、量化比較表與行內參考文獻條目。

## 🧭 專案結構

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

## ✅ 前置條件

請安裝包含 `latex/main.tex` 所使用套件的 TeX 環境。

最低實用需求：

- `latexmk`
- `pdflatex`
- `bibtex`（用於標準流程中的參考文獻處理）
- `glossaries` 流程所需的詞彙表工具（通常為 TeX 發行版提供的 `makeglossaries`）

假設：

- 本倉庫未鎖定特定套件名稱與版本；建議使用較新版本的 TeX Live 或 MiKTeX。

## 📥 安裝

複製並進入此倉庫：

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

目前倉庫中尚未定義額外的套件管理器安裝步驟。

## 🚀 使用方式

| 任務 | 指令 |
| --- | --- |
| 建議建置 | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| 單次快速編譯 | `pdflatex latex/main.tex` |
| 清理輔助檔案 | `latexmk -c latex/main.tex` |

主要建置指令（建議，來自 `AGENTS.md`）：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

快速迭代時單次編譯：

```bash
pdflatex latex/main.tex
```

清理 LaTeX 輔助檔並保留 PDF：

```bash
latexmk -c latex/main.tex
```

預期工作流程：

1. 在 `latex/main.tex` 編輯論文內容。
2. 建置 PDF。
3. 在輸出的 PDF 中進行版面與參考文獻視覺檢查。

## ⚙️ 設定

目前文件層級的設定位於 `latex/main.tex`：

- 文件類型：`article`，附帶 `11pt,a4paper`。
- 版面配置：`geometry`，`margin=1in`。
- 行距：`\onehalfspacing`。
- 以自訂 `linkblue` 與 `hyperref` 選項設定連結顏色。
- 已預先定義 `CNN`、`SNR`、`HSI` 與 `event camera` 的縮寫與詞彙表條目。

倉庫層級的忽略設定（`.gitignore`）：

- 會忽略大多數 LaTeX 建置產物（`*.aux`、`*.log`、`*.pdf` 等）。
- 預設忽略 `artifacts/` 與 `data/` 目錄。

## 🧪 使用範例

端到端建置論文：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

清理後重建：

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

編輯單一段落時快速編譯：

```bash
pdflatex latex/main.tex
```

## 🛠 開發註記

來自 `AGENTS.md` 的指引：

- 將 LaTeX 來源放在清楚的 `\section{}` 區段下。
- 一律使用一致的標籤前綴：`eq:` 代表方程式、`fig:` 代表圖、`tab:` 代表表、`alg:` 代表演算法。
- 優先使用 `\cref{}` 進行參照。
- 使用小寫加連字號的檔名（例如：`figures/snr-comparison.pdf`）。
- 在巢狀 LaTeX 區塊有助閱讀時，使用兩個空格縮排。

驗證方式：

- 目前沒有自動化測試。
- 主要驗證是成功建置 LaTeX，再加上輸出 PDF 的目視檢查。

## 🧰 疑難排解

常見問題與檢查：

- 建置失敗且回報缺少套件：請先從 TeX 發行版安裝對應套件。
- 詞彙表條目沒有顯示：確認詞彙表工具已安裝並重新執行 `latexmk`，讓詞彙表步驟完成。
- 引用或參照警告持續存在：使用 `latexmk` 重建（它會自動進行多輪編譯）。
- 輸出 PDF 未納入 Git 追蹤：這是預期行為，因為 `.gitignore` 目前忽略 `*.pdf`。

## 🗺 路線圖

根據目前檔案與指引推估的後續規劃：

1. 新增 `figures/`、`data/`、`artifacts/` 與 `code/` 目錄，隨專案推進逐步補足。
2. 在 `i18n/` 目錄下新增與語言導覽連結一致的語言 README。
3. 在 `code/` 下加入可重現圖表與表格的輔助腳本（可選）。
4. 若專案規模超出本機範本，導入 CI 以進行建置驗證。

## 🤝 貢獻

目前未定義正式的貢獻流程，請先使用以下基準：

1. 建立分支。
2. 進行聚焦修改。
3. 執行乾淨建置：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. 在 PR 中清楚摘要論文或工具變更。

建議的提交訊息風格：

- 使用清楚、祈使式的主旨。
- 範例：`Add glossary entries for sensor terms`

## 📄 授權

目前倉庫根目錄未提供授權檔。

假設：

- 所有權利與再利用條款目前仍未明確定義，將在加入 `LICENSE` 檔後補齊。

## 📚 參考與致謝

`latex/main.tex` 的範例論文目前已內建以下行內參考文獻條目：

- Goodfellow、Bengio 與 Courville, *Deep Learning* (MIT Press, 2016).
- Gallego 等, *Event-based vision: A survey* (IEEE TPAMI, 2022).

致謝狀態：

- 目前在論文中尚未有專門的致謝章節。
- 贊助與支持資訊已集中於上方 **❤️ Support** 區塊。


## ❤️ Support

<!-- support:start -->
[![GitHub Sponsors](https://img.shields.io/badge/GitHub-Sponsors-EA4AAA?style=for-the-badge&logo=githubsponsors&logoColor=white)](https://github.com/sponsors/lachlanchen)
[![LazyingArt Support](https://img.shields.io/badge/LazyingArt-Support-0EA5E9?style=for-the-badge)](https://chat.lazying.art/donate)
[![PayPal Support](https://img.shields.io/badge/PayPal-Support-00457C?style=for-the-badge&logo=paypal&logoColor=white)](https://paypal.me/RongzhouChen)
[![Stripe Support](https://img.shields.io/badge/Stripe-Support-635BFF?style=for-the-badge&logo=stripe&logoColor=white)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400)
<!-- support:end -->
