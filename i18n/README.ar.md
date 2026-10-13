[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


[![LazyingArt banner](https://github.com/lachlanchen/lachlanchen/raw/main/figs/banner.png)](https://lazying.art)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

هيكل مخطط ورقة بحثية بلاتكس مضغوط ودقيق يتوافق مع المستودع، يركّز على `latex/main.tex`، ومصمَّم للتحقق من مسار المخطط الموسع للمخطوط عبر المعادلات والخوارزميات والجداول والقواميس/الاختصارات والمراجع وأدوات بناء PDF.

## 🧩 نظرة سريعة

| البند | القيمة |
| --- | --- |
| ملف المخطوط الأساسي | `latex/main.tex` |
| نمط البناء الحالي | LaTeX محلي (`latexmk` / `pdflatex`) |
| حالة مجلد i18n | `i18n/` موجود (قد تُضاف ملفات لغة لاحقًا) |
| حالة ملف الترخيص | غير موجود حاليًا |

## 📌 نظرة عامة

يوفّر هذا المستودع حاليًا:

- ملفًا رئيسيًا واحدًا للمخطوط: `latex/main.tex`.
- بنية ورقة تمثيلية تتضمن الملخص، المنهجية، الخوارزمية، النتائج، النقاش، والخلاصة.
- تغطية حزم LaTeX لمهام كتابة الأبحاث الشائعة (الرياضيات، الاقتباسات، القواميس، والمراجع المتبادلة).
- بيانات وصفية لأنبوب الترجمة في `.auto-readme-work/` لإنشاء نسخ README متعددة اللغات.

ملاحظة مهمة للمستودع:

- يصف ملف `AGENTS.md` المجلدات المقصودة (`figures/`, `data/`, `artifacts/`, `code/`)، لكن بعضها غير موجود بعد في الشجرة الحالية. يحافظ هذا الـ README على هذا القصد ويُبيّن العناصر الناقصة بوضوح.

## ✨ الميزات

- تنسيق رياضي باستخدام `amsmath` و`amssymb` و`bm` و`mathtools` و`siunitx`.
- دعم الرسوم والجداول عبر `graphicx` و`subcaption` و`booktabs` و`multirow`.
- بيئة خوارزميات باستخدام `algorithm` و`algpseudocode`.
- دعم المراجع باستخدام `natbib`.
- دعم القواميس والاختصارات عبر `glossaries` (`\makeglossaries` مفعّل).
- مراجع متبادلة عبر `hyperref` و`cleveref`.
- محتوى نموذجي مضمّن بالفعل: معادلة دالة هدف مع تنظيم `\ell_1`، معادلة SNR بوحدة dB، شبه كود لهبوط التدرج، جدول مقارنة كمي، وإدخالات مراجع مضمنة.

## 🧭 هيكل المشروع

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

## ✅ المتطلبات المسبقة

ثبّت بيئة TeX التي تحتوي الحزم المستخدمة في `latex/main.tex`.

المتطلبات العملية الدنيا:

- `latexmk`
- `pdflatex`
- `bibtex` (لمعالجة المراجع في سير العمل القياسي)
- أدوات القواميس المطلوبة لمسارات `glossaries` (عادةً `makeglossaries` من توزيع TeX)

الافتراض:

- أسماء الإصدارات غير مثبتة في هذا المستودع؛ استخدم إصدارًا حديثًا من TeX Live أو MiKTeX.

## 📥 التثبيت

استنساخ المستودع والدخول إليه:

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

لا توجد حاليًا خطوة منفصلة لتثبيت مدير حزم إضافي داخل المستودع.

## 🚀 طريقة الاستخدام

| المهمة | الأمر |
| --- | --- |
| بناء موصى به | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| مرور واحد سريع | `pdflatex latex/main.tex` |
| تنظيف الملفات المساعدة | `latexmk -c latex/main.tex` |

أمر البناء الأساسي (موصى به، كما في `AGENTS.md`):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

ترجمة أحادية المرور (لتكرار سريع):

```bash
pdflatex latex/main.tex
```

تنظيف ملفات المساعدة في LaTeX مع الإبقاء على PDF:

```bash
latexmk -c latex/main.tex
```

سير العمل المتوقع:

1. عدّل محتوى المخطوط في `latex/main.tex`.
2. نفّذ البناء.
3. راجع ملف PDF بصريًا للتحقق من التخطيط والمراجع.

## ⚙️ الإعداد

الإعدادات على مستوى المستند موجودة الآن في `latex/main.tex`:

- نوع المستند: `article` مع `11pt,a4paper`.
- تخطيط الصفحة: `geometry` مع `margin=1in`.
- تباعد الأسطر: `\onehalfspacing`.
- إعداد ألوان الروابط عبر `linkblue` مخصص وخيارات `hyperref`.
- الاختصارات والمفردات المعرفة مسبقًا تشمل `CNN` و`SNR` و`HSI` و`event camera`.

سلوك التجاهل على مستوى المستودع (`.gitignore`):

- يتجاهل معظم ملفات مخرجات LaTeX (`*.aux`, `*.log`, `*.pdf`, وما إلى ذلك).
- يتجاهل المجلدين `artifacts/` و`data/` بشكل افتراضي.

## 🧪 أمثلة

ابنِ المخطوط من طرف إلى طرف:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

نظّف ثم أعد البناء:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

ترجمة سريعة أثناء تعديل قسم واحد:

```bash
pdflatex latex/main.tex
```

## 🛠 ملاحظات التطوير

توجيهات من `AGENTS.md`:

- احتفظ بمصدر LaTeX تحت عناوين واضحة من نوع `\section{}`.
- استخدم البوادئ المتسقة للوسوم: `eq:` للمعادلات، `fig:` للرسوم، `tab:` للجداول، و`alg:` للخوارزميات.
- يفضّل الإحالة عبر `\cref{}`.
- استخدم أسماء أصول بأحرف صغيرة ومتّصلة بـ `-` (مثال: `figures/snr-comparison.pdf`).
- ضع مسافات بادئة بحرفين في الكتل المتداخلة حيث تفيد القراءة.

نهج التحقق:

- لا توجد مجموعة اختبارات آلية.
- التحقق الأساسي هو بناء LaTeX ناجح مع فحص بصري لملف PDF الناتج.

## 🧰 استكشاف الأخطاء

المشكلات الشائعة والتحقق منها:

- يفشل البناء بسبب حزمة مفقودة: ثبّت الحزمة الناقصة من توزيع TeX.
- لا تظهر إدخالات القواميس: تأكد من تثبيت أدوات القواميس وأعد تشغيل `latexmk` حتى تُنفّذ خطوات القواميس.
- تستمر تحذيرات الاقتباس أو المرجعية: أعد البناء باستخدام `latexmk` (عمليات المرور المتعددة تتم تلقائيًا).
- ملف PDF الناتج غير متعقب ضمن git: هذا متوقع لأن `*.pdf` مُستبعد حاليًا في `.gitignore`.

## 🗺 خارطة الطريق

الخطوات التالية المتوقعة (مستندة إلى الملفات والإرشادات):

1. إضافة المجلدات `figures/` و`data/` و`artifacts/` و`code/` مع توسّع العمل.
2. إضافة ملفات README بلغات أخرى ضمن `i18n/` لتطابق روابط التنقل بين اللغات.
3. إضافة سكربتات مساعدة اختيارية لتوليد الرسوم والجداول بشكل قابل للتكرار ضمن `code/`.
4. إدخال CI للتحقق من البناء إذا نمت المشروع من قالب محلي إلى سير عمل أكبر.

## 🤝 المساهمة

لا يوجد الآن سير عمل مساهمة رسمي، لذا استخدم الأساس التالي:

1. أنشئ فرعًا.
2. أجرِ تغييرات مركزة.
3. نفّذ بناء LaTeX نظيفًا:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. أضف ملخصًا واضحًا للتغييرات في المخطوط أو أدواته داخل طلب الدمج.

نمط الالتزام المقترح من إرشادات المستودع:

- استخدم عناوين التزام واضحة وموجّهة بالأمر.
- مثال: `Add glossary entries for sensor terms`

## 📄 الترخيص

لا يوجد ملف ترخيص في جذر المستودع حاليًا.

الافتراض:

- شروط الحقوق وإعادة الاستخدام غير محددة حاليًا حتى تُضاف ملف `LICENSE`.

## 📚 المراجع والاعترافات

يتضمن مخطوط العينة في `latex/main.tex` حالياً إدخالات مرجعية مضمنة للأعمال التالية:

- Goodfellow, Bengio, and Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

حالة شكر العمل:

- لا يوجد قسم مخصص للّقطات العلمية في المخطوط حاليًا.
- روابط الدعم/الرعاية مجمّعة في قسم **❤️ Support** أعلاه.


## ❤️ Support

| Donate | PayPal | Stripe |
| --- | --- | --- |
| [![Donate](https://camo.githubusercontent.com/24a4914f0b42c6f435f9e101621f1e52535b02c225764b2f6cc99416926004b7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f6e6174652d4c617a79696e674172742d3045413545393f7374796c653d666f722d7468652d6261646765266c6f676f3d6b6f2d6669266c6f676f436f6c6f723d7768697465)](https://chat.lazying.art/donate) | [![PayPal](https://camo.githubusercontent.com/d0f57e8b016517a4b06961b24d0ca87d62fdba16e18bbdb6aba28e978dc0ea21/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f50617950616c2d526f6e677a686f754368656e2d3030343537433f7374796c653d666f722d7468652d6261646765266c6f676f3d70617970616c266c6f676f436f6c6f723d7768697465)](https://paypal.me/RongzhouChen) | [![Stripe](https://camo.githubusercontent.com/1152dfe04b6943afe3a8d2953676749603fb9f95e24088c92c97a01a897b4942/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5374726970652d446f6e6174652d3633354246463f7374796c653d666f722d7468652d6261646765266c6f676f3d737472697065266c6f676f436f6c6f723d7768697465)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400) |
