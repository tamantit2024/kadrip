# Kadri Med — Portfolio Website

> موقع Portfolio احترافي متعدد الصفحات لعلامة **Kadri Tech / Kadri Med** (قادري محمد عبد الله).
> مصمم جرافيك ومصمم مواقع وصانع محتوى رقمي.

موقع Static مبني بـ **Next.js 16 + TypeScript + Tailwind CSS 4**، جاهز للنشر على **Cloudflare Pages** مجانًا.

---

## ✨ المميزات

- **متعدد الصفحات** (Home, About, Services, Portfolio, Contact, Project Details, 404) عبر hash-routing خفيف
- **عربي أساسي RTL** مع دعم الإنجليزية للكلمات التقنية
- **هوية بصرية متناسقة**: Dark Navy `#0b192c` + Orange `#ff6500` + Light `#f9f9f9`
- **خطوط احترافية**: IBM Plex Sans Arabic (عربي) + Space Grotesk (لاتيني/Display)
- **تصميم متجاوب** بالكامل (375px → 1920px)
- **Animations خفيفة** (CSS + IntersectionObserver) تحترم `prefers-reduced-motion`
- **SEO كامل**: Meta tags, Open Graph, Twitter Card, sitemap.xml, robots.txt, manifest
- **Accessibility**: Semantic HTML5, ARIA, keyboard nav, focus visible, alt text
- **بيانات منفصلة** للمشاريع والخدمات والموقع (سهلة التعديل لغير المبرمج)
- **فلترة مشاريع** تعمل بـ JavaScript فعليًا
- **Case Study template** لصفحات تفاصيل المشاريع (Overview / Challenge / Solution / Result)
- **نموذج تواصل** جاهز للربط مع Formspree (النسخة الأولى تفتح بريد العميل عبر `mailto`)
- **Sticky Header** + Hamburger menu على الموبايل
- **Sticky Footer** يبقى أسفل الصفحة على المحتوى القصير

---

## 📁 بنية المشروع

```
kadri-med-portfolio/
├─ public/
│  ├─ favicon.svg               # أيقونة الموقع (SVG)
│  ├─ manifest.webmanifest      # PWA manifest
│  ├─ robots.txt                # تعليمات لمحركات البحث
│  ├─ sitemap.xml               # خريطة الموقع
│  ├─ og/
│  │  └─ og-image.svg           # صورة Open Graph
│  └─ projects/                 # صور المشاريع (استبدلها بصورك)
│     ├─ branding.jpg
│     ├─ social-media.jpg
│     ├─ web-design.jpg
│     ├─ video-editing.jpg
│     ├─ advertising.jpg
│     ├─ logo-design.jpg
│     ├─ ai-creative.jpg
│     └─ academic.jpg
│
├─ src/
│  ├─ app/
│  │  ├─ layout.tsx             # الـ Root Layout (RTL + خطوط + SEO metadata)
│  │  ├─ page.tsx               # نقطة الدخول الوحيدة (SPA shell + router)
│  │  └─ globals.css            # نظام التصميم (ألوان، خطوط، animations)
│  │
│  ├─ data/                     # 🟢 أهم مجلد للتعديل
│  │  ├─ site.ts                # معلوماتك الشخصية + قائمة التنقل + التصنيفات
│  │  ├─ services.ts            # الخدمات (9 خدمات كاملة بالتفاصيل)
│  │  └─ projects.ts            # المشاريع (8 مشاريع + بيانات Case Study)
│  │
│  ├─ lib/
│  │  └─ router.tsx             # Hash router خفيف (بدون مكتبة)
│  │
│  ├─ hooks/
│  │  └─ use-reveal.tsx         # IntersectionObserver hook + مكوّن Reveal
│  │
│  └─ components/
│     ├─ layout/
│     │  ├─ site-header.tsx      # الـ Header (sticky + hamburger)
│     │  └─ site-footer.tsx     # الـ Footer (sticky bottom)
│     ├─ sections/              # أقسام قابلة لإعادة الاستخدام
│     │  ├─ hero.tsx
│     │  ├─ section-heading.tsx
│     │  ├─ service-card.tsx
│     │  ├─ project-card.tsx
│     │  ├─ services-preview.tsx
│     │  ├─ portfolio-preview.tsx
│     │  ├─ process-section.tsx
│     │  ├─ cta-section.tsx
│     │  └─ smart-image.tsx     # صورة مع fallback
│     └─ pages/                 # صفحات الموقع
│        ├─ home-page.tsx
│        ├─ about-page.tsx
│        ├─ services-page.tsx
│        ├─ portfolio-page.tsx
│        ├─ project-detail-page.tsx
│        ├─ contact-page.tsx
│        └─ not-found-page.tsx
│
├─ next.config.ts
├─ tailwind.config.ts
├─ package.json
└─ README.md  (هذا الملف)
```

