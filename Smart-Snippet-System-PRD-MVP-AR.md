# Smart Snippet System — وثيقة متطلبات المنتج (MVP) — النسخة العربية

> **الإصدار:** 1.0
> **التاريخ:** 12 مايو 2026
> **الحالة:** مسودة — جاهزة لمراجعة الهندسة والتصميم
> **الجمهور:** فريق الهندسة + التصميم + المنتج
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
طبقة ذكاء النية للعملاء على متاجر سلة — تلتقط **لماذا** لم يشترِ الزائر، **ماذا** ينتظر، و**ما الذي** يجب إصلاحه على كل منتج.

### نطاق الـ MVP
**أربع ميزات:**
1. **Hesitation Capture Widget** (لماذا) — استبيانات نية المغادرة + وضوح المنتج
2. **Variant & Price Interest Capture** (ماذا ينتظر) — تنبيهات متعددة الأبعاد
3. **Intent Dashboard + Product Doctor Lite** (ما الذي يصلح) — Insights مجمعة + توصيات قائمة على قواعد
4. **Widget Analytics** (القياس) — مقاييس أداء لكل widget

### الإطلاق المستهدف
- **Beta مغلقة:** اليوم 60 (3-5 متاجر)
- **التسليم لسلة:** اليوم 90
- **الإطلاق العام:** اليوم 105

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

### ما هو داخل النطاق (ابنِ هذه الميزات الأربع)

| # | الميزة | الـ Modules المدمجة | الأولوية |
|---|---|---|---|
| 1 | Hesitation Capture Widget | M4 + M17 | P0 (نواة) |
| 2 | Variant & Price Interest Capture | M7 + M8 (variants/price/follow فقط، **بدون restock**) | P0 (نواة) |
| 3 | Intent Dashboard + Product Doctor Lite | M32 + M34 | P0 (نواة) |
| 4 | Widget Analytics | M35 | P0 (بنية تحتية) |

### ما هو خارج النطاق (مؤجل للمرحلة 1+)

| Module | السبب |
|---|---|
| M5 (Ask About Product) | تداخل مع أسئلة سلة الأصلية — يحتاج positioning مختلف |
| M8 بُعد Restock فقط | تداخل مع "أعلمني عند التوفر" الأصلية |
| M22 (Cart Rescue) | تداخل مع السلات المتروكة الأصلية |
| الباقي (Modules 1-3, 6, 9-16, 18-21, 23-31, 33, 36) | المرحلة 1+ |

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

## 27. Module 40 + خارطة Phase 1/2

هذا القسم يضيف specs صريحة لـ 20 module مذكورة في Analysis library لكنها غير مغطاة في MVP Features 1-4:
- **Module 40** (PDPL Consent Center) — متطلب MVP رسمي
- **8 Phase 1 modules** (الأشهر 4-9)
- **11 Phase 2 modules** (الأشهر 10-18)

الـ specs مكثفة (وصف + أهم FRs + تكامل سلة + Dependencies + الجهد). UX/edge cases الكاملة تُضاف عند بدء التطوير الفعلي لكل module.

---

### 27.1 Module 40 — PDPL Consent Management Center (🟢 MVP — متطلب قانوني)

**الوصف:** بوابة self-service مواجهة للعميل لإدارة بياناته وإشاراته وموافقاته. **مطلوب لامتثال PDPL** (مذكور بالفعل كمتطلب cross-cutting في Section 11.2، هذا القسم يجعله feature صريحة).

**المتطلبات الوظيفية:**
- FR-40.1: متاح عبر `/v1/public/consent/manage?token=<jwt>`. الـ token مدة 30 يومًا، قابل للتجديد.
- FR-40.2: عرض كل interest signals + submissions المرتبطة بـ phone hash العميل.
- FR-40.3: إلغاء بنقرة واحدة لكل إشارة (يضع `status='cancelled'`).
- FR-40.4: حذف bulk مع prompt تأكيد (cascade delete + audit log).
- FR-40.5: سحب الموافقة (يوقف الـ communications، يحتفظ بـ audit record).
- FR-40.6: تصدير البيانات (CSV/JSON).
- FR-40.7: تسجيل كل actions في `consent_records` table مع timestamp, IP, action type.
- FR-40.8: تأكيد بـ email بعد كل إجراء كبير (حذف، سحب).
- FR-40.9: عربي + إنجليزي (دعم RTL).

