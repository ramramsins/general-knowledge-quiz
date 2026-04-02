# General Knowledge Quiz | مسابقة المعرفة العامة

## العربية

تطبيق ويب لإدارة مسابقة معرفة عامة باللغة العربية، مع دعم:
- أسئلة اختيار من متعدد (MCQ)
- أسئلة قائمة (LIST) بإجابات متعددة
- إدارة الفرق والنقاط والمؤقت
- تحميل البيانات من ملف Excel محلي أو من Google Sheets

### الميزات الأساسية
- واجهة عربية متجاوبة (Desktop + Mobile).
- لوحة تحكم للمقدّم مع مؤقت وإدارة الأدوار.
- عرض الإجابة الصحيحة في أسئلة MCQ للمقدّم.
- أسئلة LIST مع:
  - تقسيم تلقائي لحقل `الإجابة` باستخدام `،` أو `,`
  - بطاقات قابلة للنقر لتعليم الإجابات المكتشفة
  - عدّاد مباشر `Answers found: X / Y`
  - زر `Extra Answer` لزيادة العدّاد للإجابات غير المدرجة
- تشغيل سريع بوضع Offline-first (تحميل `questions.xlsx` تلقائيا أولا).

### بنية الملفات
- `index.html`: الملف الرئيسي للتشغيل والنشر.
- `game.html`: نسخة تشغيل بديلة بنفس المنطق.
- `questions.xlsx`: ملف الأسئلة المحلي المعتمد تلقائيا.
- `netlify.toml`: إعدادات النشر ورؤوس HTTP.

### تنسيق البيانات (Excel / Google Sheets)

#### Sheet1 (MCQ)
الأعمدة المتوقعة:
1. رقم السؤال
2. الصعوبة (`س` أو `ص`)
3. التصنيف
4. السؤال
5. الخيار أ
6. الخيار ب
7. الخيار ج
8. الخيار د
9. الإجابة الصحيحة (`أ` / `ب` / `ج` / `د`)

#### Sheet2 (LIST)
الأعمدة المتوقعة:
1. رقم السؤال
2. التصنيف
3. السؤال
4. الإجابة (يمكن أن تحتوي عدة إجابات مفصولة بـ `،` أو `,`)

مثال في عمود `الإجابة`:
`الوجودية، الظاهراتية، البنيوية، ما بعد البنيوية`

### التشغيل المحلي
1. ضع ملف الأسئلة في جذر المشروع باسم `questions.xlsx`.
2. شغّل خادما محليا (مثال):
   - `py -m http.server 5500`
3. افتح:
   - `http://localhost:5500/index.html`

### Google Sheets
- يمكن التحميل يدويا عبر زر `تحميل من Google Sheets`.
- عند النجاح سيظهر مصدر البيانات: `Source: Google Sheets`.

### النشر (Netlify)
- المشروع ثابت (Static) ولا يحتاج Backend.
- `netlify.toml` يضبط:
  - `publish = "."`
  - MIME type لملفات `.xlsx`
  - بعض Security headers

---

## English

Web app for hosting an Arabic general knowledge quiz with:
- Multiple-choice questions (MCQ)
- List questions (LIST) with multiple possible answers
- Team score management and timer controls
- Data loading from local Excel file or Google Sheets

### Core Features
- Responsive Arabic UI (desktop + mobile).
- Host control panel for timer, turns, and scoring.
- Correct-answer visibility for MCQ (host view).
- LIST answer flow:
  - Parses `الإجابة` using Arabic comma `،` or normal comma `,`
  - Clickable answer cards to mark/unmark found answers
  - Live counter: `Answers found: X / Y`
  - `Extra Answer` button for valid answers not listed in the sheet
- Offline-first startup (loads local `questions.xlsx` first).

### File Structure
- `index.html`: primary app entry point for running/deploying.
- `game.html`: alternate entry with the same game logic.
- `questions.xlsx`: default local questions source.
- `netlify.toml`: deployment and header configuration.

### Data Format (Excel / Google Sheets)

#### Sheet1 (MCQ)
Expected columns:
1. Question Number
2. Difficulty (`س` easy / `ص` hard)
3. Category
4. Question
5. Option A
6. Option B
7. Option C
8. Option D
9. Correct Answer (`أ` / `ب` / `ج` / `د`)

#### Sheet2 (LIST)
Expected columns:
1. Question Number
2. Category
3. Question
4. Answers (multiple entries separated by `،` or `,`)

Example `Answers` cell:
`Existentialism, Phenomenology, Structuralism`

### Local Run
1. Place your latest questions file as `questions.xlsx` in project root.
2. Start a local static server (example):
   - `py -m http.server 5500`
3. Open:
   - `http://localhost:5500/index.html`

### Google Sheets
- Optional manual load via `Load from Google Sheets` button.
- On success, the UI shows source label: `Source: Google Sheets`.

### Deployment (Netlify)
- Static deployment, no backend required.
- `netlify.toml` config includes:
  - `publish = "."`
  - Proper MIME type for `.xlsx`
  - Basic security headers
