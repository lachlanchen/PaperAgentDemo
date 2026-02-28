[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

一个紧凑且与仓库实际状态一致的 LaTeX 论文脚手架，以 `latex/main.tex` 为核心，旨在验证并扩展包含公式、算法、表格、术语表/缩略语、参考文献以及 PDF 构建工具的论文工作流。

| 项目 | 值 |
| --- | --- |
| 主论文文件 | `latex/main.tex` |
| 当前构建方式 | 本地 LaTeX（`latexmk` / `pdflatex`） |
| i18n 文件夹状态 | `i18n/` 已存在（语言文件可逐步添加） |
| License 文件状态 | 当前不存在 |

## 📌 概览

该仓库当前提供：

- 一个主论文源码文件：`latex/main.tex`。
- 具有代表性的论文结构：摘要、方法、算法、结果、讨论与结论。
- 覆盖常见科研写作任务的 LaTeX 宏包（数学、引用、术语表、交叉引用）。
- 位于 `.auto-readme-work/` 下的多语言 README 生成流水线元数据。

重要仓库说明：

- `AGENTS.md` 描述了预期目录（`figures/`、`data/`、`artifacts/`、`code/`），但其中一些在当前目录树中尚未出现。本 README 保留该意图，并明确标注缺失项。

## ✨ 特性

- 通过 `amsmath`、`amssymb`、`bm`、`mathtools` 和 `siunitx` 进行数学排版。
- 通过 `graphicx`、`subcaption`、`booktabs` 和 `multirow` 支持图表与表格。
- 通过 `algorithm` 和 `algpseudocode` 提供算法环境。
- 通过 `natbib` 支持文献引用。
- 通过 `glossaries` 支持术语表与缩略语（已启用 `\makeglossaries`）。
- 通过 `hyperref` 与 `cleveref` 提供交叉引用。
- 已包含示例内容：带 `\ell_1` 正则项的目标函数公式、dB 表示的 SNR 公式、梯度下降伪代码、定量对比表，以及内联参考文献条目。

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
├── i18n/                         # 当前已存在；可逐步添加各语言 README 文件
└── latex/
    ├── main.tex                  # 主论文源码
    ├── main.acn                  # 生成的术语表/缩略语产物
    ├── main.glo                  # 生成的术语表产物
    └── main.ist                  # 术语表样式产物
```

## ✅ 前置要求

安装包含 `latex/main.tex` 所用宏包的 TeX 环境。

最低可用要求：

- `latexmk`
- `pdflatex`
- `bibtex`（用于标准流程中的参考文献处理）
- `glossaries` 工作流所需的术语表工具（通常是 TeX 发行版中的 `makeglossaries`）

假设：

- 本仓库未固定宏包名称与版本；请使用较新的 TeX Live 或 MiKTeX 发行版。

## 📥 安装

克隆仓库并进入目录：

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

仓库当前未定义额外的包管理器安装步骤。

## 🚀 使用

| 任务 | 命令 |
| --- | --- |
| 推荐构建 | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| 快速单次编译 | `pdflatex latex/main.tex` |
| 清理辅助文件 | `latexmk -c latex/main.tex` |

主构建命令（推荐，来自 `AGENTS.md`）：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

单次编译（快速迭代）：

```bash
pdflatex latex/main.tex
```

清理 LaTeX 辅助文件并保留 PDF：

```bash
latexmk -c latex/main.tex
```

预期工作流：

1. 在 `latex/main.tex` 中编辑论文内容。
2. 构建 PDF。
3. 在输出 PDF 中目检版式与引用。

## ⚙️ 配置

当前文档级配置位于 `latex/main.tex`：

- 文档类：`article`，参数为 `11pt,a4paper`。
- 页面布局：`geometry`，`margin=1in`。
- 行距：`\onehalfspacing`。
- 通过自定义 `linkblue` 与 `hyperref` 选项设置链接颜色。
- 已预定义 `CNN`、`SNR`、`HSI` 和 `event camera` 的缩略语与术语表条目。

仓库级忽略行为（`.gitignore`）：

- 默认忽略多数 LaTeX 构建产物（`*.aux`、`*.log`、`*.pdf` 等）。
- 默认忽略 `artifacts/` 与 `data/` 目录。

## 🧪 示例

端到端构建论文：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

先清理再重建：

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

编辑单个章节时快速编译：

```bash
pdflatex latex/main.tex
```

## 🛠 开发说明

来自 `AGENTS.md` 的指导：

- 在清晰的 `\section{}` 标题下组织 LaTeX 源码。
- 统一使用标签前缀：公式用 `eq:`，图片用 `fig:`，表格用 `tab:`，算法用 `alg:`。
- 优先通过 `\cref{}` 进行引用。
- 资源文件名使用小写并以连字符分隔（示例：`figures/snr-comparison.pdf`）。
- 在有帮助时，对嵌套的 LaTeX 块使用两个空格缩进。

验证方式：

- 当前没有自动化测试套件。
- 主要验证方式是成功完成 LaTeX 构建并目检生成的 PDF。

## 🧰 故障排查

常见问题与检查项：

- 构建因缺失宏包失败：从你的 TeX 发行版安装缺失的 LaTeX 宏包。
- 术语表条目未显示：确认已安装术语表工具，并重新运行 `latexmk` 以执行术语表步骤。
- 文献或引用警告持续存在：使用 `latexmk` 重建（自动处理多次编译）。
- 输出 PDF 未被 git 跟踪：这是预期行为，因为当前 `.gitignore` 忽略 `*.pdf`。

## 🗺 路线图

计划中或较可能的下一步（根据仓库文件与指南推断）：

1. 随工作扩展添加 `figures/`、`data/`、`artifacts/` 和 `code/` 目录。
2. 在 `i18n/` 下添加与语言导航链接对应的各语言 README 文件。
3. 在 `code/` 下添加可复现图表生成的可选辅助脚本。
4. 如果项目超出本地模板规模，引入 CI 做构建验证。

## 🤝 贡献

目前尚未定义正式贡献流程，可按以下基线执行：

1. 创建分支。
2. 提交聚焦的变更。
3. 执行一次干净的 LaTeX 构建：

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. 在 PR 中清晰说明论文内容或工具链变更。

来自仓库指南的提交风格建议：

- 使用清晰、祈使语气的提交标题。
- 示例：`Add glossary entries for sensor terms`

## 📄 许可

仓库根目录当前没有 License 文件。

假设：

- 在添加 `LICENSE` 文件之前，当前所有权与复用条款均未明确。

## 📚 参考文献与致谢

`latex/main.tex` 中的示例论文当前包含以下内联参考文献条目：

- Goodfellow, Bengio, and Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

致谢状态：

- 当前仓库文件中没有专门的致谢、赞助或捐助/支持章节。
- 如果外部存在赞助/支持信息，可在此补充，同时不要删除技术内容。