**تكامل سلة:** لا شيء (URL خاصة بنا).
**Dependencies:** database schema (`interest_signals`, `consent_records`) — موجود في MVP.
**الجهد:** متوسط (3-5 أيام).
**أسئلة مفتوحة:** هل نطلب phone OTP للحذف الكامل لمنع token-leak attacks؟

---

### 27.2 Phase 1 Modules (الأشهر 4-9)

كل modules Phase 1 تبني مباشرة على بنية بيانات MVP. مؤكدة تقنيًا، تداخل native منخفض.

#### Module 38 — Empty Search Capture (🟡 Phase 1)
**الوصف:** يلتقط استعلامات بحث العميل التي أرجعت لا نتائج. إشارة طلب مخزون مباشرة.
**أهم الـ FRs:**
- FR-38.1: كشف empty search state عبر `.s-search-no-results` CSS class أو DOM observation.
- FR-38.2: حقن نموذج التقاط: query معبأ + جوال اختياري + موافقة PDPL.
- FR-38.3: تخزين في `missed_searches` table مع تجميع frequency.
- FR-38.4: widget لوحة: "Top missed searches" مرتبة حسب العدد.

**تكامل سلة:** Twilight `<salla-search>` component customization *(مؤكد)*.
**Dependencies:** طبقة موافقة PDPL (MVP).
**الجهد:** صغير-متوسط (2-4 أيام).

#### Module 39 — First-Time vs Returning Recognition (🟡 Phase 1)
**الوصف:** ترحيب/widget مختلف للزوار الجدد vs العائدين، مع pre-tag للنية.
**أهم الـ FRs:**
- FR-39.1: كشف حالة الزائر عبر cookie + Salla customer login state.
- FR-39.2: First-time: اختيار نية بـ 3 خيارات (هدية / شخصي / تصفح).
- FR-39.3: Returning: عرض آخر منتج شوهد + recently viewed strip.
- FR-39.4: تخزين intent tag في `visitor_intents` table مرتبط بـ session.

**تكامل سلة:** Twilight SDK لـ customer state *(مؤكد)*.
**Dependencies:** لا شيء (مستقلة).
**الجهد:** متوسط (4-5 أيام).

#### Module 46 — Vertical Discovery Quiz (🟡 Phase 1)
**الوصف:** quiz قصيرة تبني customer preference profile (نوع البشرة، الستايل، عائلة العطر).
**أهم الـ FRs:**
- FR-46.1: Templates قابلة للضبط لكل vertical (beauty, fashion, perfumes).
- FR-46.2: 3-5 أسئلة، أقل من 60 ثانية للإكمال.
- FR-46.3: توليد `customer_profile` JSON مخزن في `customer_profiles` table.
- FR-46.4: تطبيق الـ profile على product filtering + recommendations.

**تكامل سلة:** Products API للفلترة.
**Dependencies:** Module 39 (First-Time recognition) كـ trigger.
**الجهد:** متوسط-كبير (5-7 أيام).

#### Module 48 — Recently Viewed Memory Strip (🟡 Phase 1 — تداخل جزئي)
**الوصف:** Sticky horizontal strip للمنتجات المشاهدة مؤخرًا + Dashboard tracking.
**أهم الـ FRs:**
- FR-48.1: تخزين آخر 20 منتج في localStorage لكل visitor.
- FR-48.2: عرض sticky strip على PDP/Cart مع horizontal scroll.
- FR-48.3: تتبع view-to-purchase conversion لكل منتج في `widget_events`.

**تكامل سلة:** Twilight body hooks *(مؤكد)*.
**Dependencies:** Module 35 (بنية Analytics).
**الجهد:** صغير-متوسط (3-4 أيام).
**ملاحظة:** بعض ثيمات سلة تعرض "recently viewed" natively. نخصص snippet لإضافة قيمة tracking، لا تكرار بصري.

#### Module 49 — Birthday/Anniversary Capture (🟡 Phase 1)
**الوصف:** التقاط تواريخ شخصية لحملات triggered.
**أهم الـ FRs:**
- FR-49.1: حقول النموذج: عيد ميلاد (DD/MM)، ذكرى (اختياري، DD/MM).
- FR-49.2: موافقة PDPL-compliant لتخزين التواريخ.
- FR-49.3: Cron يومي يفحص التواريخ، يطلق WhatsApp/Email 3 أيام قبل.
- FR-49.4: لوحة: "Birthdays this month" مع campaign launcher.

