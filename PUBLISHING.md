# النشر على GitHub Pages

## سبب تعطل النشر غالبًا

المشروع يحتوي مجلدات عمل ليست جزءًا من الموقع، مثل:

- `strategic-performance-video/`
- `.agents/`
- `.pnpm-store/`

هذه المجلدات لا يجب رفعها كجزء من الموقع. مجلد `strategic-performance-video` وحده يحتوي عددًا كبيرًا من الملفات، وقد يؤدي إلى فشل GitHub Pages أو بطء/تعطل artifact النشر.

## الطريقة الموصى بها

1. ارفع ملفات المشروع إلى GitHub بدون المجلدات المستبعدة في `.gitignore`.
2. من `Settings > Pages` اختر `GitHub Actions`.
3. تأكد أن ملف `.github/workflows/pages.yml` موجود.
4. ادفع التغييرات إلى فرع `main`.

ملف workflow الحالي ينشئ مجلد نشر نظيف اسمه `.pages` ويضع داخله ملفات الموقع فقط:

- ملفات `*.html`
- مجلد `assets`
- مجلد `data`
- مجلد `docs`
- ملفات `.nojekyll`, `README.md`, `SECURITY.md`, `CHANGELOG.md`, `LICENSE`

## إن كنت تستخدم الرفع اليدوي

ارفع هذه الملفات والمجلدات فقط:

```text
*.html
assets/
data/
docs/
.nojekyll
README.md
SECURITY.md
CHANGELOG.md
LICENSE
```

ولا ترفع:

```text
strategic-performance-video/
.agents/
.pnpm-store/
node_modules/
.git/
```

تم تجهيز نسخة محلية نظيفة في مجلد `github-pages-ready/`. عند الرفع اليدوي استخدم محتويات هذا المجلد فقط، وليس مجلد المشروع كاملًا.

## ملاحظات مهمة

- افتح رابط الموقع من جذر GitHub Pages، مثل:
  `https://USER.github.io/REPOSITORY/`
- لا تفتح `kpi-library.html` مباشرة قبل تسجيل الدخول؛ التطبيق سيعيدك إلى `login.html`.
- الحسابات تجريبية وكلمة المرور الافتراضية هي `demo`.
