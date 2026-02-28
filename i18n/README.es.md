[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


[![LazyingArt banner](https://github.com/lachlanchen/lachlanchen/raw/main/figs/banner.png)](https://github.com/lachlanchen/lachlanchen/blob/main/figs/banner.png)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

Un esqueleto de manuscrito LaTeX compacto y fiel al repositorio, centrado en `latex/main.tex`, diseñado para validar y ampliar un flujo de trabajo de manuscrito con ecuaciones, algoritmos, tablas, glosario/acrónimos, referencias y herramientas de compilación de PDF.

## 🧩 A primera vista

| Elemento | Valor |
| --- | --- |
| Archivo principal del manuscrito | `latex/main.tex` |
| Estilo de compilación actual | LaTeX local (`latexmk` / `pdflatex`) |
| Estado de la carpeta i18n | `i18n/` existe (pueden añadirse archivos de idioma con el tiempo) |
| Estado del archivo de licencia | Actualmente no está presente |

## 📌 Resumen

Este repositorio actualmente proporciona:

- Un único archivo principal de manuscrito: `latex/main.tex`.
- Una estructura de paper representativa con abstract, métodos, algoritmo, resultados, discusión y conclusión.
- Cobertura de paquetes LaTeX para tareas de escritura científica comunes (matemáticas, citas, glosario, referencias cruzadas).
- Metadatos de pipeline bajo `.auto-readme-work/` para la generación multilingüe del README.

Nota importante del repositorio:

- `AGENTS.md` describe los directorios objetivo (`figures/`, `data/`, `artifacts/`, `code/`), pero algunos aún no están presentes en el árbol actual. Este README conserva esa intención y marca explícitamente los elementos faltantes.

## ✨ Características

- Composición matemática con `amsmath`, `amssymb`, `bm`, `mathtools` y `siunitx`.
- Soporte de figuras y tablas mediante `graphicx`, `subcaption`, `booktabs` y `multirow`.
- Entorno de algoritmos mediante `algorithm` y `algpseudocode`.
- Soporte de citas mediante `natbib`.
- Soporte de glosario y acrónimos mediante `glossaries` (`\makeglossaries` habilitado).
- Referencias cruzadas mediante `hyperref` y `cleveref`.
- Contenido de ejemplo incluido: ecuación de función objetivo con regularización `\ell_1`, ecuación de SNR en dB, pseudocódigo de descenso por gradiente, una tabla de comparación cuantitativa y entradas bibliográficas en línea.

## 🧭 Estructura del proyecto

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
├── i18n/                         # actualmente presente; los archivos README por idioma pueden añadirse con el tiempo
└── latex/
    ├── main.tex                  # fuente principal del manuscrito
    ├── main.acn                  # artefacto de acrónimos generado
    ├── main.glo                  # artefacto de glosario generado
    └── main.ist                  # estilo de glosario generado
```

## ✅ Requisitos previos

Instala un entorno TeX que incluya los paquetes usados por `latex/main.tex`.

Requisitos prácticos mínimos:

- `latexmk`
- `pdflatex`
- `bibtex` (para el manejo de bibliografía en flujos estándar)
- Herramientas de glosario requeridas por los flujos de `glossaries` (normalmente `makeglossaries` de la distribución TeX)

Suposición:

- Los nombres y versiones de paquetes no están fijados en este repositorio; usa una distribución reciente de TeX Live o MiKTeX.

## 📥 Instalación

Clona y entra al repositorio:

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

No existe actualmente un paso adicional de instalación de gestores de paquetes definido en el repositorio.

## 🚀 Uso

| Tarea | Comando |
| --- | --- |
| Construcción recomendada | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| Pase único rápido | `pdflatex latex/main.tex` |
| Limpiar archivos auxiliares | `latexmk -c latex/main.tex` |

Comando de compilación principal (recomendado, de `AGENTS.md`):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Compilación de una sola pasada (para iteración rápida):

```bash
pdflatex latex/main.tex
```

Limpiar archivos auxiliares de LaTeX dejando el PDF:

```bash
latexmk -c latex/main.tex
```

Flujo de trabajo esperado:

1. Edita el contenido del manuscrito en `latex/main.tex`.
2. Compila el PDF.
3. Revisa visualmente el diseño y las referencias en el PDF generado.

## ⚙️ Configuración

La configuración actual a nivel de documento está en `latex/main.tex`:

- Clase del documento: `article` con `11pt,a4paper`.
- Diseño de página: `geometry` con `margin=1in`.
- Espaciado: `\onehalfspacing`.
- Configuración de color de enlaces vía `linkblue` personalizado y opciones de `hyperref`.
- Entradas de acrónimos y glosario predefinidas para `CNN`, `SNR`, `HSI` y `event camera`.

Comportamiento de exclusión a nivel de repositorio (`.gitignore`):

- Ignora la mayoría de artefactos de compilación LaTeX (`*.aux`, `*.log`, `*.pdf`, etc.).
- Ignora por defecto los directorios `artifacts/` y `data/`.

## 🧪 Ejemplos

Compila el manuscrito de extremo a extremo:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Limpia y recompila:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Compila rápidamente mientras editas una sola sección:

```bash
pdflatex latex/main.tex
```

## 🛠 Notas de desarrollo

Guías de `AGENTS.md`:

- Mantén el código LaTeX bajo encabezados `\section{}` claros.
- Usa prefijos de etiquetas de forma consistente: `eq:` para ecuaciones, `fig:` para figuras, `tab:` para tablas y `alg:` para algoritmos.
- Prefiere referencias con `\cref{}`.
- Usa nombres de archivo en minúsculas y con guiones (por ejemplo, `figures/snr-comparison.pdf`).
- Indenta con dos espacios los bloques LaTeX anidados cuando sea útil.

Enfoque de validación:

- No existe una suite de pruebas automatizada.
- La validación principal es una compilación LaTeX correcta más inspección visual del PDF generado.

## 🧰 Solución de problemas

Problemas y comprobaciones comunes:

- La compilación falla por paquete faltante: instala paquetes LaTeX que falten desde tu distribución TeX.
- Las entradas del glosario no aparecen: asegúrate de que las herramientas del glosario estén instaladas y vuelve a ejecutar `latexmk` para que se ejecuten los pasos de glosario.
- Persisten advertencias de citas o referencias: recompila con `latexmk` (las pasadas múltiples se gestionan automáticamente).
- El PDF de salida no aparece en git: esto es esperable porque `*.pdf` se ignora actualmente en `.gitignore`.

## 🗺️ Hoja de ruta

Próximos pasos planificados o probables (inferidos desde los archivos del repositorio y las guías):

1. Añadir los directorios `figures/`, `data/`, `artifacts/` y `code/` conforme crezca el trabajo.
2. Añadir archivos README por idioma bajo `i18n/` que coincidan con los enlaces de navegación.
3. Añadir scripts opcionales de ayuda para generación reproducible de figuras/tablas bajo `code/`.
4. Introducir CI para verificación de compilación si el proyecto crece más allá de una plantilla local.

## 🤝 Contributing

No existe actualmente un flujo formal de contribución definido, así que usa esta base:

1. Crea una rama.
2. Realiza cambios enfocados.
3. Ejecuta una compilación limpia de LaTeX:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. Incluye un resumen claro de los cambios en el manuscrito o la herramienta en tu PR.

Estilo de commits sugerido por las guías del repositorio:

- Usa asuntos de commit claros e imperativos.
- Ejemplo: `Add glossary entries for sensor terms`

## 📄 Licencia

Actualmente no existe un archivo de licencia en la raíz del repositorio.

Suposición:

- Los términos de derechos y reutilización siguen sin especificarse hasta que se añada un archivo `LICENSE`.

## 📚 Referencias y agradecimientos

El manuscrito de ejemplo en `latex/main.tex` incluye actualmente entradas bibliográficas en línea para:

- Goodfellow, Bengio y Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

Estado de agradecimientos:

- Actualmente no hay una sección dedicada de agradecimientos en el manuscrito.
- Los enlaces de patrocinio/soporte se consolidan en la sección **❤️ Support** anterior.


## ❤️ Support

| Donate | PayPal | Stripe |
| --- | --- | --- |
| [![Donate](https://camo.githubusercontent.com/24a4914f0b42c6f435f9e101621f1e52535b02c225764b2f6cc99416926004b7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f6e6174652d4c617a79696e674172742d3045413545393f7374796c653d666f722d7468652d6261646765266c6f676f3d6b6f2d6669266c6f676f436f6c6f723d7768697465)](https://chat.lazying.art/donate) | [![PayPal](https://camo.githubusercontent.com/d0f57e8b016517a4b06961b24d0ca87d62fdba16e18bbdb6aba28e978dc0ea21/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f50617950616c2d526f6e677a686f754368656e2d3030343537433f7374796c653d666f722d7468652d6261646765266c6f676f3d70617970616c266c6f676f436f6c6f723d7768697465)](https://paypal.me/RongzhouChen) | [![Stripe](https://camo.githubusercontent.com/1152dfe04b6943afe3a8d2953676749603fb9f95e24088c92c97a01a897b4942/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5374726970652d446f6e6174652d3633354246463f7374796c653d666f722d7468652d6261646765266c6f676f3d737472697065266c6f676f436f6c6f723d7768697465)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400) |
