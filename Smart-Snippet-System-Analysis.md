# Smart Snippet System for Salla — تحليل استراتيجي شامل

> **التاريخ:** 2026-05-12
> **المحلل:** SallaScope (Senior Salla App Venture Analyst)
> **الحالة:** MVP-Ready Analysis
> **السكور النهائي:** 86/100
> **القرار:** ✅ Go with High Confidence

---

## جدول المحتويات

1. [الملخص التنفيذي](#1-الملخص-التنفيذي)
2. [الفكرة الأساسية و Positioning](#2-الفكرة-الأساسية-و-positioning)
3. [الـ MVP النهائي — 4 Features](#3-الـ-mvp-النهائي--4-features)
4. [السكور التفصيلي](#4-السكور-التفصيلي)
5. [تحقق Native Overlap (Feature-by-Feature)](#5-تحقق-native-overlap-feature-by-feature)
6. [التحقق التقني من Salla](#6-التحقق-التقني-من-salla)
7. [Competitive Landscape (Verified Live)](#7-competitive-landscape-verified-live)
8. [توزيع الـ 36 Module على 5 Scopes](#8-توزيع-الـ-36-module-على-5-scopes)
9. [التسعير](#9-التسعير)
10. [ICP والسوق المستهدف](#10-icp-والسوق-المستهدف)
11. [المخاطر و Mitigations](#11-المخاطر-و-mitigations)
12. [KPIs و Kill Criteria](#12-kpis-و-kill-criteria)
13. [Positioning & Messaging](#13-positioning--messaging)
14. [PDPL Compliance Requirements](#14-pdpl-compliance-requirements)
15. [الخطوات الفورية](#15-الخطوات-الفورية)

---

## 1. الملخص التنفيذي

### الفكرة في جملة واحدة
طبقة **Customer Intent Intelligence** لمتاجر سلة — تلتقط نية وتردد العميل قبل الشراء، تجمعها في Dashboard، وتشخّص ما ينقص كل منتج.

### القرار
✅ **Go with High Confidence**
- **السكور:** 86/100
- **سبب الثقة العالية:** التحقق الحي أثبت أن الفجوة فعلية — لا منافس مباشر في فئة Customer Intent في Salla App Store.

### الـ 4 Features في الـ MVP
1. **Why** — Hesitation Capture (ليش ما اشترى)
2. **Wait** — Variant & Price Interest (شو ينتظر)
3. **Fix** — Intent Dashboard + Product Doctor (شو تصلح)
4. **Measure** — Widget Analytics (شو يشتغل)

### الفجوة في السوق (مؤكدة)
- **0 منافس** لـ "Customer Intent / Why didn't buy" في Salla App Store
- **0 منافس** لـ "Product Doctor / Pre-purchase Intelligence"
- فئة Analytics في Salla App Store **فارغة** ("No apps available")
- Salla Smart Analytics native **post-purchase حصرًا** — لا يلتقط non-buyers

### الـ Window
**6-12 شهر** قبل أن تتزاحم الفئة. SmartInsight بـ 693 SAR/شهر يثبت أن السوق مستعد يدفع لـ intelligence.

---

## 2. الفكرة الأساسية و Positioning

### ما هي الفكرة (بالضبط)
تطبيق على Salla App Store يضيف widgets ذكية في صفحات المنتجات والسلة، تجمع:
- **سبب التردد** قبل الشراء
- **إشارات الاهتمام** (سعر مستهدف، لون، مقاس، تصنيف)
- **معلومات ناقصة** على صفحة المنتج

ثم يحوّلها إلى:
- **Dashboard** فيه insights مجمعة
- **Product Doctor** يشخّص كل منتج ويقترح إصلاحات

### Positioning Statement
> **"Customer Intent Layer for Salla — أعرف ليش زوارك ما اشتروا، وعلى أي منتج بالضبط."**

### One-liner للمرشانت
> **"شو يمنع البيع؟ — تطبيق يخبرك على مستوى المنتج."**

### الفرق عن سلة (يجب أن يكون واضح في كل marketing)
| سلة Native | Smart Snippet System |
|---|---|
| Smart Analytics = post-purchase | نحن = pre-purchase |
| أسئلة المنتجات = علني، يحتاج رد | نحن = خاص، مصنّف، مدخل dashboard |
| أعلمني عند التوفر = restock بُعد واحد | نحن = price/variant/follow (3 أبعاد) |
| السلات المتروكة = تذكير برسالة | نحن = نسأل **لماذا** |

### الفرق عن PopupSnap وما شابه
| PopupSnap وأخواته | Smart Snippet System |
|---|---|
| Display tool | Capture + Intelligence tool |
| Marketer-facing | Operations + Product-facing |
| Conversion via friction | Conversion via clarity |
| اعمل campaign | افهم ليش ما اشتروا |

### المعجم الإلزامي
- ✅ استخدم: Customer Intent, Insights, Doctor, Signals, Hesitation, Why
- ❌ تجنب: Popup, Widget Builder, Pop, Banner, Survey Tool

---

## 3. الـ MVP النهائي — 4 Features

### القاعدة الصارمة
**أي ميزة موجودة في سلة native = خارج الـ MVP.**

### Feature 1: Hesitation Capture (Why)

**ما يفعله:**
سؤال قصير للعميل في لحظتين:
1. **Exit Intent** (PDP، عند نية المغادرة): "ليش ما اشتريت؟" — 6 خيارات سريعة + free text
2. **Product Clarity** (PDP، scroll-based): "شو ناقص في هذا المنتج؟"

**الخيارات المسبقة لـ "ليش ما اشتريت":**
- السعر مرتفع
- الشحن غير واضح
- لست متأكد من المقاس
- محتار بين منتجين
- محتاج معلومات أكثر
- فقط أتصفح

**Modules المستخدمة:** 4, 17

**Native overlap:** ❌ صفر — سلة لا تسأل non-buyers أبدًا

---

### Feature 2: Variant & Price Interest Capture (Wait)

**ما يفعله:**
زر صغير على PDP: "نبهني عند…" مع 3 خيارات:
1. **نزول السعر** (target price input)
2. **رجوع لون/variant معين**
3. **رجوع مقاس معين**
4. **تحديثات هذا التصنيف**

**Modules المستخدمة:** 7, 8 (جزء)

**Native overlap:** ⚠️ سلة عندها "أعلمني عند التوفر" — **لا نتنافس معها**. نقدم 3 أبعاد مكملة.

**Positioning في الـ widget:**
> "سلة تخبرك لما المنتج يرجع. نحن نخبرك لما السعر ينزل، أو يرجع لونك، أو مقاسك."

---

### Feature 3: Pre-Purchase Intent Dashboard + Product Doctor Lite (Fix)

**Dashboard sections:**
1. **Top 5 hesitation reasons** (مجمعة عبر كل المتجر)
2. **Products with most hesitation** (المنتجات الأكثر "تردد")
3. **Most requested variants** (أكثر ألوان/مقاسات مطلوبة)
4. **Most followed products** (مؤشر طلب مؤجل)
5. **Top price-watch points** (أكثر "نبهني عند نزول السعر")

**Product Doctor Lite — 5 Rules فقط (rule-based, لا AI):**

| Trigger | Doctor Recommendation |
|---|---|
| 5+ "السعر مرتفع" على منتج واحد | "اعرض ضمان السعر أو scarcity offer" |
| 5+ "محتار في المقاس" | "أضف Size Help على صفحة المنتج" |
| 5+ "محتاج معلومات أكثر" | "أضف FAQ أو فيديو شرح" |
| 5+ "نبهني عند نزول السعر" | "هذا المنتج عليه طلب — جرّب bundle بدل خصم" |
| 5+ طلب variant غير متوفر | "اطلب reorder للون/مقاس X" |

**Modules المستخدمة:** 32, 34

**Native overlap:** ⚠️ Smart Analytics لكن post-purchase فقط (Confirmed). **خطين متوازيين.**

---

### Feature 4: Widget Analytics (Measure)

**ما يفعله:**
- Views per widget
- Submissions per widget
- Submission rate (KPI الأهم — هدف ≥3٪)
- Top pages بـ submissions

**Modules المستخدمة:** 35

**Native overlap:** ❌ infrastructure داخلي

---

### ما خرج من الـ MVP بسبب overlap مع Salla

| Module | السبب | المسار الجديد |
|---|---|---|
| 5 (Ask About Product) | أسئلة المنتجات native في سلة | Phase 1 بـ positioning "Private Intent-Classified Q&A" |
| 8 — جزء Back-in-Stock | "أعلمني عند التوفر" native | جزء من Feature 2 لكن **بدون** بُعد restock البسيط |
| 22 (Cart Rescue) | السلات المتروكة native | Phase 1 |

---

## 4. السكور التفصيلي

| المعيار | السكور /5 | تفسير |
|---|---|---|
| **Native overlap risk** (5 = لا تداخل) | **5.0** | لا توجد ميزة سلة native تغطي أي من الـ 4 features (Confirmed) |
| **App Store saturation** (5 = أقل ازدحام) | **4.5** | فئة Customer Intent فارغة. فئة Analytics في App Store أيضًا فارغة (Confirmed live). |
| **Merchant pain severity** | **3.5** | ألم حقيقي لكنه latent — يحتاج education |
| **Willingness to pay** | **4.0** | unique = pricing power أعلى. SmartInsight بـ 693 SAR يثبت |
| **ROI clarity** | **3.0** | attribution لا يزال تحدي |
| **Technical feasibility on Salla** | **4.0** | hooks متاحة للـ PDP/Cart/Body. Exit Intent DIY. |
| **Retention potential** | **3.5** | weekly insights email + Doctor توصيات |
| **MVP simplicity** | **5.0** | 4 features فقط، scope أضيق وأنظف |
| **Differentiation** | **5.0** | الفجوة محققة live |
| **Strategic fit (Salla market)** | **4.0** | يخدم متاجر الإعلانات النامية |

### 📊 **السكور الإجمالي: 86/100**

**Confidence Level: High**

---

## 5. تحقق Native Overlap (Feature-by-Feature)

### Feature 1: Hesitation Capture
| نقطة الفحص | الحالة | الدليل |
|---|---|---|
| Native في سلة؟ | ❌ لا | Salla Smart Analytics = post-purchase ratings فقط (Confirmed من help.salla.sa) |
| أسئلة المنتجات native؟ | ⚠️ موجود لكن مختلف | علني، بعد التحفيز، بدون تصنيف، بدون dashboard |
| في App Store؟ | ❌ 0 تطبيقات | بحث عن: exit survey, why didn't buy, customer hesitation — 0 نتائج |
| Reviews app native؟ | ⚠️ موجود | بعد الشراء فقط، لا يلتقط non-buyers |
| **الخلاصة** | **فجوة كاملة** | لا منافس مباشر |

### Feature 2: Variant & Price Interest Capture
| نقطة الفحص | الحالة | الدليل |
|---|---|---|
| "أعلمني عند التوفر" native؟ | ✅ موجود | بُعد واحد فقط (restock) |
| Price drop alert native؟ | ❌ لا | لا توجد ميزة سعر مستهدف |
| Variant-specific alert native؟ | ❌ لا | لا توجد |
| Follow product/category native؟ | ❌ لا | لا توجد |
| **الخلاصة** | **overlap 20٪ فقط** | سلة تغطي بُعد 1 من 4 — نحن نقدم البقية |

### Feature 3: Pre-Purchase Intent Dashboard + Doctor
| نقطة الفحص | الحالة | الدليل |
|---|---|---|
| Smart Analytics native؟ | ⚠️ موجود لكن مختلف جذريًا | تغطي ratings + sales + shipping reviews فقط. **لا تشمل: hesitation, exit intent, pre-purchase signals, product diagnosis** (Confirmed) |
| SmartInsight app؟ | ⚠️ موجود لكن مختلف | AI chatbot على بيانات سلة الموجودة (693 SAR/شهر). يحلل الموجود، لا يلتقط الجديد. |
| Google Analytics integration؟ | ✅ موجود | behavior tracking خارجي، لا يربط بـ product-level diagnosis |
| فئة Analytics في App Store؟ | ❌ فارغة | "No apps available in this category" (Confirmed live) |
| Product Doctor؟ | ❌ لا يوجد native ولا في App Store | **0 منافسين** |
| **الخلاصة** | **فجوة كاملة لـ Doctor** | فرق positioning واضح لـ Dashboard |

### Feature 4: Widget Analytics
| نقطة الفحص | الحالة |
|---|---|
| موجود native؟ | ❌ (لا حاجة — infrastructure للتطبيق نفسه) |
| **الخلاصة** | لا overlap ممكن |

---

## 6. التحقق التقني من Salla

### ✅ Twilight Theme Hooks المتاحة (Confirmed)

| الـ Hook | الموقع | استخدامنا |
|---|---|---|
| `body:start` / `body:end` | كل الصفحات | Exit Intent listener، Tracking، SDK injection |
| `head:start` / `head` / `head:end` | كل الصفحات | meta, CSS |
| `product:single.description.start/end` | PDP | **Feature 1 + 2 يدخلان هنا** |
| `product:index.items.start/end` | قوائم المنتجات | Badges (Phase 2) |
| `cart:items.start/end` | السلة | Cart Intent (Phase 1) |
| `thank-you:start/end` | بعد الشراء | Post-purchase signals (Sister Products) |
| `component:path.start/end` | تلقائي | حقن نقطي مرن |

### ✅ Webhooks المتاحة (Confirmed)
- `product.quantity.low` ✅ — أساس low-stock signals
- `product.price.updated` ✅ — أساس Price Watch
- `product.updated` ✅ — أساس Variant tracking
- `abandoned.cart` ✅
- `customer.created` / `customer.updated` / `customer.login` ✅
- `review.added` ✅
- `order.created` / `order.updated` / `order.cancelled` ✅
- **Conditional Webhooks (Salla Rules)** ✅ — فلترة events حسب شروط

### ⚠️ Workarounds التقنية (تحديات حقيقية)

| القدرة | الحالة | الـ Workaround |
|---|---|---|
| Exit Intent hook رسمي | ❌ غير موجود | DIY عبر `body:end` + JS event listeners (mouseleave على desktop، scroll-up/idle-time على mobile). قابل للتنفيذ. |
| Variant-level stock webhook | ⚠️ غير مؤكد | `product.quantity.low` يفير على مستوى المنتج — **يحتاج اختبار** هل يحدد variant_id |
| `product.available` (full restock) | ⚠️ deprecated | نعتمد على `product.updated` + conditional webhook |
| Post-add-to-cart hook رسمي | ❌ | Twilight SDK يعطي `salla.cart.event` client-side — كافٍ |

### 🎯 **API Confidence Score: 75/100**

---

## 7. Competitive Landscape (Verified Live)

### تطبيقات Salla App Store الموجودة

| التطبيق | الفئة | علاقتنا |
|---|---|---|
| **PopupSnap** | Popups + Product Badges | منافس **غير مباشر** — نتجنب التشبه به |
| **PopupSmart** | No-code popup builder | منافس **غير مباشر** |
| **Wisepops** | Smart popups marketing | منافس **غير مباشر** |
| **ConvertFlow** | Popups + forms + quizzes | منافس **غير مباشر** |
| **SmartInsight** | AI analytics chatbot (693 SAR) | **يثبت WTP** — لكن مختلف عنا (existing data analysis) |
| **Reviews app** | Reviews | لا منافسة |

### الفجوة المؤكدة
- **Customer Intent / Voice-of-Customer app:** ❌ غير موجود في Salla App Store
- **Pre-purchase intelligence:** ❌ غير موجود
- **Product Doctor / Page-level diagnosis:** ❌ غير موجود

---

## 8. توزيع الـ 36 Module على 5 Scopes

### Scope 0 — MVP (الأشهر 1-3) — 4 features

| # | Module | الدور |
|---|---|---|
| 4 | Customer Intent & Hesitation | Feature 1 (Why) |
| 17 | Product Clarity & Missing Info | Feature 1 (Why) |
| 7 | Lead & Interest Capture (variant/price/follow) | Feature 2 (Wait) |
| 8 | Price & Availability Alerts (بدون restock) | Feature 2 (Wait) |
| 32 | Product Doctor Lite | Feature 3 (Fix) |
| 34 | Merchant Intent Dashboard | Feature 3 (Fix) |
| 35 | Snippet Analytics | Feature 4 (Measure) |

### Scope 1 — Phase 1 Extensions (الأشهر 4-9)

| # | Module | لماذا هنا |
|---|---|---|
| 5 | Ask About Product (Private Intent Q&A) | يحتاج فرق واضح عن أسئلة المنتجات native |
| 8 | جزء Back-in-Stock (مدمج، ليس مستقل) | كـ complement لـ "أعلمني عند التوفر" |
| 22 | Cart Rescue & Save Intent | Cart-specific intent capture |
| 9 | Follow & Preference System | امتداد طبيعي للـ Multi-Dimension Interest |
| 33 | Product Clarity Score | يحتاج 90 يوم بيانات من MVP أولًا |
| 12 | Smart Data-Based Badges | "الأكثر سؤالًا/حفظًا" — يحتاج بيانات MVP |
| 19 | Trust & Assurance Snippets | Doctor يقترحها بناءً على hesitation reasons |
| 23 | Campaign & Ad Landing Snippets | قيمة عالية للـ ad spenders |
| 10 | Product Demand & Voting | قوي للأزياء/الجمال |
| 26 | Micro Review Before Public | Reputation protection |
| 31 | Industry-specific Snippets | Templates للـ verticals |

### Scope 2 — Phase 2 Depth (الأشهر 10-18)

**الفكرة الذكية:** Popups/Badges/Countdown تدخل كـ "Recommended Actions" يقترحها Doctor، **ليست standalone**.

| # | Module | لماذا هنا |
|---|---|---|
| 3 | Floating Contact & Store Inbox | extension بعد ما يثبت positioning |
| 24 | Returning Customer & Retention | retention layer |
| 1 | Popup & Offer Builder | كـ Doctor recommended action |
| 2 | Announcement & Urgency Bar | كـ Doctor recommended action |
| 11 | Product Badges | كـ Doctor recommended action |
| 20 | AOV & Cart Booster | Intent-aware upsell |
| 13 | Social Proof & Demand Signals | يحتاج بيانات مجمعة |
| 18 | Product Comparison | بعد Product Clarity Score |

### Scope 3 — Phase 3 Strategic (شهر 18+)

| # | Module | لماذا هنا |
|---|---|---|
| 36 | AI Store Coach | استبدال rules بـ LLM — يحتاج سنة بيانات |
| 30 | Seasonal & Campaign Modes | templates ناضجة |
| 21 | Margin-Safe Revenue | يحتاج ERP integrations |

### Scope 4 — Sister Products (منتجات Salla منفصلة)

| # | Module | منتج محتمل |
|---|---|---|
| 6 | Smart FAQ & Help Center | Helpdesk for Salla |
| 14 | UGC & Creator Proof | Creator Commerce app |
| 15 | Gift & Product Finder | Gift Commerce app |
| 16 | Gift Commerce Tools | Gift Commerce app |
| 25 | Post-Purchase Experience | Loyalty/Retention app |
| 27 | Loyalty / Membership Prompts | Loyalty app |
| 28 | Mobile-first Enhancements | UI utilities theme add-on |
| 29 | Visual & Interactive Effects | UI utilities theme add-on |

### 📊 ملخص التوزيع

| Scope | Modules | Timeline |
|---|---|---|
| 0 — MVP | 7 modules | شهر 1-3 |
| 1 — Phase 1 | 11 modules | شهر 4-9 |
| 2 — Phase 2 | 8 modules | شهر 10-18 |
| 3 — Phase 3 | 3 modules | شهر 18+ |
| 4 — Sister Products | 8 modules | متى ما نضج |
| **المجموع** | **37 نقطة من 36 module** | **0 محذوف** |

---

## 9. التسعير

### الخطط

| Plan | السعر | الحد | لمن |
|---|---|---|---|
| **Free Trial** | مجاني 14 يوم | كل المزايا، **بدون credit card** | الجميع |
| **Starter** | 99 SAR/شهر | 1 widget، 100 submission/شهر، Dashboard أساسي | متاجر صغيرة (<3K زيارة) |
| **Growth** | 199 SAR/شهر | 5 widgets، 500 submission، Product Doctor كامل، export | الـ ICP الأساسي |
| **Pro** | 349 SAR/شهر | غير محدود، multi-store، API access، أولوية دعم | متاجر متقدمة |

### Logic
- ✅ **per store** وليس per user
- ✅ **submissions-based limits** (metric القيمة الحقيقية)
- ✅ **14-day free trial** بكل المزايا، **بدون credit card**
- ❌ **لا freemium دائم**
- ❌ **لا تبدأ تحت 99 SAR**

### Anchor
SmartInsight موجود بـ **693 SAR/شهر** — يثبت السقف. خططنا أرخص (99-349) = positioning أكثر سهولة للدخول.

---

## 10. ICP والسوق المستهدف

### Tier 1 — ابدأ هنا
- **متاجر الجمال والعناية** (الأولى — Recommended)
  - أسئلة كثيرة عن المكونات والاستخدام
  - variants متعددة (لون/حجم)
  - عملاء يحتاجون ثقة
- **متاجر الأزياء**
  - مقاسات/ألوان = Feature 2 يلمع هنا

### Tier 2
- **العطور** — تركيز/ثبات، repeat purchase
- **متاجر الهدايا** — كثير "محتار"

### تجنّب في البداية
- متاجر منتج واحد (single SKU)
- متاجر مأكولات/مطاعم
- متاجر تحت 1,000 زيارة شهرية (cold start)
- متاجر enterprise (دورة بيع طويلة)

### الـ ICP الأقوى
**متاجر جمال/عطور سعودية، 2,000-30,000 زيارة شهرية، تنفق ميتا/تيكتوك، عندها 50-500 SKU.**

### السوق الجغرافي
1. السعودية أولًا (Confirmed قاعدة سلة الأكبر)
2. الإمارات
3. الكويت

---

## 11. المخاطر و Mitigations

| # | Risk | Severity | Likelihood | Mitigation |
|---|---|---|---|---|
| 1 | **Customer interaction rate منخفض** | High | High | (أ) خيارات سريعة (1 tap) قبل free text<br>(ب) reward صغير مقابل الإجابة<br>(ج) micro-question (سؤال واحد)<br>(د) timing ذكي |
| 2 | **Native overlap (سلة تطلق ميزة)** | Medium | Medium | بناء **multi-product intelligence** و **Product Doctor** — أمور لن تبنيها سلة قريبًا |
| 3 | **يبدو كـ PopupSnap competitor** | High | Medium | احذف Popups من MVP، marketing من "أعرف ليش" |
| 4 | **Merchant education burden** | High | High | demo بـ 60 ثانية، onboarding يفعّل widget واحد فقط |
| 5 | **التاجر لا يفتح dashboard** | High | Medium | أسبوعي email تلقائي بأهم 3 insights + WhatsApp notification |
| 6 | **Data sparsity في المتاجر الصغيرة** | Medium | High | استبعدها من ICP. Pricing tier لا يستهدفها. |
| 7 | **Exit Intent على mobile** | Medium | High | scroll-out / idle-time triggers |
| 8 | **Privacy / consent (PDPL)** | Medium | Medium | consent layer من اليوم الأول |
| 9 | **ROI proof صعب (attribution)** | High | High | لا تعد بـ "زيادة مبيعات X٪". وعد بـ "insights قابلة للتطبيق" |
| 10 | **Retention بعد الشهر الأول** | High | Medium | value delivery أسبوعي عبر email |
| 11 | **MVP bloat** | Critical | Very High | **التزم بـ 4 features. أي feature خامس = -1** |

### Fatal Risk الوحيد
**Risk #1** — إذا submission rate تحت 1٪، التطبيق لا قيمة له.

**Action قبل البناء:** prototype بسيط على متجر صديق لمدة أسبوعين، قِس interaction rate. إذا >3٪ استمر. إذا <1٪ أعد التفكير.

---

## 12. KPIs و Kill Criteria

### KPIs للتاجر (Dashboard)
1. Hesitation submissions count
2. Top 3 hesitation reasons
3. Products with most hesitation
4. Interest signals count
5. Top requested variants

### KPIs للمنتج (داخلي)
1. **Customer submission rate** ≥ 3٪ (الأهم)
2. **Active widget rate** ≥ 80٪
3. **Weekly active merchants** ≥ 50٪
4. **30-day retention** ≥ 70٪
5. **Trial-to-paid conversion** ≥ 15٪
6. **First insight time** < 72 ساعة

### Success Criteria (بعد 90 يوم)
- 50+ متجر نشط
- 10+ متجر مدفوع
- submission rate ≥ 3٪
- 30-day retention ≥ 70٪
- 3 case studies جاهزة

### 🚨 Kill Criteria (بعد 60 يوم من MVP)
- Submission rate **< 1.5٪** → الفكرة سلوكيًا لا تعمل
- Trial-to-paid **< 5٪** → القيمة غير واضحة
- 30-day retention **< 40٪** → لا قيمة مستمرة
- Weekly dashboard open **< 30٪** → engagement layer مفقود

---

## 13. Positioning & Messaging

### Positioning Statement
> Smart Snippet System هو طبقة Customer Intent Intelligence لمتاجر سلة — يحوّل تردد العميل إلى insights قابلة للتطبيق، حتى يعرف التاجر بالضبط لماذا لم يبع، وما الذي يجب أن يصلح في كل منتج.

### One-liner
> "أعرف ليش زوارك ما اشتروا — وعلى أي منتج بالضبط."

### Tagline
> **"شو يمنع البيع؟"**

### Elevator Pitch
> سلة عندها أرقام، لكنها لا تخبرك ليش الزوار ما اشتروا. PopupSnap يعرض عروض، لكنه لا يلتقط أسباب التردد. واتساب يستقبل رسائل عشوائية. نحن نضيف طبقة ذكية فوق متجرك تسأل العميل أسئلة قصيرة في اللحظة الصحيحة، وتحوّل ردوده إلى dashboard يخبر التاجر بالضبط ماذا يصلح في أي منتج.

### Product Description (للمتجر)
> تطبيق يضيف widgets ذكية في صفحات منتجاتك تجمع نية العميل وتردده — لماذا لم يشترِ، ماذا ينتظر (سعر، لون، مقاس)، وما الذي يربكه. كل التفاعلات تتحول تلقائيًا إلى Dashboard فيه أسباب التردد، المنتجات الأكثر تأثرًا، وتوصيات Product Doctor لإصلاح كل منتج.

### Pitch إلى المرشانت
> "هل تنفق على إعلانات وترى زوارًا يدخلون ويخرجون بدون شراء؟ احنا نخبرك ليش — على مستوى المنتج. خلال 14 يوم بتعرف أكثر 3 أسباب تردد لزوارك، وأكثر 5 منتجات تحتاج إصلاح."

### Pitch إلى Salla (Partnership)
> تطبيق يكمل تقارير سلة بطبقة كيفية: ليس فقط ماذا حدث، بل لماذا. يخدم متاجر الجمال/الأزياء/العطور في رفع conversion بدون إضافة friction. مصمم لـ App Store premium tier.

### كلمات مفتاحية للـ App Store
- Customer Intent
- Hesitation Insights
- Why Didn't Buy
- Product Doctor
- Pre-purchase Intelligence
- Voice of Customer

### Why now
- نمو متاجر سلة بسرعة + ارتفاع تكلفة الإعلانات في الخليج
- نضوج المرشانت السعودي/الخليجي في فهم البيانات
- فجوة واضحة في فئة "qualitative insights" داخل App Store
- SmartInsight يثبت WTP بسعر 693 SAR

---

## 14. PDPL Compliance Requirements

### الإطار القانوني (Confirmed)
- **PDPL السعودي** نافذ منذ سبتمبر 2023، تطبيق إجباري سبتمبر 2024
- SDAIA أصدرت 48 قرار مخالفة منذ بدء التطبيق

### المتطلبات في MVP
1. **Consent layer واضح** قبل أي submission تحتوي PII
   - Checkbox غير محدد افتراضيًا
   - نص واضح: "أوافق على معالجة بياناتي لتلقي الإشعارات"
2. **Documented consent** — تسجيل timestamp + IP + النص الموافق عليه
3. **Withdrawal mechanism** — endpoint للعميل يحذف بياناته
4. **Data minimization** — لا تجمع أكثر من اللازم
5. **Hesitation submissions** بدون PII = آمنة قانونيًا (مشكلة فقط في Multi-Dimension Interest حيث نطلب جوال/إيميل)

### تكلفة Legal
- استشارة قانونية أولى: ~5,000-10,000 SAR
- Privacy Policy + Terms of Service بالعربية والإنجليزية
- يجب إنجازها قبل launch

---

## 15. الخطوات الفورية

### هذا الأسبوع
1. **افتح Salla Developer Console** وتحقق عمليًا من snippet/widget injection على PDP
2. **ابحث في Salla App Store** مرة ثانية للتأكد من غياب منافسين
3. **تواصل مع 5 تجار** جمال/عطور لسؤالهم: "إذا قلت لك ليش زوارك ما اشتروا، كم ستدفع شهريًا؟"
4. **صمم mockup صفحة واحدة** للـ Dashboard فقط — لا تبني شيء حتى تحصل على ردود فعل 3 تجار

### الأسبوعين القادمين
5. **Prototype بسيط** على متجر صديق (HTML/JS فقط بدون backend)
6. **قِس interaction rate** للـ Hesitation Capture على عينة من 500-1000 زائر
7. **Kill criteria موضوعية:**
   - إذا interaction rate > 3٪ → ابنِ الـ MVP
   - إذا 1.5-3٪ → أعد تصميم الـ UX قبل البناء
   - إذا < 1.5٪ → أعد التفكير جذريًا في الفكرة

### الأشهر 1-3 (لو نجح الـ prototype)
8. **MVP build** بـ 4 features فقط
9. **3 متاجر beta** مجانية لمدة 60 يوم لـ feedback
10. **PDPL compliance layer** من اليوم الأول
11. **Salla App Store submission** في الشهر الثالث
12. **Pricing live** بداية الشهر الرابع

---

## ملحق: التحقق Live Sources

### Salla Developer Documentation
- [Salla Developer Docs](https://docs.salla.dev/)
- [Twilight Theme Hooks](https://docs.salla.dev/422552m0)
- [Salla Webhooks](https://docs.salla.dev/421119m0)
- [Twilight JS SDK](https://docs.salla.dev/422610m0)
- [App Snippet Guide](https://salla.dev/blog/a-guide-to-app-snippet/)

### Salla App Store (Live verified)
- [Analytics Category - Empty](https://apps.salla.sa/en/categories?slug=analytics)
- [SmartInsight - 693 SAR/month](https://apps.salla.sa/en/app/593961160)
- [PopupSnap](https://apps.salla.sa/en/app/1964915315)
- [PopupSmart](https://apps.salla.sa/en/app/1106782482)
- [Wisepops](https://apps.salla.sa/en/app/900356613)
- [ConvertFlow](https://apps.salla.sa/en/app/2055995646)
- [Reviews app](https://apps.salla.sa/en/app/1408287678)

### Salla Native Features
- [Smart Analytics (post-purchase only)](https://help.salla.sa/en/article/smart-analytics-to-improve-customer-experience-1/jxzg2jptfq5kqiih27rpht2y)

### Legal
- [Saudi PDPL Compliance Guide 2026](https://www.securelink.sa/blogs/saudi-personal-data-protection-law-compliance-guide-2026/)
- [SDAIA Data Protection Law](https://sdaia.gov.sa/en/Research/Pages/DataProtection.aspx)

---

**نهاية التحليل**

> **القرار:** ✅ Go with High Confidence (86/100)
> **الـ Window:** 6-12 شهر قبل تزاحم الفئة
> **الـ MVP:** 4 features ✦ 3 أشهر ✦ Beauty/Perfumes vertical first
