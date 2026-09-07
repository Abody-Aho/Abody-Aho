# GitHub Profile Setup — Abody-Aho

هذا الباكدج مبني على نفس ترتيب دليل الإعداد المرفق: Repo → SVG banner → self-hosted stats → Snake → badges. الدليل نفسه يوصي باختبار كل مرحلة قبل الانتقال للي بعدها. 

## Phase 0 — Profile repository
1. افتح GitHub وأنشئ repository اسمه بالضبط `Abody-Aho`.
2. اجعله **Public** وفعّل **Add a README file**.
3. ارفع إلى root:
   - `README.md`
   - `dark.svg`
   - `light.svg`
   - مجلد `.github/workflows/`
   - مجلد `metrics/` إذا عندك ملفات WakaTime/Activity القديمة.

## Phase 1 — Banner
الـ README يستخدم `<picture>` حتى يبدّل تلقائياً بين `dark.svg` و`light.svg` حسب ثيم GitHub.

## Phase 2 — GitHub Stats (Self-hosted)
1. أنشئ GitHub classic token:
   - Settings → Developer settings → Tokens (classic)
   - Generate new token (classic)
   - No expiration
   - `repo` scope
2. انسخ التوكن فوراً. لا تضعه في README أو GitHub repository.
3. Fork لـ `anuraghazra/github-readme-stats`.
4. افتح Vercel → Sign up with GitHub → Hobby (Free).
5. Add New → Project → استورد الـ fork.
6. Environment Variables:
   - Name: `PAT_1`
   - Value: التوكن
7. Deploy.
8. استبدل `YOUR-VERCEL-INSTANCE` داخل README بعنوان مشروعك.

الـ `hide_rank=true` موجود عمداً لأن الـ rank يتأثر بقوة بالـ stars/followers ولا يمثل مهارة البرمجة وحدها.

## Phase 3 — Contribution Snake
قبل تشغيل الـ workflow:
Repository → Settings → Actions → General → Workflow permissions → **Read and write permissions** → Save.

الملف الجاهز هو:
`.github/workflows/snake.yml`

ويعمل:
- كل 12 ساعة
- عند push إلى `main`
- يدوياً عبر `workflow_dispatch`

بعد أول تشغيل ناجح سيظهر فرع `output`.

## Phase 4 — Social badges
البادجات موجودة داخل README، وروابط GitHub / LinkedIn / Portfolio / Email مأخوذة من README القديم.

ملاحظة: الدليل يحذر من مشكلة شعار LinkedIn في Shields.io؛ لذلك استخدمنا لون LinkedIn الرسمي `#0A66C2`.

## WakaTime
احتفظنا بقسم WakaTime من README القديم لأنه من أفضل الأشياء فيه لعرض وقت كتابة الأكواد. البادج الحالي مرتبط بحساب WakaTime الموجود في README القديم.

إذا كان عندك workflow قديم يولد:
- `metrics/wakatime.svg`
- `metrics/activity.svg`

فقط انسخهما إلى مجلد `metrics/` في هذا البروفايل.

## الملفات
- `README.md` — البروفايل الكامل
- `dark.svg` — البانر الداكن المتحرك
- `light.svg` — البانر الفاتح المتحرك
- `.github/workflows/snake.yml` — Contribution Snake
- `metrics/README.md` — ملاحظة عن ملفات الإحصائيات القديمة
