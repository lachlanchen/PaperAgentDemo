[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

قالب مدمج ودقيق للمستودع لكتابة الأوراق العلمية بـ LaTeX، يتمحور حول `latex/main.tex`، ومصمم للتحقق من سير عمل المخطوطة وتوسيعه مع المعادلات والخوارزميات والجداول والمصطلحات/الاختصارات والمراجع وأدوات بناء PDF.

| العنصر | القيمة |
| --- | --- |
| ملف المخطوطة الأساسي | `latex/main.tex` |
| نمط البناء الحالي | LaTeX محلي (`latexmk` / `pdflatex`) |
| حالة مجلد i18n | المجلد `i18n/` موجود (يمكن إضافة ملفات لغات مع الوقت) |
| حالة ملف الترخيص | غير موجود حاليًا |

## 📌 نظرة عامة

يوفر هذا المستودع حاليًا:

- ملف مصدر رئيسي واحد للمخطوطة: `latex/main.tex`.
- بنية ورقة تمثيلية تتضمن الملخص والمنهجية والخوارزمية والنتائج والمناقشة والخلاصة.
- تغطية لحزم LaTeX الخاصة بمهام الكتابة البحثية الشائعة (الرياضيات، الاستشهادات، المصطلحات، الإحالات المتقاطعة).
- بيانات وصفية لخط الأنابيب ضمن `.auto-readme-work/` لتوليد README متعدد اللغات.

ملاحظة مهمة حول المستودع:

- يوضح `AGENTS.md` المجلدات المقصودة (`figures/`, `data/`, `artifacts/`, `code/`)، لكن بعض هذه المجلدات غير موجودة بعد في الشجرة الحالية. يحافظ هذا README على هذا التوجه ويُشير بوضوح إلى الأجزاء غير الموجودة.

## ✨ الميزات

- تنضيد رياضي عبر `amsmath` و`amssymb` و`bm` و`mathtools` و`siunitx`.
- دعم الأشكال والجداول عبر `graphicx` و`subcaption` و`booktabs` و`multirow`.
- بيئة خوارزميات عبر `algorithm` و`algpseudocode`.
- دعم الاستشهادات عبر `natbib`.
- دعم المسرد والاختصارات عبر `glossaries` (مع تفعيل `\makeglossaries`).
- إحالات متقاطعة عبر `hyperref` و`cleveref`.
- محتوى مثالي مضمّن بالفعل: معادلة دالة هدف مع انتظام `\ell_1`، ومعادلة SNR بوحدة dB، وشبه كود للانحدار التدريجي، وجدول مقارنة كمي، ومداخل ببليوغرافيا مضمنة.

## 🧭 بنية المشروع

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
├── i18n/                         # موجود حاليًا؛ يمكن إضافة ملفات README للغات بمرور الوقت
└── latex/
    ├── main.tex                  # مصدر المخطوطة الأساسي
    ├── main.acn                  # ناتج مسرد/اختصارات مُولّد
    ├── main.glo                  # ناتج مسرد مُولّد
    └── main.ist                  # ناتج نمط المسرد
```

## ✅ المتطلبات المسبقة

ثبّت بيئة TeX تتضمن الحزم المستخدمة بواسطة `latex/main.tex`.

الحد الأدنى العملي من المتطلبات:

- `latexmk`
- `pdflatex`
- `bibtex` (للتعامل مع المراجع في التدفقات القياسية)
- أدوات المسرد المطلوبة ضمن تدفقات `glossaries` (عادةً `makeglossaries` من توزيعة TeX)

افتراض:

- أسماء الحزم وإصداراتها غير مثبتة في هذا المستودع؛ استخدم توزيعة حديثة من TeX Live أو MiKTeX.

## 📥 التثبيت

استنسخ المستودع ثم ادخل إليه:

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

لا توجد حاليًا خطوة تثبيت إضافية عبر مدير حزم محددة داخل المستودع.

## 🚀 الاستخدام

| المهمة | الأمر |
| --- | --- |
| البناء الموصى به | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| مرور سريع واحد | `pdflatex latex/main.tex` |
| تنظيف الملفات المساعدة | `latexmk -c latex/main.tex` |

أمر البناء الأساسي (موصى به، من `AGENTS.md`):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

ترجمة بمرور واحد (للتكرار السريع):

```bash
pdflatex latex/main.tex
```

تنظيف ملفات LaTeX المساعدة مع الإبقاء على ملف PDF:

```bash
latexmk -c latex/main.tex
```

سير العمل المتوقع:

1. عدّل محتوى المخطوطة في `latex/main.tex`.
2. ابنِ ملف PDF.
3. افحص التنسيق والإحالات بصريًا في ملف PDF الناتج.

## ⚙️ الإعدادات

إعدادات المستند الحالية موجودة في `latex/main.tex`:

- فئة المستند: `article` مع `11pt,a4paper`.
- تخطيط الصفحة: `geometry` مع `margin=1in`.
- التباعد: `\onehalfspacing`.
- إعداد ألوان الروابط عبر `linkblue` مخصص وخيارات `hyperref`.
- اختصارات ومداخل مسرد مُعرّفة مسبقًا لـ `CNN` و`SNR` و`HSI` و`event camera`.

سلوك التجاهل على مستوى المستودع (`.gitignore`):

- يتجاهل معظم نواتج بناء LaTeX (`*.aux` و`*.log` و`*.pdf`، إلخ).
- يتجاهل مجلدي `artifacts/` و`data/` افتراضيًا.

## 🧪 أمثلة

بناء المخطوطة من البداية إلى النهاية:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

تنظيف ثم إعادة البناء:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

ترجمة سريعة أثناء تعديل قسم واحد:

```bash
pdflatex latex/main.tex
```

## 🛠 ملاحظات التطوير

إرشادات من `AGENTS.md`:

- أبقِ مصدر LaTeX ضمن عناوين `\section{}` واضحة.
- استخدم بادئات الملصقات بشكل متسق: `eq:` للمعادلات، `fig:` للأشكال، `tab:` للجداول، و`alg:` للخوارزميات.
- فضّل الإحالات عبر `\cref{}`.
- استخدم أسماء ملفات صغيرة وبفواصل (`-`) للأصول (مثال: `figures/snr-comparison.pdf`).
- استخدم مسافة بادئة بمقدار مسافتين للكتل المتداخلة في LaTeX عندما يكون ذلك مفيدًا.

نهج التحقق:

- لا توجد مجموعة اختبارات آلية.
- التحقق الأساسي هو نجاح بناء LaTeX مع فحص بصري لملف PDF المُولّد.

## 🧰 استكشاف الأخطاء وإصلاحها

مشكلات شائعة وفحوصات مقترحة:

- فشل البناء بسبب حزمة مفقودة: ثبّت حزم LaTeX الناقصة من توزيعة TeX الخاصة بك.
- عدم ظهور مداخل المسرد: تأكد من تثبيت أدوات المسرد ثم أعد تشغيل `latexmk` لتنفيذ خطوات المسرد.
- استمرار تحذيرات الاستشهادات أو الإحالات: أعد البناء باستخدام `latexmk` (يتعامل تلقائيًا مع التمريرات المتعددة).
- عدم تتبع ملف PDF الناتج في git: هذا متوقع لأن `*.pdf` مُتجاهلة حاليًا في `.gitignore`.

## 🗺 خارطة الطريق

الخطوات القادمة المخطط لها أو المحتملة (مستنتجة من ملفات المستودع وإرشاداته):

1. إضافة المجلدات `figures/` و`data/` و`artifacts/` و`code/` مع توسع العمل.
2. إضافة ملفات README خاصة بكل لغة ضمن `i18n/` بما يتوافق مع روابط التنقل بين اللغات.
3. إضافة سكربتات مساعدة اختيارية لتوليد الأشكال/الجداول بشكل قابل لإعادة الإنتاج ضمن `code/`.
4. إدخال CI للتحقق من البناء إذا نما المشروع بما يتجاوز قالبًا محليًا.

## 🤝 المساهمة

لا توجد حاليًا آلية مساهمة رسمية محددة، لذا استخدم الأساس التالي:

1. أنشئ فرعًا.
2. نفّذ تغييرات مركزة.
3. شغّل بناء LaTeX نظيفًا:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. أدرج ملخصًا واضحًا لتغييرات المخطوطة أو أدوات العمل في طلب السحب (PR).

نمط الالتزام المقترح من إرشادات المستودع:

- استخدم عناوين التزامات واضحة وبصيغة الأمر.
- مثال: `Add glossary entries for sensor terms`

## 📄 الترخيص

لا يوجد حاليًا ملف ترخيص في جذر المستودع.

افتراض:

- جميع الحقوق وشروط إعادة الاستخدام غير محددة حاليًا إلى أن يُضاف ملف `LICENSE`.

## 📚 المراجع والشكر

تتضمن المخطوطة النموذجية في `latex/main.tex` حاليًا مداخل ببليوغرافية مضمنة لكل من:

- Goodfellow وBengio وCourville، *Deep Learning* (MIT Press، 2016).
- Gallego وآخرون، *Event-based vision: A survey* (IEEE TPAMI، 2022).

حالة الشكر والدعم:

- لا يوجد حاليًا قسم مخصص للشكر أو الرعاة أو التبرعات/الدعم في ملفات المستودع.
- إذا كانت معلومات الرعاة/الدعم موجودة خارجيًا، فأضفها هنا دون إزالة المحتوى التقني.