**تكامل سلة:** Customer fields *(تحقق من الدعم native)*.
**Dependencies:** Module 7 (مكونات نموذج Interest Capture).
**الجهد:** صغير (2-3 أيام).
**يحتاج تحقق:** هل Salla `customer` object يحتوي حقول birthday/anniversary natively.

#### Module 51 — Coming Soon / Pre-Launch Capture (🟡 Phase 1)
**الوصف:** التقاط اهتمام pre-launch للمنتجات غير المنشورة.
**أهم الـ FRs:**
- FR-51.1: كشف product status="hidden" أو tag مخصص "coming_soon".
- FR-51.2: استبدال PDP العادي بـ pre-launch teaser + email/phone capture.
- FR-51.3: تخصيص coupon "Early Bird discount" اختياري.
- FR-51.4: إشعار تلقائي لكل المشتركين عند تغيير status لـ "active".

**تكامل سلة:** Products API + status webhooks *(مؤكد)*.
**Dependencies:** Module 8 (بنية الإشعارات).
**الجهد:** متوسط (4-5 أيام).

#### Module 54 — Influencer Code Capture & Attribution (🟡 Phase 1)
**الوصف:** التقاط traffic من influencer-specific، تتبع revenue per-influencer.
**أهم الـ FRs:**
- FR-54.1: تحليل UTM params + URL slugs خاصة (`/?ref=sara_kn`).
- FR-54.2: عرض رسالة landing مخصصة باسم influencer.
- FR-54.3: تطبيق coupon code influencer تلقائيًا عند checkout.
- FR-54.4: لوحة: revenue per-influencer، AOV، معدل التحويل، CAC.

**تكامل سلة:** Coupons API للـ auto-apply *(مؤكد)*.
**Dependencies:** لا شيء.
**الجهد:** متوسط (4-6 أيام).

#### Module 55 — Cart Sharing & Save Link (🟡 Phase 1)
**الوصف:** توليد URL قابل للمشاركة للسلة على WhatsApp/Email مع dual reward.
**أهم الـ FRs:**
- FR-55.1: توليد JWT موقع يحتوي cart state.
- FR-55.2: URL عام `/cart/share/<token>` يعيد بناء السلة عند الزيارة.
- FR-55.3: تتبع conversions من shared carts مع referral attribution.
- FR-55.4: 10% خصم اختياري لكل من المشارك والمشتري عند الشراء.

**تكامل سلة:** Cart API لإعادة بناء الحالة.
**Dependencies:** Module 22 (بنية Cart من Phase 1).
**الجهد:** متوسط (4-5 أيام).

---

### 27.3 Phase 2 Modules (الأشهر 10-18)

Phase 2 modules تحتاج بيانات أعمق، تحقق تقني، أو positioning دقيق.

#### Module 37 — Checkout Hesitation Capture (🟠 Phase 2)
**الوصف:** التقاط أسباب abandonment على صفحة checkout بالذات.
**أهم الـ FRs:**
- FR-37.1: كشف exit intent على checkout (mouseleave / scroll-up / idle).
- FR-37.2: عرض اختيار سبب بـ 6 خيارات (شحن، دفع، أمان...).
- FR-37.3: التجميع في `checkout_hesitations` table منفصل عن PDP hesitations.
- FR-37.4: إطلاق Doctor rules مختلفة عن PDP hesitations.

**تكامل سلة:** Twilight checkout hooks (⚠️ **يحتاج تحقق**).
**Dependencies:** Feature 1 (Hesitation Capture) للمكونات المشتركة.
**الجهد:** متوسط-كبير (5-7 أيام، يعتمد على Salla checkout customization).

#### Module 41 — Live Stock Urgency Signal (🟠 Phase 2 — تداخل جزئي)
**الوصف:** عداد stock شفاف + social proof ("X متبقي + Y عميل يشاهد").
**أهم الـ FRs:**
- FR-41.1: الاشتراك في webhook `product.quantity.low` *(مؤكد)*.
- FR-41.2: عرض badge فقط عند stock ≤ threshold قابل للضبط (افتراضي 5).
- FR-41.3: تعزيز بـ viewing count من analytics events.
- FR-41.4: تخطي العرض إذا theme سلة يعرض stock count (theme detection).

