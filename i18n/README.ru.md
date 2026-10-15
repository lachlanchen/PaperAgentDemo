[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


[![LazyingArt banner — apps and four buddies](https://lazying.art/media/brand/lazyingart-intro.gif)](https://lazying.art)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

Компактный, репозиторно-точный каркас научной статьи на LaTeX, ориентированный на `latex/main.tex`, предназначенный для проверки и расширения рабочего процесса работы над рукописью с уравнениями, алгоритмами, таблицами, глоссарием/акронимами, ссылками и инструментами сборки PDF.

## 🧩 Взгляд на проект

| Пункт | Значение |
| --- | --- |
| Основной файл рукописи | `latex/main.tex` |
| Текущий стиль сборки | Локальный LaTeX (`latexmk` / `pdflatex`) |
| Состояние папки i18n | `i18n/` существует (языковые файлы могут добавляться со временем) |
| Состояние файла лицензии | Сейчас отсутствует |

## 📌 Обзор

В текущий момент репозиторий предоставляет:

- Один основной исходный файл рукописи: `latex/main.tex`.
- Типовую структуру статьи с разделами аннотации, методов, алгоритма, результатов, обсуждения и заключения.
- Поддержку LaTeX-пакетов для типичных задач научного письма (математика, цитирование, глоссарий, перекрестные ссылки).
- Метаданные конвейера в `.auto-readme-work/` для генерации многоязычных README.

Важное замечание по репозиторию:

- `AGENTS.md` описывает целевые директории (`figures/`, `data/`, `artifacts/`, `code/`), но часть из них пока еще не присутствует в текущем дереве. Этот README сохраняет этот замысел и явно отмечает отсутствующие элементы.

## ✨ Возможности

- Математическая разметка через `amsmath`, `amssymb`, `bm`, `mathtools` и `siunitx`.
- Поддержка рисунков и таблиц через `graphicx`, `subcaption`, `booktabs` и `multirow`.
- Окружение для алгоритмов через `algorithm` и `algpseudocode`.
- Поддержка цитирований через `natbib`.
- Поддержка глоссария и акронимов через `glossaries` (включён `\makeglossaries`).
- Перекрестные ссылки через `hyperref` и `cleveref`.
- Уже включён примерный контент: целевая функция с `\ell_1`-регуляризацией, уравнение SNR в dB, псевдокод градиентного спуска, количественная сравнительная таблица и встроенные записи библиографии.

## 🧭 Структура проекта

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

## ✅ Предварительные требования

Установите TeX-среду, которая включает пакеты, используемые в `latex/main.tex`.

Минимальные практические требования:

- `latexmk`
- `pdflatex`
- `bibtex` (для обработки библиографии в стандартных сценариях)
- Инструменты для `glossaries`-workflow (обычно `makeglossaries` из вашего TeX-дистрибутива)

Предположения:

- Имена и версии пакетов не фиксированы в этом репозитории; используйте актуальный дистрибутив TeX Live или MiKTeX.

## 📥 Установка

Клонируйте репозиторий и перейдите в него:

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

Дополнительный шаг установки через менеджер пакетов сейчас в репозитории не определён.

## 🚀 Использование

| Задача | Команда |
| --- | --- |
| Рекомендуемая сборка | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| Быстрый одношаговый проход | `pdflatex latex/main.tex` |
| Очистка служебных файлов | `latexmk -c latex/main.tex` |

Основная команда сборки (рекомендуемая, из `AGENTS.md`):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Однопроходная компиляция (для быстрой итерации):

```bash
pdflatex latex/main.tex
```

Очистка вспомогательных файлов LaTeX с сохранением PDF:

```bash
latexmk -c latex/main.tex
```

Ожидаемый рабочий процесс:

1. Редактируйте содержимое рукописи в `latex/main.tex`.
2. Собирайте PDF.
3. Визуально проверяйте макет и ссылки в итоговом PDF.

## ⚙️ Конфигурация

Текущая конфигурация документа находится в `latex/main.tex`:

- Класс документа: `article` с `11pt,a4paper`.
- Разметка страницы: `geometry` с `margin=1in`.
- Межстрочный интервал: `\onehalfspacing`.
- Настройка цветов ссылок через пользовательский стиль `linkblue` и параметры `hyperref`.
- Предопределённые акронимы и записи глоссария для `CNN`, `SNR`, `HSI` и `event camera`.

Игнорирование на уровне репозитория (`.gitignore`):

- Игнорируются большинство артефактов сборки LaTeX (`*.aux`, `*.log`, `*.pdf` и т.д.).
- По умолчанию игнорируются каталоги `artifacts/` и `data/`.

## 🧪 Примеры

Соберите рукопись от начала до конца:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Очистить, затем пересобрать:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Быстрая компиляция при редактировании одного раздела:

```bash
pdflatex latex/main.tex
```

## 🛠 Примечания по разработке

Рекомендации из `AGENTS.md`:

- Держите исходники LaTeX под чёткими заголовками `\section{}`.
- Последовательно используйте префиксы меток: `eq:` для уравнений, `fig:` для рисунков, `tab:` для таблиц и `alg:` для алгоритмов.
- Предпочитайте ссылки через `\cref{}`.
- Используйте имена файлов в нижнем регистре с дефисами (например: `figures/snr-comparison.pdf`).
- Отступайте вложенные LaTeX-блоки двумя пробелами, где это улучшает читаемость.

Подход к валидации:

- Автоматизированных тестов нет.
- Основной контроль — успешная сборка LaTeX и визуальный просмотр итогового PDF.

## 🧰 Устранение неполадок

Частые проблемы и проверки:

- Сборка падает из-за отсутствующего пакета: установите недостающий пакет из вашего TeX-дистрибутива.
- Записи глоссария не появляются: проверьте, что установлены нужные инструменты глоссария, и повторно запустите `latexmk`, чтобы выполнены были шаги глоссария.
- Предупреждения по ссылкам или цитатам не исчезают: пересоберите через `latexmk` (многопроходная сборка выполняется автоматически).
- Сформированный PDF не отслеживается Git: это ожидаемо, поскольку `*.pdf` сейчас игнорируется в `.gitignore`.

## 🗺 Дорожная карта

Планируемые или вероятные следующие шаги (по материалам файлов репозитория и рекомендаций):

1. Добавить директории `figures/`, `data/`, `artifacts/` и `code/` по мере расширения проекта.
2. Добавить языковые версии README в `i18n/`, соответствующие ссылкам навигации.
3. Добавить при желании вспомогательные скрипты для воспроизводимой генерации графиков/таблиц в `code/`.
4. Ввести CI для проверки сборки, если проект выйдет за рамки локального шаблона.

## 🤝 Участие в разработке

Формализованный процесс внесения изменений пока не определён, поэтому используйте такую базовую последовательность:

1. Создайте ветку.
2. Выполняйте точечные правки.
3. Запускайте чистую сборку LaTeX:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. В PR добавьте чёткое резюме изменений в рукописи или инфраструктуре сборки.

Рекомендуемый стиль коммитов из руководства репозитория:

- Используйте понятные императивные заголовки коммитов.
- Пример: `Add glossary entries for sensor terms`

## 📄 Лицензия

В корне репозитория пока отсутствует файл лицензии.

Предпосылка:

- Все права и условия повторного использования пока не определены до добавления файла `LICENSE`.

## 📚 Ссылки и благодарности

Примерная рукопись в `latex/main.tex` сейчас содержит встроенные библиографические записи для:

- Goodfellow, Bengio, and Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

Статус благодарностей:

- В текущих файлах репозитория отдельный раздел благодарностей отсутствует.
- Ссылки на спонсорскую/поддерживающую информацию собраны в разделе **❤️ Support** выше.


## ❤️ Support

<!-- support:start -->
[![GitHub Sponsors](https://img.shields.io/badge/GitHub-Sponsors-EA4AAA?style=for-the-badge&logo=githubsponsors&logoColor=white)](https://github.com/sponsors/lachlanchen)
[![LazyingArt Support](https://img.shields.io/badge/LazyingArt-Support-0EA5E9?style=for-the-badge)](https://chat.lazying.art/donate)
[![PayPal Support](https://img.shields.io/badge/PayPal-Support-00457C?style=for-the-badge&logo=paypal&logoColor=white)](https://paypal.me/RongzhouChen)
[![Stripe Support](https://img.shields.io/badge/Stripe-Support-635BFF?style=for-the-badge&logo=stripe&logoColor=white)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400)
<!-- support:end -->