---

## ✏️ كيف تعدّل المحتوى (دليل غير المبرمجين)

### 1) معلوماتك الشخصية (الاسم، البريد، السوشيال، الدومين)

افتح الملف: **`src/data/site.ts`**

عدّل القيم داخل الكائن `site` و `contact`:

```ts
export const site = {
  fullName: { ar: "قادري محمد عبد الله", en: "Kadri Mohammed Abdallah" },
  shortName: { ar: "قادري ميد", en: "Kadri Med" },
  email: "med@kadri01.com",
  website: "kadri01.online",
  // ...
};

export const contact = {
  email: "med@kadri01.com",
  instagram: "https://instagram.com/kadri_tech",
  facebook: "https://facebook.com/KADRI-Tech",
  whatsapp: "YOUR_PHONE_NUMBER",  // ← استبدل برقمك بصيغة دولية (مثال: 201000000000)
};
```

### 2) تعديل خدمة موجودة

افتح: **`src/data/services.ts`**

كل خدمة لها: `name`, `summary`, `description`, `offerings`, `benefits`, `deliverables`.
عدّل النصوص العربية فقط — لا تغيّر `id` أو `slug` إلا إذا كنت تعرف ما تفعل.

### 3) 🟢 إضافة مشروع جديد (الأهم)

افتح: **`src/data/projects.ts`**

1. انسخ كائن مشروع كامل (من `{` إلى `},`) من أحد المشاريع الموجودة.
2. الصقه في نهاية المصفوفة `projects`.
3. عدّل القيم:

```ts
{
  id: "my-new-project",              // معرّف فريد بالإنجليزية بدون مسافات
  slug: "my-new-project",            // يظهر في الرابط: #/project/my-new-project
  title: { ar: "اسم المشروع", en: "Project Name" },
  category: "branding",             // واحدة من: graphic-design | branding | social-media | web-design | video-editing
  description: { ar: "وصف قصير", en: "Short desc" },
  client: { ar: "اسم العميل", en: "Client Name" },
  year: "2024",
  services: [
    { ar: "تصميم شعار", en: "Logo Design" },
  ],
  thumbnail: "/projects/branding.jpg",   // مسار الصورة داخل مجلد public/
  gallery: ["/projects/branding.jpg"],   // صور المعرض (يمكن إضافة أكثر من صورة)
  overview: { ar: "...", en: "..." },
  challenge: { ar: "...", en: "..." },
  solution: { ar: "...", en: "..." },
  result: { ar: "...", en: "..." },
  featured: true,                   // ضع true ليظهر المشروع في الصفحة الرئيسية
},
```

المشروع سيظهر تلقائيًا في صفحة `الأعمال` وفي فلتر التصنيف المناسب.

### 4) استبدال صور المشاريع بصورك الحقيقية

1. ضع صورتك في مجلد **`public/projects/`**
2. إما أن تعطيها نفس اسم الملف الموجود (تُستبدل تلقائيًا)، أو تعطيها اسمًا جديدًا وتعدّل مسار `thumbnail` في `projects.ts`.