**تكامل سلة:** Webhook + Twilight PDP hooks *(مؤكد)*.
**Dependencies:** Webhook handlers من MVP.
**الجهد:** صغير-متوسط (3-5 أيام).

#### Module 42 — Mobile One-Tap Interest (🟠 Phase 2 — تداخل مع Salla Wishlist)
**الوصف:** التقاط اهتمام anonymous على الجوال فقط بدون نموذج. مكمّل (لا بديل) لـ Salla Wishlist.
**أهم الـ FRs:**
- FR-42.1: عرض sticky heart icon على PDP موبايل فقط.
- FR-42.2: حفظ product ID في cookie + إرسال anonymous event.
- FR-42.3: عند return visit، استعادة من cookie مع banner تذكير.
- FR-42.4: تجميع "most anonymous-saved products" لـ Doctor.

**تكامل سلة:** Twilight SDK + mobile detection.
**Dependencies:** بنية Analytics (MVP).
**الجهد:** صغير (2-3 أيام).
**Kill Criterion:** إذا incremental volume vs Salla Wishlist native < 2x في pilot، حذف من roadmap.

#### Module 43 — Pre-Checkout Confidence Booster (🟠 Phase 2)
**الوصف:** Trust signals + WhatsApp CTA على checkout فوق "Place Order".
**أهم الـ FRs:**
- FR-43.1: حقن block ثقة قابل للضبط (شحن، استرداد، أمان دفع).
- FR-43.2: زر دعم WhatsApp اختياري لحظة أخيرة.
- FR-43.3: تتبع impression/click-to-WhatsApp conversion.

**تكامل سلة:** Twilight checkout hooks (⚠️ **يحتاج تحقق**).
**Dependencies:** نفس checkout verification لـ Module 37.
**الجهد:** صغير (2-3 أيام، يعتمد على hooks).

#### Module 44 — Smart Reorder Timing (🟠 Phase 2)
**الوصف:** تذكيرات reorder auto-triggered بناءً على timing فئة المنتج.
**أهم الـ FRs:**
- FR-44.1: تعريف `reorder_category_timings` config table (مثال: serum=60d، perfume=90d).
- FR-44.2: Cron يومي يفحص الـ completed orders، يحدد reorders due.
- FR-44.3: إرسال WhatsApp reminder مع one-click reorder link.
- FR-44.4: تتبع reorder rate per category للضبط.

**تكامل سلة:** Orders API + WhatsApp BSP.
**Dependencies:** بنية WhatsApp من MVP.
**الجهد:** متوسط (5-7 أيام).

#### Module 45 — Comparison Shopping Detector (🟠 Phase 2)
**الوصف:** كشف العملاء الذين يشاهدون 3+ منتجات مشابهة، التدخل بـ help.
**أهم الـ FRs:**
- FR-45.1: تتبع PDP visits لكل session real-time (server-side).
- FR-45.2: عند 3+ PDPs من نفس category خلال 10 دقائق، إطلاق widget.
- FR-45.3: Widget يسأل: "ما الذي يصعّب القرار؟" بـ 5 خيارات.
- FR-45.4: عرض insights في Doctor لـ category-level optimization.

**تكامل سلة:** Products API لمطابقة الفئة.
**Dependencies:** بنية session tracking (Module 35 Analytics).
**الجهد:** متوسط-كبير (6-8 أيام).

#### Module 47 — Customer Bundle Builder (🟠 Phase 2)
**الوصف:** العميل يختار 3+ منتجات لتكوين bundle مخصص مع auto-discount.
**أهم الـ FRs:**
- FR-47.1: قواعد قابلة للضبط: min/max products، فئات مؤهلة، tiers خصم.
- FR-47.2: Bundle UI مع selected items، dynamic pricing، "complete bundle" CTA.
- FR-47.3: تطبيق discount كـ Salla coupon عند checkout.
- FR-47.4: لوحة: "Top customer-built combinations" لإعلام official bundles.

**تكامل سلة:** Coupons API + Products API.
**Dependencies:** لا شيء.
**الجهد:** كبير (8-10 أيام).

