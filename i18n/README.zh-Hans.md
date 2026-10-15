[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


[![LazyingArt banner — apps and four buddies](https://lazying.art/media/brand/lazyingart-intro.gif)](https://lazying.art)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

这是一个以 `latex/main.tex` 为核心、紧贴仓库内容的精简 LaTeX 论文脚手架，用于验证并扩展以方程、算法、表格、术语表/缩写词、参考文献和 PDF 构建工具为核心的稿件工作流。

## 🧩 一览

| 条目 | 数值 |
| --- | --- |
| 主要稿件文件 | `latex/main.tex` |
| 当前构建方式 | 本地 LaTeX（`latexmk` / `pdflatex`） |
| i18n 文件夹状态 | `i18n/` 已存在（可持续新增语言文件） |
| 许可文件状态 | 目前不存在 |

## 📌 概览

该仓库目前提供：

- 单一主稿件源文件：`latex/main.tex`。
- 包含摘要、方法、算法、结果、讨论与结论的典型论文结构。
- 覆盖常见学术写作任务的 LaTeX 宏包（数学排版、引用、术语表、交叉引用）。
- 多语言 README 生成的管道元数据位于 `.auto-readme-work/`。

重要仓库说明：

- `AGENTS.md` 描述了预期目录（`figures/`、`data/`、`artifacts/`、`code/`），但当前树中部分目录尚未出现。该 README 保留该目标并明确标注缺失项。

## ✨ 特性

- 通过 `amsmath`、`amssymb`、`bm`、`mathtools` 和 `siunitx` 实现数学公式排版。
- 通过 `graphicx`、`subcaption`、`booktabs` 和 `multirow` 支持图表。
- 通过 `algorithm` 和 `algpseudocode` 提供算法环境。
- 通过 `natbib` 提供引用支持。
- 通过 `glossaries`（启用 `\makeglossaries`）支持术语表和缩略词。
- 通过 `hyperref` 与 `cleveref` 提供交叉引用。
- 已包含示例内容：带 `\ell_1` 正则化的目标函数方程、dB 中的 SNR 方程、梯度下降伪代码、定量对比表以及内嵌参考文献条目。

## 🧭 项目结构

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
├── i18n/                         # 当前存在；语言 README 文件可持续添加
└── latex/
    ├── main.tex                  # primary manuscript source
    ├── main.acn                  # generated glossary/acronym artifact
    ├── main.glo                  # generated glossary artifact
    └── main.ist                  # glossary style artifact
```

## ✅ 先决条件

安装包含 `latex/main.tex` 所需宏包的 TeX 环境。

实际最低要求：

- `latexmk`
- `pdflatex`
- `bibtex`（用于标准流程中的参考文献处理）
- `glossaries` 工作流所需的术语表工具（通常来自 TeX 发行版的 `makeglossaries`）

假设：

- 本仓库未对宏包名称和版本进行固定；请使用较新版本的 TeX Live 或 MiKTeX。

## 📥 安装

克隆并进入仓库：

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

当前仓库内未定义额外的包管理器安装步骤。

## 🚀 使用说明

| 任务 | 命令 |
| --- | --- |
| 推荐构建 | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| 快速单次编译 | `pdflatex latex/main.tex` |
| 清理辅助文件 | `latexmk -c latex/main.tex` |

主要构建命令（来自 `AGENTS.md`）：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

快速迭代时可用单次编译：

```bash
pdflatex latex/main.tex
```

清理 LaTeX 中间文件但保留 PDF：

```bash
latexmk -c latex/main.tex
```

预期工作流：

1. 在 `latex/main.tex` 中编辑稿件内容。
2. 构建 PDF。
3. 可视化检查输出 PDF 中的布局和引用。

## ⚙️ 配置

当前文档级配置位于 `latex/main.tex`：

- 文档类：`article`，`11pt,a4paper`。
- 页面布局：`geometry`，`margin=1in`。
- 行距：`\\onehalfspacing`。
- 通过自定义 `linkblue` 与 `hyperref` 选项设置链接颜色。
- 预定义缩略词和术语表条目：`CNN`、`SNR`、`HSI` 与 `event camera`。

仓库级忽略规则（`.gitignore`）：

- 忽略大多数 LaTeX 构建产物（`*.aux`、`*.log`、`*.pdf` 等）。
- 默认忽略 `artifacts/` 与 `data/` 目录。

## 🧪 示例

端到端构建稿件：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

清理后重建：

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

编辑单个章节时的快速编译：

```bash
pdflatex latex/main.tex
```

## 🛠 开发说明

来自 `AGENTS.md` 的指导：

- 将 LaTeX 源代码放在清晰的 `\\section{}` 标题下。
- 统一使用标签前缀：方程用 `eq:`，图示用 `fig:`，表格用 `tab:`，算法用 `alg:`。
- 优先使用 `\\cref{}` 进行引用。
- 资源文件命名统一小写并用连字符（例如 `figures/snr-comparison.pdf`）。
- 在有助于可读性的情况下，用两个空格缩进嵌套的 LaTeX 块。

验证方式：

- 没有自动化测试套件。
- 主要验证方式是成功构建 LaTeX 并对生成的 PDF 进行人工检查。

## 🧰 故障排查

常见问题与检查项：

- 构建因缺少宏包失败：请从 TeX 发行版安装缺失宏包。
- 术语表条目未显示：请确保术语表工具已安装并重新运行 `latexmk`，以执行术语表步骤。
- 引用警告持续存在：使用 `latexmk` 重新构建（其会自动处理多次编译）。
- 输出 PDF 未被 Git 跟踪：这是预期行为，因为当前 `.gitignore` 忽略 `*.pdf`。

## 🗺 路线图

基于仓库文件与指南推断的计划：

1. 随项目推进，新增 `figures/`、`data/`、`artifacts/` 与 `code/` 目录。
2. 在 `i18n/` 下补齐与语言导航对应的 README 文件。
3. 在 `code/` 下增加可复现图表/表格生成的可选辅助脚本。
4. 若项目扩展到本地模板之外，考虑引入构建校验 CI。

## 🤝 贡献

目前尚未定义正式贡献流程，请按以下基线执行：

1. 创建分支。
2. 进行聚焦修改。
3. 运行一次清洁 LaTeX 构建：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. 在 PR 中明确总结稿件或工具变更。

仓库建议的提交规范：

- 使用清晰、祈使式的提交主题。
- 示例：`Add glossary entries for sensor terms`

## 📄 许可证

仓库根目录当前未包含许可证文件。

说明：

- 在添加 `LICENSE` 文件前，所有权利与再利用条款均未明确。

## 📚 参考与致谢

`latex/main.tex` 中的示例稿件目前包含以下内嵌参考文献条目：

- Goodfellow, Bengio, 和 Courville, *Deep Learning*（MIT Press, 2016）。
- Gallego 等, *Event-based vision: A survey*（IEEE TPAMI, 2022）。

致谢说明：

- 当前稿件中暂未设置独立的致谢章节。
- 赞助与支持链接已集中放在上方的 **❤️ Support** 区块。


## ❤️ Support

| Donate | PayPal | Stripe |
| --- | --- | --- |
| [![Donate](https://camo.githubusercontent.com/24a4914f0b42c6f435f9e101621f1e52535b02c225764b2f6cc99416926004b7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f6e6174652d4c617a79696e674172742d3045413545393f7374796c653d666f722d7468652d6261646765266c6f676f3d6b6f2d6669266c6f676f436f6c6f723d7768697465)](https://chat.lazying.art/donate) | [![PayPal](https://camo.githubusercontent.com/d0f57e8b016517a4b06961b24d0ca87d62fdba16e18bbdb6aba28e978dc0ea21/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f50617950616c2d526f6e677a686f754368656e2d3030343537433f7374796c653d666f722d7468652d6261646765266c6f676f3d70617970616c266c6f676f436f6c6f723d7768697465)](https://paypal.me/RongzhouChen) | [![Stripe](https://camo.githubusercontent.com/1152dfe04b6943afe3a8d2953676749603fb9f95e24088c92c97a01a897b4942/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5374726970652d446f6e6174652d3633354246463f7374796c653d666f722d7468652d6261646765266c6f676f3d737472697065266c6f676f436f6c6f723d7768697465)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400) |
