[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

Una plantilla compacta y fiel al repositorio para artículos en LaTeX, centrada en `latex/main.tex`, diseñada para validar y ampliar un flujo de trabajo de manuscritos con ecuaciones, algoritmos, tablas, glosario/acrónimos, referencias y herramientas de compilación a PDF.

| Elemento | Valor |
| --- | --- |
| Archivo principal del manuscrito | `latex/main.tex` |
| Estilo de compilación actual | LaTeX local (`latexmk` / `pdflatex`) |
| Estado de la carpeta i18n | `i18n/` existe (se pueden añadir archivos de idioma con el tiempo) |
| Estado del archivo de licencia | No está presente actualmente |

## 📌 Resumen

Este repositorio ofrece actualmente:

- Un único archivo fuente principal del manuscrito: `latex/main.tex`.
- Una estructura de artículo representativa con resumen, métodos, algoritmo, resultados, discusión y conclusión.
- Cobertura de paquetes LaTeX para tareas comunes de redacción científica (matemáticas, citas, glosario, referencias cruzadas).
- Metadatos de pipeline en `.auto-readme-work/` para generación multilingüe del README.

Nota importante del repositorio:

- `AGENTS.md` describe directorios previstos (`figures/`, `data/`, `artifacts/`, `code/`), pero algunos de ellos todavía no están presentes en el árbol actual. Este README conserva esa intención y marca explícitamente las partes faltantes.

## ✨ Características

- Composición matemática mediante `amsmath`, `amssymb`, `bm`, `mathtools` y `siunitx`.
- Soporte para figuras y tablas mediante `graphicx`, `subcaption`, `booktabs` y `multirow`.
- Entorno de algoritmos mediante `algorithm` y `algpseudocode`.
- Soporte de citas mediante `natbib`.
- Soporte de glosario y acrónimos mediante `glossaries` (`\makeglossaries` habilitado).
- Referencias cruzadas mediante `hyperref` y `cleveref`.
- Contenido de ejemplo ya incluido: ecuación de función objetivo con regularización `\ell_1`, ecuación de SNR en dB, pseudocódigo de descenso por gradiente, una tabla de comparación cuantitativa y entradas bibliográficas en línea.

## 🧭 Estructura del Proyecto

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
├── i18n/                         # actualmente presente; se pueden añadir archivos README de idioma con el tiempo
└── latex/
    ├── main.tex                  # fuente principal del manuscrito
    ├── main.acn                  # artefacto generado de glosario/acrónimos
    ├── main.glo                  # artefacto generado de glosario
    └── main.ist                  # artefacto de estilo de glosario
```

## ✅ Requisitos Previos

Instala un entorno TeX que incluya los paquetes usados por `latex/main.tex`.

Requisitos prácticos mínimos:

- `latexmk`
- `pdflatex`
- `bibtex` (para manejo de bibliografía en flujos estándar)
- Herramientas de glosario requeridas por flujos de `glossaries` (normalmente `makeglossaries` en la distribución TeX)

Suposición:

- Los nombres y versiones de paquetes no están fijados en este repositorio; usa una distribución reciente de TeX Live o MiKTeX.

## 📥 Instalación

Clona el repositorio y entra en él:

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

Actualmente no hay un paso adicional de instalación con gestor de paquetes definido dentro del repositorio.

## 🚀 Uso

| Tarea | Comando |
| --- | --- |
| Compilación recomendada | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| Compilación rápida de una pasada | `pdflatex latex/main.tex` |
| Limpiar archivos auxiliares | `latexmk -c latex/main.tex` |

Comando principal de compilación (recomendado, desde `AGENTS.md`):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Compilación de una pasada (iteración rápida):

```bash
pdflatex latex/main.tex
```

Limpia archivos auxiliares de LaTeX manteniendo el PDF:

```bash
latexmk -c latex/main.tex
```

Flujo de trabajo esperado:

1. Edita el contenido del manuscrito en `latex/main.tex`.
2. Compila el PDF.
3. Inspecciona visualmente el diseño y las referencias en el PDF de salida.

## ⚙️ Configuración

La configuración actual a nivel de documento está en `latex/main.tex`:

- Clase de documento: `article` con `11pt,a4paper`.
- Diseño de página: `geometry` con `margin=1in`.
- Espaciado: `\onehalfspacing`.
- Configuración de color de enlaces mediante `linkblue` personalizado y opciones de `hyperref`.
- Acrónimos y entradas de glosario predefinidos para `CNN`, `SNR`, `HSI` y `event camera`.

Comportamiento de ignore a nivel de repositorio (`.gitignore`):

- Ignora la mayoría de artefactos de compilación de LaTeX (`*.aux`, `*.log`, `*.pdf`, etc.).
- Ignora por defecto los directorios `artifacts/` y `data/`.

## 🧪 Ejemplos

Compila el manuscrito de extremo a extremo:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Limpia y vuelve a compilar:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Compilación rápida mientras editas una sección:

```bash
pdflatex latex/main.tex
```

## 🛠 Notas de Desarrollo

Guía de `AGENTS.md`:

- Mantén el código fuente LaTeX bajo encabezados `\section{}` claros.
- Usa prefijos de etiquetas de forma consistente: `eq:` para ecuaciones, `fig:` para figuras, `tab:` para tablas y `alg:` para algoritmos.
- Prefiere referencias mediante `\cref{}`.
- Usa nombres de recursos en minúsculas y con guiones (ejemplo: `figures/snr-comparison.pdf`).
- Indenta bloques LaTeX anidados con dos espacios cuando sea útil.

Enfoque de validación:

- No hay un conjunto de pruebas automatizadas.
- La validación principal es una compilación LaTeX exitosa más una inspección visual del PDF generado.

## 🧰 Solución de Problemas

Problemas comunes y comprobaciones:

- La compilación falla por paquete faltante: instala los paquetes LaTeX faltantes desde tu distribución TeX.
- Las entradas del glosario no aparecen: asegúrate de que las herramientas de glosario estén instaladas y vuelve a ejecutar `latexmk` para que se ejecuten los pasos del glosario.
- Persisten advertencias de citas o referencias: recompila con `latexmk` (las múltiples pasadas se gestionan automáticamente).
- El PDF de salida no está rastreado por git: esto es esperado porque actualmente `*.pdf` está ignorado en `.gitignore`.

## 🗺 Hoja de Ruta

Siguientes pasos planificados o probables (inferidos a partir de archivos y guías del repositorio):

1. Añadir directorios `figures/`, `data/`, `artifacts/` y `code/` a medida que el trabajo se amplíe.
2. Añadir archivos README específicos de idioma en `i18n/` que coincidan con los enlaces de navegación de idioma.
3. Añadir scripts auxiliares opcionales para generación reproducible de figuras/tablas bajo `code/`.
4. Introducir CI para verificación de compilación si el proyecto crece más allá de una plantilla local.

## 🤝 Contribuciones

Actualmente no hay un flujo formal de contribución definido, así que usa esta base:

1. Crea una rama.
2. Haz cambios enfocados.
3. Ejecuta una compilación LaTeX limpia:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. Incluye un resumen claro de los cambios del manuscrito o de herramientas en tu PR.

Estilo de commits sugerido según la guía del repositorio:

- Usa asuntos de commit claros e imperativos.
- Ejemplo: `Add glossary entries for sensor terms`

## 📄 Licencia

Actualmente no hay un archivo de licencia en la raíz del repositorio.

Suposición:

- Todos los derechos y términos de reutilización no están especificados por ahora, hasta que se agregue un archivo `LICENSE`.

## 📚 Referencias y Agradecimientos

El manuscrito de ejemplo en `latex/main.tex` incluye actualmente entradas bibliográficas en línea para:

- Goodfellow, Bengio y Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

Estado de agradecimientos:

- Actualmente no hay una sección dedicada de agradecimientos, patrocinio o donaciones/soporte en los archivos del repositorio.
- Si existe información de patrocinio/soporte externamente, añádela aquí sin eliminar contenido técnico.
