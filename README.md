# برنامج مؤشرات الأداء الاستراتيجي والمبادرات

تطبيق ويب ثابت لمتابعة مؤشرات أداء وكالة البنية التحتية في أمانة منطقة المدينة المنورة. النسخة الحالية هي MVP تعمل بملفات HTML وCSS وJavaScript فقط، ومناسبة للنشر على GitHub Pages والتجربة المحلية.

## التشغيل

افتح `index.html` أو شغل خادمًا محليًا من جذر المشروع:

```powershell
python -m http.server 8765
```

ثم افتح:

```text
http://127.0.0.1:8765/
```

## الحسابات التجريبية

- مدير النظام: `مدير النظام`
- حسابات الوحدات: موجودة في صفحة الدخول
- كلمة المرور التجريبية لأي حساب: `demo`

يمكن لمدير النظام تعديل كلمات مرور الحسابات من صفحة `admin.html`.

> هذه الحسابات للتجربة فقط. لا تستخدم كلمات مرور حقيقية أو بيانات حساسة داخل تطبيق ثابت منشور على GitHub Pages. النسخة التشغيلية الحقيقية تحتاج Supabase أو Firebase للمصادقة وقاعدة البيانات.

## الهيكل

```text
index.html
login.html
dashboard.html
unit-entry.html
kpi-library.html
reports.html
admin.html
export-excel.html
assets/css/style.css
assets/js/app.js
assets/js/auth.js
assets/js/storage.js
assets/js/kpi.js
assets/js/charts.js
assets/js/export-excel.js
assets/img/logo.png
data/seed-units.json
data/seed-kpis.json
data/backup.json
REQUIREMENTS.md
TODO.md
.nojekyll
404.html
.github/workflows/pages.yml
```

## ملاحظات فنية

- التخزين الحالي عبر `localStorage`.
- يتم تحميل بيانات أولية عند أول تشغيل.
- تصدير Excel يستخدم SheetJS عند توفره عبر CDN، مع بديل CSV عند عدم توفر الاتصال.
- الرسوم البيانية تستخدم Chart.js عند توفره، مع رسم Canvas مبسط كبديل.

## النشر على GitHub Pages

راجع أيضًا `PUBLISHING.md` قبل الرفع. لا ترفع مجلدات العمل غير التابعة للموقع مثل `strategic-performance-video/` أو `.agents/` أو `.pnpm-store/`.

الطريقة الأولى من إعدادات GitHub:

1. ارفع ملفات المشروع إلى مستودع GitHub.
2. افتح `Settings` ثم `Pages`.
3. اختر النشر من فرع `main` والمجلد `/root`.
4. افتح الرابط الذي يظهر في صفحة GitHub Pages.

الطريقة الثانية عبر GitHub Actions:

1. ارفع الملف `.github/workflows/pages.yml` مع بقية المشروع.
2. من `Settings > Pages` اختر `GitHub Actions` كمصدر للنشر.
3. عند أي تحديث على فرع `main` سيتم نشر الموقع تلقائيًا.

الصفحة الرئيسية `index.html` تحول المستخدم إلى `login.html`، وملف `.nojekyll` يمنع GitHub Pages من معالجة الملفات عبر Jekyll.

## التحديثات التشغيلية الأخيرة

- دعم نماذج مؤشر أكثر اكتمالًا تشمل المبادرة، مالك البيانات، الدليل، سبب الانحراف، جودة البيانات، وحالة سير العمل.
- دعم حساب الأداء التصاعدي والتنازلي وضمن النطاق والإنجاز المرحلي، مع حدود حالة قابلة للتعديل لكل مؤشر.
- إضافة اعتماد الفترة وإعادتها للتصحيح من صفحة التقارير، مع إغلاق التعديل على حسابات الوحدات عند الاعتماد أو الإغلاق.
- إضافة سجل تدقيق إداري لعمليات الحفظ، التعديل، الاعتماد، الاستيراد، والتصدير.
- توسيع التصدير إلى Excel وCSV وJSON مع صفحات إرشادية لتقارير PDF وPowerPoint.
- إضافة أدلة تشغيل في `docs/user-guide.md` و`docs/admin-guide.md`، وملفات `SECURITY.md` و`CHANGELOG.md` و`LICENSE`.
