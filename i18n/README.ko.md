[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


[![LazyingArt banner — apps and four buddies](https://github.com/lachlanchen/LazyingArtWebsite/raw/main/media/brand/lazyingart-intro.gif)](https://lazying.art)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

`latex/main.tex`를 중심으로 구성된, 저장소 실제 상태와 일치하는 간결한 LaTeX 논문 스캐폴드입니다. 수식, 알고리즘, 표, 용어집/약어, 참고문헌, PDF 빌드 도구를 포함한 원고 워크플로를 검증하고 확장하도록 설계되었습니다.

## 🧩 한눈에 보기

| 항목 | 값 |
| --- | --- |
| 기본 원고 파일 | `latex/main.tex` |
| 현재 빌드 방식 | 로컬 LaTeX (`latexmk` / `pdflatex`) |
| i18n 폴더 상태 | `i18n/` 존재 (언어 파일은 점진적으로 추가 가능) |
| 라이선스 파일 상태 | 현재 없음 |

## 📌 개요

이 저장소는 현재 다음을 제공합니다.

- 단일 메인 원고 소스 파일: `latex/main.tex`.
- 초록, 방법론, 알고리즘, 결과, 논의, 결론을 포함한 대표적인 논문 구조.
- 일반적인 연구 논문 작성 작업을 위한 LaTeX 패키지 구성(수학, 인용, 용어집, 교차 참조).
- 다국어 README 생성을 위한 `.auto-readme-work/` 하위 파이프라인 메타데이터.

저장소 중요 안내:

- `AGENTS.md`에는 의도된 디렉터리(`figures/`, `data/`, `artifacts/`, `code/`)가 설명되어 있으나, 현재 트리에는 일부가 아직 없습니다. 이 README는 해당 의도를 유지하며 누락된 요소를 명시적으로 표시합니다.

## ✨ 기능

- `amsmath`, `amssymb`, `bm`, `mathtools`, `siunitx`를 통한 수학 조판.
- `graphicx`, `subcaption`, `booktabs`, `multirow`를 통한 그림/표 지원.
- `algorithm` 및 `algpseudocode`를 통한 알고리즘 환경.
- `natbib` 기반 인용 지원.
- `glossaries` 기반 용어집 및 약어 지원(`\makeglossaries` 활성화).
- `hyperref` 및 `cleveref` 기반 교차 참조.
- 이미 포함된 예시 콘텐츠: `\ell_1` 정규화가 포함된 목적 함수 식, dB 단위 SNR 식, 경사하강법 의사코드, 정량 비교 표, 인라인 참고문헌 항목.

## 🧭 프로젝트 구조

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
├── i18n/                         # 현재 존재; 언어별 README 파일은 점진적으로 추가 가능
└── latex/
    ├── main.tex                  # 기본 원고 소스
    ├── main.acn                  # 생성된 용어집/약어 산출물
    ├── main.glo                  # 생성된 용어집 산출물
    └── main.ist                  # 용어집 스타일 산출물
```

## ✅ 선행 조건

`latex/main.tex`에서 사용하는 패키지를 포함한 TeX 환경을 설치하세요.

실사용 기준 최소 요구 사항:

- `latexmk`
- `pdflatex`
- `bibtex` (표준 워크플로에서 참고문헌 처리용)
- `glossaries` 워크플로에 필요한 용어집 도구(일반적으로 TeX 배포판의 `makeglossaries`)

가정:

- 이 저장소에서는 패키지 이름과 버전을 고정하지 않습니다. 최신 TeX Live 또는 MiKTeX 배포판을 사용하세요.

## 📥 설치

저장소를 클론하고 진입합니다.

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

현재 저장소 내부에는 추가 패키지 매니저 설치 단계가 정의되어 있지 않습니다.

## 🚀 사용법

| 작업 | 명령어 |
| --- | --- |
| 권장 빌드 | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| 빠른 단일 패스 | `pdflatex latex/main.tex` |
| 보조 파일 정리 | `latexmk -c latex/main.tex` |

기본 빌드 명령(권장, `AGENTS.md` 기준):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

단일 패스 컴파일(빠른 반복 작업):

```bash
pdflatex latex/main.tex
```

PDF를 유지한 채 LaTeX 보조 파일 정리:

```bash
latexmk -c latex/main.tex
```

권장 워크플로:

1. `latex/main.tex`에서 원고 내용을 수정합니다.
2. PDF를 빌드합니다.
3. 출력 PDF에서 레이아웃과 참조를 시각적으로 점검합니다.

## ⚙️ 설정

현재 문서 수준 설정은 `latex/main.tex`에 있습니다.

- 문서 클래스: `11pt,a4paper`의 `article`.
- 페이지 레이아웃: `margin=1in`의 `geometry`.
- 줄 간격: `\onehalfspacing`.
- 사용자 정의 `linkblue` 및 `hyperref` 옵션을 통한 링크 색상 설정.
- `CNN`, `SNR`, `HSI`, `event camera`에 대한 약어/용어집 항목 사전 정의.

저장소 수준 ignore 동작(`.gitignore`):

- 대부분의 LaTeX 빌드 산출물(`*.aux`, `*.log`, `*.pdf` 등)을 무시.
- 기본적으로 `artifacts/` 및 `data/` 디렉터리를 무시.

## 🧪 예시

원고를 엔드투엔드로 빌드:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

정리 후 재빌드:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

한 섹션을 편집하면서 빠르게 컴파일:

```bash
pdflatex latex/main.tex
```

## 🛠 개발 노트

`AGENTS.md`의 가이드:

- LaTeX 소스는 명확한 `\section{}` 헤딩 아래에 유지합니다.
- 라벨 접두사는 일관되게 사용합니다: 수식 `eq:`, 그림 `fig:`, 표 `tab:`, 알고리즘 `alg:`.
- 참조는 `\cref{}` 사용을 우선합니다.
- 에셋 파일명은 소문자 하이픈 형식을 사용합니다(예: `figures/snr-comparison.pdf`).
- 중첩된 LaTeX 블록은 필요 시 두 칸 들여쓰기를 사용합니다.

검증 방식:

- 자동 테스트 스위트는 없습니다.
- 기본 검증은 LaTeX 빌드 성공 + 생성된 PDF 시각 점검입니다.

## 🧰 문제 해결

자주 발생하는 문제와 점검 항목:

- 빌드가 누락 패키지로 실패: TeX 배포판에서 필요한 LaTeX 패키지를 설치하세요.
- 용어집 항목이 출력되지 않음: 용어집 도구 설치 여부를 확인하고, 용어집 단계가 실행되도록 `latexmk`를 다시 실행하세요.
- 인용/참조 경고가 계속됨: `latexmk`로 재빌드하세요(여러 패스가 자동 처리됨).
- 출력 PDF가 git에서 추적되지 않음: `.gitignore`에서 현재 `*.pdf`를 무시하므로 정상 동작입니다.

## 🗺 로드맵

예상되거나 예정된 다음 단계(저장소 파일 및 가이드 기준 추론):

1. 작업 확장에 맞춰 `figures/`, `data/`, `artifacts/`, `code/` 디렉터리를 추가.
2. 언어 네비게이션 링크와 일치하는 언어별 README 파일을 `i18n/` 아래에 추가.
3. 재현 가능한 그림/표 생성을 위해 `code/` 아래에 선택적 헬퍼 스크립트 추가.
4. 프로젝트가 로컬 템플릿을 넘어 확장될 경우 빌드 검증용 CI 도입.

## 🤝 기여

현재 공식 기여 워크플로는 정의되어 있지 않으므로 다음 기본 절차를 사용하세요.

1. 브랜치를 생성합니다.
2. 범위를 좁힌 변경을 적용합니다.
3. 깨끗한 LaTeX 빌드를 실행합니다.

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. PR에 원고 또는 도구 변경 사항을 명확히 요약해 포함합니다.

저장소 가이드의 권장 커밋 스타일:

- 명확한 명령형 커밋 제목을 사용합니다.
- 예시: `Add glossary entries for sensor terms`

## 📄 라이선스

현재 저장소 루트에는 라이선스 파일이 없습니다.

가정:

- `LICENSE` 파일이 추가되기 전까지 모든 권리 및 재사용 조건은 지정되지 않은 상태입니다.

## 📚 참고문헌 및 감사의 글

`latex/main.tex`의 샘플 원고에는 현재 다음 인라인 참고문헌 항목이 포함되어 있습니다.

- Goodfellow, Bengio, and Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

감사의 글 상태:

- 저장소 파일에는 현재 전용 감사의 글 섹션이 없습니다.
- 후원/지원 링크는 위의 **❤️ Support** 섹션에 통합되어 있습니다.


## ❤️ Support

| Donate | PayPal | Stripe |
| --- | --- | --- |
| [![Donate](https://camo.githubusercontent.com/24a4914f0b42c6f435f9e101621f1e52535b02c225764b2f6cc99416926004b7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f6e6174652d4c617a79696e674172742d3045413545393f7374796c653d666f722d7468652d6261646765266c6f676f3d6b6f2d6669266c6f676f436f6c6f723d7768697465)](https://chat.lazying.art/donate) | [![PayPal](https://camo.githubusercontent.com/d0f57e8b016517a4b06961b24d0ca87d62fdba16e18bbdb6aba28e978dc0ea21/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f50617950616c2d526f6e677a686f754368656e2d3030343537433f7374796c653d666f722d7468652d6261646765266c6f676f3d70617970616c266c6f676f436f6c6f723d7768697465)](https://paypal.me/RongzhouChen) | [![Stripe](https://camo.githubusercontent.com/1152dfe04b6943afe3a8d2953676749603fb9f95e24088c92c97a01a897b4942/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5374726970652d446f6e6174652d3633354246463f7374796c653d666f722d7468652d6261646765266c6f676f3d737472697065266c6f676f436f6c6f723d7768697465)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400) |