**ملاحظات للصور:**
- الأبعاد المفضّلة: **1024×1024** للصور المربعة، **1344×768** للأفقية.
- صيغة **JPG** أسرع، **PNG** للصور الشفافة.
- اضغط الصور قبل الرفع (استخدم [squoosh.app](https://squoosh.app) مجانًا).

### 5) تغيير الألوان

كل الألوان معرّفة كـ CSS variables في ملف **`src/app/globals.css`** في كتلة `:root`.
غير القيم هناك وستنعكس على كامل الموقع:

```css
:root {
  --navy: #0b192c;
  --orange: #ff6500;
  --canvas: #f9f9f9;
}
```

---

## 🚀 التشغيل محليًا (للتعديل والمعاينة)

### المتطلبات
- [Node.js](https://nodejs.org) 18+ أو [Bun](https://bun.sh)
- محرر أكواد (موصى به: [VS Code](https://code.visualstack.com))

### الخطوات

```bash
# 1. ثبّت الحزم
bun install
# أو: npm install

# 2. شغّل خادم التطوير
bun run dev
# أو: npm run dev

# 3. افتح المتصفح على
http://localhost:3000
```

أي تعديل في الملفات ينعكس مباشرة في المتصفح.

---

## 📤 الرفع إلى GitHub

### 1) أنشئ مستودعًا جديدًا على GitHub
- اذهب إلى [github.com/new](https://github.com/new)
- اسم المستودع: `kadri-med-portfolio` (مثال)
- اختر **Public** أو **Private** (لا فرق مع Cloudflare Pages)
- **لا** تفعّل "Initialize with README" (المشروع يحتوي README)
- اضغط **Create repository**

### 2) ارفع الملفات من جهازك

في مجلد المشروع على جهازك:

```bash
# تأكد أنك في مجلد المشروع
cd path/to/kadri-med-portfolio

# جهّز Git
git init
git add .
git commit -m "Initial commit — Kadri Med portfolio"

# اربط المستودع (استبدل USERNAME بمستخدم GitHub)
git branch -M main
git remote add origin https://github.com/USERNAME/kadri-med-portfolio.git
git push -u origin main
```

---

## ☁️ النشر على Cloudflare Pages (مجاني)

### 1) اذهب إلى Cloudflare Pages
- سجّل/سجّل الدخول على [dash.cloudflare.com](https://dash.cloudflare.com)
- من القائمة الجانبية اختر **Workers & Pages**
- اضغط **Create** → **Pages** → **Connect to Git**

### 2) اربط مستودع GitHub
- اختر **Connect to Git**
- اختر GitHub، امنح الصلاحيات
- اختر مستودع `kadri-med-portfolio`

### 3) إعدادات البناء (Build settings)

| الحقل | القيمة |
|---|---|
| **Framework preset** | `Next.js` |
| **Build command** | `npm run build` |
| **Build output directory** | `.next` |
| **Root directory** | (اتركه فارغًا) |

**ملاحظات:**
- في إعدادات Environment Variables (اختياري)، أضف:
  - `NODE_VERSION` = `20`
- Cloudflare Pages يدعم Next.js تلقائيًا عبر `@cloudflare/next-on-pages`. أول نشر قد يأخذ 2-4 دقائق.

### 4) اضغط **Save and Deploy**

خلال دقائق سيكون موقعك على رابط مثل:
`https://kadri-med-portfolio.pages.dev`

---

## 🌐 ربط الدومين المخصص `kadri01.online`

### 1) أضف الدومين في Cloudflare Pages
- في صفحة مشروعك على Cloudflare Pages، اذهب إلى **Custom domains** → **Set up a custom domain**
- أدخل: `kadri01.online` (و `www.kadri01.online` لو أردت)
- اضغط **Continue** → **Activate domain**

### 2) وجّه DNS الدومين إلى Cloudflare
- إذا كان دومينك مُسجّل على Cloudflare نفسها، تُضاف سجلات DNS تلقائيًا.
- إذا كان على مزوّد آخر (Namecheap, GoDaddy...):
  - غيّر **Nameservers** على الدومين إلى مزوّد Cloudflare الذي يعطيك إياه، أو
  - أضف **CNAME record**: `@ → kadri-med-portfolio.pages.dev` (و `www → kadri-med-portfolio.pages.dev`)

### 3) انتظر تفعيل SSL
- Cloudflare توفّر شهادة SSL/TLS مجانية تلقائيًا.
- خلال دقائق إلى ساعة (نادرًا 24 ساعة)، سيكون موقعك على `https://kadri01.online` ✅

---

## 🔧 تعليمات سريعة (Quick Reference)

| تريد أن... | افتح هذا الملف |
|---|---|
| تغيّر اسمك/بريدك/سوشيال ميديا | `src/data/site.ts` |
| تعدّل نصوص الخدمات | `src/data/services.ts` |
| تضيف مشروعًا جديدًا | `src/data/projects.ts` |
| تغيّر الألوان | `src/app/globals.css` (كتلة `:root`) |
| تعدّل القائمة الرئيسية | `src/data/site.ts` → `navItems` |
| تضيف تصنيف جديد للأعمال | `src/data/site.ts` → `projectCategories` |
| تعدّل نصوص Footer/Header | `src/components/layout/` |

---

## 📞 معلومات التواصل (للحصول على مساعدة لاحقًا)

- **Email**: med@kadri01.com
- **Instagram**: [@kadri_tech](https://instagram.com/kadri_tech)
- **Facebook**: [KADRI-Tech](https://facebook.com/KADRI-Tech)
- **Website**: [kadri01.online](https://kadri01.online)

---

## 📝 ملاحظات

- الصور الحالية في `public/projects/` هي **صور عيّنة مولّدة بالـ AI** كنماذج بصرية. استبدلها بصورك الحقيقية.
- أرقام الهواتف وبيانات العميل مُعبّأة بقيم واضحة مثل `YOUR_PHONE_NUMBER` — استبدلها قبل النشر النهائي.
- النموذج في صفحة Contact يفتح بريد الزائر عبر `mailto:`. للنسخة الاحترافية، اربط [Formspree](https://formspree.io) (مجاني حتى 50 رسالة/شهر) بالكود في `src/components/pages/contact-page.tsx`.

---

© 2027 Kadri Mohammed Abdallah. All Rights Reserved.
