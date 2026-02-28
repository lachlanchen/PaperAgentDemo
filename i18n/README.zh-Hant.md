[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

一個精簡且與儲存庫現況一致的 LaTeX 論文骨架，核心為 `latex/main.tex`，用於驗證與擴充論文工作流程，涵蓋公式、演算法、表格、詞彙表/縮寫、參考文獻與 PDF 建置工具。

| 項目 | 值 |
| --- | --- |
| 主要論文檔案 | `latex/main.tex` |
| 目前建置方式 | 本機 LaTeX（`latexmk` / `pdflatex`） |
| i18n 資料夾狀態 | `i18n/` 已存在（語言檔案可逐步新增） |
| 授權檔案狀態 | 目前不存在 |

## 📌 概覽

此儲存庫目前提供：

- 單一主要論文原始檔：`latex/main.tex`。
- 具代表性的論文結構，包含摘要、方法、演算法、結果、討論與結論。
- 常見研究寫作任務所需的 LaTeX 套件覆蓋（數學、引用、詞彙表、交叉參照）。
- 位於 `.auto-readme-work/` 的多語 README 產線中繼資料。

重要儲存庫說明：

- `AGENTS.md` 描述了預期目錄（`figures/`、`data/`、`artifacts/`、`code/`），但其中部分目錄目前尚未出現在現有樹狀結構中。本 README 保留該設計意圖，並明確標示缺漏項。

## ✨ 功能特色

- 透過 `amsmath`、`amssymb`、`bm`、`mathtools` 與 `siunitx` 進行數學排版。
- 透過 `graphicx`、`subcaption`、`booktabs` 與 `multirow` 支援圖與表。
- 透過 `algorithm` 與 `algpseudocode` 提供演算法環境。
- 透過 `natbib` 支援文獻引用。
- 透過 `glossaries` 支援詞彙表與縮寫（已啟用 `\makeglossaries`）。
- 透過 `hyperref` 與 `cleveref` 進行交叉參照。
- 已內建示例內容：含 `\ell_1` 正則化的目標函數方程式、以 dB 表示的 SNR 方程式、梯度下降偽程式碼、定量比較表，以及行內 bibliography 條目。

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

## ✅ 先決條件

請安裝包含 `latex/main.tex` 所用套件的 TeX 環境。

最低可行需求：

- `latexmk`
- `pdflatex`
- `bibtex`（標準流程中的文獻處理）
- `glossaries` 工作流程所需的詞彙表工具（通常為 TeX 發行版中的 `makeglossaries`）

假設：

- 本儲存庫未釘選套件名稱與版本；請使用近期版本的 TeX Live 或 MiKTeX 發行版。

## 📥 安裝

複製並進入儲存庫：

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

目前儲存庫內尚未定義額外的套件管理器安裝步驟。

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

單次編譯（快速迭代）：

```bash
pdflatex latex/main.tex
```

清理 LaTeX 輔助檔但保留 PDF：

```bash
latexmk -c latex/main.tex
```

預期工作流程：

1. 在 `latex/main.tex` 編輯論文內容。
2. 建置 PDF。
3. 目視檢查輸出 PDF 的版面與交叉參照。

## ⚙️ 設定

目前文件層級設定位於 `latex/main.tex`：

- 文件類別：`article`，選項為 `11pt,a4paper`。
- 版面配置：`geometry`，`margin=1in`。
- 行距：`\onehalfspacing`。
- 透過自訂 `linkblue` 與 `hyperref` 選項設定連結顏色。
- 已預先定義 `CNN`、`SNR`、`HSI` 與 `event camera` 的縮寫與詞彙表條目。

儲存庫層級忽略行為（`.gitignore`）：

- 會忽略多數 LaTeX 建置產物（`*.aux`、`*.log`、`*.pdf` 等）。
- 預設忽略 `artifacts/` 與 `data/` 目錄。

## 🧪 範例

端到端建置論文：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

先清理再重建：

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

編輯單一章節時的快速編譯：

```bash
pdflatex latex/main.tex
```

## 🛠 開發說明

來自 `AGENTS.md` 的建議：

- 將 LaTeX 來源內容置於清楚的 `\section{}` 標題下。
- 一致使用標籤前綴：方程式用 `eq:`、圖用 `fig:`、表格用 `tab:`、演算法用 `alg:`。
- 優先以 `\cref{}` 進行參照。
- 使用小寫連字號命名素材（例如：`figures/snr-comparison.pdf`）。
- 在有助可讀性的情況下，巢狀 LaTeX 區塊以兩個空白縮排。

驗證方式：

- 目前沒有自動化測試。
- 主要驗證方式是 LaTeX 成功建置，加上人工檢查產生的 PDF。

## 🧰 疑難排解

常見問題與檢查項目：

- 建置因缺少套件失敗：從你的 TeX 發行版安裝缺少的 LaTeX 套件。
- 詞彙表條目未顯示：確認已安裝詞彙表工具，並重新執行 `latexmk` 以觸發詞彙表步驟。
- 引用或參照警告持續出現：改用 `latexmk` 重建（可自動處理多次編譯）。
- 輸出 PDF 未被 git 追蹤：這是預期行為，因為 `.gitignore` 目前忽略 `*.pdf`。

## 🗺 路線圖

規劃中或可能的下一步（根據儲存庫檔案與指引推斷）：

1. 隨專案擴展新增 `figures/`、`data/`、`artifacts/` 與 `code/` 目錄。
2. 在 `i18n/` 下新增與語言導覽連結一致的各語系 README 檔。
3. 在 `code/` 下加入可重現圖表/表格產生流程的輔助腳本（可選）。
4. 若專案超出本機樣板規模，導入 CI 進行建置驗證。

## 🤝 貢獻

目前尚未定義正式貢獻流程，可先遵循以下基準：

1. 建立分支。
2. 進行聚焦變更。
3. 執行乾淨的 LaTeX 建置：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. 在 PR 中提供清楚的論文或工具變更摘要。

儲存庫指南建議的 commit 風格：

- 使用清楚、祈使句的 commit 主旨。
- 範例：`Add glossary entries for sensor terms`

## 📄 授權

儲存庫根目錄目前沒有授權檔案。

假設：

- 在加入 `LICENSE` 檔之前，所有權利與再利用條款目前均未明確定義。

## 📚 參考與致謝

`latex/main.tex` 的示例論文目前包含以下行內 bibliography 條目：

- Goodfellow, Bengio, and Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

致謝狀態：

- 目前儲存庫檔案中沒有獨立的致謝、贊助或捐助/支援章節。
- 若贊助/支援資訊存在於儲存庫外部，請在不移除技術內容的前提下加入此處。