#### Module 50 — Out-of-Stock Substitute Engine (🟠 Phase 2)
**الوصف:** اقتراح بدائل فورًا عند OOS + التقاط التفضيل.
**أهم الـ FRs:**
- FR-50.1: كشف OOS state عبر stock = 0 check.
- FR-50.2: استعلام Products API للمنتجات المشابهة (فئة، سعر، attributes).
- FR-50.3: عرض 3 بدائل + خيار "wait for original".
- FR-50.4: تتبع substitute conversion rate مقابل wait rate.

**تكامل سلة:** Products API للـ similarity queries.
**Dependencies:** لا شيء.
**الجهد:** متوسط (5-6 أيام).

#### Module 52 — Smart Coupon Discovery (🟠 Phase 2)
**الوصف:** بحث coupon مواجه للعميل + التقاط codes غير موجودة المبحوثة.
**أهم الـ FRs:**
- FR-52.1: شريط بحث في cart/checkout: "تبحث عن coupon؟"
- FR-52.2: اقتراح coupons متاحة مؤهلة بناءً على cart contents.
- FR-52.3: التقاط كل code names المبحوثة (حتى غير الموجودة) في `coupon_searches` table.
- FR-52.4: لوحة: "Codes مبحوثة غير موجودة في النظام" → يكشف ghost influencer codes.

**تكامل سلة:** Coupons API.
**Dependencies:** لا شيء.
**الجهد:** متوسط (4-6 أيام).

#### Module 53 — Shipping Transparency Calculator (🟠 Phase 2)
**الوصف:** حاسبة تكلفة شحن قبل checkout على PDP/Cart.
**أهم الـ FRs:**
- FR-53.1: City/region dropdown مع auto-detect من IP.
- FR-53.2: عرض خيارات الشحن + التكلفة real-time.
- FR-53.3: "أضف X ر.س لشحن مجاني" progress bar.
- FR-53.4: تتبع shipping objection rate مقابل cart abandonment الأصلي.

**تكامل سلة:** Shipping API (⚠️ **تحقق من التوفر**).
**Dependencies:** لا شيء.
**الجهد:** متوسط (5-7 أيام، يعتمد على API).

#### Module 56 — Free Sample / Trial Request (🟠 Phase 2)
**الوصف:** workflow طلب sample للمنتجات high-AOV (>500 ر.س).
**أهم الـ FRs:**
- FR-56.1: كشف منتجات مؤهلة (price threshold + sample-eligible tag).
- FR-56.2: نموذج طلب sample مع address + phone.
- FR-56.3: إنشاء Salla order مع sample SKU (custom flow).
- FR-56.4: تتبع sample-to-purchase conversion + revenue attribution.

**تكامل سلة:** Orders API.
**Dependencies:** بنية إدارة الطلبات.
**الجهد:** كبير (8-10 أيام، يشمل operational workflow).

---

### 27.4 ملخص الجهد الإجمالي

| المرحلة | Modules | الجهد الإجمالي |
|---|---|---|
| MVP (Module 40 صريح) | 1 | 3-5 أيام |
| Phase 1 (38, 39, 46, 48, 49, 51, 54, 55) | 8 | 25-35 يوم |
| Phase 2 (37, 41, 42, 43, 44, 45, 47, 50, 52, 53, 56) | 11 | 55-75 يوم |
| **الإجمالي** | **20** | **~80-110 يوم تطوير (~16-22 أسبوع)** |

### 27.5 Critical Path Items

هذه يمكن أن تعيق modules متعددة:
1. **تحقق Salla checkout customization** — يعيق 37, 43 (وربما 53).
2. **إعداد WhatsApp Business API** — يعيق إشعارات 44, 49, 51.
3. **توفر Salla customer fields** — يعيق 49 (Birthday).
4. **بنية session tracking** — يعيق 45 (Comparison Detector).

### 27.6 ملاحظات Out of Scope للـ Roadmap

- الـ modules المذكورة **ليست** جزءًا من MVP scope. بناؤها مبكرًا يعرّض timeline MVP للخطر.
- كل module يجب أن يجتاز MVP kill criteria قبل بدء تطويره.
- إعادة ترتيب الـ roadmap كل ربع بناءً على feedback المرشانت الحقيقي.

---

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
