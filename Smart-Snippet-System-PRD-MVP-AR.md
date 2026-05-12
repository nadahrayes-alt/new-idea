# Smart Snippet System — وثيقة متطلبات المنتج (MVP) — النسخة العربية

> **الإصدار:** 2.0 — Expanded MVP (14 features)
> **التاريخ:** 12 مايو 2026
> **آخر تحديث:** Section 27 تم توسيعها بـ specs مفصّلة لكل الـ 20 modules (10 MVP Features 5-14 + 10 Phase 2)
> **الحالة:** مسودة — جاهزة لمراجعة الهندسة والتصميم
> **الجمهور:** فريق الهندسة + التصميم + المنتج
> **الحجم الإجمالي:** 4,624 سطر
> **الوثائق ذات الصلة:**
> - [التحليل الاستراتيجي](./Smart-Snippet-System-Analysis.md)
> - [تحليل المنافسين](./Competitive-Landscape-Analysis.md)
> - [خطة العمل](./Smart-Snippet-System-Business-Plan.md)

---

## جدول المحتويات

1. [الملخص التنفيذي](#1-الملخص-التنفيذي)
2. [الخلفية والسياق](#2-الخلفية-والسياق)
3. [الأهداف وغير الأهداف](#3-الأهداف-وغير-الأهداف)
4. [الشخصيات (Personas)](#4-الشخصيات-personas)
5. [قصص المستخدمين](#5-قصص-المستخدمين)
6. [نطاق الـ MVP](#6-نطاق-الـ-mvp)
7. [الميزة الأولى — التقاط التردد (Hesitation Capture)](#7-الميزة-الأولى--التقاط-التردد)
8. [الميزة الثانية — التقاط اهتمام Variant والسعر](#8-الميزة-الثانية--التقاط-اهتمام-variant-والسعر)
9. [الميزة الثالثة — لوحة Intent + Product Doctor](#9-الميزة-الثالثة--لوحة-intent--product-doctor)
10. [الميزة الرابعة — تحليلات الـ Widget](#10-الميزة-الرابعة--تحليلات-الـ-widget)
11. [المتطلبات المشتركة](#11-المتطلبات-المشتركة)
12. [الهيكلية التقنية](#12-الهيكلية-التقنية)
13. [مواصفات التكامل مع سلة](#13-مواصفات-التكامل-مع-سلة)
14. [نموذج البيانات](#14-نموذج-البيانات)
15. [مواصفات واجهات APIs](#15-مواصفات-واجهات-apis)
16. [متطلبات تجربة المستخدم والواجهات](#16-متطلبات-تجربة-المستخدم-والواجهات)
17. [تدفق التهيئة (Onboarding)](#17-تدفق-التهيئة-onboarding)
18. [الإشعارات](#18-الإشعارات)
19. [التحليلات والقياس](#19-التحليلات-والقياس)
20. [مقاييس النجاح](#20-مقاييس-النجاح)
21. [معايير الإطلاق](#21-معايير-الإطلاق)
22. [خارج النطاق](#22-خارج-النطاق)
23. [أسئلة مفتوحة](#23-أسئلة-مفتوحة)
24. [المخاطر والتخفيف منها](#24-المخاطر-والتخفيف-منها)
25. [الجدول الزمني والمراحل](#25-الجدول-الزمني-والمراحل)
26. [الملاحق](#26-الملاحق)

---

## 1. الملخص التنفيذي

### الرؤية
**منصة Customer Intent Intelligence** لمتاجر سلة — تلتقط **لماذا** لم يشترِ الزائر، **ماذا** ينتظر، و**ما الذي** يجب إصلاحه. مع 10 ميزات إضافية تغطي insights البحث، influencer attribution، OOS recovery، و lifecycle marketing.

### نطاق الـ MVP — موسّع (14 Feature)

**النواة (Features 1-4) — حلقة Customer Intent:**
1. **Hesitation Capture Widget** (لماذا) — استبيانات نية المغادرة + وضوح المنتج
2. **Variant & Price Interest Capture** (ماذا ينتظر) — تنبيهات متعددة الأبعاد
3. **Intent Dashboard + Product Doctor Lite** (ما الذي يصلح) — Insights + توصيات قواعد
4. **Widget Analytics** (القياس) — مقاييس أداء لكل widget

**10 ميزات MVP إضافية (مضافة بناءً على القيمة الاستراتيجية):**
5. **PDPL Consent Center** (Module 40) — بوابة إدارة بيانات العميل *(إلزامي قانونًا)*
6. **Empty Search Capture** (Module 38) — إشارات طلب inventory من بحث فاشل
7. **Influencer Attribution** (Module 54) — تتبع revenue per-influencer
8. **OOS Substitute Engine** (Module 50) — استرداد conversion عند نفاذ المخزون
9. **First-Time vs Returning Recognition** (Module 39) — pre-tag intent + personalization
10. **Coming Soon / Pre-Launch Capture** (Module 51) — قائمة طلب pre-launch
11. **Cart Sharing & Save Link** (Module 55) — social commerce بمكافأة مزدوجة
12. **Vertical Discovery Quiz** (Module 46) — preference profile لكل vertical
13. **Birthday/Anniversary Capture** (Module 49) — حملات lifecycle email/WhatsApp
14. **Smart Reorder Timing** (Module 44) — automation repeat purchase حسب الفئة

### الإطلاق المستهدف (Expanded MVP Timeline)
- **Closed Beta:** اليوم 90 (كان 60)
- **التسليم لسلة:** اليوم 140 (كان 90)
- **الإطلاق العام:** اليوم 155 (كان 105)

**ملاحظة:** Timeline توسع من 15 أسبوع → 20-22 أسبوع لاستيعاب الـ 14 feature. (افتراض: Founder + Junior dev)

### السوق المستهدف (MVP)
متاجر سلة سعودية في قطاعات الجمال والعطور والأزياء. 2,000-30,000 زيارة شهريًا. 50-500 منتج.

### التسعير
99 / 199 / 349 ريال شهريًا. تجربة مجانية 14 يومًا بدون بطاقة ائتمان.

---

## 2. الخلفية والسياق

### بيان المشكلة
تعرف متاجر سلة حاليًا **ماذا** حدث في متاجرها (طلبات، مبيعات، تقييمات). لكنها لا تعرف **لماذا** لم يشترِ الزوار على مستوى كل منتج. الأدوات الحالية إما تعرض popups (مثل PopupSnap)، أو تحلل بيانات ما بعد الشراء (مثل SmartInsight وSmart Analytics)، أو ترسل تنبيهات إعادة توفير (سلة الأصلية). **لا توجد أداة تلتقط نية ما قبل الشراء وتحولها إلى توصيات قابلة للتطبيق لكل منتج.**

### الفجوة في السوق
- **0 منافس** في متجر تطبيقات سلة يقدم التقاط نية العميل
- **0 منافس** يقدم Product Doctor / تشخيص ما قبل الشراء
- Smart Analytics من سلة تخص ما بعد الشراء فقط (تم التحقق منها)
- SmartInsight تحليلات ما بعد الشراء (184 دولار/شهر) — توجيه مختلف
- Shopify يحتوي على Simplify Exit Intent Survey (4.99 دولار) لكنه بدون تكامل مع سلة

### لماذا الآن
- ارتفاع تكاليف الإعلانات في السوق الخليجي = التجار بحاجة لتقليل الفاقد في التحويل
- نمو قاعدة تجار سلة بشكل سريع
- SmartInsight بسعر 693 ريال يثبت الاستعداد للدفع مقابل أدوات الذكاء
- نافذة 6-12 شهرًا قبل ازدحام الفئة

---

## 3. الأهداف وغير الأهداف

### أهداف الـ MVP (ثلاثة رئيسية)

**الهدف 1 — إثبات الفرضية السلوكية**
التحقق من أن زوار متاجر سلة سيتفاعلون مع استبيانات التردد بمعدل تقديم ≥3%.

**الهدف 2 — إثبات الاستعداد للدفع**
التحقق من أن التجار سيدفعون 99-349 ريال شهريًا مقابل insights نية ما قبل الشراء.

**الهدف 3 — تثبيت positioning دفاعي**
بناء حضور قوي في متجر تطبيقات سلة في فئة Customer Intent باعتبارنا أول من يدخلها.

### أهداف النجاح (90 يومًا بعد الإطلاق)
- 50+ متجر نشط (تجريبي + مدفوع)
- 10+ تاجر مدفوع
- معدل تقديم ≥3% على widget التردد
- معدل احتفاظ 30 يومًا ≥70%
- 3 case studies منشورة

### غير الأهداف الصريحة (خارج الـ MVP)
- ❌ توصيات قائمة على AI (مرحلة 3)
- ❌ Popup builder / أدوات تسويق عامة
- ❌ Helpdesk / إدارة FAQs
- ❌ ميزة Wishlist مستقلة
- ❌ برامج الولاء
- ❌ تدفقات ما بعد الشراء (NPS، مراجعات...)
- ❌ إدارة متعدد المتاجر (متجر واحد لكل حساب)
- ❌ White-label / ميزات الوكالات
- ❌ تطبيق جوال (لوحة ويب فقط)
- ❌ إرسال SMS مباشر (نستخدم قنوات سلة)
- ❌ Email marketing automation (digest أساسي فقط)
- ❌ محرك A/B testing
- ❌ تتبع تحويل / إيرادات (مرحلة 2)
- ❌ شرائح عملاء (Customer segmentation)
- ❌ متعدد اللغات بخلاف العربية والإنجليزية

---

## 4. الشخصيات (Personas)

### الشخصية الأساسية: التاجرة على سلة

**الاسم:** سارة العتيبي
**العمر:** 32
**الدور:** مؤسسة/مالكة متجر تجميل على سلة
**إحصائيات المتجر:**
- 15,000 زيارة شهرية
- 200 منتج
- معدل تحويل ~3%
- 25,000 ريال/شهر إنفاق إعلاني (ميتا + تيك توك)

**الأهداف:**
- زيادة التحويل دون رفع ميزانية الإعلانات
- فهم لماذا الزوار لا يشترون
- اتخاذ قرارات مخزون أفضل (أي الألوان/المقاسات لإعادة الطلب)
- تقليل الاعتماد على الوكالات/المستشارين

**نقاط الإحباط:**
- تقارير سلة تظهر الأرقام لكن لا تشرح الأسباب
- رسائل واتساب غير منظمة
- لا تعرف أي منتج يحتاج اهتمام
- لوحات التسويق مرهقة

**المعرفة التقنية:** متوسطة. تستطيع تثبيت التطبيقات واستخدام لوحة سلة وضبط الإعدادات الأساسية. لا تكتب الكود ولا تستخدم أدوات تحليلات معقدة.

**اقتباس:** *"عندي 200 منتج، ما عندي وقت أحلل كل واحد. خليني أعرف اللي يحتاج اهتمام."*

**أين يلائم Smart Snippet:**
الساعة 9:30 صباحًا — تفتح لوحة Smart Snippet، تقرأ digest الأسبوعي، تطبق توصيتين من Doctor.

### الشخصية الثانوية: العميل النهائي

**الاسم:** فاطمة
**العمر:** 27
**السلوك:** تتصفح متاجر سلة على الجوال (85% من الجلسات)، عادة في المساء.

**نمط الشراء:**
- تزور 3-5 متاجر في كل جلسة تسوق
- تضيف للسلة في 40% من الحالات
- تكمل الدفع في 15% من الحالات
- أسباب عدم الشراء: مقارنة الأسعار، عدم التأكد من المقاس، انتظار التخفيضات

**أين يلائم Smart Snippet:**
بعد 60 ثانية على صفحة منتج، أثناء التمرير دون إضافة للسلة، يظهر سؤال غير مزعج: "شو ناقص في هذه الصفحة؟"

تختار "دليل المقاسات" وترسل في 5 ثوانٍ. التاجرة تحصل على الإشارة.

---

## 5. قصص المستخدمين

### قصص التاجر

**T1.** كتاجرة على سلة، أريد تثبيت Smart Snippet System من متجر تطبيقات سلة بنقرة واحدة لأبدأ جمع بيانات النية دون إعداد تقني.

**T2.** كتاجرة، أريد تهيئة موجّهة من 5 دقائق تفعّل أول widget لأرى القيمة خلال 24 ساعة.

**T3.** كتاجرة، أريد رؤية لماذا تخلى الزوار عن أهم 5 منتجات هذا الأسبوع لتحديد أولويات الإصلاح.

**T4.** كتاجرة، أريد أن يقترح Product Doctor إجراءات محددة (لا مجرد بيانات) لأعرف ماذا أفعل دون محلل.

**T5.** كتاجرة، أريد ملخصًا أسبوعيًا بالإيميل حتى لا أحتاج تسجيل دخول يومي.

**T6.** كتاجرة، أريد رؤية أي variants (ألوان/مقاسات) يطلبها العملاء أكثر لاتخاذ قرارات reorder.

**T7.** كتاجرة، أريد تخصيص أسباب التردد بالعربية والإنجليزية لتطابق لغة متجري.

**T8.** كتاجرة، أريد أن يستطيع عملائي ضبط تنبيهات السعر لألتقط الطلب الحساس للسعر.

**T9.** كتاجرة، أريد لسان تحليلات widget للتحقق من أن الـ widgets تعمل (معدل تقديم ≥3%).

**T10.** كتاجرة، أريد تجربة مجانية 14 يومًا بدون بطاقة ائتمان للتجربة دون مخاطرة.

### قصص العميل

**C1.** كزائر متجر سلة، أريد تقديم ملاحظات سريعة (نقرة واحدة) عن سبب عدم شرائي لمساعدة التاجر دون ملء نماذج.

**C2.** كزائر مهتم بمنتج لكن غير جاهز للشراء، أريد ضبط تنبيه سعر لإشعاري عند الانخفاض.

**C3.** كزائر مقاسي/لوني غير متوفر، أريد تسجيل اهتمامي لإشعاري عند إعادة التوفير.

**C4.** كزائر، أريد أن أعرف أن بياناتي محمية (PDPL) ويمكنني سحب الموافقة في أي وقت.

**C5.** كزائر جوال، أريد widgets لا تقاطع تجربة التصفح.

---

## 6. نطاق الـ MVP

### ما هو داخل النطاق (ابنِ هذه الـ 14 Feature)

**النواة — حلقة Customer Intent (Features 1-4):**

| # | الميزة | الـ Modules المدمجة | الأولوية |
|---|---|---|---|
| 1 | Hesitation Capture Widget | M4 + M17 | P0 (نواة) |
| 2 | Variant & Price Interest Capture | M7 + M8 (variants/price/follow فقط، **بدون restock**) | P0 (نواة) |
| 3 | Intent Dashboard + Product Doctor Lite | M32 + M34 | P0 (نواة) |
| 4 | Widget Analytics | M35 | P0 (بنية تحتية) |

**Features 5-14 — راجع Section 27 للـ specs المفصلة:**

| # | الميزة | Module | الأولوية | الجهد |
|---|---|---|---|---|
| 5 | PDPL Consent Center | M40 | P0 (قانوني) | 3-5 أيام |
| 6 | Empty Search Capture | M38 | P0 | 2-4 أيام |
| 7 | Influencer Attribution | M54 | P0 | 4-6 أيام |
| 8 | OOS Substitute Engine | M50 | P0 | 5-6 أيام |
| 9 | First-Time vs Returning | M39 | P0 | 4-5 أيام |
| 10 | Coming Soon Capture | M51 | P0 | 4-5 أيام |
| 11 | Cart Sharing | M55 | P0 | 4-5 أيام |
| 12 | Discovery Quiz | M46 | P0 | 5-7 أيام |
| 13 | Birthday Capture | M49 | P0 | 2-3 أيام |
| 14 | Smart Reorder Timing | M44 | P0 | 5-7 أيام |

**إجمالي الجهد الإضافي:** 38-53 يوم تطوير (~8-11 أسبوع لـ solo، 4-5 أسابيع لـ 2 devs).

### ما هو خارج النطاق (مؤجل للمرحلة 1/2)

| Module | السبب |
|---|---|
| M5 (Ask About Product) | تداخل مع أسئلة سلة الأصلية |
| M8 بُعد Restock فقط | تداخل مع "أعلمني عند التوفر" |
| M22 (Cart Rescue) | تداخل مع السلات المتروكة |
| M37 (Checkout Hesitation) | يحتاج verification لـ Salla checkout |
| M41 (Live Stock Urgency) | تداخل themes |
| M42 (Mobile One-Tap) | تداخل Salla Wishlist |
| M43 (Pre-Checkout) | يحتاج verification لـ Salla checkout |
| M45 (Comparison Detector) | session tracking معقد |
| M47 (Bundle Builder) | جهد كبير (8-10 أيام) |
| M48 (Recently Viewed) | تداخل themes |
| M52 (Coupon Discovery) | يحتاج بيانات search تاريخية |
| M53 (Shipping Calc) | يحتاج verification Shipping API |
| M56 (Sample Request) | كبير + operational workflow |
| Modules 1-3, 6, 9-16, 18-21, 23-31, 33, 36 | Phase 1+ / Sister Products |

---

## 7. الميزة الأولى — التقاط التردد

### 7.1 الوصف
widget غير مزعج يسأل الزوار لماذا لا يكملون التحويل، يلتقط ردودًا منظمة، ويجمعها في insights للتاجر.

**نوعان من Triggers (قابلة للضبط لكل تاجر):**
- **النوع A: Exit Intent** — يظهر حين يشير الزائر لنية المغادرة من PDP أو Cart
- **النوع B: Product Clarity** — يظهر بعد التمرير دون add-to-cart على PDP

### 7.2 تدفق المستخدم

```
[العميل يزور صفحة منتج (PDP)]
      ↓
[يتصفح 30+ ثانية، لا يضيف للسلة]
      ↓
[الـ Trigger ينطلق]
      ├── Desktop: حدث mouseleave نحو الأعلى
      └── Mobile: scroll-up + خمول 5 ثوانٍ
      ↓
[الـ Widget يظهر كـ modal/sheet]
      ↓
[العميل ينقر خيارًا] → إرسال
              أو
[العميل يكتب في "أخرى"] → إرسال
              أو
[العميل يغلق] → تسجيل حدث الإغلاق
      ↓
[رسالة شكر: ثانيتان]
      ↓
[الـ Widget يُغلق]
```

### 7.3 المتطلبات الوظيفية

**FR-1.1** يجب أن يُعرض الـ widget على صفحة المنتج (PDP) والـ Cart فقط (قابل للضبط لكل تاجر).

**FR-1.2** يجب أن يدعم الـ widget نوعَي trigger (exit intent / clarity) كل منهما قابل للتفعيل مستقلًا لكل نوع صفحة.

**FR-1.3** يجب ألا ينطلق الـ widget أكثر من **مرة واحدة لكل جلسة** لكل نوع صفحة (deduplication عبر sessionStorage).

**FR-1.4** يجب ألا ينطلق الـ widget للعملاء الذين سبق أن قدموا ردًا خلال 30 يومًا الماضية (cookie أو customer-id).

**FR-1.5** يجب أن يعرض الـ widget 6 أسباب افتراضية + خيار نص حر، كلها قابلة للضبط لكل تاجر.

**FR-1.6** يجب أن يُرسل الـ widget الرد للـ backend خلال 200 مللي ثانية (optimistic UI: عرض "شكرًا" فورًا عند النقر).

**FR-1.7** يجب أن يلتقط الـ widget metadata: product_id، page_url، session_id، customer_id (إن كان مسجل دخول)، timestamp، device_type، referrer، UTM params.

**FR-1.8** يجب أن يكون الـ widget قابلًا للإغلاق عبر زر X ومفتاح ESC (Desktop).

**FR-1.9** يجب ألا يحجب الـ widget الصفحة الأساسية (لا overlay full-screen على الجوال — استخدم bottom sheet بدلًا).

**FR-1.10** يجب أن يدعم الـ widget العربية والإنجليزية مع كشف تلقائي من locale المتجر في سلة.

**FR-1.11** يجب أن يجمع الـ widget موافقة PDPL إذا طُلبت أي PII (في widget التردد بـ MVP، لا PII = لا حاجة لموافقة إلا إذا أضاف التاجر حقل تواصل اختياري).

**FR-1.12** يجب أن يكون مدخل النص الحر محدودًا بـ 500 حرف ومعقّمًا server-side.

### 7.4 متطلبات تجربة المستخدم

**التصميم البصري:**
- بسيط، غير عدواني (ليس popup-styled)
- يرث ألوان theme سلة عبر Twilight design tokens حيثما أمكن
- زوايا مستديرة (8-12px)
- ظل خفيف
- لا ألوان فاقعة أو علامات استعجال

**الحركة:**
- انزلاق من الأسفل على الجوال (300ms ease-out)
- ظهور تدريجي على Desktop (200ms)
- انزلاق للأسفل عند الإغلاق

**سهولة الوصول (Accessibility):**
- ARIA labels على كل عناصر التفاعل
- Navigable عبر لوحة المفاتيح (Tab بين الخيارات، Enter للاختيار)
- Focus trap حين يكون مفتوحًا
- Screen reader announcements (`aria-live="polite"` لرسالة الشكر)
- تباين الألوان WCAG AA كحد أدنى

**Responsive:**
- Desktop: Modal مركزي بعرض أقصى 480px
- Tablet: Modal مع هوامش جانبية
- Mobile: Bottom sheet، عرض كامل

### 7.5 خيارات الإعداد (لكل تاجر)

```typescript
interface HesitationWidgetConfig {
  enabled: boolean;
  triggers: {
    exitIntent: {
      enabled: boolean;
      pages: ('pdp' | 'cart')[];
      minTimeOnPage: number; // ثوانٍ، افتراضي 30
    };
    productClarity: {
      enabled: boolean;
      scrollThreshold: number; // %، افتراضي 50
      idleTime: number; // ثوانٍ، افتراضي 60
    };
  };
  reasons: {
    id: string;
    label_ar: string;
    label_en: string;
    enabled: boolean;
    order: number;
  }[];
  allowFreeText: boolean;
  freeTextPlaceholder_ar: string;
  freeTextPlaceholder_en: string;
  thankYouMessage_ar: string;
  thankYouMessage_en: string;
  showRewardCoupon: boolean; // حافز اختياري
  couponCode?: string;
}
```

**الأسباب الافتراضية (vertical الجمال/العطور):**
1. السعر مرتفع / Price too high
2. الشحن غير واضح / Unclear shipping
3. لست متأكد من المقاس/الحجم / Unsure about size
4. محتار بين منتجات / Comparing products
5. محتاج معلومات أكثر / Need more info
6. فقط أتصفح / Just browsing

### 7.6 منطق الـ Triggers

**Exit Intent — Desktop:**
```javascript
document.addEventListener('mouseleave', (e) => {
  if (e.clientY < 20 && !triggered) {
    triggered = true;
    showWidget();
  }
});
```

**Exit Intent — Mobile (بديل):**
```javascript
// كشف الخمول + scroll-up
let lastScrollY = window.scrollY;
let idleTimer;

window.addEventListener('scroll', () => {
  const currentY = window.scrollY;
  if (currentY < lastScrollY - 100 && !triggered) {
    triggered = true;
    showWidget();
  }
  lastScrollY = currentY;
  
  clearTimeout(idleTimer);
  idleTimer = setTimeout(() => {
    if (!triggered && timeOnPage > 30) {
      showWidget(); // احتياطي: خمول 30 ثانية
    }
  }, 30000);
});
```

**Product Clarity (مبني على التمرير):**
```javascript
const scrollListener = () => {
  if (scrollPercent() > 50 && timeOnPage > 60 && !triggered) {
    triggered = true;
    showWidget();
  }
};
```

### 7.7 البيانات الملتقطة

```typescript
interface HesitationSubmission {
  id: string; // UUID
  merchant_id: string;
  widget_id: string;
  trigger_mode: 'exit_intent' | 'product_clarity';
  reason_id?: string;
  reason_label?: string;
  free_text?: string;
  product_id: string;
  product_handle: string;
  product_price: number;
  page_url: string;
  page_type: 'pdp' | 'cart';
  customer_id?: string;
  session_id: string;
  device_type: 'desktop' | 'mobile' | 'tablet';
  user_agent: string;
  referrer?: string;
  utm_source?: string;
  utm_medium?: string;
  utm_campaign?: string;
  time_on_page_seconds: number;
  scroll_depth_percent: number;
  created_at: timestamp;
  ip_country?: string;
}
```

### 7.8 حالات الحافة (Edge Cases)

| الحالة | السلوك |
|---|---|
| العميل سبق أن قدم اليوم | لا تعرض الـ widget. سجل skip في analytics. |
| الصفحة بدون product data (404، مخصصة) | لا تُعرض الـ widget. |
| العميل يمرر بسرعة (>10 events/s) | Throttle لتجنب CPU spike. |
| عدة PDPs في جلسة واحدة | كل PDP ينطلق مستقلًا (حد أقصى 3 لكل جلسة). |
| العميل بـ JavaScript معطل | الـ widget لا يُعرض. Graceful degradation. |
| theme سلة يبطل styling أساسي | الـ widget يستخدم Shadow DOM للعزل. |
| شبكة بطيئة (3G) | الإرسال يُحفظ في localStorage، يُعاد المحاولة عند تحميل صفحة جديدة. |
| فشل الإرسال (خطأ 500) | عرض "تم الاستلام" optimistically، إعادة محاولة 3 مرات خلفية. |

### 7.9 اعتبارات الجوال
- Bottom sheet بدلًا من modal
- أزرار مناسبة للمس (حد أدنى 44px)
- وعي بالكيبورد للنص الحر (تمرير للحفاظ على رؤية المدخل)
- Swipe-down للإغلاق
- لا exit intent عبر mouseleave (استخدم scroll-up + خمول)

### 7.10 سهولة الوصول
- كل الأزرار لديها `role="button"` وlabels واضحة
- الـ modal لديه `role="dialog"` + `aria-modal="true"`
- Focus ينتقل لأول خيار عند الفتح
- Focus يعود لعنصر trigger عند الإغلاق
- تباين الألوان حد أدنى 4.5:1 للنصوص

---

## 8. الميزة الثانية — التقاط اهتمام Variant والسعر

### 8.1 الوصف
تلتقط الاهتمام الكامن من الزوار الذين لا يشترون بسبب السعر، أو variant مفقود (لون/مقاس)، أو رغبتهم في متابعة التحديثات. تُجمَع في خريطة اهتمام متعددة الأبعاد.

### 8.2 تدفق المستخدم

```
[العميل على PDP]
      ↓
[يرى زر "نبهني" بجانب Add to Cart]
      ↓
[ينقر الزر]
      ↓
[Modal يعرض خيارات الاهتمام]
      ↓
[العميل يختار: نزول السعر / variant / متابعة]
      ↓
[يُدخل رقم الجوال (تنسيق سعودي/خليجي)]
      ↓
[Checkbox موافقة PDPL (غير مفعّل افتراضيًا)]
      ↓
[إرسال] → تأكيد
      ↓
[العميل يستلم واتساب/SMS عند تحقق الشرط]
```

### 8.3 المتطلبات الوظيفية

**FR-2.1** يجب أن يُعرض زر "نبهني" على PDP، قريبًا من زر Add to Cart.

**FR-2.2** يجب أن يدعم النظام 4 أنواع اهتمام: target_price، variant_color، variant_size، follow_product.

**FR-2.3** يجب أن يدعم النظام follow_category وfollow_brand (قابلة للتفعيل، معطلة افتراضيًا في MVP).

**FR-2.4** يجب أن يُدخل العميل رقم جوال بصيغة سعودي/خليجي (validation: +966، +971، +965، +973، +968، +974).

**FR-2.5** يجب أن يضع العميل علامة صريحة على checkbox موافقة PDPL (غير مفعّل افتراضيًا).

**FR-2.6** يجب ألا يرسل النظام إشعارات حتى يُخزَّن timestamp الموافقة.

**FR-2.7** عند تحقق شرط target_price (عبر webhook `product.price.updated`)، يجب أن يضع النظام إشعار في طابور.

**FR-2.8** عند تحقق شرط restock لـ variant (عبر webhook `product.updated`)، يجب أن يضع النظام إشعارًا.

**FR-2.9** يجب أن تُرسل الإشعارات عبر WhatsApp Business API (الأساسي) مع SMS كاحتياط.

**FR-2.10** يجب أن يتمكن كل عميل من رؤية وحذف إشارات اهتمامه عبر URL إدارة موافقة عام.

**FR-2.11** يجب أن يعمل كشف الـ variants مع product options في سلة (لون، مقاس...) — التعامل مع المتاجر ذات الخيارات المخصصة.

**FR-2.12** يجب أن يزيل النظام التكرار في إشارات الاهتمام (نفس العميل + نفس المنتج + نفس الشرط = سجل واحد).

### 8.4 متطلبات تجربة المستخدم

**أسلوب الزر:**
- زر ثانوي (ليس primary — لا ينافس Add to Cart)
- أيقونة: 🔔 أو SVG جرس
- النص: "نبهني" / "Notify me"
- الموقع: تحت أو بجانب Add to Cart

**أسلوب الـ Modal:**
- Bottom sheet ينزلق على الجوال
- Modal مركزي على Desktop (عرض أقصى 420px)
- أقسام واضحة: اختيار الاهتمام → الجوال → الموافقة

**إشارات الثقة في الـ Modal:**
- "🔒 بياناتك محمية وفق نظام PDPL"
- "✋ يمكنك إلغاء التنبيهات في أي وقت"

### 8.5 خيارات الإعداد

```typescript
interface InterestWidgetConfig {
  enabled: boolean;
  buttonPosition: 'next_to_add_to_cart' | 'below_add_to_cart' | 'sticky_bottom';
  buttonLabel_ar: string;
  buttonLabel_en: string;
  enabledInterestTypes: {
    targetPrice: boolean;
    variantColor: boolean;
    variantSize: boolean;
    followProduct: boolean;
    followCategory: boolean;
    followBrand: boolean;
  };
  notificationChannels: {
    whatsapp: boolean;
    sms: boolean;
    email: boolean;
  };
  defaultMessage_ar: string;
  defaultMessage_en: string;
  consentText_ar: string;
  consentText_en: string;
  privacyPolicyUrl: string;
}
```

### 8.6 البيانات الملتقطة

```typescript
interface InterestSignal {
  id: string;
  merchant_id: string;
  customer_phone: string; // مُجزَّأ في التخزين، آخر 4 أرقام مرئية
  customer_email?: string;
  customer_salla_id?: string;
  product_id: string;
  product_variant_id?: string;
  interest_type: 'target_price' | 'variant_color' | 'variant_size' | 'follow_product' | 'follow_category' | 'follow_brand';
  target_value?: {
    price?: number;
    color?: string;
    size?: string;
    category_id?: string;
    brand_id?: string;
  };
  status: 'active' | 'triggered' | 'cancelled' | 'expired';
  consent_given_at: timestamp;
  consent_ip: string;
  consent_text_version: string;
  notification_channel: 'whatsapp' | 'sms' | 'email';
  notification_sent_at?: timestamp;
  notification_clicked_at?: timestamp;
  cancelled_at?: timestamp;
  expires_at: timestamp; // افتراضي: 90 يومًا
  created_at: timestamp;
}
```

### 8.7 حالات الحافة

| الحالة | السلوك |
|---|---|
| الجوال مسجَّل بالفعل لهذا المنتج | تحديث السجل الموجود، لا تكرار |
| العميل يُدخل جوال غير سعودي/خليجي | رفض مع رسالة خطأ واضحة |
| validation: تنسيق غير صحيح | خطأ inline، لا إرسال |
| الموافقة غير مفعّلة | زر الإرسال معطّل |
| سعر مستهدف ≤ السعر الحالي | تحذير: "السعر الحالي أقل من الذي حددته" |
| الـ Variant لم يعد موجودًا | إشعار العميل بإلغاء الـ variant |
| العميل ضرب endpoint الحذف | حذف cascade لكل إشاراته لهذا التاجر |
| webhook وصل بعد إلغاء العميل | تخطي الإشعار |
| فشل الإشعار (WA blocked) | احتياط لـ SMS، ثم email |

### 8.8 التكامل مع Webhooks سلة

```javascript
// Pseudo-code لمعالج webhook
on('product.price.updated', async (event) => {
  const { product_id, new_price, old_price } = event.data;
  
  if (new_price >= old_price) return; // فقط عند الانخفاض
  
  const matchingSignals = await db.interestSignals.find({
    product_id,
    interest_type: 'target_price',
    status: 'active',
    'target_value.price': { $gte: new_price },
  });
  
  for (const signal of matchingSignals) {
    await notificationQueue.enqueue({
      signal_id: signal.id,
      channel: signal.notification_channel,
      template: 'price_drop',
      params: { product_id, new_price, old_price },
    });
  }
});

on('product.updated', async (event) => {
  // تحقق من تغير توفر الـ variants
  // مطابقة مع إشارات variant_color وvariant_size
});

on('product.quantity.low', async (event) => {
  // ملاحظة: restock ليس جزءًا من MVP (سلة الأصلية تتعامل معه)
  // لكن low quantity قد يطلق إشارات urgency لاحقًا
});
```

### 8.9 اعتبارات الجوال
- مدخل الجوال: لوحة مفاتيح رقمية
- قائمة رمز الدولة تعرض العلم
- زر الإرسال: عرض كامل على الجوال

### 8.10 سهولة الوصول
- labels النموذج مرتبطة بالمدخلات (htmlFor)
- رسائل الخطأ تُعلَن عبر `aria-live`
- checkbox الموافقة: label واضحة، تاب target كبير

---

## 9. الميزة الثالثة — لوحة Intent + Product Doctor

### 9.1 الوصف
لوحة تواجه التاجر تجمع submissions التردد وإشارات الاهتمام في insights قابلة للتطبيق، مع Product Doctor قائم على قواعد يوصي بإصلاحات محددة لكل منتج.

### 9.2 أقسام اللوحة

**القسم أ: الإحصائيات العلوية (Hero)**
```
هذا الأسبوع:
- Hesitation Submissions: 142 (↑18% مقارنة بالأسبوع الماضي)
- Interest Signals: 87 (↑22%)
- Active Widgets: 4 / 5
- معدل التقديم: 3.1% ✅
```

**القسم ب: أهم 3 أسباب تردد**
رسم بياني شريطي مع %، عدد خام. فلتر: هذا الأسبوع / آخر 30 يوم / كل الوقت.

**القسم ج: منتجات تحتاج اهتمام**
جدول مرتب حسب إجمالي intent signals (hesitation + interest). نقر الصف → تفاصيل المنتج.

```
المنتج                       Issues  Severity
─────────────────────────────────────────────
Vitamin C Serum                15     🔴 High
Black Maxi Dress               12     🟡 Medium
Oud Royal 100ml                 9     🟡 Medium
Niacinamide Serum               7     🟢 Low
```

**القسم د: Variant Heatmap**
يعرض أكثر variants طلبًا (ألوان/مقاسات) عبر كل المنتجات.

**القسم هـ: توصيات Doctor**
قائمة بطاقات للتوصيات النشطة. كل بطاقة فيها زر تطبيق.

### 9.3 قواعد Doctor (5 قواعد MVP)

```typescript
interface DoctorRule {
  id: string;
  name: string;
  condition: (signals: ProductSignals) => boolean;
  recommendation: {
    title_ar: string;
    title_en: string;
    explanation_ar: string;
    explanation_en: string;
    actionType: 'create_snippet' | 'reorder_inventory' | 'create_bundle' | 'add_content';
    actionPayload: any;
  };
  severity: 'low' | 'medium' | 'high';
}

const MVP_RULES: DoctorRule[] = [
  {
    id: 'rule_high_price_complaints',
    name: 'High Price Complaints',
    condition: (s) => s.hesitationByReason['price_high'] >= 5,
    recommendation: {
      title_ar: 'السعر يبدو مرتفعًا لـ X عميل',
      title_en: 'Price seems high to X customers',
      explanation_ar: 'فكر في bundle بدلًا من خصم، أو اعرض ضمان السعر',
      explanation_en: 'Consider a bundle instead of discount, or offer price guarantee',
      actionType: 'create_bundle',
      actionPayload: { product_id: '$product_id', suggested_bundle_value: 0.15 },
    },
    severity: 'high',
  },
  {
    id: 'rule_size_confusion',
    name: 'Size Confusion',
    condition: (s) => s.hesitationByReason['size_unclear'] >= 5,
    recommendation: {
      title_ar: 'X عميل غير متأكد من المقاس',
      title_en: 'X customers unsure about size',
      explanation_ar: 'أضف Size Help snippet أو دليل المقاسات',
      explanation_en: 'Add a Size Help snippet or size chart',
      actionType: 'create_snippet',
      actionPayload: { snippet_template: 'size_help' },
    },
    severity: 'high',
  },
  {
    id: 'rule_info_missing',
    name: 'Information Missing',
    condition: (s) => s.hesitationByReason['need_more_info'] >= 5 || s.clarityByMissing['video'] >= 5,
    recommendation: {
      title_ar: 'صفحة المنتج تحتاج معلومات أكثر',
      title_en: 'Product page needs more info',
      explanation_ar: 'أضف FAQ أو فيديو شرح',
      explanation_en: 'Add FAQ or explanation video',
      actionType: 'add_content',
      actionPayload: { content_type: 'faq_or_video' },
    },
    severity: 'medium',
  },
  {
    id: 'rule_price_demand',
    name: 'Price Drop Demand',
    condition: (s) => s.interestByType['target_price'] >= 5,
    recommendation: {
      title_ar: 'X عميل ينتظر نزول السعر',
      title_en: 'X customers waiting for price drop',
      explanation_ar: 'جرّب bundle بدلًا من خصم لتحويلهم',
      explanation_en: 'Try a bundle instead of discount to convert them',
      actionType: 'create_bundle',
      actionPayload: { audience: 'price_watchers' },
    },
    severity: 'medium',
  },
  {
    id: 'rule_variant_demand',
    name: 'Variant Demand',
    condition: (s) => s.interestByType['variant_color'] + s.interestByType['variant_size'] >= 5,
    recommendation: {
      title_ar: 'X عميل يطلب variant غير متوفر',
      title_en: 'X customers requesting unavailable variant',
      explanation_ar: 'فكّر في reorder للمخزون',
      explanation_en: 'Consider reordering inventory',
      actionType: 'reorder_inventory',
      actionPayload: { suggested_quantity: '$signal_count * 2' },
    },
    severity: 'high',
  },
];
```

### 9.4 محرك التوصيات

**الـ Pipeline:**
1. **Daily Cron Job** يعمل في الساعة 4 صباحًا (توقيت السعودية)
2. لكل تاجر نشط، يحسب signals لكل منتج من آخر 7 أيام
3. يقيّم كل قاعدة مقابل signals كل منتج
4. يولّد سجلات Recommendation جديدة (الحالة: `pending`)
5. يزيل التكرار مقابل recommendations الموجودة (لا يعاد التوصية بنفس الشيء خلال 7 أيام)
6. يرسل digest أسبوعي صباح الإثنين 9 صباحًا

**دورة حياة التوصية:**
- `pending` → التاجر يراها في اللوحة
- `applied` → التاجر ضغط Apply
- `dismissed` → التاجر ضغط Dismiss
- `expired` → 14 يومًا بدون إجراء

**إجراءات الـ Apply (MVP):**
- `create_snippet`: يفتح معالج إنشاء snippet مع template معبأ
- `reorder_inventory`: يصدّر CSV مع variant + كمية مقترحة
- `create_bundle`: يفتح إنشاء bundle سلة في تاب جديد
- `add_content`: يعرض قائمة محتوى مقترح

### 9.5 Digest الأسبوعي عبر Email

**وقت الإرسال:** الإثنين 9 صباحًا توقيت السعودية
**العنوان:** "📊 ملخص أسبوع متجرك — 3 توصيات جاهزة"

**نموذج المحتوى:**
```
السلام عليكم [اسم التاجر]،

هذا ملخص intent signals لمتجرك هذا الأسبوع:

📥 Submissions: 142 (↑18%)
🔔 Interest Signals: 87 (↑22%)

أهم 3 أسباب التردد:
1. السعر مرتفع — 54 رد
2. غير متأكد من المقاس — 32
3. معلومات ناقصة — 28

🩺 توصيات Doctor جاهزة:
1. Vitamin C Serum: أضف فيديو شرح
2. Black Dress L: 30 طلب — reorder priority
3. Oud Royal 100ml: 18 طلب نزول سعر — جرّب bundle

[افتح Dashboard للتفاصيل →]
```

### 9.6 المتطلبات الوظيفية

**FR-3.1** يجب أن تحمل اللوحة في <2 ثانية على شبكة 3G (هدف <500ms على 4G).

**FR-3.2** يجب أن تتحدث كل المقاييس كل 5 دقائق (أو عند الطلب عبر زر تحديث).

**FR-3.3** يجب أن تدعم اللوحة فلترة بنطاق التاريخ: 7 أيام، 30 يومًا، 90 يومًا، الكل.

**FR-3.4** يجب ألا تظهر توصيات Doctor نفس التوصية لنفس المنتج أكثر من مرة كل 7 أيام (إلا إذا تضاعف الحد).

**FR-3.5** إجراء Apply يجب أن يكون بنقرة واحدة حيثما أمكن.

**FR-3.6** كل الأرقام يجب أن تكون قابلة للنقر (drill down إلى البيانات المصدرية).

**FR-3.7** الـ Digest الأسبوعي يجب أن يرسل لإيميل التاجر الأساسي (من ملف متجر سلة).

**FR-3.8** اللوحة يجب أن تكون mobile-responsive (التاجر قد يفتحها على الجوال).

### 9.7 متطلبات تجربة المستخدم

**تسلسل المعلومات:**
1. ما هو عاجل (إشارات حمراء) — أعلى الصفحة
2. ما هو قابل للتطبيق (توصيات Doctor) — بعدها
3. ما هو مثير للاهتمام (trends، charts) — في الأسفل

**التصميم البصري:**
- نظيف، dense بالبيانات (ليس marketing-styled)
- استخدام اللون بحذر: أحمر/أصفر/أخضر للـ severity
- أرقام واضحة، labels أخف
- أزرار الإجراءات واضحة المرئية

**حالات الفراغ:**
- اليوم 1: "👋 مرحبًا — ابنِ widget أول وستظهر بياناتك خلال 24 ساعة"
- أقل من 10 submissions: "📊 جمعنا 7 ردود — نحتاج 10+ لإنتاج insights"
- لا توصيات: "✅ كل المنتجات بحالة جيدة هذا الأسبوع"

### 9.8 حالات الحافة

| الحالة | السلوك |
|---|---|
| التاجر لديه 0 submissions | عرض حالة فراغ مع نصائح onboarding |
| التاجر لديه <10 submissions لمنتج | لا تظهره في Doctor (بيانات غير كافية) |
| التاجر يرفض نفس التوصية 3 مرات | كبح تلك القاعدة لذلك المنتج لـ 30 يومًا |
| قاعدتان تنطلقان لنفس المنتج | عرض كلتيهما، مرتبتين حسب الـ severity |
| متجر التاجر لديه 5,000+ منتج | Pagination (50 لكل صفحة)، lazy load |

---

## 10. الميزة الرابعة — تحليلات الـ Widget

### 10.1 الوصف
مقاييس أداء لكل widget. خفيفة في الـ MVP — لا تحليل funnel، لا A/B testing.

### 10.2 المتطلبات الوظيفية

**FR-4.1** يجب أن يتتبع النظام هذه الأحداث لكل widget:
- `widget_viewed` (impression)
- `widget_interacted` (أي نقر/لمس)
- `widget_submitted` (إرسال ناجح)
- `widget_dismissed` (إغلاق بدون إرسال)

**FR-4.2** يجب أن تعرض اللوحة لكل widget:
- Views (عدد)
- Submissions (عدد)
- معدل التقديم (= submissions / views)
- أهم 5 صفحات حسب submissions
- رسم trend 7 أيام (sparkline)

**FR-4.3** معدل التقديم يجب أن يعرض مؤشرًا بصريًا:
- ≥3%: ✅ أخضر
- 1.5-3%: 🟡 أصفر
- <1.5%: 🔴 أحمر مع تنبيه "أعد فكرة الـ widget"

**FR-4.4** التحليلات يجب أن تكون قابلة للاستعلام بنطاق التاريخ (7 أيام، 30 يومًا، الكل).

### 10.3 نموذج البيانات

```typescript
interface WidgetEvent {
  id: string;
  merchant_id: string;
  widget_id: string;
  event_type: 'viewed' | 'interacted' | 'submitted' | 'dismissed';
  page_url: string;
  page_type: 'pdp' | 'cart' | 'other';
  product_id?: string;
  session_id: string;
  device_type: 'desktop' | 'mobile' | 'tablet';
  created_at: timestamp;
}

interface WidgetMetricsDaily {
  merchant_id: string;
  widget_id: string;
  date: date;
  views: number;
  interactions: number;
  submissions: number;
  dismissals: number;
}
```

### 10.4 متطلبات تجربة المستخدم

تصميم بطاقة لكل widget:
```
┌─────────────────────────────────────┐
│ 📈 Exit Survey Widget                │
│                                     │
│ Views:           4,532               │
│ Submissions:       142               │
│ Rate:            3.1% ✅             │
│                                     │
│ ▁▂▃▅▇▆▅  آخر 7 أيام                 │
│                                     │
│ أهم الصفحات:                          │
│  /products/vitamin-c    24          │
│  /products/black-dress  18          │
│                                     │
│ [ تفاصيل ]                          │
└─────────────────────────────────────┘
```

---

## 11. المتطلبات المشتركة

### 11.1 التوطين (i18n)
- اللغات الافتراضية: العربية (ar) + الإنجليزية (en)
- الكشف من locale متجر سلة عبر API
- السماح للتاجر بتجاوز الإعداد في الإعدادات
- كل نصوص الواجهة externalized إلى ملفات i18n
- تنسيق التاريخ/الأرقام لكل locale
- دعم RTL للعربية (استخدم `dir="rtl"` وCSS logical properties)

### 11.2 الامتثال لـ PDPL (إلزامي)
- موافقة opt-in صريحة لأي جمع PII (جوال، إيميل)
- Checkbox الموافقة غير مفعّل افتراضيًا
- موافقة موثقة: timestamp + IP + نسخة نص الموافقة + locale
- رابط Privacy Policy يوفره التاجر (نحن نولّد template)
- Endpoint حقوق صاحب البيانات: `/customer/consent/manage?token=...`
  - عرض كل بياناتي
  - حذف كل بياناتي
  - سحب الموافقة
- الاحتفاظ بالبيانات: 90 يومًا للبيانات بدون موافقة، إلى أجل غير مسمى (حتى السحب) للموافقة عليها
- لا بيع/مشاركة بيانات مع طرف ثالث
- موقع الخادم: يجب أن يكون السعودية أو منطقة متوافقة

### 11.3 ميزانية الأداء
- Bundle الـ snippet JS: ≤30 KB مضغوط
- تحميل الـ snippet: ≤200ms على 4G
- تأثير تحميل الصفحة: ≤100ms (TTI delta)
- أوقات استجابة API:
  - GET /dashboard: ≤500ms p95
  - POST /widget/submit: ≤200ms p95
  - POST /interest/track: ≤200ms p95
- معالجة Webhook: ≤2s p95

### 11.4 التجاوب مع الجوال
- تصميم mobile-first
- اختبار على iPhone SE (الأصغر)، iPhone 14، iPhone 14 Pro Max، Galaxy S22، iPad
- كل الـ widgets: مناسبة للمس (44px tap target أدنى)
- اللوحة: جدول متجاوب → بطاقات على الجوال

### 11.5 سهولة الوصول (WCAG 2.1 AA)
- تباين الألوان 4.5:1 حد أدنى للنصوص
- Navigation عبر لوحة المفاتيح لكل عناصر التفاعل
- Focus مرئي على كل عناصر focusable
- Screen reader announcements للمحتوى الديناميكي
- Alt text على كل الصور
- Labels النموذج مرتبطة بالمدخلات

### 11.6 الأمان
- HTTPS في كل مكان
- CSP headers (لا inline scripts في production)
- مصادقة API: OAuth 2.0 مع سلة + JWT لـ backend
- تحديد المعدل: 100 req/min لكل تاجر، 10 submissions/min لكل جلسة
- تعقيم المدخلات على كل النصوص المُدخلة (server-side)
- منع SQL injection (queries مع parameters / ORM)
- منع XSS (escape كل النصوص المعروضة)
- CSRF tokens على endpoints تغير الحالة
- البيانات الحساسة (أرقام الجوالات) مُجزَّأة في الـ rest، عرض جزئي
- Audit log لكل إجراءات admin

### 11.7 دعم المتصفحات
- Chrome: آخر إصدارين
- Safari: آخر إصدارين (iOS Safari حرج)
- Firefox: آخر إصدارين
- Edge: آخر إصدارين
- IE 11: غير مدعوم

---

## 12. الهيكلية التقنية

### 12.1 الرسم العالي المستوى

```
┌─────────────────────────────────────────────────────────────┐
│            Salla Storefront (واجهة العميل)                  │
│  ┌──────────────────────────────────────────────────────┐   │
│  │ Twilight Theme + Smart Snippet JS (يُحقن عبر          │   │
│  │ body:end hook + product/cart hooks)                   │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────┬───────────────────────────────────┘
                          │ HTTPS (POST events)
                          ▼
┌─────────────────────────────────────────────────────────────┐
│           Smart Snippet Backend (خدمتنا)                     │
│  ┌─────────────────┐  ┌─────────────────┐                   │
│  │  Public API     │  │  Merchant API   │                   │
│  │  (storefront)   │  │  (dashboard)    │                   │
│  └────────┬────────┘  └────────┬────────┘                   │
│           ▼                    ▼                            │
│  ┌─────────────────────────────────────┐                    │
│  │       منطق التطبيق                   │                    │
│  │  - معالجة Submission                  │                    │
│  │  - محرك قواعد Doctor                  │                    │
│  │  - مرسل الإشعارات                     │                    │
│  └──────────────┬──────────────────────┘                    │
│                 ▼                                            │
│  ┌─────────────────────────────────────┐                    │
│  │       قاعدة بيانات PostgreSQL         │                    │
│  └─────────────────────────────────────┘                    │
└─────────────────────────────────────────────────────────────┘
         ▲                          ▲
         │ Webhooks                 │ API calls
         │                          │
┌────────┴──────────────────────────┴─────────────────────────┐
│                       منصة سلة                                │
└──────────────────────────────────────────────────────────────┘
```

### 12.2 الـ Tech Stack الموصى به

**Frontend (Storefront Widget):**
- Vanilla TypeScript أو Preact (small footprint)
- بدون framework ثقيل — تحت 30 KB مضغوط
- Shadow DOM لعزل الـ styling
- Inline SVG للأيقونات

**Frontend (لوحة التاجر):**
- Next.js (SSR + DX جيد)
- TypeScript
- Tailwind CSS (متوافق مع design tokens سلة)
- React Query لجلب البيانات
- shadcn/ui أو مماثل للمكونات

**Backend:**
- Node.js (TypeScript) — pool توظيف سهل في السعودية
- Framework: NestJS أو Fastify
- ORM: Prisma أو Drizzle
- Queue: BullMQ + Redis
- Cron: node-cron أو مماثل

**قاعدة البيانات:**
- PostgreSQL 16+
- Read replica لاستعلامات analytics (اختياري في MVP)

**البنية التحتية:**
- الاستضافة: AWS منطقة الرياض (PDPL compliance)
- CDN: CloudFront أو Bunny
- المراقبة: Sentry + Datadog/Grafana
- Logs: CloudWatch أو Loki

**أطراف ثالثة:**
- WhatsApp Business API: Meta مباشرة أو Wati/Twilio
- Email: SendGrid أو Postmark
- SMS: Unifonic (Saudi-focused) أو Twilio

### 12.3 استراتيجية النشر
- CI/CD: GitHub Actions
- البيئات: dev / staging / production
- ترحيلات قاعدة البيانات: Prisma Migrate
- Feature flags: Unleash أو env vars بسيطة
- نشر بدون توقف: blue-green أو rolling

---

## 13. مواصفات التكامل مع سلة

### 13.1 تسجيل التطبيق
سجّل كتطبيق سلة عبر Salla Partners Portal:
- اسم التطبيق: Smart Snippet System
- النوع: Public (App Store)
- Redirect URLs: `https://app.smartsnippet.sa/auth/salla/callback`

### 13.2 OAuth Scopes المطلوبة

| Scope | الغرض | المبرر |
|---|---|---|
| `read_orders` | مستقبلًا: post-purchase context | المرحلة 2 — نطلبه الآن للاستخدام المستقبلي |
| `read_customers` | مطابقة إشارات الاهتمام بالعملاء | مطلوب للميزة 2 |
| `read_products` | عرض المنتجات في اللوحة | مطلوب لكل الميزات |
| `write_app_settings` | تخزين إعدادات التاجر | مطلوب |

**التحقق من أسماء scopes الدقيقة في وثائق سلة.**

### 13.3 Webhooks المشتركة (MVP)

| حدث Webhook | الاستخدام | المعالج |
|---|---|---|
| `product.price.updated` | إطلاق إشعارات target_price | `webhooks/price-updated.ts` |
| `product.updated` | كشف restock للـ variants | `webhooks/product-updated.ts` |
| `product.quantity.low` | استخدام مستقبلي | `webhooks/quantity-low.ts` (تسجيل فقط في MVP) |
| `customer.created` | مطابقة إشارات مجهولة بالعملاء | `webhooks/customer-created.ts` |
| `app.installed` | إطلاق onboarding | `webhooks/app-installed.ts` |
| `app.uninstalled` | تنظيف + email وداع | `webhooks/app-uninstalled.ts` |

### 13.4 Hooks ثيم Twilight المستخدمة (تم التحقق)

| الـ Hook | الاستخدام |
|---|---|
| `body:end` | حقن bundle الـ snippet الرئيسي + Exit Intent listener |
| `head:end` | حقن CSS لأنماط Shadow DOM |
| `product:single.description.end` | وضع زر Interest Capture + anchor widget التردد على PDP |
| `cart:items.end` | وضع widget التردد على صفحة Cart |

### 13.5 Endpoints API سلة المستخدمة (تحقق من المسارات الدقيقة)

| Endpoint | الغرض |
|---|---|
| `GET /products/:id` | جلب تفاصيل المنتج للوحة |
| `GET /products?filter[ids]=...` | جلب كميات منتجات |
| `GET /customers/:id` | مطابقة الإشارات بالعملاء |
| `GET /store` | الحصول على معلومات المتجر، locale |

### 13.6 إعداد App Snippet
سجّل App Snippets في Salla Partners Portal:
- Snippet 1: `smart_snippet_main` — body:end، كل الصفحات
- Snippet 2: `smart_snippet_pdp` — product:single.description.end
- Snippet 3: `smart_snippet_cart` — cart:items.end

---

## 14. نموذج البيانات

### 14.1 مخططات الـ Schema (PostgreSQL)

```sql
-- التجار (متاجر سلة تستخدم تطبيقنا)
CREATE TABLE merchants (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  salla_store_id VARCHAR(255) UNIQUE NOT NULL,
  store_name VARCHAR(255),
  store_url VARCHAR(255),
  store_locale VARCHAR(10) DEFAULT 'ar',
  store_currency VARCHAR(10) DEFAULT 'SAR',
  store_timezone VARCHAR(50) DEFAULT 'Asia/Riyadh',
  email VARCHAR(255),
  phone VARCHAR(50),
  plan VARCHAR(20) DEFAULT 'trial',
  trial_ends_at TIMESTAMP,
  subscription_status VARCHAR(20) DEFAULT 'trial',
  salla_access_token TEXT, -- مشفّر
  salla_refresh_token TEXT, -- مشفّر
  installed_at TIMESTAMP NOT NULL DEFAULT NOW(),
  uninstalled_at TIMESTAMP,
  created_at TIMESTAMP NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMP NOT NULL DEFAULT NOW()
);

-- الـ Widgets (تاجر واحد يمكن أن يكون له عدة widgets)
CREATE TABLE widgets (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  merchant_id UUID NOT NULL REFERENCES merchants(id) ON DELETE CASCADE,
  type VARCHAR(50) NOT NULL,
  name VARCHAR(255),
  enabled BOOLEAN DEFAULT TRUE,
  config JSONB NOT NULL,
  created_at TIMESTAMP NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMP NOT NULL DEFAULT NOW()
);

CREATE INDEX idx_widgets_merchant ON widgets(merchant_id);
CREATE INDEX idx_widgets_enabled ON widgets(enabled) WHERE enabled = TRUE;

-- Submissions التردد
CREATE TABLE hesitation_submissions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  merchant_id UUID NOT NULL REFERENCES merchants(id) ON DELETE CASCADE,
  widget_id UUID NOT NULL REFERENCES widgets(id) ON DELETE CASCADE,
  trigger_mode VARCHAR(50) NOT NULL,
  reason_id VARCHAR(100),
  reason_label_ar VARCHAR(255),
  reason_label_en VARCHAR(255),
  free_text TEXT,
  product_id VARCHAR(255),
  product_handle VARCHAR(255),
  product_price DECIMAL(10,2),
  page_url TEXT,
  page_type VARCHAR(20),
  customer_id VARCHAR(255),
  session_id VARCHAR(255),
  device_type VARCHAR(20),
  user_agent TEXT,
  referrer TEXT,
  utm_source VARCHAR(255),
  utm_medium VARCHAR(255),
  utm_campaign VARCHAR(255),
  time_on_page_seconds INT,
  scroll_depth_percent INT,
  ip_country VARCHAR(10),
  created_at TIMESTAMP NOT NULL DEFAULT NOW()
);

CREATE INDEX idx_hesitation_merchant_created ON hesitation_submissions(merchant_id, created_at DESC);
CREATE INDEX idx_hesitation_product ON hesitation_submissions(merchant_id, product_id);
CREATE INDEX idx_hesitation_reason ON hesitation_submissions(merchant_id, reason_id);

-- إشارات الاهتمام
CREATE TABLE interest_signals (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  merchant_id UUID NOT NULL REFERENCES merchants(id) ON DELETE CASCADE,
  customer_phone_hash VARCHAR(255),
  customer_phone_last4 VARCHAR(4),
  customer_email VARCHAR(255),
  customer_salla_id VARCHAR(255),
  product_id VARCHAR(255) NOT NULL,
  product_variant_id VARCHAR(255),
  interest_type VARCHAR(50) NOT NULL,
  target_value JSONB,
  status VARCHAR(20) DEFAULT 'active',
  consent_given_at TIMESTAMP NOT NULL,
  consent_ip VARCHAR(45),
  consent_text_version VARCHAR(20),
  notification_channel VARCHAR(20) DEFAULT 'whatsapp',
  notification_sent_at TIMESTAMP,
  notification_clicked_at TIMESTAMP,
  cancelled_at TIMESTAMP,
  expires_at TIMESTAMP NOT NULL,
  created_at TIMESTAMP NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMP NOT NULL DEFAULT NOW(),
  UNIQUE(merchant_id, customer_phone_hash, product_id, interest_type, target_value)
);

CREATE INDEX idx_interest_merchant ON interest_signals(merchant_id);
CREATE INDEX idx_interest_product ON interest_signals(merchant_id, product_id);
CREATE INDEX idx_interest_status ON interest_signals(status) WHERE status = 'active';

-- توصيات Doctor
CREATE TABLE recommendations (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  merchant_id UUID NOT NULL REFERENCES merchants(id) ON DELETE CASCADE,
  rule_id VARCHAR(100) NOT NULL,
  product_id VARCHAR(255),
  severity VARCHAR(20) NOT NULL,
  title_ar VARCHAR(500),
  title_en VARCHAR(500),
  explanation_ar TEXT,
  explanation_en TEXT,
  action_type VARCHAR(50),
  action_payload JSONB,
  signal_count INT,
  status VARCHAR(20) DEFAULT 'pending',
  applied_at TIMESTAMP,
  dismissed_at TIMESTAMP,
  expires_at TIMESTAMP NOT NULL,
  created_at TIMESTAMP NOT NULL DEFAULT NOW()
);

CREATE INDEX idx_recommendations_merchant_status ON recommendations(merchant_id, status);
CREATE INDEX idx_recommendations_product ON recommendations(merchant_id, product_id);

-- أحداث الـ Widget (analytics)
CREATE TABLE widget_events (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  merchant_id UUID NOT NULL,
  widget_id UUID NOT NULL,
  event_type VARCHAR(50) NOT NULL,
  page_url TEXT,
  page_type VARCHAR(20),
  product_id VARCHAR(255),
  session_id VARCHAR(255),
  device_type VARCHAR(20),
  created_at TIMESTAMP NOT NULL DEFAULT NOW()
);

CREATE INDEX idx_events_merchant_widget_date ON widget_events(merchant_id, widget_id, created_at DESC);

-- مقاييس يومية مجمعة (يعاد بناؤها ليلًا)
CREATE TABLE widget_metrics_daily (
  merchant_id UUID NOT NULL,
  widget_id UUID NOT NULL,
  date DATE NOT NULL,
  views INT DEFAULT 0,
  interactions INT DEFAULT 0,
  submissions INT DEFAULT 0,
  dismissals INT DEFAULT 0,
  PRIMARY KEY (merchant_id, widget_id, date)
);

-- سجلات الموافقة (PDPL)
CREATE TABLE consent_records (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  merchant_id UUID NOT NULL,
  customer_phone_hash VARCHAR(255),
  customer_email VARCHAR(255),
  consent_text TEXT NOT NULL,
  consent_text_version VARCHAR(20),
  consent_ip VARCHAR(45),
  consent_user_agent TEXT,
  consent_locale VARCHAR(10),
  given_at TIMESTAMP NOT NULL DEFAULT NOW(),
  withdrawn_at TIMESTAMP
);
```

### 14.2 سياسة الاحتفاظ بالبيانات
- Submissions التردد (بدون PII): إلى أجل غير مسمى (مُجهَّلة بعد 12 شهرًا)
- إشارات الاهتمام مع الموافقة: حتى السحب أو الانتهاء (90 يومًا افتراضيًا)
- إشارات الاهتمام بدون موافقة: لا يمكن أن توجد (الموافقة مطلوبة عند الإنشاء)
- أحداث الـ Widget: 12 شهرًا خامة، ثم مجمعة فقط
- سجلات الموافقة: 7 سنوات (امتثال قانوني)
- بيانات التاجر: تُحذف بعد 90 يومًا من إلغاء التثبيت

---

## 15. مواصفات واجهات APIs

### 15.1 Public API (Storefront — يُستدعى من الـ snippet)

**Base URL:** `https://api.smartsnippet.sa/v1/public`

#### POST /submissions
إرسال رد تردد.

```http
POST /v1/public/submissions
Content-Type: application/json
X-Merchant-Token: <store-specific public token>

{
  "widget_id": "uuid",
  "trigger_mode": "exit_intent",
  "reason_id": "price_high",
  "free_text": null,
  "product": {
    "id": "12345",
    "handle": "vitamin-c-serum",
    "price": 199.00
  },
  "page": {
    "url": "https://store.salla.sa/products/vitamin-c-serum",
    "type": "pdp"
  },
  "session": {
    "id": "anon-session-uuid",
    "device_type": "mobile",
    "time_on_page_seconds": 45,
    "scroll_depth_percent": 67
  },
  "utm": { "source": "instagram", "campaign": "spring2026" },
  "customer_id": null
}

→ 200 OK
{ "submitted": true, "thank_you_message": "شكرًا لمساعدتك" }

→ 429 Too Many Requests (تجاوز الحد)
→ 400 Bad Request (payload غير صحيح)
```

#### POST /interest
تسجيل إشارة اهتمام (تتطلب موافقة).

```http
POST /v1/public/interest
{
  "product_id": "12345",
  "product_variant_id": "67890",
  "interest_type": "target_price",
  "target_value": { "price": 150.00 },
  "phone": "+966501234567",
  "consent": {
    "given": true,
    "text_version": "v1.0-ar",
    "locale": "ar"
  },
  "notification_channel": "whatsapp"
}

→ 201 Created
{ "interest_id": "uuid", "status": "active" }

→ 422 Unprocessable Entity (موافقة مفقودة أو جوال غير صحيح)
```

#### POST /events
تتبع أحداث widget (impressions، dismissals).

```http
POST /v1/public/events
{
  "widget_id": "uuid",
  "event_type": "viewed",
  "page_url": "...",
  "session_id": "..."
}

→ 202 Accepted (fire and forget)
```

#### GET /consent/manage
صفحة إدارة الموافقة المواجهة للعميل (HTML).

```http
GET /v1/public/consent/manage?token=<jwt>

→ 200 OK (HTML page مع: عرض الإشارات، حذف الإشارات، سحب الموافقة)
```

### 15.2 Merchant API (Dashboard — مصدّق عليه)

**Base URL:** `https://api.smartsnippet.sa/v1/merchant`
**المصادقة:** Bearer JWT (يُصدر بعد Salla OAuth)

#### GET /me
الحصول على ملف التاجر الحالي.

#### GET /dashboard/insights?period=7d
يعيد إحصائيات hero، أهم الأسباب، منتجات تحتاج اهتمام، variant heatmap.

```http
GET /v1/merchant/dashboard/insights?period=7d

→ 200 OK
{
  "period": "7d",
  "stats": {
    "submissions_total": 142,
    "submissions_delta_percent": 18,
    "interest_signals_total": 87,
    "interest_signals_delta_percent": 22,
    "active_widgets": 4,
    "total_widgets": 5,
    "submission_rate": 0.031
  },
  "top_reasons": [
    { "reason_id": "price_high", "label_ar": "السعر مرتفع", "count": 54 },
    { "reason_id": "size_unclear", "label_ar": "غير متأكد من المقاس", "count": 32 }
  ],
  "products_needing_attention": [
    {
      "product_id": "12345",
      "product_name": "Vitamin C Serum",
      "issue_count": 15,
      "severity": "high"
    }
  ],
  "variant_heatmap": [
    { "color": "Black", "size": "L", "requests": 30 }
  ]
}
```

#### GET /widgets
قائمة كل widgets التاجر.

#### POST /widgets
إنشاء widget جديد.

#### PATCH /widgets/:id
تحديث إعداد widget.

#### GET /widgets/:id/analytics?period=7d
تحليلات لكل widget.

#### GET /recommendations?status=pending
قائمة توصيات Doctor.

#### POST /recommendations/:id/apply
وضع علامة "applied" + اختياريًا تنفيذ الإجراء.

#### POST /recommendations/:id/dismiss

#### GET /submissions?product_id=...&period=30d
قائمة submissions الخام (مع فلاتر).

#### GET /interest-signals?status=active

#### POST /billing/subscribe
بدء اشتراك خطة مدفوعة (يربط بسلة billing).

### 15.3 معالجات Webhooks (داخلية)

**Base URL:** `https://api.smartsnippet.sa/v1/webhooks/salla`

#### POST /webhooks/salla/product-price-updated
#### POST /webhooks/salla/product-updated
#### POST /webhooks/salla/customer-created
#### POST /webhooks/salla/app-installed
#### POST /webhooks/salla/app-uninstalled

كل webhooks سلة مُتحقَّق منها عبر HMAC SHA256 signature.

---

## 16. متطلبات تجربة المستخدم والواجهات

### 16.1 مبادئ التصميم

1. **حد أدنى من الاحتكاك** — لا تقطع تدفق التسوق
2. **تسلسل معلومات واضح** — أهم معلومة أولًا
3. **موجّه للإجراء** — كل شاشة لها خطوة تالية واضحة
4. **واثق بالبيانات** — لا تخفِ الأرقام، اعرضها بوضوح
5. **شعور Salla-native** — يرث design tokens حيثما أمكن
6. **حالات فراغ صادقة** — قل للمستخدم ما المفقود وكيف يصلح
7. **لا dark patterns** — لا إلحاح زائف، لا تكاليف خفية

### 16.2 تصميم Widget مواجه العميل

**لوحة الألوان (افتراضية — يمكن تجاوزها لكل تاجر):**
- Primary: يرث Salla theme primary color
- Background: White / Dark gray (كشف تلقائي)
- Text: #1A1A1A / #FFFFFF
- Borders: rgba(0,0,0,0.08)
- Success: #10B981
- Error: #EF4444

**الطباعة:**
- العربية: "IBM Plex Sans Arabic" / fallback إلى system
- الإنجليزية: "Inter" / fallback إلى system
- الأحجام: 14px body، 16px buttons، 18px titles

**التباعد:**
- الوحدة الأساسية: 4px
- Modal padding: 24px desktop، 16px mobile
- Button padding: 12px 24px

**المكونات:**
- Buttons: rounded-lg (8px)، لا shadows
- Inputs: rounded-md (6px)، border 1px
- Radio buttons: targets دائرية كبيرة (24px)

### 16.3 تصميم لوحة التاجر

**التخطيط:**
- Top nav: Logo، اسم المتجر، شارة الخطة، help، قائمة profile
- Sidebar يساري: Dashboard، Widgets، Doctor، Analytics، Settings
- المحتوى الرئيسي: تخطيط بطاقات

**الصفحة الرئيسية للوحة:**
```
┌─ الإحصائيات العلوية ──────────────────────────────────┐
│  [142 ↑18%]  [87 ↑22%]  [4/5 widgets]  [3.1% ✅]    │
└────────────────────────────────────────────────────┘

┌─ أهم 3 أسباب تردد ─────────┐  ┌─ Variant Heatmap ──┐
│ 1. السعر مرتفع    54 (38%) │  │ Black L      30 ▓▓▓│
│ 2. غير متأكد المقاس 32   │  │ Red M        22 ▓▓ │
│ 3. معلومات ناقصة   28   │  │ Beige S      14 ▓  │
└─────────────────────────────┘  └────────────────────┘

┌─ منتجات تحتاج اهتمام ───────────────────────────────┐
│ المنتج                 Issues  Severity  [→]      │
│ Vitamin C Serum         15      🔴 High            │
│ Black Maxi Dress        12      🟡 Medium          │
└────────────────────────────────────────────────────┘

┌─ توصيات Doctor (3 معلقة) ──────────────────────────┐
│ 💊 Vitamin C Serum: 8 عملاء محتارون في الاستخدام  │
│    → أضف فيديو أو FAQ                              │
│    [ تطبيق ]  [ تجاهل ]                            │
└────────────────────────────────────────────────────┘
```

### 16.4 مكتبة المكونات

ابنِ/استخدم هذه المكونات:
- `<Button>` (أنواع primary، secondary، ghost)
- `<Card>` (مع header، body، footer)
- `<StatTile>` (رقم + delta + label)
- `<ProgressBar>` (لمعدل التقديم)
- `<RecommendationCard>` (شارة severity + إجراءات)
- `<EmptyState>` (أيقونة + رسالة + CTA)
- `<DataTable>` (قابل للترتيب، paginated)
- `<SparklineChart>` (trend 7 أيام)
- `<BarChart>` (أهم الأسباب)
- `<Heatmap>` (طلب variant)
- `<Toast>` (تأكيدات الإجراء)
- `<Modal>` (مربعات حوار إعدادات)

### 16.5 حالات الفراغ

**اليوم 1 (لا بيانات):**
> 👋 مرحبًا بك في Smart Snippet System
> ابدأ بتفعيل أول widget — ستظهر بياناتك خلال 24 ساعة
> [ ابدأ Onboarding ]

**لا submissions بعد (بيانات <10):**
> 📊 جمعنا 4 ردود حتى الآن
> نحتاج 10+ لإنتاج insights موثوقة
> [ شارك الـ widgets الحالية ]

**لا توصيات:**
> ✅ كل المنتجات بحالة جيدة هذا الأسبوع
> سنخبرك حين يحتاج منتج لاهتمامك

**معدل widget <1.5%:**
> 🔴 معدل تفاعل ضعيف (1.2%)
> اقتراحات لتحسينه: [3 nudges]

---

## 17. تدفق التهيئة (Onboarding)

### 17.1 الإعداد لأول مرة (5 خطوات، <5 دقائق)

**الخطوة 1: ترحيب (تلقائي بعد التثبيت)**
- "👋 مرحبًا [اسم المتجر] — لنبدأ بتفعيل أول widget"
- اختر القطاع: Beauty / Fashion / Perfumes / Gifts / Other

**الخطوة 2: أول Widget — Hesitation Capture**
- معبأ مسبقًا بالافتراضيات حسب القطاع
- معاينة widget مباشرة على الجانب
- "هذا الـ widget سيظهر للزوار الذين على وشك المغادرة"
- تخصيص الأسباب (اختياري) — أو قبول الافتراضيات
- [ فعّل Widget ]

**الخطوة 3: إعداد سياسة الخصوصية**
- "نولّد لك Privacy Policy template — راجعها وأضفها لمتجرك"
- رابط URL المولّد
- Checkbox: "أؤكد أن لدي Privacy Policy منشورة"

**الخطوة 4: تفضيلات الإيميل**
- معبأة بإيميل حساب سلة
- Toggle: weekly digest، تنبيهات توصيات، billing
- "أول digest يصلك صباح الإثنين القادم"

**الخطوة 5: تم**
- "🎉 جاهز! الـ widget مفعّل على متجرك"
- ما يمكن توقعه: "خلال 24 ساعة سترى أول submissions"
- "تريد تفعيل المزيد؟" → [ فعّل Interest Capture ]
- Skip: "خذ جولة في Dashboard"

### 17.2 جولة Dashboard الفارغة
بعد أول زيارة للوحة بدون بيانات:
- Tooltips على كل قسم تشرح ما سيظهر
- معاينة بيانات نموذجية (رمادية): "هذا مثال على ما سترى"

---

## 18. الإشعارات

### 18.1 إشعارات التاجر

**Email Digest أسبوعي (الإثنين 9 صباحًا توقيت السعودية):**
- ملخص الإحصائيات
- أهم 3 أسباب تردد
- 3 توصيات Doctor
- CTA: افتح اللوحة

**Email في الوقت الفعلي (opt-in):**
- توصية Doctor عالية الـ severity جديدة
- معدل widget نزل تحت 1.5%
- 10+ عملاء يطلبون نفس variant (إشارة reorder عاجلة)

**داخل التطبيق (Dashboard):**
- Toast على توصية جديدة
- شارة على بند قائمة Doctor مع العدد

### 18.2 إشعارات العميل

**مفعّلة (عند تحقق الشروط):**
- رسالة WhatsApp (الأساسية)
- SMS كاحتياط
- Email (إذا لا جوال، يوجد إيميل)

**Templates (WhatsApp Business):**

Template 1 — نزول السعر:
```
مرحبًا 👋
المنتج اللي تابعته نزل سعره!

[اسم المنتج]
السعر السابق: 199 ر.س
السعر الآن: 149 ر.س ✨

اشترِ الآن: [link]

— [اسم المتجر]
لإلغاء التنبيهات: [manage link]
```

Template 2 — Variant متوفر:
```
مرحبًا 👋
الـ [لون/مقاس] اللي طلبته رجع!

[اسم المنتج]
[تفاصيل الـ Variant]

اشترِ قبل ينفد: [link]

— [اسم المتجر]
لإلغاء التنبيهات: [manage link]
```

---

## 19. التحليلات والقياس

### 19.1 أحداث للتتبع (Internal Product Analytics)

**أحداث التاجر:**
- `app_installed`
- `onboarding_step_completed` (props: step_number، time_spent)
- `onboarding_completed` (props: total_time)
- `widget_created` (props: type، vertical_template)
- `widget_activated`
- `widget_deactivated`
- `dashboard_viewed` (props: section)
- `recommendation_applied` (props: rule_id، severity)
- `recommendation_dismissed`
- `trial_started`
- `trial_converted` (props: plan، days_to_convert)
- `trial_expired`
- `subscription_cancelled` (props: reason)

**أحداث العميل:**
- `widget_viewed`
- `widget_interacted`
- `widget_submitted`
- `widget_dismissed`
- `interest_signal_created` (props: type)
- `consent_given`
- `consent_withdrawn`

### 19.2 خصائص (مشتركة)
- `merchant_id`
- `merchant_plan`
- `store_vertical`
- `device_type`
- `locale`
- `timestamp`

### 19.3 لوحات داخلية (لنا)
- الاكتساب: تثبيتات/يوم، بدء تجارب/يوم
- التفعيل: % من التثبيتات التي تفعّل أول widget خلال 24 ساعة
- الإنخراط: تجار أسبوعيون نشطون
- الاحتفاظ: 7 أيام، 30 يومًا، 90 يومًا
- الإيرادات: MRR، ARR، churn
- Funnel: تثبيت → onboard → أول submission → 10 submissions → تحويل trial

---

## 20. مقاييس النجاح

### 20.1 المقياس الرئيسي (North Star)
**التجار النشطون أسبوعيًا مع توصية ≥1 مطبقة**
يثبت كل من الإنخراط وتقديم القيمة.

### 20.2 المؤشرات الرائدة (يومي/أسبوعي)
- تثبيتات جديدة/يوم
- معدل تفعيل أول widget (هدف ≥80% خلال 24 ساعة)
- متوسط معدل التقديم لكل widget (هدف ≥3%)
- وقت أول insight (هدف <72 ساعة من التثبيت)
- معدل تطبيق توصيات Doctor (هدف ≥30%)

### 20.3 المؤشرات المتأخرة (شهري)
- تحويل Trial-to-paid (هدف ≥15%)
- احتفاظ 30 يومًا (هدف ≥70%)
- احتفاظ 90 يومًا (هدف ≥50%)
- نمو MRR (هدف 25% MoM في أول 6 شهور)
- NPS (هدف ≥40)

### 20.4 معايير الإلغاء (اليوم 60 من إطلاق MVP)
- معدل تقديم <1.5% (مستمر لـ 30 يومًا)
- Trial-to-paid <5%
- احتفاظ 30 يومًا <40%
- معدل فتح اللوحة أسبوعيًا <30%

إذا تحقق أي اثنين من هذه، أوقف عمل الميزات الجديدة وأعد التقييم.

---

## 21. معايير الإطلاق

### 21.1 Beta المغلقة (اليوم 60)
**الجمهور:** 3-5 تجار مدعوون (قطاع الجمال/العطور)

**معايير القبول:**
- كل ميزات MVP الأربعة تعمل end-to-end
- Onboarding يكتمل بنجاح
- Submissions widget التردد ملتقطة ومرئية في اللوحة خلال دقيقة واحدة
- Doctor يولّد توصية واحدة على الأقل عند تحقق العتبة
- إشعارات WhatsApp تُسلَّم بنجاح
- طبقة موافقة PDPL تعمل
- لا أخطاء P0

**الهدف:** 1-2 أسبوع من bug bash + UX feedback

### 21.2 Beta المفتوحة (اليوم 75)
**الجمهور:** 20-30 تاجر (دعوة فقط، قنوات تسويق)

**معايير القبول:**
- ملاحظات beta المغلقة مدمجة
- ميزانية الأداء محققة (أوقات التحميل)
- Templates Privacy Policy نهائية بالعربية والإنجليزية
- كل تدفقات الدفع مختبرة (تكامل سلة billing)
- وثائق المساعدة منشورة

### 21.3 تسليم متجر تطبيقات سلة (اليوم 90)

**Checklist التسليم:**
- [ ] القائمة بالعربية والإنجليزية
- [ ] Screenshots (5+ لكل: AR، EN)
- [ ] فيديو demo (60 ثانية)
- [ ] رابط Privacy Policy
- [ ] رابط Terms of Service
- [ ] إيميل + هاتف دعم
- [ ] OAuth scopes مبررة
- [ ] أسعار التطبيق مضبوطة
- [ ] عملية مراجعة متجر سلة (عادة 2-7 أيام)

### 21.4 الإطلاق العام (اليوم 105 — تقديري)
- متجر سلة معتمد
- إعلان الإطلاق (social، email)
- 3 case studies منشورة من تجار beta
- دعم العملاء جاهز (استجابة <4 ساعات أيام العمل)

---

## 22. خارج النطاق (قائمة "لا" صريحة لـ MVP)

### ميزات خارج MVP
- ❌ توصيات قائمة على AI (مرحلة 3)
- ❌ Popup builder للتسويق العام
- ❌ حملات email marketing
- ❌ حملات SMS marketing
- ❌ Helpdesk / ticketing
- ❌ برنامج ولاء
- ❌ تطبيق Reviews
- ❌ Wishlist كأداة مستقلة
- ❌ محرك A/B testing
- ❌ Conversion attribution / تتبع الإيرادات
- ❌ شرائح العملاء
- ❌ تصدير audience لمنصات الإعلانات
- ❌ حسابات متعدد المتاجر
- ❌ White-label / agency mode
- ❌ متعدد اللغات بخلاف AR + EN
- ❌ تطبيق جوال أصلي (لوحة ويب فقط)
- ❌ Voice / chatbot interface
- ❌ حقن CSS مخصص
- ❌ JavaScript event API للتجار
- ❌ تكاملات مباشرة (Zapier، Make، إلخ)

### تقني خارج MVP
- ❌ نشر متعدد المناطق (السعودية فقط)
- ❌ Custom domains للـ white label
- ❌ SSO / SAML
- ❌ Webhooks للتجار (نستقبل webhooks سلة لكن لا نرسل خاصة بنا)
- ❌ API عام للتجار

### قطاعات خارج MVP
- ❌ متاجر B2B-only
- ❌ توصيل طعام / مطاعم
- ❌ شركات خدمات (غير منتجات)
- ❌ Marketplaces (بائعون متعددون)

---

## 23. أسئلة مفتوحة

تحتاج إلى الحل قبل/خلال البناء:

**أسئلة منصة سلة:**
1. ❓ هل webhook `product.quantity.low` ينطلق لكل variant_id أم product_id فقط؟ **التحقق في Salla Developer Console.**
2. ❓ ما حدود معدل استدعاءات Salla Merchant API؟ خطط للوحة بناءً عليه.
3. ❓ هل app snippets معزولة (Shadow DOM enforced) أم وصول DOM كامل؟
4. ❓ هل سلة تعطي customer_id في storefront events للعملاء المسجلين؟
5. ❓ ما تدفق فواتير متجر تطبيقات سلة؟ فاتورة تاجر مباشرة أم سلة تجمعها؟
6. ❓ هل توجد قيود على عناصر widget البصرية (مثلًا، popups محظورة في بعض الصفحات)؟

**أسئلة المنتج:**
7. ❓ هل نقدم "Quick Setup" (افتراضيات) مقابل "Custom Setup" (إعداد كامل) للـ onboarding؟
8. ❓ هل يكون weekly digest اختياريًا من اليوم 1، أم مفعّل افتراضيًا مع opt-out؟
9. ❓ هل نعرض مقاييس المنافسين (benchmarks مجهلة) في اللوحة؟ آثار خصوصية؟
10. ❓ هل إجراءات "Apply" تمر عبر موافقة التاجر لأول 10، ثم تطبيق تلقائي لاحقًا؟

**أسئلة تقنية:**
11. ❓ هل نستخدم Shadow DOM أم iframe لعزل widget؟ (Shadow DOM = UX أفضل، iframe = أمان أفضل)
12. ❓ كيف نتعامل مع تحديثات themes سلة التي قد تكسر نقاط الحقن؟
13. ❓ ما خطة الـ failover إذا تعطل backend (لا تكسر storefront التاجر)؟
14. ❓ هل أسباب التردد قابلة للتحرير من اليوم 1 أم مثبتة لأول 30 يومًا (لتحليل cohort)؟

**أسئلة قانونية / امتثال:**
15. ❓ هل نحتاج Data Processing Agreement منفصل مع كل تاجر (PDPL)؟
16. ❓ هل يمكن استخدام بيانات التاجر (مجهلة) لـ cross-merchant benchmarks؟ (يحتمل يحتاج موافقة صريحة)
17. ❓ ما SLA لطلبات حذف البيانات؟

---

## 24. المخاطر والتخفيف منها

### R1 — معدل التقديم تحت الهدف
**المخاطرة:** العملاء لا يتفاعلون مع widgets (<1.5%)
**الحدّة:** حرجة (مخاطرة قاتلة)
**الاحتمال:** عالٍ
**التخفيف:**
- A/B test توقيت الـ trigger في beta
- عرض reward coupon اختياري (قابل للضبط)
- استخدام خيارات بنقرة واحدة (ليس نص حر أولًا)
- تحسين النصوص للودية، ليس الاستجواب
- **إجراء قبل البناء:** اعمل paper-prototype على تاجر واحد لمدة أسبوعين، قِس baseline.

### R2 — تداخل ميزة سلة الأصلية
**المخاطرة:** سلة تطلق ميزة مماثلة، يأكل قيمتنا
**الحدّة:** عالية
**الاحتمال:** متوسط
**التخفيف:**
- بناء عمق (قواعد Doctor، ذكاء variant) سلة لن تكرّره بسرعة
- شراكة مع سلة مبكرًا (pitch كمكمّل)
- مراقبة إعلانات منتج سلة أسبوعيًا

### R3 — يُنظر إليه كـ "أداة popup أخرى"
**المخاطرة:** التجار يربطوننا بـ PopupSnap، يقللون التقدير
**الحدّة:** عالية
**الاحتمال:** متوسط
**التخفيف:**
- positioning صارم: مفردات "Intent Layer"، "Doctor"، "Insights"
- demo يركز على Dashboard، ليس widgets
- تسعير أعلى من PopupSnap (إشارة premium)
- تجنب "popup" في النصوص التسويقية

### R4 — عدم امتثال PDPL
**المخاطرة:** غرامات PDPL سعودية لموافقة غير سليمة
**الحدّة:** عالية
**الاحتمال:** منخفض
**التخفيف:**
- مراجعة قانونية قبل الإطلاق
- طبقة موافقة في تصميم اليوم 1
- توثيق كل شيء (نسخة نص الموافقة، timestamps، IPs)
- URL إدارة موافقة مواجه للعميل

### R5 — توافق ثيمات سلة
**المخاطرة:** widgets تكسر على themes متنوعة
**الحدّة:** متوسطة
**الاحتمال:** متوسط
**التخفيف:**
- عزل Shadow DOM
- اختبار على أعلى 10 ثيمات سلة خلال beta
- أنماط fallback لحالات الحافة
- مراقبة support tickets لمشكلات الـ theme

### R6 — قيود WhatsApp Business API
**المخاطرة:** Meta تقيد حجم الإشعارات أو الـ templates
**الحدّة:** متوسطة
**الاحتمال:** متوسط
**التخفيف:**
- اعتماد templates مسبقًا مع Meta
- استخدام Wati أو BSP مماثل (أكثر مرونة من Meta مباشرة)
- SMS كاحتياط جاهز

### R7 — تأثير الأداء على المتاجر
**المخاطرة:** widget يبطئ storefronts التجار
**الحدّة:** عالية
**الاحتمال:** منخفض (مع الانضباط)
**التخفيف:**
- ميزانية أداء صارمة (30KB، 100ms TTI delta)
- تحميل async
- CDN ذاتي الاستضافة مع edge caching
- اختبارات regression للأداء في CI

---

## 25. الجدول الزمني والمراحل

### خطة أسبوعية لـ 90 يومًا

#### المرحلة أ: الأساس (الأسابيع 1-3)

**الأسبوع 1: الإعداد والهيكلية**
- حساب مطور سلة + تسجيل التطبيق
- إعداد المستودعات (frontend، backend، dashboard)
- تطبيق database schema
- خط CI/CD
- بنية الاستضافة (AWS الرياض)

**الأسبوع 2: نواة تكامل سلة**
- تدفق OAuth مع سلة
- مستقبلو Webhooks (price_updated، product_updated، customer_created، app_installed)
- تسجيل وحقن app snippet يعمل على متجر اختبار
- Twilight hooks أساسية مختبرة

**الأسبوع 3: هيكل Backend**
- Endpoints Public API (submissions، interest، events)
- المصادقة (JWT للوحة التاجر)
- طبقة وصول قاعدة البيانات
- تحديد المعدل
- معالجة الأخطاء + logging (Sentry)

#### المرحلة ب: بناء الميزة 1 (الأسابيع 4-5)

**الأسبوع 4: Hesitation Widget — Frontend**
- عرض الـ widget (Shadow DOM)
- Triggers Exit Intent (desktop + mobile fallback)
- Triggers Product Clarity
- تحميل الإعداد من backend
- تدفق الإرسال
- حالة الشكر
- تجاوب الجوال
- العربية والإنجليزية

**الأسبوع 5: Hesitation Widget — Backend + Dashboard**
- معالجة الإرسال
- التخزين + indexes
- عرض dashboard أساسي (قائمة submissions خام)
- UI إعداد widget (CRUD)
- لسان analytics لكل widget

#### المرحلة ج: بناء الميزة 2 (الأسابيع 6-7)

**الأسبوع 6: Interest Capture — Frontend**
- زر "نبهني" على PDP
- Modal مع اختيار نوع الاهتمام
- تحقق الجوال (سعودي/خليجي)
- طبقة موافقة PDPL
- تدفق الإرسال

**الأسبوع 7: Interest Capture — Backend + الإشعارات**
- تخزين إشارة الاهتمام
- معالجات Webhook تعمل بشكل صحيح
- تكامل WhatsApp Business (إعداد BSP)
- SMS كاحتياط (Unifonic)
- Template approval مُقدَّم
- صفحة إدارة موافقة العميل

#### المرحلة د: بناء الميزة 3 (الأسابيع 8-9)

**الأسبوع 8: Intent Dashboard**
- الصفحة الرئيسية للوحة (إحصائيات، أهم الأسباب، منتجات)
- Variant heatmap
- فلترة نطاق التاريخ
- حالات الفراغ
- تحسين الأداء (queries)

**الأسبوع 9: Product Doctor**
- محرك القواعد (5 قواعد MVP)
- Cron يومي (4 صباحًا توقيت السعودية)
- توصيات CRUD
- معالجات إجراء Apply
- UI التوصيات

#### المرحلة هـ: الميزة 4 + Polish (الأسبوع 10)

**الأسبوع 10: Analytics + Weekly Digest**
- لوحة Widget Analytics
- Cron تجميع يومي
- نموذج digest أسبوعي
- إعداد مرسل الإيميل (SendGrid)
- اختبار أول digest

#### المرحلة و: تحضير Beta (الأسابيع 11-12)

**الأسبوع 11: Onboarding + Polish**
- معالج onboarding 5 خطوات
- جولات حالة فراغ
- وثائق مساعدة (صفحات FAQ)
- مولّد template Privacy Policy
- حالات تحميل في كل مكان

**الأسبوع 12: QA داخلي + Bug Bash**
- اختبار end-to-end على staging
- اختبار الأداء
- اختبار cross-browser (Chrome، Safari، Firefox)
- اختبار cross-device (iPhone، Galaxy، iPad)
- اختبار توافق الـ theme (أعلى 5 ثيمات سلة)
- مراجعة الأمان
- تحديد تجار beta المغلقة + outreach

#### المرحلة ز: Beta + الإطلاق (الأسابيع 13-15)

**الأسبوع 13: إطلاق Beta المغلقة**
- 3-5 تجار onboarded مع دعم white-glove
- متابعات يومية
- إصلاح bugs بأولوية

**الأسبوع 14: Beta المفتوحة + Iteration**
- توسيع إلى 20-30 تاجر
- جمع feedback
- iterate على مشكلات UX
- تحسين قواعد Doctor بناءً على بيانات حقيقية

**الأسبوع 15: تسليم متجر تطبيقات سلة**
- كل المواد تجهيزها
- فيديو demo مسجّل
- تسليم مُقدَّم
- بدء مراجعة feedback سلة إن وجد

### مسار حرج
1. اعتماد حساب مطور سلة (الأسبوع 1) — يمكن أن يعيق البداية
2. اعتماد template WhatsApp Business (الأسابيع 7-8) — يمكن أن يعيق الإشعارات
3. مراجعة متجر تطبيقات سلة (الأسبوع 15+) — يمكن أن يعيق الإطلاق

---

## 26. الملاحق

### أ. المسرد (Glossary)

| المصطلح | التعريف |
|---|---|
| **Hesitation Capture** | Widget يسأل العميل لماذا لم يشتر |
| **Intent Signal** | أي نقطة بيانات سلوكية ما قبل الشراء (تردد، اهتمام) |
| **Interest Signal** | تسجيل العميل لإشعار مستقبلي (سعر، variant) |
| **Product Doctor** | محرك قائم على قواعد يوصي بإصلاحات لكل منتج |
| **Submission** | رد العميل على widget التردد |
| **معدل التقديم** | Submissions ÷ Widget Views |
| **PDPL** | نظام حماية البيانات الشخصية السعودي (2023-2024) |
| **Salla Twilight** | محرك ثيمات سلة + JS SDK |
| **App Snippet** | آلية سلة لحقن JS/HTML في storefronts |
| **Conditional Webhook** | ميزة سلة لفلترة webhooks بقواعد |

### ب. نموذج إعداد قاعدة Doctor (للتوسع المستقبلي)

```typescript
// القواعد ستكون مدفوعة بقاعدة بيانات لسهولة التكرار
interface DoctorRuleDb {
  id: string;
  name: string;
  enabled: boolean;
  conditions: ConditionExpression;
  recommendation_template: {
    title_template_ar: string;
    title_template_en: string;
    explanation_ar: string;
    explanation_en: string;
    action_type: string;
    action_payload_template: any;
  };
  severity: 'low' | 'medium' | 'high';
  cooldown_days: number;
  min_signal_count: number;
  vertical_filter?: string[];
}
```

### ج. تصنيف أسباب التردد (الافتراضي)

```typescript
const DEFAULT_REASONS = [
  { id: 'price_high', label_ar: 'السعر مرتفع', label_en: 'Price too high', category: 'price' },
  { id: 'shipping_unclear', label_ar: 'الشحن غير واضح', label_en: 'Shipping unclear', category: 'shipping' },
  { id: 'size_unclear', label_ar: 'غير متأكد من المقاس', label_en: 'Unsure about size', category: 'product' },
  { id: 'comparing', label_ar: 'محتار بين منتجات', label_en: 'Comparing products', category: 'decision' },
  { id: 'need_more_info', label_ar: 'محتاج معلومات أكثر', label_en: 'Need more info', category: 'product' },
  { id: 'just_browsing', label_ar: 'فقط أتصفح', label_en: 'Just browsing', category: 'low_intent' },
  { id: 'ingredients_concern', label_ar: 'قلق من المكونات', label_en: 'Concerned about ingredients', category: 'product', verticals: ['beauty'] },
  { id: 'authenticity', label_ar: 'متشكك في الأصالة', label_en: 'Authenticity concerns', category: 'trust', verticals: ['perfumes', 'fashion'] },
];
```

### د. أمثلة Payloads إضافية

**Webhook payload من سلة (`product.price.updated`):**
```json
{
  "event": "product.price.updated",
  "merchant": 12345,
  "created_at": "2026-05-12T14:30:00Z",
  "data": {
    "id": 67890,
    "name": "Vitamin C Serum",
    "old_price": 199.00,
    "new_price": 149.00,
    "currency": "SAR"
  }
}
```

**إنشاء توصية Doctor:**
```json
{
  "rule_id": "rule_size_confusion",
  "product_id": "67890",
  "severity": "high",
  "title_ar": "8 عملاء غير متأكدين من المقاس على Vitamin C Serum",
  "title_en": "8 customers unsure about size on Vitamin C Serum",
  "explanation_ar": "أضف Size Help snippet أو دليل المقاسات",
  "explanation_en": "Add a Size Help snippet or size chart",
  "action_type": "create_snippet",
  "action_payload": {
    "snippet_template": "size_help"
  },
  "signal_count": 8,
  "status": "pending",
  "expires_at": "2026-05-26T14:30:00Z"
}
```

### هـ. المراجع

- **التحليل الاستراتيجي:** [Smart-Snippet-System-Analysis.md](./Smart-Snippet-System-Analysis.md)
- **تحليل المنافسين:** [Competitive-Landscape-Analysis.md](./Competitive-Landscape-Analysis.md)
- **خطة العمل:** [Smart-Snippet-System-Business-Plan.md](./Smart-Snippet-System-Business-Plan.md)
- **وثائق مطوري سلة:** https://docs.salla.dev/
- **Webhooks سلة:** https://docs.salla.dev/421119m0
- **Hooks ثيم Twilight:** https://docs.salla.dev/422552m0
- **امتثال PDPL:** https://sdaia.gov.sa/en/Research/Pages/DataProtection.aspx

---

## 27. Specs المفصلة — MVP Features 5-14 + خارطة Phase 2

> **تنبيه Scope:**
> هذا القسم يقدم **مواصفات feature-level كاملة** لـ MVP Features 5-14 (10 modules تمت ترقيتها إلى MVP). العمق يماثل Features 1-4 (Sections 7-10): الوصف، User Flow، Functional Requirements، UX Requirements، Configuration، Data Schema، Edge Cases، Mobile، Accessibility، وتكامل سلة.
>
> القسم 27.11 يحتوي على specs مكثفة لـ **10 modules المتبقية في Phase 2** (37، 41، 42، 43، 45، 47، 48، 52، 53، 56).

---

### 27.1 Feature 5 — PDPL Consent Management Center (Module 40)

#### الوصف
بوابة self-service مواجهة للعميل تُفتح عبر URL مع token موقع، تتيح للعميل عرض كل إشاراته المخزنة، إلغاء signals فردية أو bulk، سحب الموافقة (يوقف الـ communications المستقبلية)، وتصدير بياناته بصيغة CSV أو JSON. هذه الـ feature **مطلوبة قانونًا** بموجب نظام PDPL السعودي (نافذ سبتمبر 2023، تطبيق إجباري منذ سبتمبر 2024) وتحمي من غرامات SDAIA (48 قرار مخالفة منذ بدء التطبيق).

البوابة تُفتح عبر JWT token مدمج في كل WhatsApp/Email يصل للعميل. لا يُطلب تسجيل دخول — الـ token هو دليل الهوية.

#### User Flow

```
[العميل يستلم WhatsApp/Email]
     ↓
[ينقر "إدارة بياناتي"]
     ↓
[URL مع token يفتح portal]
     ↓
[العرض:
  - كل interest signals (active + triggered)
  - كل submissions (إن وجد PII)
  - timestamp + version الموافقة
]
     ↓
[الإجراءات المتاحة:
  - إلغاء signal واحد
  - حذف كل البيانات
  - سحب الموافقة
  - تصدير (CSV/JSON)
]
     ↓
[email تأكيد + audit log entry]
```

#### المتطلبات الوظيفية

- **FR-40.1** URL pattern: `/v1/public/consent/manage?token=<jwt>`. JWT يحتوي: customer_phone_hash، merchant_id، issued_at، expires_at (30 يوم من الإصدار).
- **FR-40.2** Token موقع بـ RS256 مع مفتاح rotating (rotation كل 90 يوم).
- **FR-40.3** عرض كل interest signals حيث status IN ('active', 'triggered', 'expired') مرتبة DESC.
- **FR-40.4** عرض كل hesitation submissions حيث customer_phone يطابق (فقط إذا PII مُرفق).
- **FR-40.5** "إلغاء signal" → status='cancelled', cancelled_at=NOW(). يُزال من notification queue.
- **FR-40.6** "حذف كل بياناتي" مع modal تأكيد، ثم cascade delete (audit log محفوظ قانونًا).
- **FR-40.7** "سحب الموافقة" → consent_records.withdrawn_at=NOW()، يوقف communications مستقبلية.
- **FR-40.8** "تصدير البيانات" → CSV/JSON مع: signal_id، product_name، interest_type، target_value، created_at، status.
- **FR-40.9** كل actions مسجلة في `consent_actions` table مع: action_type، ip، user_agent، performed_at.
- **FR-40.10** Email تأكيد بعد كل إجراء كبير (حذف، سحب) باستخدام template التاجر.
- **FR-40.11** الصفحة متاحة بالعربية + الإنجليزية مع كشف تلقائي.
- **FR-40.12** Rate limit: 10 actions/min per token (منع abuse في حال تسريب token).

#### UX Requirements

**التصميم البصري:**
- نظيف، يبني ثقة (ليس marketing-styled)
- ألوان هادئة: خلفية بيضاء، نص داكن، blue accent
- تسلسل واضح: الهوية → قائمة البيانات → أزرار الإجراءات
- timestamp "آخر تحديث" مرئي

**هيكل الصفحة:**
1. Header: "إدارة بياناتي" + جوال مقنّع (آخر 4 أرقام)
2. Section: signals نشطة (cards مع زر cancel)
3. Section: signals triggered/expired (مطوية افتراضيًا)
4. Footer: bulk actions (Export, Delete All, Withdraw)
5. PDPL compliance notice + contact

**Responsive:** Mobile-first (معظم الزيارات من email على الجوال)

#### Configuration

```typescript
interface ConsentCenterConfig {
  tokenExpiryDays: number;         // default 30
  tokenRotationDays: number;       // 90
  rateLimitPerMin: number;         // 10
  emailTemplateAr: string;
  emailTemplateEn: string;
  brandPrimaryColor: string;
  brandLogoUrl: string;
  privacyPolicyUrl: string;
}
```

#### Data Captured

```typescript
interface ConsentAction {
  id: string;
  merchant_id: string;
  customer_phone_hash: string;
  action_type: 'page_view' | 'cancel_signal' | 'bulk_delete' | 'withdraw_consent' | 'export_data';
  signal_ids?: string[];
  export_format?: 'csv' | 'json';
  ip: string;
  user_agent: string;
  locale: 'ar' | 'en';
  performed_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| Token منتهي | عرض صفحة regeneration |
| Signature غير صحيح | 401 + log security event |
| العميل ليس لديه signals | "ما عندك بيانات مخزنة معنا" |
| Bulk delete على 1000+ signal | batch processing (100/batch) |
| سبق سحب الموافقة | banner مع خيار re-enroll |
| طلب export > 10MB | إرسال عبر email بدلًا من download |
| Token مسرّب | rate limit + security audit |
| التاجر ألغى التطبيق | "Merchant no longer active" + السماح بحذف |

#### Mobile, Accessibility & Integration

- **Mobile:** Bottom sheets، تاب targets 48px، single-column
- **A11y:** WCAG AA، announce results via `aria-live`
- **Salla Integration:** لا تكامل مباشر (URL خاصة بنا). الـ link يجب إدراجه في كل templates إشعارات سلة.

#### الجهد المقدر
متوسط: **3-5 أيام تطوير**

---

### 27.2 Feature 6 — Empty Search Capture (Module 38)

#### الوصف
يلتقط استعلامات بحث العميل التي أرجعت لا نتائج، يحوّل "inventory misses غير المرئية" إلى إشارة طلب منظمة. عندما يبحث الزائر عن منتج لا يحمله المتجر، بدلًا من تركه يخرج بصمت، نلتقط الـ query + بيانات اتصال اختيارية، ونعرض insights مجمعة في لوحة التاجر. هذا يحول فشل البحث إلى فرص reorder/expansion.

#### User Flow

```
[العميل يبحث في متجر سلة]
     ↓
[البحث يُرجع 0 نتائج]
     ↓
[الصفحة تكشف empty state عبر .s-search-no-results]
     ↓
[نموذج Smart Snippet يُحقن تلقائيًا]
     ↓
[النموذج يُعبئ query تلقائيًا]
     ↓
[العميل يضيف جوال (اختياري) + موافقة PDPL]
     ↓
[إرسال → "نخبرك إذا وفرناه"]
     ↓
[تجميع في missed_searches table]
```

#### المتطلبات الوظيفية

- **FR-38.1** كشف empty search state عبر DOM: presence of `.s-search-no-results` class أو text content matching "لا توجد نتائج" / "No results".
- **FR-38.2** حقن capture form خلال 100ms من كشف empty state.
- **FR-38.3** ملء search query في النموذج تلقائيًا (display read-only + hidden field).
- **FR-38.4** الجوال optional (موافقة PDPL مطلوبة فقط إذا الجوال موجود).
- **FR-38.5** التخزين في `missed_searches` table مع: merchant_id، query، customer_phone_hash، session_id، page_url، search_timestamp.
- **FR-38.6** تجميع الـ queries المتطابقة (case-insensitive، normalized) وزيادة عداد frequency.
- **FR-38.7** Dashboard widget: "Top missed searches" مرتبة بـ frequency، قابلة للفلترة (7d/30d/all).
- **FR-38.8** Doctor rule: إذا query frequency > 10 في 30 يوم → اقترح "فكر في إضافة هذا المنتج/الفئة".
- **FR-38.9** اختياري: إشعار العملاء إذا تمت إضافة المنتج المطابق لاحقًا (consent-based).
- **FR-38.10** Anonymous mode: التقاط query حتى بدون جوال (signal بحجم عالٍ).

#### UX Requirements

**أسلوب النموذج:**
- بسيط، غير مزعج
- يظهر تحت رسالة "No results" مع slide-in سلس
- "نريد توفير ما تبحث عنه!" headline
- جوال single-line + checkbox PDPL + Submit

**التصميم البصري:**
- خلفية subtle (أزرق/رمادي خفيف)
- نفس border-radius لـ Salla theme
- emoji ودود 📩 أو 🔍

#### Configuration

```typescript
interface EmptySearchCaptureConfig {
  enabled: boolean;
  detectionSelectors: string[];
  detectionTextPatterns: string[];
  capturePhone: boolean;
  capturePhoneRequired: boolean;
  headline_ar: string;
  headline_en: string;
  ctaLabel_ar: string;
  ctaLabel_en: string;
  notifyOnMatch: boolean;
}
```

#### Data Captured

```typescript
interface MissedSearch {
  id: string;
  merchant_id: string;
  query: string;
  normalized_query: string;
  customer_phone_hash?: string;
  customer_email?: string;
  consent_given_at?: timestamp;
  session_id: string;
  page_url: string;
  search_timestamp: timestamp;
  device_type: 'desktop' | 'mobile' | 'tablet';
  notified_at?: timestamp;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| query فارغ (whitespace فقط) | لا التقاط |
| بحث بـ SKU أو product code | التقاط (signal مفيد) |
| العميل يرسل نفس search مرتين في جلسة | تحديث timestamp، لا تكرار |
| Salla theme يستخدم class مختلف | detection selectors قابلة للضبط |
| البحث أرجع 1 نتيجة والعميل غادر | لا trigger (فقط على 0 نتائج) |
| Queries خبيثة (SQL injection) | sanitize، خزّن، flag للمراجعة |
| 1000+ query متطابقة في يوم | throttle aggregation، احتفظ بالكل |
| العميل لم يُرسل (غادر الصفحة) | التقاط query بشكل anonymous |

#### Mobile, Accessibility & Integration

- **Mobile:** ترتيب رأسي، input field كبير، sticky submit
- **A11y:** Form labeled، أخطاء via `aria-live`، keyboard navigation
- **Salla Integration:** Twilight `<salla-search>` component (مؤكد).

#### الجهد المقدر
صغير-متوسط: **2-4 أيام**

---

### 27.3 Feature 7 — Influencer Code Capture & Attribution (Module 54)

#### الوصف
يلتقط traffic العميل من influencers محددين (عبر UTM params أو URL slugs خاصة)، يعرض landing experience مخصصة، يطبق coupon code الـ influencer تلقائيًا عند checkout، ويتتبع revenue/AOV/conversion/CAC لكل influencer. يحل مشكلة حرجة: التجار الذين ينفقون على influencer marketing لا يعرفون أي influencer يدفع revenue حقيقية.

#### User Flow

```
[Influencer ينشر: "استخدمي SARA20 — store.sa/?ref=sara_kn"]
     ↓
[العميل ينقر → يصل مع UTM أو ?ref= slug]
     ↓
[Smart Snippet يحلل URL ويحدد influencer]
     ↓
[Banner مخصص: "👋 شكرًا لزيارتك من سارة!"]
     ↓
[العميل يتصفح، يضيف للسلة]
     ↓
[عند checkout: SARA20 يُطبق تلقائيًا]
     ↓
[الطلب يكتمل → attribution تُسجل]
     ↓
[Dashboard يعرض: Sara generated X orders, Y revenue, Z% CVR]
```

#### المتطلبات الوظيفية

- **FR-54.1** تحليل URL عند كل page load لـ: `utm_source`، `utm_medium`، `utm_campaign`، `?ref=`، `?influencer=`.
- **FR-54.2** المطابقة ضد `influencers` config table لكل تاجر (slug، coupon_code، display_name، profile_pic_url).
- **FR-54.3** تخزين attribution في cookie (30-day window) وsession.
- **FR-54.4** عرض landing banner مخصص مع اسم influencer + صورة + رسالة ترحيب.
- **FR-54.5** تطبيق coupon تلقائيًا عند checkout عبر Salla Coupons API.
- **FR-54.6** تتبع كل order من جلسات influencer-attributed في `influencer_orders` table.
- **FR-54.7** Dashboard: per-influencer table مع orders count، revenue، AOV، conversion rate، CAC.
- **FR-54.8** Influencer management UI في dashboard التاجر: add/edit/disable، توليد URLs.
- **FR-54.9** اختياري: pre-applied coupon يبقى حتى لو العميل فرّغ السلة.
- **FR-54.10** Multi-influencer support: لو العميل زار عبر influencers مختلفين، attribution_mode (first vs last touch).

#### UX Requirements

**Landing Banner:**
- Sticky top (قابل للإغلاق)
- صورة influencer + اسم + رسالة ترحيب
- "Code automatically applied at checkout" reassurance
- Branded بـ theme التاجر

**Checkout Display:**
- Line item: "Discount (Influencer: Sara) -20%"
- يبني ثقة + شفافية

**Merchant Dashboard:**
- Influencer leaderboard مرتب بالـ revenue
- Drill-down per influencer: orders, top products
- Export CSV

#### Configuration

```typescript
interface InfluencerConfig {
  id: string;
  merchant_id: string;
  slug: string;                            // e.g., "sara_kn"
  display_name: string;
  profile_pic_url?: string;
  coupon_code: string;
  commission_percent?: number;
  is_active: boolean;
  attribution_window_days: number;         // default 30
  attribution_mode: 'first_touch' | 'last_touch';
  welcome_message_ar: string;
  welcome_message_en: string;
}
```

#### Data Captured

```typescript
interface InfluencerOrder {
  id: string;
  merchant_id: string;
  influencer_id: string;
  salla_order_id: string;
  order_total: number;
  order_subtotal: number;
  coupon_discount: number;
  attribution_source: 'utm' | 'ref_slug' | 'direct_code';
  first_touch_at: timestamp;
  order_placed_at: timestamp;
  customer_id?: string;
  utm_params?: { source: string; medium: string; campaign: string };
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| العميل زار عبر 2 influencers في جلسة | تطبيق attribution_mode |
| coupon influencer منتهي في سلة | "Code expired" + log alert |
| Influencer disabled مid-session | تكريم الجلسة، لا attribution جديد |
| العميل يدخل coupon مختلف يدويًا | تكريم اليدوي، log فقدان attribution |
| Bot traffic مع influencer params | فلترة بـ user_agent + heuristics |
| UTM params تغيرت mid-checkout | last-applied wins |
| طلب refund بعد attribution | تحديد attribution كـ refunded |
| التاجر يضيف influencer بـ duplicate slug | validation error في admin |

#### Mobile, Accessibility & Integration

- **Mobile:** Banner sticky-top مع حجم أصغر
- **A11y:** اسم influencer يُعلن عند landing
- **Salla Integration:** Coupons API لـ auto-apply (مؤكد). Webhooks لـ order tracking. Twilight body hooks للـ banner.

#### الجهد المقدر
متوسط: **4-6 أيام**

---

### 27.4 Feature 8 — Out-of-Stock Substitute Engine (Module 50)

#### الوصف
عندما يصل العميل لـ PDP لمنتج نافد، بدلًا من عرض "أعلمني عند التوفر" فقط (الذي يلتقط الاهتمام الكامن ويفقد المبيعات الفورية)، هذا المحرك يقترح 3 بدائل مشابهة فورًا + يلتقط تفضيل العميل (بديل أم انتظار الأصلي). يدفع conversion بديلة (هدف: 30-40% من traffic OOS تتحول).

#### User Flow

```
[العميل يزور PDP لمنتج]
     ↓
[المنتج نافد (stock = 0)]
     ↓
[رسالة "Out of Stock" تُستبدل بـ substitute panel]
     ↓
[Panel يعرض:
  - "😔 هذا المنتج نفد. هل تجربين بدائل؟"
  - 3 بدائل (نفس الفئة، سعر مشابه)
  - "أو احفظ الأصلي للانتظار"
]
     ↓
[العميل إما:
  A) ينقر بديل → PDP بديل → قد يشتري
  B) يحفظ الأصلي → back-in-stock flow
  C) يغادر → "lost despite substitute offer"
]
```

#### المتطلبات الوظيفية

- **FR-50.1** كشف OOS state عبر Salla Products API: stock_quantity === 0.
- **FR-50.2** استعلام Products API للـ similar products: same category، price ±30%، similar tags/attributes.
- **FR-50.3** ترتيب المرشحين: same brand (+10)، close price (+5)، same color/size (+5)، best-seller (+3).
- **FR-50.4** عرض top 3 candidates في substitute panel مع image، name، price، "View" button.
- **FR-50.5** استبدال Salla "Out of Stock" message بـ panel substitute.
- **FR-50.6** Secondary action: "احفظ هذا المنتج" → fallthrough لـ Module 8.
- **FR-50.7** تتبع events: was offered، was clicked، did_convert.
- **FR-50.8** Dashboard metric: "OOS Recovery Rate" = substitute conversions / OOS PDP visits.
- **FR-50.9** matching configurable: category only، attributes، AI similarity (Phase 3).
- **FR-50.10** Doctor signal: لو substitute conversion < 15%، اقترح تحسين product taxonomy.

#### UX Requirements

**Substitute Panel:**
- يستبدل "Out of Stock" badge على PDP
- تعاطف: "😔 هذا المنتج نفد — إليكِ بدائل قد تعجبكِ"
- 3 product cards أفقية (mobile: عمودي)
- لكل card: image، name، price، "تصفح" button
- "بدلًا من ذلك، احفظ الأصلي" link

**التصميم البصري:**
- Cards مشابهة لـ Salla product cards (يرث theme)
- highlight خفيف عند hover
- مقارنة سعر واضحة إذا البدائل أرخص

#### Configuration

```typescript
interface OOSSubstituteConfig {
  enabled: boolean;
  numberOfAlternatives: number;            // default 3
  matchingStrategy: 'category_only' | 'attributes' | 'ai_similar';
  priceRangeFactor: number;                // default 0.3
  fallbackToBackInStock: boolean;
  rankingWeights: {
    sameBrand: number;
    closePrice: number;
    sameAttributes: number;
    bestSeller: number;
  };
}
```

#### Data Captured

```typescript
interface OOSEvent {
  id: string;
  merchant_id: string;
  original_product_id: string;
  session_id: string;
  alternatives_shown: string[];
  alternative_clicked?: string;
  saved_original: boolean;
  resulted_in_purchase?: boolean;
  purchased_product_id?: string;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| المنتج بدون similar items في catalog | إخفاء substitute panel، عرض back-in-stock فقط |
| كل البدائل أيضًا OOS | فلتر فقط in-stock |
| العميل كان يبحث SKU محدد | أولوية أقل للبدائل |
| البديل أغلى | عرض فرق السعر بوضوح |
| Substitute vs original restock | كلاهما tracked منفصلين |
| Bot/scraper detected | تخطي substitute display |
| التاجر يعطل المنتج mid-display | auto-refresh، استبعاد |
| العميل أغلق panel | عرض back-in-stock CTA |

#### Mobile, Accessibility & Integration

- **Mobile:** عمودي للبدائل، صور أكبر
- **A11y:** كل بديل focusable button، أسعار تُعلن
- **Salla Integration:** Products API للـ similarity، Twilight PDP hooks. قد يحتاج custom event listener.

#### الجهد المقدر
متوسط: **5-6 أيام**

---

### 27.5 Feature 9 — First-Time vs Returning Recognition (Module 39)

#### الوصف
يقدم تجربة first-touch مختلفة بناءً على ما إذا كان الزائر جديدًا (anonymous، بدون cookie) أو عائدًا (معروف عبر cookie أو Salla customer login). للجدد: 3-option intent selector (هدية / شخصي / تصفح). للعائدين: عرض آخر منتج شوهد + welcome-back. ينتج intent classification فوري للـ segmentation + تجربة مخصصة أفضل.

#### User Flow

```
[الزائر يصل homepage أو category]
     ↓
[Smart Snippet يفحص:
  - Cookie: has_visited=true?
  - Salla customer.is_logged_in?
]
     ↓
[CASE A: First-time]
     ↓
[Welcome banner: 3 intent options]
     ↓
[العميل ينقر: "🎁 هدية" / "💄 لي" / "🔍 أتصفح"]
     ↓
[Tag في session + cookie set]
     ↓
[Navigation مخصصة]

[CASE B: Returning]
     ↓
[Welcome-back banner مع اسم (إن كان معروف)]
     ↓
[Last-viewed product strip]
     ↓
[اختياري: AI suggestion بناءً على intent سابق]
```

#### المتطلبات الوظيفية

- **FR-39.1** كشف visitor state عند load: قراءة `ss_returning` cookie + Salla customer.is_logged_in.
- **FR-39.2** First-time: عرض intent banner على homepage و category pages (ليس PDP/cart).
- **FR-39.3** Intent options قابلة للضبط لكل تاجر (default 3: gift/personal/browse).
- **FR-39.4** عند click intent: ضبط cookie `ss_returning=true` + `ss_intent=<value>`.
- **FR-39.5** Returning visitor: عرض banner مخصص مع intent مخزون أو نشاط سابق.
- **FR-39.6** إذا Salla customer logged in: عرض الاسم من Salla customer object.
- **FR-39.7** Last-viewed product strip يستخدم localStorage cache.
- **FR-39.8** Dashboard: توزيع visitor intent (% gift، personal، browse) للـ segmentation.
- **FR-39.9** Doctor rule: لو gift intent > 30%، اقترح gift-focused homepage أو Gift Finder.
- **FR-39.10** اختياري: تمرير intent tag لـ URL params لـ marketing pixels.

#### UX Requirements

**First-Time Banner:**
- أعلى الصفحة، قابل للإغلاق
- 3 أزرار كبيرة سهلة الـ tap
- emoji + label واضح
- subtle، ليس عدواني

**Returning Banner:**
- أكثر شخصية: "👋 مرحبًا بعودتك" + اسم
- يعرض: آخر منتج + "متابعة"
- "Continue where you left off"

**التصميم البصري:**
- ألوان مختلفة: first-time (أزرق welcoming) vs returning (أصفر/برتقالي دافئ)
- slide-in animation
- auto-dismiss بعد intent (first-time)

#### Configuration

```typescript
interface VisitorRecognitionConfig {
  enabled: boolean;
  firstTimePages: string[];
  intentOptions: {
    id: string;
    label_ar: string;
    label_en: string;
    icon: string;
  }[];
  returningBanner: {
    showLastViewed: boolean;
    showNameIfKnown: boolean;
    autoDismissSeconds?: number;
  };
  cookieExpiryDays: number;                // default 365
  passIntentToPixel: boolean;
}
```

#### Data Captured

```typescript
interface VisitorIntent {
  id: string;
  merchant_id: string;
  session_id: string;
  customer_id?: string;
  visitor_state: 'first_time' | 'returning';
  intent_tag?: string;
  selected_at?: timestamp;
  last_visit_at?: timestamp;
  total_visits: number;
  first_visit_at: timestamp;
  last_intent?: string;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| العميل فرّغ cookies | يعامل first-time مرة ثانية |
| Salla logged-in لكن لا cookie | استخدم customer ID |
| Cookie returning لكن Salla logged out | trust cookie، لا اسم |
| Intent selected ثم العميل غيّر رأيه | السماح بـ override |
| Banner dismissed بدون intent | log dismissal، لا tag |
| Mobile vs desktop different browsers | مستقل (مقبول) |
| Bot/crawler traffic | تخطي banner (UA detection) |
| Ad blocker | banner قد لا يُعرض؛ graceful fallback |

#### Mobile, Accessibility & Integration

- **Mobile:** أزرار stacked، تاب targets أكبر
- **A11y:** intent options كـ buttons، keyboard navigable
- **Salla Integration:** Twilight SDK لـ customer state (مؤكد)

#### الجهد المقدر
متوسط: **4-5 أيام**

---

### 27.6 Feature 10 — Coming Soon / Pre-Launch Capture (Module 51)

#### الوصف
للمنتجات المهيأة لكن غير منشورة بعد (status="hidden" أو tag "coming_soon")، يستبدل PDP العادي بـ teaser pre-launch فيه صورة المنتج، تاريخ الإطلاق المتوقع، ونموذج التقاط الاهتمام (جوال أو email). اختياريًا يقدم خصم early-bird للمشتركين. عندما status يتغير لـ "active"، إشعار تلقائي لكل المشتركين عبر WhatsApp/Email.

يحول pre-launch curiosity إلى قائمة guaranteed first-day sales.

#### User Flow

```
[التاجر ينشئ منتج بـ status="hidden" + tag "coming_soon"]
     ↓
[العميل يصل URL (preview، URL مسرّب، إلخ)]
     ↓
[Smart Snippet يكشف status، يستبدل PDP بـ teaser]
     ↓
[Teaser يعرض:
  - صورة المنتج (blur اختياري)
  - تاريخ الإطلاق المتوقع
  - وصف teaser
  - "اشتركي للتنبيه عند الإطلاق"
  - اختياري: "احصلي على 15% خصم Early Bird"
]
     ↓
[العميل يُرسل → إضافة لـ pre_launch_subscribers]
     ↓
[عند status → "active":
  - إشعار تلقائي للكل
  - coupon early-bird إذا مهيأ
]
```

#### المتطلبات الوظيفية

- **FR-51.1** كشف product status من Twilight context: status === 'hidden' أو tag 'coming_soon'.
- **FR-51.2** استبدال Salla PDP الافتراضي بـ pre-launch template.
- **FR-51.3** Template يعرض: صور (blur configurable)، اسم، وصف teaser، تاريخ متوقع.
- **FR-51.4** نموذج capture: جوال أو email (واحد مطلوب على الأقل) + موافقة PDPL + early-bird opt-in اختياري.
- **FR-51.5** تخزين في `pre_launch_subscribers`: customer_phone_hash، product_id، subscribed_at، early_bird_opt_in.
- **FR-51.6** الاشتراك في Salla `product.status.updated` webhook.
- **FR-51.7** عند تغيير status لـ 'active': queue notifications للكل خلال 5 دقائق.
- **FR-51.8** Template الإشعار: product link، coupon early-bird اختياري (auto-generated single-use).
- **FR-51.9** تتبع conversion: subscribers → first-day purchases attribution.
- **FR-51.10** Dashboard: per-product subscriber count، conversion rate.

#### UX Requirements

**Pre-Launch Page:**
- يبني anticipation: صورة كبيرة، tagline teaser
- Countdown timer لتاريخ الإطلاق
- "اشترك للوصول المبكر" CTA
- إشارات ثقة: "X متابع للإطلاق"
- أزرار مشاركة (Twitter/Instagram)

**التصميم:**
- شعور cinematic
- typography premium
- animation خفيفة على countdown

**Notification UX:**
- WhatsApp مع صورة المنتج + "تم الإطلاق!" + early-bird code
- Email مع rich preview

#### Configuration

```typescript
interface PreLaunchConfig {
  enabled: boolean;
  detectionMethod: 'status_hidden' | 'custom_tag' | 'both';
  customTagName: string;                   // default "coming_soon"
  imageBlur: boolean;
  showCountdown: boolean;
  earlyBirdEnabled: boolean;
  earlyBirdDiscountPercent: number;        // default 15
  earlyBirdCouponPrefix: string;
  notificationChannels: ('whatsapp' | 'email')[];
  notificationDelaySeconds: number;        // default 300
}
```

#### Data Captured

```typescript
interface PreLaunchSubscriber {
  id: string;
  merchant_id: string;
  product_id: string;
  customer_phone_hash?: string;
  customer_email?: string;
  consent_given_at: timestamp;
  early_bird_opt_in: boolean;
  notified_at?: timestamp;
  notification_clicked_at?: timestamp;
  purchase_attributed?: string;
  subscribed_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| status reverts من active → hidden | لا re-notify، عرض "back to pre-launch" للزوار الجدد |
| المشترك لديه حساب | match بـ email/phone، link |
| تاريخ الإطلاق مر بدون تغيير status | عرض "delayed" + إعادة اشتراك |
| العميل ألغى الاشتراك قبل الإطلاق | احترام فوري |
| Early-bird limits (مثلاً أول 100) | configurable limit + waitlist |
| منتجات متعددة coming soon | اشتراكات مستقلة |
| التاجر حذف المنتج قبل الإطلاق | إشعار subscribers بالإلغاء |
| 1000+ subscribers عند الإطلاق | Batch notifications خلال ساعة |

#### Mobile, Accessibility & Integration

- **Mobile:** تجربة full-screen، CTA كبير أسفل
- **A11y:** countdown يُعلن دوريًا، form labeled
- **Salla Integration:** Products API لـ status detection، `product.updated` webhook (مؤكد)، Twilight PDP override

#### الجهد المقدر
متوسط: **4-5 أيام**

---

### 27.7 Feature 11 — Cart Sharing & Save Link (Module 55)

#### الوصف
يولّد URL قابل للمشاركة يحتوي cart state العميل، يتيح إرسال السلة لأصدقاء/عائلة/نفسه عبر WhatsApp أو Email أو copy-paste. اختياريًا يكافئ المشارك والمشتري بخصم إذا تحولت السلة المشتركة. يفعّل social commerce patterns (gift lists، "شو أبغى" sharing) التي لا تدعمها سلة natively.

#### User Flow

```
[العميل يضيف 3-5 items للسلة]
     ↓
[يرى زر "💾 احفظي أو شاركي السلة"]
     ↓
[ينقر → modal مع خيارات]
     ↓
[3 خيارات:
  A) نسخ الرابط
  B) WhatsApp share (deep link)
  C) إرسال لـ email
]
     ↓
[Link يُولّد مع JWT يحتوي cart state]
     ↓
[المستلم يفتح link → cart يُعاد بناؤه]
     ↓
[إذا اشترى المستلم → كلاهما يحصل على 10% خصم]
     ↓
[Tracking في cart_shares]
```

#### المتطلبات الوظيفية

- **FR-55.1** زر "Share Cart" يُحقن في Salla cart page عبر Twilight hooks.
- **FR-55.2** عند click: serialize cart state إلى JWT (product_ids، quantities، variants، coupons).
- **FR-55.3** توليد shareable URL: `/cart/share/<jwt_token>` مع 30-day expiry.
- **FR-55.4** Modal يعرض: copy link، WhatsApp share، email share، sharer's note اختياري (max 200 chars).
- **FR-55.5** المستلم ينقر → cart state يُعاد بناؤه في Salla session له.
- **FR-55.6** المستلم يرى "هذه السلة من [Sharer]" مع note إذا متوفر.
- **FR-55.7** Track share-to-purchase attribution: cart_share_id linked لـ order لاحق.
- **FR-55.8** Dual reward (إذا مهيأ): coupon للمستلم، credit للمشارك.
- **FR-55.9** Dashboard: إجمالي shares، share conversion rate، top sharers leaderboard.
- **FR-55.10** تحليلات: أي قنوات أفضل، avg cart value مشترك.

#### UX Requirements

**Share Modal:**
- 3 أزرار كبيرة (copy، WhatsApp، email)
- معاينة cart (top 3 items + total)
- حقل note اختياري
- "🎁 كلاكما يحصل على 10% خصم" reassurance

**Recipient Experience:**
- Banner ودود: "👋 [Name] شاركت معك هذه السلة"
- note المشارك معروض
- Items معبأة في cart المستلم
- "إكمال الشراء" primary CTA

#### Configuration

```typescript
interface CartSharingConfig {
  enabled: boolean;
  shareChannels: ('copy' | 'whatsapp' | 'email')[];
  allowSharerNote: boolean;
  noteMaxLength: number;                   // default 200
  linkExpiryDays: number;                  // default 30
  dualReward: {
    enabled: boolean;
    sharerDiscountPercent: number;         // default 10
    buyerDiscountPercent: number;          // default 10
    minOrderValue?: number;
  };
}
```

#### Data Captured

```typescript
interface CartShare {
  id: string;
  merchant_id: string;
  sharer_customer_id?: string;
  sharer_session_id: string;
  cart_state: {
    items: { product_id: string; variant_id?: string; quantity: number }[];
    applied_coupons: string[];
  };
  sharer_note?: string;
  share_channel: 'copy' | 'whatsapp' | 'email';
  shared_at: timestamp;
  expires_at: timestamp;
  recipient_opened_at?: timestamp;
  resulted_in_order_id?: string;
  attribution_revenue?: number;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| المستلم يضيف items + items مشتركة | دمج في cart واحد |
| item مشترك الآن OOS | "X غير متاح الآن" + إزالة |
| coupon مشترك منتهي | notice، المستلم يقدر يشتري بالسعر العادي |
| Token مُلاعب | 400 + log security event |
| Token منتهي (>30 يوم) | "هذه السلة المشتركة منتهية" + تصفح جديد |
| نفس المستلم يفتح link 10 مرات | tracking unique vs total |
| المشارك ليس logged in | يقدر يشارك، attribution في cookie |
| Self-share (المشارك = المستلم) | السماح (use case شرعي) |

#### Mobile, Accessibility & Integration

- **Mobile:** WhatsApp share intent، iOS/Android share sheets
- **A11y:** خيارات share keyboard accessible
- **Salla Integration:** Cart API لـ state reconstruction، Coupons API للـ dual reward

#### الجهد المقدر
متوسط: **4-5 أيام**

---

### 27.8 Feature 12 — Vertical Discovery Quiz (Module 46)

#### الوصف
quiz قصير تفاعلي (3-5 أسئلة، < 60 ثانية) مخصص لـ vertical التاجر (Beauty / Fashion / Perfumes / Gifts / Other) يبني `customer_profile` JSON. الـ profile يلتقط التفضيلات (مثل: نوع البشرة، تفضيل الستايل، عائلة العطر) يُعلم product recommendations، email campaigns، وdashboard segmentation. يرفع repeat purchase rate بـ ~2.3x.

#### User Flow

```
[العميل يزور homepage أو category]
     ↓
[First-time + اختار "Personal" intent (من Module 39)]
     ↓
[CTA يظهر: "🌟 اعرفي بشرتك خلال 60 ثانية"]
     ↓
[العميل ينقر → quiz modal يفتح]
     ↓
[3-5 multi-choice questions per vertical]
     ↓
[يولّد profile: { skin_type: 'oily', concerns: ['acne'], routine_level: 'intermediate' }]
     ↓
[يعرض: "✨ ملف بشرتك جاهز" + 3 recommended products]
     ↓
[اختياري: capture جوال للتوصيات لاحقًا]
     ↓
[Profile مخزون، يُستخدم للفلترة + campaigns]
```

#### المتطلبات الوظيفية

- **FR-46.1** Quiz templates قابلة للضبط لكل vertical.
- **FR-46.2** كل template: 3-5 questions، multi-choice أو single-choice، branching logic.
- **FR-46.3** Quiz UI: progress bar، Next/Back، "Skip" option.
- **FR-46.4** توليد `customer_profile` JSON مع vertical-specific dimensions.
- **FR-46.5** تخزين profile في `customer_profiles` (linked بـ phone hash أو customer_id).
- **FR-46.6** تطبيق profile على PDP filtering.
- **FR-46.7** Doctor rule: surface المنتجات اللي العملاء profiled لكن ما اشتروا.
- **FR-46.8** Profile-based segmentation في dashboard.
- **FR-46.9** Email/WhatsApp campaigns يمكن فلترتها بـ profile.
- **FR-46.10** السماح بتحديث/إعادة الـ quiz.
- **FR-46.11** "Recommended for you" badges على المنتجات المطابقة (subtle).
- **FR-46.12** Track completion rate، drop-off question، time-to-complete.

#### UX Requirements

**Quiz Design:**
- Modal "ممتع، ليس استجواب"
- خيارات بصرية مع أيقونات
- transitions سلسة
- "Skip" متاح لكن مثبط

**Result Screen:**
- "✨ ملف بشرتك جاهز" مع summary
- 3 recommended products فورًا
- "احفظي ملفك" CTA (capture جوال اختياري)

**Profile Application:**
- "Match" badge subtle على المنتجات المطابقة
- "ملفك" filter chip في category pages

#### Configuration

```typescript
interface DiscoveryQuizConfig {
  enabled: boolean;
  vertical: 'beauty' | 'fashion' | 'perfumes' | 'gifts' | 'custom';
  questions: {
    id: string;
    type: 'single_choice' | 'multi_choice' | 'slider' | 'text';
    label_ar: string;
    label_en: string;
    options: { value: string; label_ar: string; label_en: string; icon?: string }[];
    skippable: boolean;
  }[];
  resultMapping: {
    [dimension: string]: { from: string; value: string }[];
  };
  recommendationStrategy: 'tag_match' | 'category_match' | 'ai_similar';
}
```

#### Data Captured

```typescript
interface CustomerProfile {
  id: string;
  merchant_id: string;
  customer_phone_hash?: string;
  customer_id?: string;
  vertical: string;
  profile_data: Record<string, any>;
  quiz_completion_seconds: number;
  questions_answered: number;
  questions_skipped: number;
  completed_at: timestamp;
  updated_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| العميل بدأ quiz، تخلى mid-way | save progress، السماح بـ resume |
| العميل أخذ quiz عدة مرات | overwrite profile (مع تأكيد) |
| Quiz template تغير بعد save | re-prompt للتحديث |
| العميل تخطى كل الأسئلة | لا save، اقترح إعادة |
| لا منتجات تطابق profile | fallback لـ category bestsellers |
| إجابات متناقضة | last answer wins، flag للمراجعة |
| Profile قديم (سنتين) | اقتراح تحديث بعد 365 يوم |
| Mobile vs desktop different profiles | sync عبر email/phone |

#### Mobile, Accessibility & Integration

- **Mobile:** Full-screen modal، swipe بين الأسئلة
- **A11y:** كل options keyboard-navigable
- **Salla Integration:** Products API للفلترة، Customer object للـ profile linking

#### الجهد المقدر
متوسط-كبير: **5-7 أيام**

---

### 27.9 Feature 13 — Birthday/Anniversary Capture (Module 49)

#### الوصف
يلتقط تواريخ شخصية (عيد ميلاد، ذكرى زواج، إلخ) من العملاء عبر opt-in forms (post-checkout أو account section)، ثم يطلق حملات WhatsApp/Email مخصصة قبل 3 أيام من المناسبة مع gift code أو special offer. حملات Birthday تحقق 3-4x higher CTR من generic emails وتبني loyalty عاطفية.

#### User Flow

```
[Trigger A: Post-checkout success]
     ↓
[Banner: "🎉 لنحتفل بكِ! أخبرينا متى عيد ميلادك (اختياري)"]
     ↓
[العميل يملأ DD/MM (السنة اختيارية)]
     ↓
[تخزين في birthday_subscribers مع موافقة PDPL]

     ────────────────────────────

[Trigger B: Cron يومي 8 صباحًا توقيت السعودية]
     ↓
[يجد المشتركين الذين birthday بعد 3 أيام]
     ↓
[Queue WhatsApp/Email مع gift code مخصص]
     ↓
[العميل يستلم: "🎂 عيد ميلاد سعيد! هدية: code BIRTHDAY20"]
```

#### المتطلبات الوظيفية

- **FR-49.1** حقول النموذج: birthday (DD/MM مطلوب، YYYY اختياري)، anniversary (DD/MM اختياري).
- **FR-49.2** موافقة PDPL: checkbox صريح، موثقة.
- **FR-49.3** Trigger points: post-checkout، account section، banner — قابلة للضبط.
- **FR-49.4** Cron يومي 8 صباحًا يفحص `birthday_subscribers` للتواريخ المطابقة (today + 3).
- **FR-49.5** Queue notification: greeting شخصي، gift code (auto-generated single-use)، expiry (14 يوم).
- **FR-49.6** Gift code amount قابل للضبط (default 20% off).
- **FR-49.7** Track campaign metrics: sent، opened، clicked، redeemed.
- **FR-49.8** Dashboard: "Birthdays this month" calendar view.
- **FR-49.9** اختياري: anniversary campaigns نفس logic مع رسالة مختلفة.
- **FR-49.10** Year of birth ليس مطلوب (احترام الخصوصية).

#### UX Requirements

**Capture Form:**
- ودود: "🎉 لنحتفل بكِ"
- date inputs (DD/MM dropdowns)
- السنة optional مع ملاحظة
- consent checkbox واضح

**Notification:**
- WhatsApp festive مع emoji + صورة
- اسم شخصي إن وُجد
- CTA: "استخدمي الكود قبل [date]"

**Dashboard:**
- Calendar view لـ birthdays قادمة
- Campaign creator مع template preview

#### Configuration

```typescript
interface BirthdayCaptureConfig {
  enabled: boolean;
  triggerPoints: ('post_checkout' | 'account_section' | 'banner')[];
  captureAnniversary: boolean;
  notificationDaysBefore: number;          // default 3
  giftCode: {
    discountType: 'percent' | 'fixed';
    discountValue: number;
    maxValue?: number;
    expiryDays: number;                    // default 14
    codePrefix: string;                    // "BIRTHDAY_"
  };
  channels: ('whatsapp' | 'email')[];
  messageTemplate_ar: string;
  messageTemplate_en: string;
}
```

#### Data Captured

```typescript
interface BirthdaySubscriber {
  id: string;
  merchant_id: string;
  customer_phone_hash?: string;
  customer_email?: string;
  birthday_day: number;                    // 1-31
  birthday_month: number;                  // 1-12
  birthday_year?: number;
  anniversary_day?: number;
  anniversary_month?: number;
  consent_given_at: timestamp;
  last_notified_at?: timestamp;
  last_redemption_at?: timestamp;
  subscribed_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| عيد ميلاد Feb 29 | إشعار Feb 28 في السنوات غير الكبيسة |
| العميل أدخل تاريخ ماضٍ لـ anniversary | accept، treat as past |
| Subscribers متعددين بنفس الجوال | استخدم آخر submission |
| العميل ألغى الاشتراك قبل birthday | احترام فوري، لا إشعار |
| Birthday اليوم (لا 3-day buffer) | إرسال same-day بدون gift code expiring |
| القناة فشلت (WhatsApp blocked) | fallback لـ email |
| Gift code استُخدم | "Already redeemed" + خصم عادي |
| التاجر عطل campaign mid-cycle | إيقاف إشعارات مستقبلية، احترام in-progress |

#### Mobile, Accessibility & Integration

- **Mobile:** Native date picker
- **A11y:** date fields labeled، year-optional واضح
- **Salla Integration:** Salla customer.birthday — verify natively. Coupons API لتوليد gift code. WhatsApp/Email من MVP.

#### الجهد المقدر
صغير: **2-3 أيام**

---

### 27.10 Feature 14 — Smart Reorder Timing (Module 44)

#### الوصف
تذكيرات reorder auto-triggered بناءً على timing فئة المنتج (مثلاً: serum=60 يوم، supplement=30 يوم، perfume=90 يوم). بعد شراء العميل، النظام يتتبع depletion المتوقع حسب فئة المنتج، ثم يرسل WhatsApp reminder مع one-click reorder link. يرفع reorder rate بـ 22-35% بدون جهد التاجر.

#### User Flow

```
[العميل يشتري Vitamin C Serum (30ml)]
     ↓
[المنتج مربوط بفئة "serum" (timing 60 يوم)]
     ↓
[Cron يومي 8 صباحًا يفحص orders 55-65 يوم]
     ↓
[يجد matching orders، يضع WhatsApp في queue]
     ↓
[العميل يستلم:
  "مرحبًا [Name] 👋
  طلبتي Vitamin C Serum قبل 60 يوم.
  حان وقت إعادة الطلب
  
  [إعادة الطلب] [ذكّريني لاحقًا]"
]
     ↓
[العميل ينقر إعادة → cart معبأ، جاهز للـ checkout]
     ↓
[Track conversion في reorder_reminders]
```

#### المتطلبات الوظيفية

- **FR-44.1** Config table `reorder_category_timings` يربط فئات/tags بـ depletion days.
- **FR-44.2** Default timings: serum 60d، shampoo 45d، perfume 90d، supplement 30d (قابلة للضبط).
- **FR-44.3** Cron يومي 8 صباحًا يفحص orders aged [timing-5, timing+5] days.
- **FR-44.4** لكل order مطابق، تحقق إذا العميل لم يعد طلب نفس المنتج.
- **FR-44.5** إرسال WhatsApp reminder عبر template التاجر (Meta-approved).
- **FR-44.6** Reorder link يعيد بناء cart مع المنتجات الأصلية + shipping الافتراضي.
- **FR-44.7** Track outcomes: reminder_sent، reminder_clicked، resulted_in_reorder.
- **FR-44.8** Dashboard: reorder reminder funnel (sent → clicked → converted).
- **FR-44.9** Doctor rule: لو reorder rate < 15% لفئة، اقترح إعادة تقييم timing.
- **FR-44.10** Throttle: max 1 reminder per customer per product.
- **FR-44.11** العميل يقدر يلغي via WhatsApp reply أو consent center.

#### UX Requirements

**WhatsApp Message:**
- شخصي: اسم + منتج
- قيمة واضحة: "حان وقت إعادة الطلب"
- خياران: Reorder now / Remind later
- Unsubscribe link في footer

**Merchant Dashboard:**
- "Reorder Reminders" section
- Funnel chart
- Per-category breakdown
- Revenue attributed

#### Configuration

```typescript
interface ReorderTimingConfig {
  enabled: boolean;
  categoryTimings: Map<string, number>;    // category_id → days
  productTagTimings: Map<string, number>;
  defaultTiming: number;                   // 60
  scanRangeDays: number;                   // 5
  reminderTemplateAr: string;
  reminderTemplateEn: string;
  channels: ('whatsapp' | 'email')[];
  maxRemindersPerCustomerPerProduct: number; // 1
  throttlePerDay: number;
}
```

#### Data Captured

```typescript
interface ReorderReminder {
  id: string;
  merchant_id: string;
  customer_phone_hash: string;
  original_order_id: string;
  product_id: string;
  product_category: string;
  expected_reorder_date: date;
  reminder_sent_at: timestamp;
  reminder_clicked_at?: timestamp;
  reorder_order_id?: string;
  reorder_revenue?: number;
  customer_opted_out_at?: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| العميل أعاد طلب قبل reminder | skip، لا إرسال |
| العميل اشترى كمية متعددة | adjust expected depletion (2x = 2x timing) |
| المنتج لم يعد متاحًا | اقتراح بديل أو skip |
| العميل غيّر رقم الجوال | استخدم الأحدث من Salla |
| Category timing غير معروف لمنتج جديد | استخدم default |
| العميل ألغى | احترام، لا إشعارات |
| Reminder فشل (WhatsApp error) | إعادة مرة، ثم mark failed |
| العميل أعاد طلب بعد reminder بشكل منفصل | تتبع كـ converted (window 7 أيام) |

#### Mobile, Accessibility & Integration

- **Mobile:** WhatsApp deep link مع cart معبأ
- **A11y:** Email version للـ screen readers
- **Salla Integration:** Orders API لفحص الطلبات (مؤكد)، WhatsApp BSP، Cart API لإعادة البناء

#### الجهد المقدر
متوسط: **5-7 أيام**

---

### 27.11 Module 37 — Checkout Hesitation Capture (🟠 Phase 2)

#### الوصف
يلتقط أسباب abandonment على صفحة checkout بالذات. مختلف عن hesitation على PDP (Feature 1) لأن checkout abandonment له أسباب مختلفة (مفاجأة تكلفة الشحن، مشاكل طريقة الدفع، مخاوف الأمان، إجمالي غير متوقع). العملاء الذين يصلون checkout high-intent، ففهم لماذا ينسحبون = revenue insight حرج.

#### User Flow

```
[العميل يصل صفحة checkout]
     ↓
[يملأ delivery info، يرى الإجمالي النهائي]
     ↓
[Smart Snippet يكشف exit intent أو back navigation]
     ↓
[Modal خفيف: "ما يمنعك من إكمال الطلب؟"]
     ↓
[6 خيارات أسباب checkout-specific]
     ↓
[Submit → تخزين منفصل عن PDP hesitations]
     ↓
[Doctor يطلق قواعد checkout-specific]
```

#### المتطلبات الوظيفية

- **FR-37.1** كشف exit intent على checkout: mouseleave + scroll-up + idle threshold.
- **FR-37.2** عرض 6 أسباب checkout-specific: تكلفة الشحن، مشكلة الدفع، الأمان، الإجمالي غير متوقع، طريقة دفع مفقودة، سأعود لاحقًا.
- **FR-37.3** السماح بـ free text (max 500 chars).
- **FR-37.4** تخزين في `checkout_hesitations` table (منفصل عن `hesitation_submissions`).
- **FR-37.5** التقاط: cart_total، payment_method_selected، shipping_method_selected، delivery_country.
- **FR-37.6** Doctor rule: لو سبب الشحن > 5/أسبوع، اقترح مراجعة free shipping threshold.
- **FR-37.7** Dashboard: Checkout abandonment funnel + أهم الأسباب.
- **FR-37.8** A/B test الـ trigger timing: فوري vs بعد 30s idle.
- **FR-37.9** اختياري: عرض last-chance discount للـ carts عالية القيمة (>500 ر.س).
- **FR-37.10** Mobile: bottom-sheet modal (أقل تطفلًا).

#### UX Requirements

**التصميم البصري:**
- أقل عدوانية من PDP hesitation (العميل استثمر وقت)
- نبرة متعاطفة: "نقدر وقتك — أخبرنا ليش"
- خيارات quick-tap + skip متاح

**أسلوب Modal:**
- ينزلق من الأسفل على الجوال
- مركزي على Desktop، max-width 500px
- إشارات ثقة: "ردك يبقى خاص"

#### Configuration

```typescript
interface CheckoutHesitationConfig {
  enabled: boolean;
  triggerMode: 'exit_intent' | 'idle_timeout' | 'back_navigation';
  idleThresholdSeconds: number;
  reasons: { id: string; label_ar: string; label_en: string; enabled: boolean; }[];
  showLastChanceOffer: boolean;
  lastChanceOfferThreshold: number;
  lastChanceOfferCouponCode: string;
}
```

#### Data Captured

```typescript
interface CheckoutHesitation {
  id: string;
  merchant_id: string;
  trigger_mode: string;
  reason_id?: string;
  free_text?: string;
  cart_total: number;
  cart_items_count: number;
  payment_method_selected?: string;
  shipping_method_selected?: string;
  delivery_country: string;
  delivery_city: string;
  customer_id?: string;
  session_id: string;
  time_on_checkout_seconds: number;
  was_lastchance_offered: boolean;
  was_lastchance_accepted: boolean;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| العميل أكمل بعد رؤية modal | mark as "recovered" |
| محاولات checkout متعددة في جلسة | aggregate، لا تكرر modal |
| العميل أغلق modal | تتبع dismissal event |
| Payment method فعليًا معطوب | surface في Doctor كـ critical |
| العميل على بطء شبكة | لا trigger (تجنب friction) |
| Salla checkout customization غير متاح | fall back لـ cart-page exit intent |
| Last-chance discount استُخدم | تخطي العرض |
| Bot/scraper على checkout | تخطي modal |

#### Mobile, Accessibility & Integration

- **Mobile:** Bottom sheet، swipe-to-dismiss، large tap targets
- **A11y:** Modal focus trap، ARIA labels، keyboard navigation
- **Salla Integration:** Twilight checkout hooks (⚠️ **يحتاج verification**)

#### الجهد المقدر
متوسط-كبير: **5-7 أيام** (يعتمد على Salla checkout hooks)

---

### 27.12 Module 41 — Live Stock Urgency Signal (🟠 Phase 2)

#### الوصف
يعرض stock count شفاف + viewing count badge على PDP لما المخزون منخفض فعليًا. عكس fake urgency widgets، يستخدم بيانات حقيقية من webhook `product.quantity.low` وأحداث analytics. يبني ثقة عبر الشفافية مع خلق scarcity شرعي.

#### User Flow

```
[Salla webhook: product.quantity.low يطلق]
     ↓
[Smart Snippet يكاش: product X له Y stock]
     ↓
[العميل يزور PDP لـ X]
     ↓
[يفحص: stock < threshold AND theme لا يعرض stock]
     ↓
[عرض badge: "⚠️ بقي 3 قطع + 12 يشاهد الآن"]
     ↓
[viewing count يحدث real-time]
     ↓
[تتبع: badge_view، badge_impression، purchase_attribution]
```

#### المتطلبات الوظيفية

- **FR-41.1** الاشتراك في Salla `product.quantity.low` webhook.
- **FR-41.2** كاش low-stock products في Redis مع TTL = 1 ساعة.
- **FR-41.3** عند PDP load: فحص إذا المنتج في low-stock cache.
- **FR-41.4** عرض urgency badge فقط إذا stock_qty ≤ threshold (default 5).
- **FR-41.5** Theme detection: لو Salla theme يعرض stock count، تخطي badge.
- **FR-41.6** Real-time viewing count: aggregate `widget_viewed` events للمنتج في آخر 5 دقائق.
- **FR-41.7** Badge يحدث كل 30 ثانية عبر polling خفيف أو WebSocket.
- **FR-41.8** تتبع badge_impression، badge_dismissed events.
- **FR-41.9** A/B test impact: badge shown vs hidden control.
- **FR-41.10** Dashboard: products مع active urgency badges + conversion lift.

#### UX Requirements

**أسلوب Badge:**
- Inline مع PDP (مش popup)
- amber/orange subtle (تحذير، ليس panic)
- أيقونة واضحة: ⚠️ أو ⏰
- نص صادق: "X قطع متبقية"
- عدد المشاهدين الحي: "Y يشاهد الآن"

**التصميم البصري:**
- يرث Salla theme typography
- 8px border-radius، ظل خفيف
- count change animated

#### Configuration

```typescript
interface LiveStockUrgencyConfig {
  enabled: boolean;
  stockThreshold: number;
  showViewingCount: boolean;
  viewingCountWindowMinutes: number;
  themeDetectionEnabled: boolean;
  badgeStyle: 'subtle' | 'prominent';
  updateIntervalSeconds: number;
  badgeText_ar: string;
  badgeText_en: string;
}
```

#### Data Captured

```typescript
interface UrgencyBadgeEvent {
  id: string;
  merchant_id: string;
  product_id: string;
  stock_at_view: number;
  viewers_count: number;
  badge_shown: boolean;
  customer_id?: string;
  session_id: string;
  resulted_in_purchase?: boolean;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| Stock فعلًا 0 | إخفاء urgency، عرض OOS substitute (Module 50) |
| Theme يعرض "بقي X" | تخطي badge لتجنب التكرار |
| Webhook متأخر (بيانات قديمة) | refresh من Salla API عند PDP load |
| Stock زاد بعد low signal | تحديث cache، إخفاء badge |
| Bot يضخم viewing count | فلترة bot user agents |
| العميل لديه ad blocker | badge قد لا يحمل، fallback |
| Variants مختلفة بـ stock مختلف | badge per variant إن أمكن |
| Webhook فشل | fallback لـ periodic Salla API check |

#### Mobile, Accessibility & Integration

- **Mobile:** Badge أصغر، typography محسّن للجوال
- **A11y:** ARIA label وصفي، announce stock + viewers
- **Salla Integration:** webhook (مؤكد)، Products API، Twilight PDP hooks

#### الجهد المقدر
صغير-متوسط: **3-5 أيام**

---

### 27.13 Module 42 — Mobile One-Tap Interest (🟠 Phase 2)

#### الوصف
Anonymous mobile-only interest capture بدون نموذج. Sticky heart icon على PDP يتيح one-tap save بدون جوال أو email أو login. Cookie-based tracking. **مكمل لـ Salla Wishlist** (ليس بديل) — يلتقط volume أعلى لأنه بدون login friction. Kill criterion: إذا volume < 2x Salla Wishlist بعد pilot، حذف.

#### User Flow

```
[العميل يزور PDP على الجوال]
     ↓
[يرى Salla Add-to-Cart + heart icon (sticky bottom-right)]
     ↓
[نقرة واحدة → cookie يخزن: { product_id, timestamp }]
     ↓
[Heart يمتلئ بالأحمر — feedback بصري]
     ↓
[العميل يكمل تصفح أو يغادر]
     ↓
[زيارة لاحقة: heart pre-filled للمنتجات المحفوظة]
     ↓
[Dashboard: anonymous saves trending → demand signal لـ Doctor]
```

#### المتطلبات الوظيفية

- **FR-42.1** Sticky heart icon على PDP (mobile فقط via user-agent).
- **FR-42.2** نقرة واحدة toggle save state.
- **FR-42.3** تخزين في `ss_saved_products` cookie (max 50، FIFO).
- **FR-42.4** إرسال anonymous event: `mobile_save` مع product_id، session_id.
- **FR-42.5** لا PII مطلوب (anonymous-first).
- **FR-42.6** عند return visit (نفس المتصفح): heart pre-filled.
- **FR-42.7** Dashboard: "most anonymous-saved products".
- **FR-42.8** Doctor signal: high save-to-purchase delta = high-intent blocked.
- **FR-42.9** Position بحذر لتجنب conflict مع Salla theme favorites.
- **FR-42.10** Pilot kill: إذا volume < 2x Salla Wishlist في شهر، deprecate.

#### UX Requirements

**Heart Icon:**
- 48px tap target
- Position: bottom-right corner، sticky
- Animations: fill عند tap، pulse خفيف
- Inactive: outline heart
- Active: solid red + "تم الحفظ" tooltip (1.5s)

**Subtle:**
- لا badges، لا notification dots

#### Configuration

```typescript
interface MobileOneTapConfig {
  enabled: boolean;
  position: 'bottom-right' | 'bottom-left' | 'sticky-top';
  iconStyle: 'heart' | 'bookmark' | 'plus';
  maxSavedPerCookie: number;
  showSalleWishlistAlongside: boolean;
  pilotKillThresholdMonths: number;
  pilotMinVolumeMultiplier: number;
}
```

#### Data Captured

```typescript
interface MobileSaveEvent {
  id: string;
  merchant_id: string;
  product_id: string;
  session_id: string;
  device_type: 'mobile' | 'tablet';
  action: 'save' | 'unsave';
  is_returning_visitor: boolean;
  saved_count_in_cookie: number;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| User على desktop | لا تعرض icon (mobile-only) |
| Cookie فُرّغ | العميل يخسر saves (مقبول لـ anonymous) |
| 50+ saves | FIFO eviction مع إشعار |
| Salla theme فيه favorites | position لتجنب overlap |
| العميل يستخدم Salla Wishlist | كلاهما tracked منفصل |
| Ad blocker يحظر cookie | feature يتدهور بصمت |
| العميل سجل دخول بعد saves | لا auto-merge لـ Wishlist (نية مختلفة) |
| Pilot فشل | إزالة via admin toggle |

#### Mobile, Accessibility & Integration

- **Mobile:** Optimized لـ thumb reach
- **A11y:** ARIA label وصفي
- **Salla Integration:** Twilight SDK، theme detection. Salla Wishlist يبقى الأساسي.

#### الجهد المقدر
صغير: **2-3 أيام** (مع kill criterion review في Month 1)

---

### 27.14 Module 43 — Pre-Checkout Confidence Booster (🟠 Phase 2)

#### الوصف
Trust signals + WhatsApp CTA يُحقن فوق "Place Order" على checkout. مصمم لتقليل التردد في اللحظة الأخيرة في متاجر luxury/high-AOV حيث كل 0.5% CVR = آلاف SAR شهريًا. Trust block قابل للضبط (شحن، إرجاع، أمان، دعم).

#### User Flow

```
[العميل يملأ checkout form]
     ↓
[يصل خطوة الدفع، على وشك "Place Order"]
     ↓
[Pre-Checkout block فوق الزر:
  - Trust signals
  - زر WhatsApp: "تواصل قبل الدفع؟"
]
     ↓
[العميل إما:
  A) ينقر Place Order → conversion
  B) ينقر WhatsApp → محادثة مع التاجر
  C) يغادر → tracked
]
```

#### المتطلبات الوظيفية

- **FR-43.1** حقن trust block قابل للضبط فوق CTA الأساسي.
- **FR-43.2** Trust signals: تذكير شحن مجاني، سياسة إرجاع، دفع آمن، توفر دعم.
- **FR-43.3** WhatsApp button اختياري: deep link مع رسالة معبأة.
- **FR-43.4** الرسالة المعبأة: "أنا على وشك إكمال طلب — لدي سؤال أخير".
- **FR-43.5** تتبع impression، click WhatsApp، conversion attribution.
- **FR-43.6** عرض فقط على checkout (ليس cart، ليس PDP).
- **FR-43.7** قابل للضبط: أي signals تظهر، نصوص مخصصة.
- **FR-43.8** Mobile-optimized: stacks vertically، WhatsApp prominent.
- **FR-43.9** A/B test: trust block shown vs hidden.
- **FR-43.10** Dashboard: trust block conversion lift، WhatsApp conversations.

#### UX Requirements

**Trust Block:**
- خلفية subtle (رمادي/أزرق خفيف)
- icons + نص قصير (✓ شحن مجاني فوق 200)
- 3-5 signals max

**WhatsApp Button:**
- واضح، prominent
- لون أخضر/branded
- "تواصل بسرعة" tagline

#### Configuration

```typescript
interface PreCheckoutConfidenceConfig {
  enabled: boolean;
  trustSignals: { id: string; icon: string; text_ar: string; text_en: string; enabled: boolean; }[];
  whatsAppEnabled: boolean;
  whatsAppNumber: string;
  whatsAppMessage_ar: string;
  whatsAppMessage_en: string;
  position: 'above_cta' | 'below_cta' | 'sidebar';
}
```

#### Data Captured

```typescript
interface PreCheckoutEvent {
  id: string;
  merchant_id: string;
  session_id: string;
  customer_id?: string;
  cart_total: number;
  trust_block_shown: boolean;
  whatsapp_clicked: boolean;
  resulted_in_purchase: boolean;
  resulted_in_whatsapp_conversation: boolean;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| التاجر بدون WhatsApp Business | إخفاء WhatsApp، عرض trust signals فقط |
| العميل نقر WhatsApp ثم أكمل الطلب | tracked كـ "WhatsApp-assisted conversion" |
| Trust block لا يلائم mobile | collapse signals أقل أهمية |
| Salla checkout مقيد | حقن فوق cart total بدلًا |
| Ad blocker | block لا يحمل، لا تأثير على checkout |
| رسالة WhatsApp pre-filled محظورة | fallback لرسالة عامة |
| أجهزة checkout متعددة | tracked unique per device |
| رقم WhatsApp تغير | auto-update من إعدادات التاجر |

#### Mobile, Accessibility & Integration

- **Mobile:** Stacked، WhatsApp full-width
- **A11y:** Trust signals كـ ARIA list
- **Salla Integration:** Twilight checkout hooks (⚠️ **يحتاج verification**)، WhatsApp BSP

#### الجهد المقدر
صغير: **2-3 أيام** (يعتمد على Salla checkout hooks)

---

### 27.15 Module 45 — Comparison Shopping Detector (🟠 Phase 2)

#### الوصف
يكشف العملاء الذين يقارنون منتجات (3+ products نفس فئة خلال 10 دقائق) ويتدخل بـ help widget: "ما الذي يصعب القرار؟". يكشف decision-friction reasons (سعر، attributes، style، إلخ) ويغذي Doctor لـ category-level optimization.

#### User Flow

```
[العميل يرى Product A]
     ↓
[يرجع، يرى Product B (نفس فئة)]
     ↓
[يرى Product C (نفس فئة، خلال 10 دقائق)]
     ↓
[Smart Snippet يكشف comparison pattern]
     ↓
[Widget يظهر: "محتارة بين هذه المنتجات؟"]
     ↓
[5 خيارات: السعر، المقاس/الفت، الجودة، الستايل، المناسبة]
     ↓
[Submit → تخزين في comparison_signals]
     ↓
[Doctor: category-level friction insights]
```

#### المتطلبات الوظيفية

- **FR-45.1** تتبع PDP visits لكل session real-time (server-side).
- **FR-45.2** كشف comparison pattern: 3+ PDPs نفس فئة خلال 10 دقائق.
- **FR-45.3** الفئات تطابق عبر Salla Products API (category_id).
- **FR-45.4** Trigger widget على PDP 4 (بعد كشف).
- **FR-45.5** Widget يسأل: "ما الذي يصعب القرار؟" مع 5 خيارات.
- **FR-45.6** الخيارات: السعر، المقاس/الفت، الجودة، الستايل، المناسبة (قابلة للضبط).
- **FR-45.7** تخزين في `comparison_signals` مع: session_id، category_id، products_viewed[]، friction_reason.
- **FR-45.8** Dashboard: نسبة comparison shoppers، أهم friction reasons per category.
- **FR-45.9** Doctor rule: لو "السعر" > 30% friction → اقترح price-comparison snippet.
- **FR-45.10** Cooldown: لا تعرض widget أكثر من مرة في جلسة.

#### UX Requirements

**أسلوب Widget:**
- non-intrusive bottom-right pop-in (ليس modal)
- نبرة ودودة: "محتارة بين هذه؟ ساعدينا نساعدك"
- 5 خيارات tap كبيرة + skip
- Dismissible

**التصميم البصري:**
- accent purple/blue (research mode)
- slide-in من الزاوية
- Skip ظاهر

#### Configuration

```typescript
interface ComparisonDetectorConfig {
  enabled: boolean;
  detectionThreshold: number;
  detectionWindowMinutes: number;
  categoriesMustMatch: boolean;
  cooldownMinutes: number;
  frictionOptions: { id: string; label_ar: string; label_en: string; enabled: boolean; }[];
  vertical?: 'fashion' | 'beauty' | 'electronics';
}
```

#### Data Captured

```typescript
interface ComparisonSignal {
  id: string;
  merchant_id: string;
  session_id: string;
  customer_id?: string;
  category_id: string;
  products_viewed: string[];
  viewing_duration_seconds: number;
  friction_reason?: string;
  free_text?: string;
  resulted_in_purchase?: string;
  abandoned: boolean;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| العميل يشاهد فئات متعددة (ليس واحدة) | لا trigger |
| نفس المنتج 3 مرات | لا comparison |
| 10-min window edge | tolerance ±1 دقيقة |
| العميل أغلق widget | cooldown، لا عرض في جلسة |
| Bot crawler يشاهد كثير | فلترة via bot detection |
| Category data غير متاح | fallback لـ product tags |
| Session انتهت بين views | reset comparison tracking |
| العميل اشترى بعد widget | track friction_reason + outcome |

#### Mobile, Accessibility & Integration

- **Mobile:** Bottom sheet بدل corner pop-in
- **A11y:** Options keyboard navigable
- **Salla Integration:** Products API للفئات، session tracking (Module 35)

#### الجهد المقدر
متوسط-كبير: **6-8 أيام**

---

### 27.16 Module 47 — Customer Bundle Builder (🟠 Phase 2)

#### الوصف
العميل يختار 3+ منتجات لتكوين bundle مخصص مع auto-discount. يختلف عن merchant-defined bundles بأن العميل يختار. قواعد قابلة للضبط (min/max products، فئات مؤهلة، tiers خصم). تطبيق discount عبر Salla Coupons API. Dashboard يكشف "Top customer-built combinations" لإعلام official bundles.

#### User Flow

```
[العميل يتصفح category]
     ↓
[يرى "Build Your Bundle" CTA: "اختر 3 منتجات واحصلي على 15% خصم"]
     ↓
[ينقر → bundle builder modal]
     ↓
[يختار منتجات (مع eligibility check)]
     ↓
[الاختيارات تبني، tier discount يرتفع:
  - 3 = 10% off
  - 5 = 15% off
  - 7+ = 20% off
]
     ↓
[ينقر "Add Bundle to Cart"]
     ↓
[Salla coupon يُطبق تلقائيًا عند checkout]
     ↓
[Conversion + combination مسجل]
```

#### المتطلبات الوظيفية

- **FR-47.1** قواعد bundle قابلة للضبط: min/max، فئات مؤهلة، tiers.
- **FR-47.2** "Build Bundle" CTA على category pages و homepage.
- **FR-47.3** Modal: يعرض الاختيارات الحالية + المساحات المتبقية + tier الحالي.
- **FR-47.4** Eligibility check لكل منتج: matches categories، in stock.
- **FR-47.5** Dynamic discount calculation.
- **FR-47.6** "Add Bundle to Cart" ينشئ cart entries + يطبق coupon.
- **FR-47.7** Coupon auto-generated per bundle (single-use، 24h expiry).
- **FR-47.8** Dashboard: top combinations.
- **FR-47.9** Doctor rule: لو combination X بُني 20+ مرة، اقترح official bundle.
- **FR-47.10** Cancel/restart bundle بدون التأثير على cart الحالي.

#### UX Requirements

**Modal Builder:**
- Full-screen على mobile، large modal على desktop
- Progress bar: "1 of 3" → "3 of 3 — 15% discount!"
- Product cards بصرية
- Total + savings display

**التصميم البصري:**
- Gamified: progress bar، "Unlock more!"
- Confetti animation عند milestone
- CTA واضح

#### Configuration

```typescript
interface BundleBuilderConfig {
  enabled: boolean;
  minProducts: number;
  maxProducts: number;
  eligibleCategoryIds: string[];
  discountTiers: { minProducts: number; discountPercent: number; }[];
  ctaPlacement: ('category' | 'homepage' | 'pdp')[];
  couponExpiryHours: number;
  trackCombinations: boolean;
}
```

#### Data Captured

```typescript
interface BundleCreation {
  id: string;
  merchant_id: string;
  customer_id?: string;
  session_id: string;
  products_selected: string[];
  total_value: number;
  discount_percent: number;
  discount_amount: number;
  coupon_code: string;
  added_to_cart: boolean;
  completed_purchase: boolean;
  order_id?: string;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| Product يصبح OOS أثناء البناء | إشعار، السماح بـ swap |
| العميل غيّر رأيه | UI سهل لـ remove/swap |
| Bundle يخلق conflict مع items موجودة | تأكيد قبل merge |
| Coupon منتهي قبل checkout | auto-regenerate أو إشعار |
| Discount أكبر من حد التاجر | cap على الحد |
| العميل تخلى | save state، السماح بـ resume |
| نفس المنتج مرتين (variants) | معاملة كمنتجات منفصلة |
| 100+ منتج مؤهل | pagination + search |

#### Mobile, Accessibility & Integration

- **Mobile:** Full-screen modal، swipe
- **A11y:** Keyboard navigation، announce tier unlocks
- **Salla Integration:** Coupons API، Products API، Cart API

#### الجهد المقدر
كبير: **8-10 أيام**

---

### 27.17 Module 48 — Recently Viewed Memory Strip (🟠 Phase 2)

#### الوصف
Sticky horizontal strip يعرض المنتجات المشاهدة مؤخرًا + Dashboard tracking. يساعد العملاء يجدون المنتجات اللي ما اشتروها. ينتج analytics: المنتجات المشاهدة لكن غير مشترية (high-friction signal). **تنبيه تداخل themes:** بعض Salla themes تعرض "recently viewed" — قيمتنا المضافة في Dashboard tracking.

#### User Flow

```
[العميل يتصفح PDPs A, B, C, D (بدون شراء)]
     ↓
[Smart Snippet يتتبع كل view في localStorage]
     ↓
[العميل في category page]
     ↓
[Sticky strip يظهر أسفل: "Recently viewed: A B C D"]
     ↓
[ينقر أي → يرجع للـ PDP]
     ↓
[Analytics: view-to-purchase conversion per product]
     ↓
[Doctor: products بـ high views لكن low purchases = signal]
```

#### المتطلبات الوظيفية

- **FR-48.1** تتبع PDP visits في localStorage (max 20، FIFO).
- **FR-48.2** عرض sticky strip أسفل category/homepage (ليس PDP).
- **FR-48.3** Horizontal scroll لـ 5+ products.
- **FR-48.4** كشف إذا Salla theme يعرض recently viewed → تخطي.
- **FR-48.5** Click على منتج → navigate، track click event.
- **FR-48.6** Backend tracking: view-to-purchase per product.
- **FR-48.7** Dashboard widget: "Most viewed، never purchased".
- **FR-48.8** Doctor signal: high-view + low-purchase = friction.
- **FR-48.9** قابل للضبط: position، max products.
- **FR-48.10** Dismissible per session.

#### UX Requirements

**Strip:**
- Sticky bottom، 60px height
- Horizontal scroll لـ 5+
- Product mini-cards: image + name + price
- "View All Recently Viewed" link

**التصميم البصري:**
- Subtle: لا ينافس المحتوى الرئيسي
- يرث theme colors
- Smooth scroll على mobile

#### Configuration

```typescript
interface RecentlyViewedConfig {
  enabled: boolean;
  maxProductsTracked: number;
  maxProductsDisplayed: number;
  position: 'top' | 'bottom' | 'sidebar';
  showOnPages: ('homepage' | 'category' | 'cart')[];
  themeDetection: boolean;
  dismissible: boolean;
}
```

#### Data Captured

```typescript
interface RecentlyViewedEvent {
  id: string;
  merchant_id: string;
  session_id: string;
  product_id: string;
  view_count_in_session: number;
  added_to_cart: boolean;
  purchased: boolean;
  time_to_purchase_minutes?: number;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| localStorage فُرّغ | Strip فارغ حتى views جديدة |
| Theme يعرض recently viewed | إخفاء strip (configurable) |
| 20+ products | FIFO eviction |
| العميل على private browsing | يعمل في جلسة، يضيع عند الإغلاق |
| Product حُذف | إزالة من strip + localStorage |
| العميل أغلق strip | إخفاء للجلسة |
| Mobile viewport صغير | scroll horizontal smooth |
| Strip يحجب محتوى مهم | position قابل للضبط |

#### Mobile, Accessibility & Integration

- **Mobile:** Bottom strip، swipeable
- **A11y:** كل منتج focusable، keyboard arrows
- **Salla Integration:** Twilight body hooks (مؤكد)، theme detection

#### الجهد المقدر
صغير-متوسط: **3-4 أيام**

---

### 27.18 Module 52 — Smart Coupon Discovery (🟠 Phase 2)

#### الوصف
بحث coupon في cart + التقاط codes غير موجودة. العميل يقدر يبحث عن promo codes. يعرض valid codes إذا موجودة، يلتقط invalid searches لذكاء التاجر. يكشف demand لحملات promo.

#### User Flow

```
[العميل في cart]
     ↓
[يرى "هل لديك كود خصم؟" قسم expandable]
     ↓
[يكتب: "BLACKFRIDAY2024"]
     ↓
[النظام يفحص Coupons API]
     ↓
[CASE A: Valid → مُطبق + تأكيد]
[CASE B: Invalid → "هذا الكود غير صالح" + capture]
     ↓
[Dashboard: top searched-but-not-found codes]
     ↓
[Doctor: "customers يبحثون X، فكر في إنشاء هذا promo"]
```

#### المتطلبات الوظيفية

- **FR-52.1** Cart-side coupon search input (collapsible).
- **FR-52.2** Real-time validation via Salla Coupons API.
- **FR-52.3** Valid code → auto-apply، عرض savings.
- **FR-52.4** Invalid → friendly error + capture في `coupon_searches`.
- **FR-52.5** اقتراح coupons نشطة إذا invalid.
- **FR-52.6** Dashboard: "Top searched-but-not-found" + frequency.
- **FR-52.7** Doctor rule: لو نفس code 10+ مرات، اقترح إنشاءه.
- **FR-52.8** Rate limit: max 5 attempts per session.
- **FR-52.9** التقاط context: cart_total، products، source.
- **FR-52.10** Spam protection: فلتر bot patterns.

#### UX Requirements

**Coupon Search UI:**
- Collapsible "هل لديك كود خصم؟" في cart
- Single input + Apply button
- Inline error/success feedback
- اقتراح active coupons عند error

**التصميم البصري:**
- Subtle، لا يهيمن
- Success: أخضر + "وفّرت X ريال"
- Error: أحمر + "الكود غير صالح" + alternatives

#### Configuration

```typescript
interface CouponDiscoveryConfig {
  enabled: boolean;
  maxAttemptsPerSession: number;
  suggestActiveCouponsOnFail: boolean;
  captureSearchedCodes: boolean;
  doctorThreshold: number;
  cartUIPosition: 'top' | 'middle' | 'bottom';
}
```

#### Data Captured

```typescript
interface CouponSearch {
  id: string;
  merchant_id: string;
  searched_code: string;
  found: boolean;
  cart_total: number;
  cart_items_count: number;
  customer_id?: string;
  session_id: string;
  attempt_number: number;
  resulted_in_purchase: boolean;
  searched_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| 5+ محاولات | rate limit، "Too many attempts" |
| Code valid لكن منتهي | "Code expired on X" + alternatives |
| Code valid لكن min order لم يُحقق | "كود يحتاج طلب فوق X" |
| SQL injection | sanitize، log security |
| نفس code searched كثير | aggregate، flag للتاجر |
| Code valid لكن مُطبق | "Already applied" |
| Multiple codes في checkout | track each attempt |
| Influencer code never created | Doctor recommends |

#### Mobile, Accessibility & Integration

- **Mobile:** Input أكبر، Apply button mobile-friendly
- **A11y:** Input labeled، errors via ARIA live
- **Salla Integration:** Coupons API

#### الجهد المقدر
متوسط: **4-6 أيام**

---

### 27.19 Module 53 — Shipping Transparency Calculator (🟠 Phase 2)

#### الوصف
Pre-checkout shipping cost calculator على PDP و Cart. يقلل checkout abandonment من مفاجأة shipping cost. Auto-detect city من IP أو يسأل العميل. يعرض "add X SAR for free shipping" progress bar لتشجيع AOV.

#### User Flow

```
[العميل على PDP أو cart]
     ↓
[Smart Snippet يكشف city من IP (أو يسأل)]
     ↓
[يستدعي Salla Shipping API]
     ↓
[يعرض:
  - خيارات الشحن + الأسعار
  - Free shipping threshold
  - Progress bar: "أضف 23 ر.س للشحن المجاني"
]
     ↓
[العميل يضيف أكثر → progress bar يحدث]
     ↓
[يصل threshold → "🎉 شحن مجاني!"]
```

#### المتطلبات الوظيفية

- **FR-53.1** كشف city via IP geolocation.
- **FR-53.2** Fallback: اسأل العميل اختيار city.
- **FR-53.3** استدعاء Salla Shipping API لخيارات + أسعار.
- **FR-53.4** عرض الخيارات inline على PDP و cart.
- **FR-53.5** عرض "free shipping at X ر.س" badge.
- **FR-53.6** Progress bar يحدث مع cart total.
- **FR-53.7** "🎉 شحن مجاني!" celebration عند threshold.
- **FR-53.8** Cache shipping data per city لـ 24 ساعة.
- **FR-53.9** Doctor signal: shipping cost objection rate.
- **FR-53.10** A/B test: مع vs بدون calculator.

#### UX Requirements

**Widget:**
- Collapsible (expanded default)
- أيقونة truck/delivery
- City selector (dropdown مع auto-detect)
- Shipping options كـ cards

**Progress Bar:**
- Animated fill
- Colors: red → yellow → green
- Celebration عند threshold

#### Configuration

```typescript
interface ShippingCalculatorConfig {
  enabled: boolean;
  autoDetectCity: boolean;
  fallbackToManualSelect: boolean;
  showOnPages: ('pdp' | 'cart')[];
  freeShippingThreshold?: number;
  progressBarEnabled: boolean;
  cacheHours: number;
}
```

#### Data Captured

```typescript
interface ShippingCalculation {
  id: string;
  merchant_id: string;
  session_id: string;
  customer_id?: string;
  detected_city: string;
  manually_selected_city?: string;
  cart_total: number;
  cheapest_shipping_cost: number;
  free_shipping_threshold?: number;
  reached_free_threshold: boolean;
  resulted_in_purchase: boolean;
  shipping_method_chosen?: string;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| IP geolocation فشل | عرض manual selector فورًا |
| City بدون shipping | "Shipping unavailable" + alternatives |
| التاجر غير shipping rates | invalidate cache |
| العميل غير city mid-session | recalculate، update progress |
| Salla Shipping API down | message عام، إخفاء calculator |
| Free shipping threshold removed | إخفاء progress bar |
| Shipping دولي | configurable |
| VPN user | السماح بـ manual override |

#### Mobile, Accessibility & Integration

- **Mobile:** Collapsed default
- **A11y:** City selector accessible، progress bar مع label
- **Salla Integration:** Shipping API (⚠️ **يحتاج verification**)

#### الجهد المقدر
متوسط: **5-7 أيام**

---

### 27.20 Module 56 — Free Sample / Trial Request (🟠 Phase 2)

#### الوصف
Sample request workflow للمنتجات high-AOV (مثل عطور > 500 ر.س، skincare). يقلل purchase risk للمنتجات premium بالسماح بـ try-before-buy. منتجات مؤهلة قابلة للضبط. Sample ينشئ Salla order مع sample SKU + يتتبع sample-to-full-purchase conversion. يشمل operational workflow للتاجر.

#### User Flow

```
[العميل على PDP high-AOV (>500 SAR threshold)]
     ↓
[يرى "Try a sample first" CTA بجانب Add to Cart]
     ↓
[ينقر → sample request modal]
     ↓
[Modal:
  - معلومات المنتج
  - حجم/نوع العينة
  - نموذج الشحن
  - "Free with X SAR shipping" أو "Cost X SAR"
]
     ↓
[Submit → ينشئ Salla order مع sample SKU]
     ↓
[التاجر يكمّل الـ sample]
     ↓
[Follow-up: 7-14 يوم بعد، "هل أعجبتك؟ اشتري الكامل"]
     ↓
[Conversion: sample → full purchase]
```

#### المتطلبات الوظيفية

- **FR-56.1** كشف eligibility: products مع `sample_eligible` tag أو price > threshold.
- **FR-56.2** "Try a sample" CTA على eligible PDPs.
- **FR-56.3** Sample request modal: product، sample variant، shipping address.
- **FR-56.4** إنشاء Salla order مع parent_product_id + sample_sku.
- **FR-56.5** Sample fulfillment مسجل منفصل.
- **FR-56.6** Auto follow-up email/WhatsApp بعد 7-14 يوم.
- **FR-56.7** تتبع sample → full purchase (window 30 يوم).
- **FR-56.8** Dashboard: sample requests، fulfilled، conversion rate، revenue.
- **FR-56.9** إعدادات التاجر: أي منتجات مؤهلة، sample cost، max samples per customer.
- **FR-56.10** Customer profile flag: "Sample requestor".

#### UX Requirements

**Sample CTA على PDP:**
- Secondary CTA (لا ينافس "Add to Cart")
- "🧪 جربيها أولاً — عينة مجانية"
- Eligibility indicator

**Sample Request Modal:**
- إشارات ثقة: "ستصلك خلال X أيام"
- Address form واضح
- أسئلة اختيارية عن skin/preferences
- Submit + confirmation

**Follow-up:**
- دافئ: "كيف كانت تجربتك مع العينة؟"
- CTA: "اطلبي الحجم الكامل بـ X ر.س"
- Discount incentive

#### Configuration

```typescript
interface SampleRequestConfig {
  enabled: boolean;
  eligibilityRules: {
    priceThreshold: number;
    tagsRequired: string[];
  };
  sampleCost: number;
  maxSamplesPerCustomer: number;
  followUpDelayDays: number;
  followUpDiscountPercent: number;
  fulfillmentMethod: 'merchant_manual' | 'auto_order';
}
```

#### Data Captured

```typescript
interface SampleRequest {
  id: string;
  merchant_id: string;
  customer_id?: string;
  customer_phone_hash: string;
  parent_product_id: string;
  sample_sku?: string;
  shipping_address: object;
  sample_order_id?: string;
  fulfillment_status: 'pending' | 'fulfilled' | 'delivered';
  delivered_at?: timestamp;
  followup_sent_at?: timestamp;
  followup_clicked_at?: timestamp;
  full_purchase_order_id?: string;
  attribution_revenue?: number;
  created_at: timestamp;
}
```

#### Edge Cases

| الحالة | السلوك |
|---|---|
| العميل طلب sample نفس المنتج | "أنتِ بالفعل طلبتِ عينة لهذا المنتج" |
| Sample stock نفد | "Samples unavailable" + offer regular |
| العميل وصل max samples | عرض حد |
| العميل لا ينخرط مع follow-up | track silent failure، retry مرة |
| العميل اشترى الكامل قبل follow-up | skip follow-up، mark converted |
| Sample shipping cost عالي | configurable، قد يحتاج bundle |
| التاجر عطّل sample للمنتج | إخفاء CTA فورًا |
| Address validation فشل | error ودود، اقترح alternatives |

#### Mobile, Accessibility & Integration

- **Mobile:** Modal full-screen، نموذج مبسط
- **A11y:** Form fields labeled، address validation announced
- **Salla Integration:** Orders API لإنشاء sample order، custom SKU tagging

#### الجهد المقدر
كبير: **8-10 أيام** (يشمل operational workflow + follow-up automation)

---
### 27.21 ملخص الجهد الإجمالي (Expanded MVP)

| Phase | Modules | الجهد الإجمالي |
|---|---|---|
| **MVP Features 5-14** | 10 | 41-51 يوم |
| Phase 2 Roadmap (10 متبقية) | 10 | 51-69 يوم |
| **Total Roadmap** | 20 | **~92-120 يوم (~18-24 أسبوع)** |

**مع 2 devs (founder + junior):** ~20-22 أسبوع timeline MVP.

### 27.22 Critical Path Items

العناصر التي يمكن أن تعيق modules متعددة:
1. **تحقق Salla checkout customization** — يعيق Phase 2 Modules 37، 43، ربما 53.
2. **WhatsApp Business API setup** — يعيق MVP Features 13، 14، 10.
3. **توفر Salla customer.birthday field** — يؤثر على Feature 13.
4. **توفر Salla Shipping API** — يعيق Phase 2 Module 53.
5. **بنية session tracking** — يحتاج لـ Phase 2 Module 45.

### 27.23 المخاطر والتخفيف من Expanded MVP

| الخطر | التخفيف |
|---|---|
| Timeline يتجاوز 22 أسبوع | scope discipline صارم. حذف features 12-14 إذا في خطر. |
| Cash runway غير كافٍ لـ 6 شهور | جمع pre-seed أو تقليل burn |
| الجودة تتأثر من العرض | أسبوع QA إلزامي قبل كل feature launch |
| Feedback متأخر (لا MVP feedback حتى Month 5) | مقابلات عملاء مدفوعة شهريًا |
| Engineering bandwidth | hire junior dev بحلول Month 2 |
## التوقيع

| الدور | الاسم | التاريخ | الحالة |
|---|---|---|---|
| مالك المنتج | [المؤسس] | لاحقًا | معلّق |
| قائد الهندسة | لاحقًا | لاحقًا | معلّق |
| قائد التصميم | لاحقًا | لاحقًا | معلّق |
| مراجعة قانونية | لاحقًا | لاحقًا | معلّق |

---

**نهاية PRD — MVP (النسخة العربية)**

> **التحدي الأكبر:** الانضباط بنطاق الـ MVP. أي ميزة إضافية = -1 من الأربعة الأساسية.
> **النجاح:** معدل تقديم ≥3% + Trial-to-paid ≥15% + احتفاظ 30 يومًا ≥70%
> **الجدول:** 15 أسبوعًا من اليوم 1 إلى تسليم متجر تطبيقات سلة.
