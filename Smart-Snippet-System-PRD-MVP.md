# Smart Snippet System — Product Requirements Document (MVP)

> **Version:** 1.0
> **Date:** 2026-05-12
> **Status:** Draft — Ready for Engineering & Design Review
> **Audience:** Engineering + Design + Product
> **Related Docs:**
> - [Smart-Snippet-System-Analysis.md](./Smart-Snippet-System-Analysis.md)
> - [Competitive-Landscape-Analysis.md](./Competitive-Landscape-Analysis.md)

---

## جدول المحتويات

1. [Executive Summary](#1-executive-summary)
2. [Background & Context](#2-background--context)
3. [Goals & Non-Goals](#3-goals--non-goals)
4. [Personas](#4-personas)
5. [User Stories](#5-user-stories)
6. [MVP Scope](#6-mvp-scope)
7. [Feature 1 — Hesitation Capture Widget](#7-feature-1--hesitation-capture-widget)
8. [Feature 2 — Variant & Price Interest Capture](#8-feature-2--variant--price-interest-capture)
9. [Feature 3 — Intent Dashboard + Product Doctor](#9-feature-3--intent-dashboard--product-doctor)
10. [Feature 4 — Widget Analytics](#10-feature-4--widget-analytics)
11. [Cross-Cutting Requirements](#11-cross-cutting-requirements)
12. [Technical Architecture](#12-technical-architecture)
13. [Salla Integration Specifications](#13-salla-integration-specifications)
14. [Data Model](#14-data-model)
15. [API Specifications](#15-api-specifications)
16. [UX / UI Requirements](#16-ux--ui-requirements)
17. [Onboarding Flow](#17-onboarding-flow)
18. [Notifications](#18-notifications)
19. [Analytics & Instrumentation](#19-analytics--instrumentation)
20. [Success Metrics](#20-success-metrics)
21. [Launch Criteria](#21-launch-criteria)
22. [Out of Scope](#22-out-of-scope)
23. [Open Questions](#23-open-questions)
24. [Risks & Mitigations](#24-risks--mitigations)
25. [Timeline & Milestones](#25-timeline--milestones)
26. [Appendix](#26-appendix)

---

## 1. Executive Summary

### Vision
A Customer Intent Intelligence layer for Salla stores — captures *why* visitors don't buy, *what* they're waiting for, and *what* to fix on each product.

### MVP Scope
**4 Features:**
1. **Hesitation Capture Widget** (Why) — Exit intent + Product Clarity surveys
2. **Variant & Price Interest Capture** (Wait) — Multi-dimensional alerts
3. **Intent Dashboard + Product Doctor Lite** (Fix) — Aggregated insights + rule-based recommendations
4. **Widget Analytics** (Measure) — Per-widget performance metrics

### Target Launch
- **Beta:** Day 60 (closed, 3-5 stores)
- **App Store Submission:** Day 90
- **Public Launch:** Day 105

### Target Market (MVP)
Saudi Arabian Salla stores in Beauty, Perfumes, Fashion. 2,000-30,000 monthly visits. 50-500 SKUs.

### Pricing
99 / 199 / 349 SAR per month. 14-day free trial, no credit card.

---

## 2. Background & Context

### Problem Statement
Salla merchants currently know **what** happened in their stores (orders, sales, reviews). They don't know **why** visitors didn't buy on a per-product basis. Existing tools either show display popups (PopupSnap), analyze post-purchase data (SmartInsight, Smart Analytics), or send restock alerts (Salla native). No tool captures pre-purchase intent and turns it into actionable per-product recommendations.

### Market Gap
- **0 competitors** in Salla App Store offering Customer Intent capture
- **0 competitors** offering Product Doctor / Pre-purchase diagnosis
- Salla Smart Analytics is post-purchase only (verified)
- SmartInsight is post-purchase analytics chat ($184 USD/month) — different positioning
- Shopify has Simplify Exit Intent Survey ($4.99) but no Salla integration

### Why Now
- Rising ad costs in Gulf market = merchants need to reduce conversion waste
- Salla merchant base growing rapidly
- SmartInsight at 693 SAR proves WTP for intelligence tools
- 6-12 month window before category gets crowded

---

## 3. Goals & Non-Goals

### MVP Goals (3 main)

**G1 — Prove Behavioral Hypothesis**
Verify that Salla store visitors will respond to hesitation surveys at ≥3% submission rate.

**G2 — Prove Willingness to Pay**
Validate that merchants will pay 99-349 SAR/month for pre-purchase intent insights.

**G3 — Establish Defensible Positioning**
Build Salla App Store presence in Customer Intent category as first-mover.

### Success Targets (90 days post-launch)
- 50+ stores active (free trial + paid)
- 10+ paid merchants
- ≥3% submission rate on Hesitation widget
- ≥70% 30-day retention
- 3 published case studies

### Explicit Non-Goals (Out of MVP)
- ❌ AI-powered recommendations (rule-based only in MVP — AI in Phase 3)
- ❌ Popup builder / general marketing tool functionality
- ❌ Helpdesk / FAQ management
- ❌ Wishlist standalone feature
- ❌ Loyalty / membership programs
- ❌ Post-purchase flows (NPS, reviews, etc.)
- ❌ Multi-store management (single store per account)
- ❌ White-label / agency features
- ❌ Mobile app (web dashboard only)
- ❌ Direct SMS sending (use Salla's existing channels)
- ❌ Email marketing automation (basic digest only)
- ❌ A/B testing engine
- ❌ Conversion attribution / revenue tracking (Phase 2)
- ❌ Multi-language beyond Arabic + English

---

## 4. Personas

### Primary: The Salla Merchant

**Name:** Sara Al-Otaibi
**Age:** 32
**Role:** Founder / Owner of beauty store on Salla
**Store stats:**
- 15,000 monthly visits
- 200 SKUs
- ~3% conversion rate
- 25,000 SAR/month ad spend (Meta + TikTok)

**Goals:**
- Increase conversion without raising ad budget
- Understand why visitors don't buy
- Make better inventory decisions (which colors/sizes to reorder)
- Reduce dependence on agency/consultant

**Frustrations:**
- Salla reports show numbers but not reasons
- WhatsApp messages are unorganized
- Doesn't know which products need attention
- Marketing dashboards are intimidating

**Tech Literacy:** Medium. Can install apps, use Salla dashboard, configure basic settings. Doesn't write code or use complex analytics tools.

**Quote:** *"عندي 200 منتج، ما عندي وقت أحلل كل واحد. خليني أعرف اللي يحتاج اهتمام."*

**Daily Workflow Today:**
- 9:00 AM: Check Salla dashboard, orders count
- 11:00 AM: Reply to WhatsApp messages
- 2:00 PM: Update product listings
- 5:00 PM: Review ad performance

**Where Smart Snippet Fits:**
9:30 AM — Opens Smart Snippet dashboard, reads weekly digest, applies 2 Doctor recommendations.

### Secondary: The End Customer

**Name:** Fatima
**Age:** 27
**Behavior:** Browses Salla stores on mobile (85% of sessions), often during evening hours.

**Buying Pattern:**
- Visits 3-5 stores per shopping session
- Adds to cart 40% of the time
- Completes checkout 15% of the time
- Reasons for not buying: price comparison, sizing uncertainty, waiting for sale

**Where Smart Snippet Fits:**
After 60 seconds on a product, scrolling without adding to cart, a non-intrusive question appears: "شو ناقص في هذه الصفحة؟"

She taps "دليل المقاسات" and submits in 5 seconds. The merchant gets the signal.

---

## 5. User Stories

### Merchant Stories

**M1.** As a Salla merchant, I want to install Smart Snippet System from the Salla App Store in one click so I can start collecting intent data without technical setup.

**M2.** As a Salla merchant, I want a guided 5-minute onboarding that activates my first widget so I can see value within 24 hours.

**M3.** As a Salla merchant, I want to see why visitors abandoned my top 5 products this week so I can prioritize fixes.

**M4.** As a Salla merchant, I want Product Doctor to suggest specific actions (not just data) so I know what to do without an analyst.

**M5.** As a Salla merchant, I want a weekly email summary so I don't need to log in daily.

**M6.** As a Salla merchant, I want to see which variants (colors/sizes) customers want most so I can make reorder decisions.

**M7.** As a Salla merchant, I want to customize hesitation reasons in Arabic and English so they match my store vocabulary.

**M8.** As a Salla merchant, I want my customers to be able to set price alerts so I capture price-sensitive demand.

**M9.** As a Salla merchant, I want a snippet analytics tab to verify widgets are performing (≥3% submission rate).

**M10.** As a Salla merchant, I want a free 14-day trial without credit card so I can test risk-free.

### Customer Stories

**C1.** As a Salla store visitor, I want to give quick feedback (one tap) about why I'm not buying so I help the merchant without filling forms.

**C2.** As a visitor interested in a product but not ready to buy, I want to set a price alert so I'm notified when it drops.

**C3.** As a visitor where my size/color isn't available, I want to register interest so I'm notified when restocked.

**C4.** As a visitor, I want to know my data is protected (PDPL) and I can withdraw consent any time.

**C5.** As a mobile visitor, I want widgets that don't interrupt my browsing experience.

---

## 6. MVP Scope

### What's In (Build These 4 Features)

| # | Feature | Modules Combined | Priority |
|---|---|---|---|
| 1 | Hesitation Capture Widget | M4 + M17 | P0 (Core) |
| 2 | Variant & Price Interest Capture | M7 + M8 (variants/price/follow only, **not restock**) | P0 (Core) |
| 3 | Intent Dashboard + Product Doctor Lite | M32 + M34 | P0 (Core) |
| 4 | Widget Analytics | M35 | P0 (Infrastructure) |

### What's Out (Defer to Phase 1+)

| Module | Why Out |
|---|---|
| M5 (Ask About Product) | Overlap with Salla Q&A native — needs different positioning |
| M8 Restock-only dimension | Overlap with "أعلمني عند التوفر" native |
| M22 (Cart Rescue) | Overlap with Salla abandoned cart native |
| Everything else (Modules 1-3, 6, 9-16, 18-21, 23-31, 33, 36) | Phase 1+ |

---

## 7. Feature 1 — Hesitation Capture Widget

### 7.1 Description
A non-intrusive widget that asks visitors why they're not converting, captures structured responses, and aggregates them into merchant insights.

**Two trigger modes (configurable per merchant):**
- **Mode A: Exit Intent** — Shows when visitor signals intent to leave PDP or Cart
- **Mode B: Product Clarity** — Shows after scroll without add-to-cart on PDP

### 7.2 User Flow

```
[Customer visits PDP]
      ↓
[Browses 30+ seconds, no add to cart]
      ↓
[Trigger fires]
      ├── Desktop: mouseleave event toward top
      └── Mobile: scroll-up direction + idle 5s
      ↓
[Widget appears as modal/sheet]
      ↓
[Customer taps one option] → Submit
              OR
[Customer types in "Other"] → Submit
              OR
[Customer dismisses] → Track dismissal event
      ↓
[Thank you message: 2 seconds]
      ↓
[Widget closes]
```

### 7.3 Functional Requirements

**FR-1.1** Widget MUST render on Product Detail Page (PDP) and Cart pages only (configurable per merchant).

**FR-1.2** Widget MUST support two trigger modes (exit intent / clarity) configurable independently per page type.

**FR-1.3** Widget MUST NOT trigger more than **once per session** per page type (deduplication via sessionStorage).

**FR-1.4** Widget MUST NOT trigger for customers who have already submitted in last 30 days (cookie or customer-id based).

**FR-1.5** Widget MUST display 6 default reason options + 1 free text option, all configurable per merchant.

**FR-1.6** Widget MUST submit response to backend within 200ms (optimistic UI: show "thank you" immediately on tap).

**FR-1.7** Widget MUST capture metadata: product_id, page_url, session_id, customer_id (if logged in), timestamp, device_type, referrer, UTM params.

**FR-1.8** Widget MUST be dismissible via X button and ESC key (desktop).

**FR-1.9** Widget MUST NOT block the underlying page (no full-screen overlay on mobile — use bottom sheet instead).

**FR-1.10** Widget MUST support Arabic and English with automatic detection from Salla store locale.

**FR-1.11** Widget MUST collect PDPL-compliant consent if any PII is requested (in Hesitation widget MVP, no PII = no consent needed unless merchant adds optional contact field).

**FR-1.12** Free text input MUST be limited to 500 characters and sanitized server-side.

### 7.4 UX Requirements

**Visual Design:**
- Minimal, non-aggressive (NOT popup-styled)
- Inherits Salla theme colors via Twilight design tokens where possible
- Rounded corners (8-12px)
- Subtle drop shadow
- No bright colors / urgency cues

**Animation:**
- Slide-up from bottom on mobile (300ms ease-out)
- Fade-in on desktop (200ms)
- Slide-down dismiss

**Accessibility:**
- ARIA labels on all interactive elements
- Keyboard navigable (Tab through options, Enter to select)
- Focus trap when open
- Screen reader announcements (`aria-live="polite"` for thank you message)
- Color contrast WCAG AA minimum

**Responsive:**
- Desktop: Centered modal max-width 480px
- Tablet: Modal with side margins
- Mobile: Bottom sheet, full width

### 7.5 Configuration Options (Per Merchant)

```typescript
interface HesitationWidgetConfig {
  enabled: boolean;
  triggers: {
    exitIntent: {
      enabled: boolean;
      pages: ('pdp' | 'cart')[];
      minTimeOnPage: number; // seconds, default 30
    };
    productClarity: {
      enabled: boolean;
      scrollThreshold: number; // %, default 50
      idleTime: number; // seconds, default 60
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
  showRewardCoupon: boolean; // optional incentive
  couponCode?: string; // if showRewardCoupon
}
```

**Default Reasons (Beauty/Perfumes vertical):**
1. السعر مرتفع / Price too high
2. الشحن غير واضح / Unclear shipping
3. لست متأكد من المقاس/الحجم / Unsure about size
4. محتار بين منتجات / Comparing products
5. محتاج معلومات أكثر / Need more info
6. فقط أتصفح / Just browsing

### 7.6 Trigger Logic

**Exit Intent — Desktop:**
```javascript
// Pseudo-code
document.addEventListener('mouseleave', (e) => {
  if (e.clientY < 20 && !triggered) {
    triggered = true;
    showWidget();
  }
});
```

**Exit Intent — Mobile (alternative):**
```javascript
// Idle + scroll-up detection
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
      showWidget(); // backup: idle 30s
    }
  }, 30000);
});
```

**Product Clarity (scroll-based):**
```javascript
// Fires after scrolling past 50% + 60s on page
const scrollListener = () => {
  if (scrollPercent() > 50 && timeOnPage > 60 && !triggered) {
    triggered = true;
    showWidget();
  }
};
```

### 7.7 Data Captured

```typescript
interface HesitationSubmission {
  id: string; // UUID
  merchant_id: string;
  widget_id: string;
  trigger_mode: 'exit_intent' | 'product_clarity';
  reason_id?: string; // if predefined
  reason_label?: string; // computed at submission time
  free_text?: string; // sanitized
  product_id: string;
  product_handle: string;
  product_price: number;
  page_url: string;
  page_type: 'pdp' | 'cart';
  customer_id?: string; // if logged in to Salla
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
  ip_country?: string; // for analytics, not stored as PII
}
```

### 7.8 Edge Cases

| Edge Case | Behavior |
|---|---|
| Customer already submitted today | Don't show widget. Track skip in analytics. |
| Page has no product data (404, custom) | Don't render widget. |
| Customer scrolling fast (>10 events/s) | Throttle to avoid CPU spike. |
| Multiple PDPs in single session | Each PDP can trigger independently (max 3 per session). |
| Customer with JavaScript disabled | Widget doesn't render. Graceful degradation. |
| Salla theme overrides body styles | Widget uses Shadow DOM to isolate styling. |
| Slow network (3G) | Submission queues to localStorage, retries on next page load. |
| Submission fails (500 error) | Show "تم الاستلام" anyway (optimistic), retry in background up to 3 times. |

### 7.9 Mobile Considerations
- Bottom sheet instead of modal
- Touch-friendly buttons (44px min height)
- Keyboard-aware for free text (scroll to keep input visible)
- Swipe-down to dismiss
- No exit intent via mouseleave (use scroll-up + idle instead)

### 7.10 Accessibility
- All buttons have `role="button"` and accessible labels
- Modal has `role="dialog"` + `aria-modal="true"`
- Focus moves to first option on open
- Focus returns to trigger element on close
- Color contrast minimum 4.5:1 for text

---

## 8. Feature 2 — Variant & Price Interest Capture

### 8.1 Description
Captures latent interest from visitors who don't buy due to price, missing variant (color/size), or wanting to follow updates. Aggregates into Multi-Dimensional Interest Graph.

### 8.2 User Flow

```
[Customer on PDP]
      ↓
[Sees "نبهني" button next to Add to Cart]
      ↓
[Taps button]
      ↓
[Modal shows interest options]
      ↓
[Customer selects: price drop / variant / follow]
      ↓
[Enters phone number (Saudi format)]
      ↓
[PDPL consent checkbox (unchecked by default)]
      ↓
[Submit] → Confirmation
      ↓
[Customer receives WhatsApp/SMS when trigger fires]
```

### 8.3 Functional Requirements

**FR-2.1** "نبهني" button MUST render on PDP, positioned near Add to Cart button.

**FR-2.2** System MUST support 4 interest types: target_price, variant_color, variant_size, follow_product.

**FR-2.3** System MUST support follow_category and follow_brand (toggleable, off by default in MVP).

**FR-2.4** Customer MUST enter Saudi/Gulf phone format (validation: +966, +971, +965, +973, +968, +974).

**FR-2.5** Customer MUST explicitly check PDPL consent checkbox (unchecked default).

**FR-2.6** System MUST NOT send notifications until consent timestamp is stored.

**FR-2.7** When target_price condition met (via `product.price.updated` webhook), system MUST queue notification to customer.

**FR-2.8** When variant restock condition met (via `product.updated` webhook), system MUST queue notification.

**FR-2.9** Notifications MUST be sent via WhatsApp Business API (primary) with SMS fallback.

**FR-2.10** Each customer MUST be able to view and delete their interest signals via a public consent management URL.

**FR-2.11** Variant detection MUST work with Salla product options (color, size, etc.) — handle stores with custom options.

**FR-2.12** System MUST deduplicate interest signals (same customer + same product + same condition = 1 record).

### 8.4 UX Requirements

**Button Style:**
- Secondary button (not primary — doesn't compete with Add to Cart)
- Icon: 🔔 or bell SVG
- Text: "نبهني" / "Notify me"
- Position: below or beside Add to Cart

**Modal Style:**
- Slide-up bottom sheet on mobile
- Centered modal on desktop (max-width 420px)
- Clear sections: choose interest → phone → consent

**Trust Signals in Modal:**
- "🔒 بياناتك محمية وفق نظام PDPL"
- "✋ يمكنك إلغاء التنبيهات في أي وقت"

### 8.5 Configuration Options

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
    followCategory: boolean; // off by default
    followBrand: boolean; // off by default
  };
  notificationChannels: {
    whatsapp: boolean; // requires merchant WA Business setup
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

### 8.6 Data Captured

```typescript
interface InterestSignal {
  id: string;
  merchant_id: string;
  customer_phone: string; // hashed in storage, last 4 visible
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
  expires_at: timestamp; // default: 90 days
  created_at: timestamp;
}
```

### 8.7 Edge Cases

| Edge Case | Behavior |
|---|---|
| Phone already registered for this product | Update existing record, don't create duplicate |
| Customer enters non-Saudi/Gulf phone | Reject with clear error message |
| Phone validation: invalid format | Inline error, don't submit |
| Consent unchecked | Submit button disabled |
| Target price ≤ current price | Show warning: "السعر الحالي أقل من الذي حددته" |
| Variant doesn't exist anymore | Notify customer that variant was discontinued |
| Customer hits delete endpoint | Cascade delete all their signals for this merchant |
| Webhook arrives after customer cancelled | Skip notification |
| Notification fails (WA blocked) | Fallback to SMS, then email |

### 8.8 Integration with Salla Webhooks

```javascript
// Pseudo-code for backend webhook handler
on('product.price.updated', async (event) => {
  const { product_id, new_price, old_price } = event.data;
  
  if (new_price >= old_price) return; // only on price drops
  
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
  // Check variant availability changes
  // Match against variant_color and variant_size signals
});

on('product.quantity.low', async (event) => {
  // Note: restock not part of MVP (Salla native handles)
  // But low quantity could trigger urgency signals later
});
```

### 8.9 Mobile Considerations
- Phone input: numeric keyboard
- Country code dropdown shows flag
- Submit button: full width on mobile

### 8.10 Accessibility
- Form labels associated with inputs (htmlFor)
- Error messages announced via `aria-live`
- Consent checkbox: clear label, large tap target

---

## 9. Feature 3 — Intent Dashboard + Product Doctor

### 9.1 Description
Merchant-facing dashboard that aggregates hesitation submissions and interest signals into actionable insights, with a rule-based Product Doctor that recommends specific fixes per product.

### 9.2 Dashboard Sections

**Section A: Top Stats (Hero)**
```
This Week:
- Hesitation Submissions: 142 (↑18% vs last week)
- Interest Signals: 87 (↑22%)
- Active Widgets: 4 / 5
- Submission Rate: 3.1% ✅
```

**Section B: Top 3 Hesitation Reasons**
Bar chart with %, raw count. Filter: This Week / Last 30 Days / All Time.

**Section C: Products Needing Attention**
Table sorted by total intent signals (hesitation + interest). Click row → product detail view.

```
Product                    Issues  Severity
─────────────────────────────────────────────
Vitamin C Serum             15     🔴 High
Black Maxi Dress             12     🟡 Medium
Oud Royal 100ml               9     🟡 Medium
Niacinamide Serum             7     🟢 Low
```

**Section D: Variant Heatmap**
Shows most requested variants (colors/sizes) across all products.

**Section E: Doctor Recommendations**
Card list of active recommendations. Each card has Apply button.

### 9.3 Doctor Rules (5 Rules MVP)

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

### 9.4 Recommendations Engine

**Pipeline:**
1. **Daily Cron Job** runs at 4 AM (Saudi time)
2. For each active merchant, computes per-product signals from last 7 days
3. Evaluates each rule against each product's signals
4. Generates new Recommendation records (status: `pending`)
5. Deduplicates against existing pending/applied recommendations (don't re-recommend the same thing within 7 days)
6. Sends weekly digest email Monday 9 AM

**Recommendation Lifecycle:**
- `pending` → merchant sees in dashboard
- `applied` → merchant clicked Apply
- `dismissed` → merchant clicked Dismiss
- `expired` → 14 days without action

**Apply Actions (MVP):**
- `create_snippet`: Opens snippet creation wizard with template pre-filled
- `reorder_inventory`: Exports CSV with suggested variant + quantity
- `create_bundle`: Opens Salla bundle creation in new tab (link to Salla admin)
- `add_content`: Shows checklist of suggested content additions

### 9.5 Weekly Email Digest

**Send Time:** Monday 9 AM Saudi time
**Subject:** "📊 ملخص أسبوع متجرك — 3 توصيات جاهزة"

**Content Template:**
```
السلام عليكم [Merchant Name],

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

### 9.6 Functional Requirements

**FR-3.1** Dashboard MUST load in <2 seconds on 3G connection (target <500ms on 4G).

**FR-3.2** All metrics MUST refresh every 5 minutes (or on-demand via refresh button).

**FR-3.3** Dashboard MUST support date range filtering: 7d, 30d, 90d, all-time.

**FR-3.4** Doctor Recommendations MUST NOT show same recommendation for same product more than once every 7 days (unless threshold doubles).

**FR-3.5** Apply action MUST be one-click where possible.

**FR-3.6** All numbers MUST be clickable (drill down to source data).

**FR-3.7** Weekly digest MUST send to merchant's primary email (from Salla store profile).

**FR-3.8** Dashboard MUST be mobile-responsive (merchant might check on phone).

### 9.7 UX Requirements

**Information Hierarchy:**
1. What's urgent (red flags) — top of page
2. What's actionable (Doctor recommendations) — next
3. What's interesting (trends, charts) — bottom

**Visual Design:**
- Clean, data-dense (NOT marketing-styled)
- Use color sparingly: red/yellow/green for severity
- Bold numbers, lighter labels
- Action buttons clearly visible

**Empty States:**
- Day 1: "👋 مرحبًا — ابنِ widget أول وستظهر بياناتك خلال 24 ساعة"
- Less than 10 submissions: "📊 جمعنا 7 ردود — نحتاج 10+ لإنتاج insights"
- No recommendations: "✅ كل المنتجات بحالة جيدة هذا الأسبوع"

### 9.8 Edge Cases

| Edge Case | Behavior |
|---|---|
| Merchant has 0 submissions | Show empty state with onboarding tips |
| Merchant has <10 submissions for product | Don't show in Doctor (insufficient data) |
| Merchant dismisses same rec 3 times | Suppress that rule for that product for 30 days |
| Two rules trigger for same product | Show both, sorted by severity |
| Merchant's store has 5,000+ products | Pagination (50 per page), lazy load |

---

## 10. Feature 4 — Widget Analytics

### 10.1 Description
Per-widget performance metrics. Lightweight in MVP — no funnel analysis, no A/B testing.

### 10.2 Functional Requirements

**FR-4.1** System MUST track these events per widget:
- `widget_viewed` (impression)
- `widget_interacted` (any click/tap)
- `widget_submitted` (successful submission)
- `widget_dismissed` (closed without submitting)

**FR-4.2** Dashboard MUST display per widget:
- Views (count)
- Submissions (count)
- Submission rate (= submissions / views)
- Top pages by submissions (top 5)
- 7-day trend chart (sparkline)

**FR-4.3** Submission rate MUST display visual indicator:
- ≥3%: ✅ green
- 1.5-3%: 🟡 yellow
- <1.5%: 🔴 red with hint "اعد فكرة الـ widget"

**FR-4.4** Analytics MUST be queryable by date range (7d, 30d, all).

### 10.3 Data Model

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

// Aggregated views (for performance)
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

### 10.4 UX Requirements

Per-widget card layout:
```
┌─────────────────────────────────────┐
│ 📈 Exit Survey Widget                │
│                                     │
│ Views:           4,532               │
│ Submissions:       142               │
│ Rate:            3.1% ✅             │
│                                     │
│ ▁▂▃▅▇▆▅  Last 7 days                │
│                                     │
│ Top pages:                          │
│  /products/vitamin-c    24          │
│  /products/black-dress  18          │
│                                     │
│ [ View Details ]                    │
└─────────────────────────────────────┘
```

---

## 11. Cross-Cutting Requirements

### 11.1 Internationalization (i18n)
- Default languages: Arabic (ar) + English (en)
- Detect from Salla store locale via API
- Allow merchant override in settings
- All UI strings externalized to i18n files
- Date/number formatting per locale
- RTL support for Arabic (use `dir="rtl"` and CSS logical properties)

### 11.2 PDPL Compliance (MANDATORY)
- Explicit opt-in consent for any PII collection (phone, email)
- Consent checkbox unchecked by default
- Documented consent: timestamp + IP + consent text version + locale
- Privacy Policy URL provided by merchant (we generate template)
- Data Subject Rights endpoint: `/customer/consent/manage?token=...`
  - View all my data
  - Delete all my data
  - Withdraw consent
- Data retention: 90 days for unconsented data, indefinite (until withdrawal) for consented
- No selling/sharing data with third parties
- Server location: must be Saudi Arabia or compliant region

### 11.3 Performance Budget
- Snippet JS bundle: ≤30 KB gzipped
- Snippet load: ≤200ms on 4G
- Page load impact: ≤100ms (TTI delta)
- API response times:
  - GET /dashboard: ≤500ms p95
  - POST /widget/submit: ≤200ms p95
  - POST /interest/track: ≤200ms p95
- Webhook processing: ≤2s p95

### 11.4 Mobile Responsiveness
- Mobile-first design
- Test on iPhone SE (smallest target), iPhone 14, iPhone 14 Pro Max, Galaxy S22, iPad
- All widgets: touch-friendly (44px tap targets minimum)
- Dashboard: responsive table → cards on mobile

### 11.5 Accessibility (WCAG 2.1 AA)
- Color contrast 4.5:1 minimum for text
- Keyboard navigation for all interactive elements
- Focus visible on all focusable elements
- Screen reader announcements for dynamic content
- Alt text on all images
- Form labels associated with inputs

### 11.6 Security
- HTTPS everywhere
- CSP headers (no inline scripts in production)
- API auth: OAuth 2.0 with Salla + JWT for our backend
- Rate limiting: 100 req/min per merchant, 10 submissions/min per session
- Input sanitization on all user-submitted strings (server-side)
- SQL injection prevention (parameterized queries / ORM)
- XSS prevention (escape all rendered text)
- CSRF tokens on state-changing endpoints
- Sensitive data (phone numbers) hashed at rest, partial display
- Audit log for all admin actions

### 11.7 Browser Support
- Chrome: latest 2 versions
- Safari: latest 2 versions (iOS Safari critical)
- Firefox: latest 2 versions
- Edge: latest 2 versions
- IE 11: NOT supported

---

## 12. Technical Architecture

### 12.1 High-Level Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                  Salla Storefront (Customer)                 │
│  ┌──────────────────────────────────────────────────────┐   │
│  │ Twilight Theme + Smart Snippet JS (injected via      │   │
│  │ body:end hook + product/cart hooks)                   │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────┬───────────────────────────────────┘
                          │ HTTPS (POST events)
                          ▼
┌─────────────────────────────────────────────────────────────┐
│              Smart Snippet Backend (our service)             │
│  ┌─────────────────┐  ┌─────────────────┐                   │
│  │  Public API     │  │  Merchant API   │                   │
│  │  (storefront)   │  │  (dashboard)    │                   │
│  └────────┬────────┘  └────────┬────────┘                   │
│           ▼                    ▼                            │
│  ┌─────────────────────────────────────┐                    │
│  │       Application Logic              │                    │
│  │  - Submission processing             │                    │
│  │  - Doctor rules engine               │                    │
│  │  - Notification dispatcher           │                    │
│  └──────────────┬──────────────────────┘                    │
│                 ▼                                            │
│  ┌─────────────────────────────────────┐                    │
│  │       PostgreSQL Database            │                    │
│  └─────────────────────────────────────┘                    │
└─────────────────────────────────────────────────────────────┘
         ▲                          ▲
         │ Webhooks                 │ API calls
         │                          │
┌────────┴──────────────────────────┴─────────────────────────┐
│                       Salla Platform                         │
└──────────────────────────────────────────────────────────────┘

         ▲
         │ HTTPS
         │
┌────────┴────────────────────────┐
│   Merchant Dashboard (Next.js)  │
└─────────────────────────────────┘
```

### 12.2 Tech Stack Recommendation

**Frontend (Storefront Widget):**
- Vanilla TypeScript or Preact (small footprint)
- No heavy framework — under 30 KB gzipped
- Shadow DOM for style isolation
- Inline SVG for icons

**Frontend (Merchant Dashboard):**
- Next.js (SSR + good DX)
- TypeScript
- Tailwind CSS (compatible with Salla design tokens)
- React Query for data fetching
- shadcn/ui or similar for components

**Backend:**
- Node.js (TypeScript) — easy hire pool in Saudi
- Framework: NestJS or Fastify
- ORM: Prisma or Drizzle
- Queue: BullMQ + Redis
- Cron: node-cron or similar

**Database:**
- PostgreSQL 16+
- Read replica for analytics queries (optional in MVP)

**Infrastructure:**
- Hosting: AWS Riyadh region (PDPL compliance)
- CDN: CloudFront or Bunny
- Monitoring: Sentry + Datadog/Grafana
- Logs: CloudWatch or Loki

**Third-party:**
- WhatsApp Business API: Meta direct or Wati/Twilio
- Email: SendGrid or Postmark
- SMS: Unifonic (Saudi-focused) or Twilio

### 12.3 Deployment Strategy
- CI/CD: GitHub Actions
- Environments: dev / staging / production
- Database migrations: Prisma Migrate
- Feature flags: Unleash or simple env vars
- Zero-downtime deploys: blue-green or rolling

---

## 13. Salla Integration Specifications

### 13.1 App Registration
Register as Salla App via Salla Partners Portal:
- App name: Smart Snippet System
- Type: Public (App Store)
- Redirect URLs: `https://app.smartsnippet.sa/auth/salla/callback`

### 13.2 OAuth Scopes Required

| Scope | Purpose | Justification |
|---|---|---|
| `read_orders` | Future: post-purchase context | Phase 2 — request now for future use |
| `read_customers` | Match interest signals to customers | Required for Feature 2 |
| `read_products` | Display products in dashboard | Required for all features |
| `write_app_settings` | Store merchant config | Required |

**Verify exact scope names in Salla docs.**

### 13.3 Webhooks Subscribed (MVP)

| Webhook Event | Used For | Handler |
|---|---|---|
| `product.price.updated` | Trigger target_price notifications | `webhooks/price-updated.ts` |
| `product.updated` | Detect variant restock | `webhooks/product-updated.ts` |
| `product.quantity.low` | Future use | `webhooks/quantity-low.ts` (log only in MVP) |
| `customer.created` | Match anonymous signals to customers | `webhooks/customer-created.ts` |
| `app.installed` | Onboarding trigger | `webhooks/app-installed.ts` |
| `app.uninstalled` | Cleanup + offboard email | `webhooks/app-uninstalled.ts` |

### 13.4 Twilight Theme Hooks Used (Confirmed)

| Hook | Used For |
|---|---|
| `body:end` | Inject main snippet bundle + Exit Intent listener |
| `head:end` | Inject CSS for Shadow DOM styles |
| `product:single.description.end` | Place Interest Capture button + Hesitation widget anchor on PDP |
| `cart:items.end` | Place Hesitation widget on Cart page |

### 13.5 Salla API Endpoints Used (Verify exact paths in Salla Merchant API docs)

| Endpoint | Purpose |
|---|---|
| `GET /products/:id` | Fetch product details for dashboard |
| `GET /products?filter[ids]=...` | Bulk product fetch |
| `GET /customers/:id` | Match signals to customers |
| `GET /store` | Get store info, locale |

### 13.6 App Snippet Configuration
Register App Snippets in Salla Partners Portal:
- Snippet 1: `smart_snippet_main` — body:end, all pages
- Snippet 2: `smart_snippet_pdp` — product:single.description.end
- Snippet 3: `smart_snippet_cart` — cart:items.end

---

## 14. Data Model

### 14.1 Schema Diagrams (PostgreSQL)

```sql
-- Merchants (Salla stores using our app)
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
  plan VARCHAR(20) DEFAULT 'trial', -- trial / starter / growth / pro
  trial_ends_at TIMESTAMP,
  subscription_status VARCHAR(20) DEFAULT 'trial', -- trial / active / past_due / cancelled
  salla_access_token TEXT, -- encrypted
  salla_refresh_token TEXT, -- encrypted
  installed_at TIMESTAMP NOT NULL DEFAULT NOW(),
  uninstalled_at TIMESTAMP,
  created_at TIMESTAMP NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMP NOT NULL DEFAULT NOW()
);

-- Widgets (one merchant can have multiple widgets)
CREATE TABLE widgets (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  merchant_id UUID NOT NULL REFERENCES merchants(id) ON DELETE CASCADE,
  type VARCHAR(50) NOT NULL, -- 'hesitation' / 'interest' / 'clarity'
  name VARCHAR(255),
  enabled BOOLEAN DEFAULT TRUE,
  config JSONB NOT NULL, -- WidgetConfig (see TypeScript types)
  created_at TIMESTAMP NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMP NOT NULL DEFAULT NOW()
);

CREATE INDEX idx_widgets_merchant ON widgets(merchant_id);
CREATE INDEX idx_widgets_enabled ON widgets(enabled) WHERE enabled = TRUE;

-- Hesitation Submissions
CREATE TABLE hesitation_submissions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  merchant_id UUID NOT NULL REFERENCES merchants(id) ON DELETE CASCADE,
  widget_id UUID NOT NULL REFERENCES widgets(id) ON DELETE CASCADE,
  trigger_mode VARCHAR(50) NOT NULL, -- 'exit_intent' / 'product_clarity'
  reason_id VARCHAR(100),
  reason_label_ar VARCHAR(255),
  reason_label_en VARCHAR(255),
  free_text TEXT,
  product_id VARCHAR(255),
  product_handle VARCHAR(255),
  product_price DECIMAL(10,2),
  page_url TEXT,
  page_type VARCHAR(20),
  customer_id VARCHAR(255), -- Salla customer ID if logged in
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

-- Interest Signals
CREATE TABLE interest_signals (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  merchant_id UUID NOT NULL REFERENCES merchants(id) ON DELETE CASCADE,
  customer_phone_hash VARCHAR(255), -- SHA256
  customer_phone_last4 VARCHAR(4),
  customer_email VARCHAR(255),
  customer_salla_id VARCHAR(255),
  product_id VARCHAR(255) NOT NULL,
  product_variant_id VARCHAR(255),
  interest_type VARCHAR(50) NOT NULL, -- 'target_price' / 'variant_color' / etc.
  target_value JSONB,
  status VARCHAR(20) DEFAULT 'active', -- 'active' / 'triggered' / 'cancelled' / 'expired'
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

-- Doctor Recommendations
CREATE TABLE recommendations (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  merchant_id UUID NOT NULL REFERENCES merchants(id) ON DELETE CASCADE,
  rule_id VARCHAR(100) NOT NULL,
  product_id VARCHAR(255),
  severity VARCHAR(20) NOT NULL, -- 'low' / 'medium' / 'high'
  title_ar VARCHAR(500),
  title_en VARCHAR(500),
  explanation_ar TEXT,
  explanation_en TEXT,
  action_type VARCHAR(50),
  action_payload JSONB,
  signal_count INT,
  status VARCHAR(20) DEFAULT 'pending', -- 'pending' / 'applied' / 'dismissed' / 'expired'
  applied_at TIMESTAMP,
  dismissed_at TIMESTAMP,
  expires_at TIMESTAMP NOT NULL,
  created_at TIMESTAMP NOT NULL DEFAULT NOW()
);

CREATE INDEX idx_recommendations_merchant_status ON recommendations(merchant_id, status);
CREATE INDEX idx_recommendations_product ON recommendations(merchant_id, product_id);

-- Widget Events (analytics)
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

-- Aggregated daily metrics (rebuilt nightly)
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

-- Consent Records (PDPL)
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

### 14.2 Data Retention Policy
- Hesitation submissions (no PII): retained indefinitely (anonymized after 12 months)
- Interest signals with consent: until customer withdraws or expires (90 days default)
- Interest signals without consent: cannot exist (consent required at creation)
- Widget events: 12 months raw, then aggregated only
- Consent records: 7 years (legal compliance)
- Merchant data: deleted 90 days after uninstall

---

## 15. API Specifications

### 15.1 Public API (Storefront — called from snippet)

**Base URL:** `https://api.smartsnippet.sa/v1/public`

#### POST /submissions
Submit a hesitation response.

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

→ 429 Too Many Requests (rate limit)
→ 400 Bad Request (invalid payload)
```

#### POST /interest
Register an interest signal (requires consent).

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

→ 422 Unprocessable Entity (consent missing or invalid phone)
```

#### POST /events
Track widget events (impressions, dismissals).

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
Customer-facing consent management page (HTML).

```http
GET /v1/public/consent/manage?token=<jwt>

→ 200 OK (renders HTML page with: view signals, delete signals, withdraw consent)
```

### 15.2 Merchant API (Dashboard — authenticated)

**Base URL:** `https://api.smartsnippet.sa/v1/merchant`
**Auth:** Bearer JWT (issued after Salla OAuth)

#### GET /me
Get current merchant profile.

#### GET /dashboard/insights?period=7d
Returns hero stats, top reasons, products needing attention, variant heatmap.

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
List all merchant widgets.

#### POST /widgets
Create a new widget.

#### PATCH /widgets/:id
Update widget config.

#### GET /widgets/:id/analytics?period=7d
Per-widget analytics.

#### GET /recommendations?status=pending
List Doctor recommendations.

#### POST /recommendations/:id/apply
Mark recommendation as applied + optionally trigger action.

#### POST /recommendations/:id/dismiss

#### GET /submissions?product_id=...&period=30d
List raw submissions (with filters).

#### GET /interest-signals?status=active

#### POST /billing/subscribe
Initiate paid plan subscription (links to Salla billing).

### 15.3 Webhook Handlers (Internal)

**Base URL:** `https://api.smartsnippet.sa/v1/webhooks/salla`

#### POST /webhooks/salla/product-price-updated
#### POST /webhooks/salla/product-updated
#### POST /webhooks/salla/customer-created
#### POST /webhooks/salla/app-installed
#### POST /webhooks/salla/app-uninstalled

All Salla webhooks verified via HMAC SHA256 signature.

---

## 16. UX / UI Requirements

### 16.1 Design Principles

1. **Minimal friction** — Don't interrupt the shopping flow
2. **Clear information hierarchy** — Most important info first
3. **Action-oriented** — Every screen has a clear next step
4. **Data-confident** — Don't hide numbers, show them clearly
5. **Salla-native feeling** — Inherit theme tokens where possible
6. **Honest empty states** — Tell user what's missing and how to fix
7. **No dark patterns** — No fake urgency, no hidden costs

### 16.2 Customer-Facing Widget Design

**Color Palette (default — overridable per merchant):**
- Primary: Inherits Salla theme primary color
- Background: White / Dark gray (auto-detect)
- Text: #1A1A1A / #FFFFFF
- Borders: rgba(0,0,0,0.08)
- Success: #10B981
- Error: #EF4444

**Typography:**
- Arabic: "IBM Plex Sans Arabic" / fallback to system
- English: "Inter" / fallback to system
- Sizes: 14px body, 16px buttons, 18px titles

**Spacing:**
- Base unit: 4px
- Modal padding: 24px desktop, 16px mobile
- Button padding: 12px 24px

**Components:**
- Buttons: rounded-lg (8px), no shadows
- Inputs: rounded-md (6px), border 1px
- Radio buttons: large circular targets (24px)

### 16.3 Merchant Dashboard Design

**Layout:**
- Top nav: Logo, store name, plan badge, help, profile menu
- Left sidebar: Dashboard, Widgets, Doctor, Analytics, Settings
- Main content: card-based layout

**Dashboard Home:**
```
┌─ Top Stats ────────────────────────────────────────┐
│  [142 ↑18%]  [87 ↑22%]  [4/5 widgets]  [3.1% ✅]  │
└────────────────────────────────────────────────────┘

┌─ Top 3 Hesitation Reasons ─┐  ┌─ Variant Heatmap ──┐
│ 1. السعر مرتفع    54 (38%)│  │ Black L      30 ▓▓▓│
│ 2. غير متأكد المقاس 32   │  │ Red M        22 ▓▓ │
│ 3. معلومات ناقصة   28   │  │ Beige S      14 ▓  │
└─────────────────────────────┘  └────────────────────┘

┌─ Products Needing Attention ───────────────────────┐
│ Product               Issues  Severity   [→]      │
│ Vitamin C Serum       15      🔴 High            │
│ Black Maxi Dress      12      🟡 Medium          │
└────────────────────────────────────────────────────┘

┌─ Doctor Recommendations (3 pending) ───────────────┐
│ 💊 Vitamin C Serum: 8 customers confused on usage │
│    → Add video or FAQ                              │
│    [ Apply ]  [ Dismiss ]                          │
└────────────────────────────────────────────────────┘
```

### 16.4 Component Library

Build/use these components:
- `<Button>` (primary, secondary, ghost variants)
- `<Card>` (with header, body, footer)
- `<StatTile>` (number + delta + label)
- `<ProgressBar>` (for submission rate)
- `<RecommendationCard>` (severity badge + actions)
- `<EmptyState>` (icon + message + CTA)
- `<DataTable>` (sortable, paginated)
- `<SparklineChart>` (7-day trend)
- `<BarChart>` (top reasons)
- `<Heatmap>` (variant demand)
- `<Toast>` (action confirmations)
- `<Modal>` (configuration dialogs)

### 16.5 Empty States

**Day 1 (no data):**
> 👋 مرحبًا بك في Smart Snippet System
> ابدأ بتفعيل أول widget — ستظهر بياناتك خلال 24 ساعة
> [ ابدأ Onboarding ]

**No submissions yet (data <10):**
> 📊 جمعنا 4 ردود حتى الآن
> نحتاج 10+ لإنتاج insights موثوقة
> [ شاركة الـ widgets الحالية ]

**No recommendations:**
> ✅ كل المنتجات بحالة جيدة هذا الأسبوع
> سنخبرك حين يحتاج منتج لاهتمامك

**Widget rate <1.5%:**
> 🔴 معدل تفاعل ضعيف (1.2%)
> اقتراحات لتحسينه: [3 nudges]

---

## 17. Onboarding Flow

### 17.1 First-Time Setup (5 steps, <5 minutes)

**Step 1: Welcome (auto after install)**
- "👋 مرحبًا [Store Name] — لنبدأ بتفعيل أول widget"
- Choose vertical: Beauty / Fashion / Perfumes / Gifts / Other

**Step 2: First Widget — Hesitation Capture**
- Pre-filled with vertical-specific defaults
- Preview live widget on side
- "هذا الـ widget سيظهر للزوار الذين على وشك المغادرة"
- Customize reasons (optional) — or accept defaults
- [ Activate Widget ]

**Step 3: Privacy Policy Setup**
- "نولّد لك Privacy Policy template — راجعها وأضفها لمتجرك"
- Generated URL link
- Checkbox: "أؤكد أن لدي Privacy Policy منشورة"

**Step 4: Email Preferences**
- Pre-filled with Salla account email
- Toggle: weekly digest, recommendations alerts, billing
- "أول digest يصلك صباح الإثنين القادم"

**Step 5: Done**
- "🎉 جاهز! الـ widget مفعّل على متجرك"
- Show first thing to expect: "خلال 24 ساعة سترى أول submissions"
- "تريد تفعيل المزيد؟" → [ Activate Interest Capture ]
- Skip: "خذ جولة في Dashboard"

### 17.2 Empty Dashboard Tour
After first visit to dashboard with no data:
- Tooltips on each section explaining what'll appear
- Sample data preview (greyed): "هذا مثال على ما سترى"

---

## 18. Notifications

### 18.1 Merchant Notifications

**Weekly Email Digest (Monday 9 AM Saudi):**
- Stats summary
- Top 3 hesitation reasons
- 3 Doctor recommendations
- CTA: open dashboard

**Real-time Email (opt-in):**
- New high-severity Doctor recommendation
- Widget rate dropped below 1.5%
- 10+ customers requesting same variant (urgent reorder signal)

**In-App (Dashboard):**
- Toast on new recommendation
- Badge on Doctor menu item with count

### 18.2 Customer Notifications

**Triggered (when conditions met):**
- WhatsApp message (primary)
- SMS fallback
- Email (if no phone, has email)

**Templates (WhatsApp Business):**

Template 1 — Price Drop:
```
مرحبًا 👋
المنتج اللي تابعته نزل سعره!

[Product Name]
السعر السابق: 199 ر.س
السعر الآن: 149 ر.س ✨

اشترِ الآن: [link]

— [Store Name]
لإلغاء التنبيهات: [manage link]
```

Template 2 — Variant Available:
```
مرحبًا 👋
الـ [color/size] اللي طلبته رجع!

[Product Name]
[Variant details]

اشترِ قبل ينفد: [link]

— [Store Name]
لإلغاء التنبيهات: [manage link]
```

---

## 19. Analytics & Instrumentation

### 19.1 Events to Track (Internal Product Analytics)

**Merchant Events:**
- `app_installed`
- `onboarding_step_completed` (props: step_number, time_spent)
- `onboarding_completed` (props: total_time)
- `widget_created` (props: type, vertical_template)
- `widget_activated`
- `widget_deactivated`
- `dashboard_viewed` (props: section)
- `recommendation_applied` (props: rule_id, severity)
- `recommendation_dismissed`
- `trial_started`
- `trial_converted` (props: plan, days_to_convert)
- `trial_expired`
- `subscription_cancelled` (props: reason)

**Customer Events:**
- `widget_viewed`
- `widget_interacted`
- `widget_submitted`
- `widget_dismissed`
- `interest_signal_created` (props: type)
- `consent_given`
- `consent_withdrawn`

### 19.2 Properties (Common)
- `merchant_id`
- `merchant_plan`
- `store_vertical`
- `device_type`
- `locale`
- `timestamp`

### 19.3 Internal Dashboards (For Us)
- Acquisition: installs / day, trial starts / day
- Activation: % of installs that activate first widget within 24h
- Engagement: weekly active merchants
- Retention: 7-day, 30-day, 90-day
- Revenue: MRR, ARR, churn
- Funnel: install → onboard → first submission → 10 submissions → trial convert

---

## 20. Success Metrics

### 20.1 North Star Metric
**Weekly Active Merchants with ≥1 Applied Recommendation**
This proves both engagement AND value delivery.

### 20.2 Leading Indicators (Daily/Weekly)
- New installs per day
- First-widget activation rate (target ≥80% within 24h)
- Average submission rate per widget (target ≥3%)
- Time to first insight (target <72h from install)
- Doctor recommendation apply rate (target ≥30%)

### 20.3 Lagging Indicators (Monthly)
- Trial-to-paid conversion (target ≥15%)
- 30-day retention (target ≥70%)
- 90-day retention (target ≥50%)
- MRR growth (target 25% MoM in first 6 months)
- NPS (target ≥40)

### 20.4 Kill Criteria (Day 60 from MVP launch)
- Submission rate <1.5% (sustained over 30 days)
- Trial-to-paid <5%
- 30-day retention <40%
- Weekly dashboard open rate <30%

If any TWO of these hit, pause new feature work and re-evaluate.

---

## 21. Launch Criteria

### 21.1 Closed Beta (Day 60)
**Audience:** 3-5 invited merchants (Beauty/Perfumes vertical)

**Acceptance Criteria:**
- All 4 MVP features functional end-to-end
- Onboarding completes successfully
- Hesitation widget submissions captured and visible in dashboard within 1 minute
- Doctor generates at least 1 recommendation when threshold met
- WhatsApp notifications successfully delivered
- PDPL consent layer functional
- No P0 bugs

**Goal:** 1-2 weeks of bug bash + UX feedback

### 21.2 Open Beta (Day 75)
**Audience:** 20-30 merchants (invite-only, marketing channels)

**Acceptance Criteria:**
- Closed beta feedback incorporated
- Performance budget met (load times)
- Privacy policy templates finalized in AR + EN
- All payment flows tested (Salla billing integration)
- Help docs published

### 21.3 Salla App Store Submission (Day 90)

**Submission Checklist:**
- [ ] App listing in AR + EN
- [ ] Screenshots (5+ for each: AR, EN)
- [ ] Demo video (60 seconds)
- [ ] Privacy Policy URL
- [ ] Terms of Service URL
- [ ] Support email + phone
- [ ] OAuth scopes justified
- [ ] App pricing configured
- [ ] Salla App Store review process (typically 2-7 days)

### 21.4 Public Launch (Day 105 — estimate)
- Salla App Store approved
- Launch announcement (social, email)
- 3 case studies published from beta merchants
- Customer support ready (response <4h business hours)

---

## 22. Out of Scope (Explicit "No" list for MVP)

### Features Out of MVP
- ❌ AI-powered recommendations (Phase 3)
- ❌ Popup builder for general marketing
- ❌ Email marketing campaigns
- ❌ SMS marketing campaigns
- ❌ Helpdesk / ticketing
- ❌ Loyalty program
- ❌ Reviews app
- ❌ Wishlist as standalone
- ❌ A/B testing engine
- ❌ Conversion attribution / revenue tracking
- ❌ Customer segmentation
- ❌ Audience export to ad platforms
- ❌ Multi-store accounts
- ❌ White-label / agency mode
- ❌ Multi-language beyond AR + EN
- ❌ Native mobile app (web dashboard only)
- ❌ Voice / chatbot interface
- ❌ Custom CSS injection
- ❌ JavaScript event API for merchants
- ❌ Direct integrations (Zapier, Make, etc.)

### Technical Out of MVP
- ❌ Multi-region deployment (Saudi Arabia only)
- ❌ Custom domains for white label
- ❌ SSO / SAML
- ❌ Webhooks for merchants (we receive Salla webhooks, but don't send our own to merchants)
- ❌ Public API for merchants

### Vertical Out of MVP
- ❌ B2B-only stores
- ❌ Food delivery / restaurants
- ❌ Service businesses (non-product)
- ❌ Marketplaces (multi-seller)

---

## 23. Open Questions

These need to be resolved before/during build:

**Salla Platform Questions:**
1. ❓ Does `product.quantity.low` webhook fire per variant_id or product_id only? **Verify in Salla Developer Console.**
2. ❓ What's the rate limit for Salla Merchant API calls? Plan accordingly for dashboard.
3. ❓ Are app snippets sandboxed (Shadow DOM enforced) or full DOM access?
4. ❓ Does Salla provide a customer_id on storefront events for logged-in customers?
5. ❓ What's the Salla App Store billing flow? Direct merchant billing or Salla-collected?
6. ❓ Are there restrictions on widget visual elements (e.g., popups disallowed in some pages)?

**Product Questions:**
7. ❓ Should we offer "Quick Setup" (defaults) vs "Custom Setup" (full config) for onboarding?
8. ❓ Should weekly digest be optional from Day 1, or default-on with opt-out?
9. ❓ Should we show competitor metrics (anonymized benchmarks) in dashboard? Privacy implications?
10. ❓ Should "Apply" actions go through merchant approval for first 10, then auto-apply later?

**Technical Questions:**
11. ❓ Should we use Shadow DOM or iframe for widget isolation? (Shadow DOM = better UX, iframe = better security)
12. ❓ How do we handle Salla theme updates that might break our injection points?
13. ❓ What's the failover plan if our backend goes down (don't break merchant's storefront)?
14. ❓ Should hesitation reasons be merchant-editable from Day 1 or fixed for first 30 days (for cohort analysis)?

**Legal / Compliance Questions:**
15. ❓ Do we need a separate Data Processing Agreement with each merchant (PDPL)?
16. ❓ Can we use merchant data (anonymized) for cross-merchant benchmarks? (probably needs explicit consent)
17. ❓ What's our SLA on data deletion requests?

---

## 24. Risks & Mitigations

### R1 — Submission Rate Below Target
**Risk:** Customers don't engage with widgets (<1.5%)
**Severity:** Critical (Fatal Risk)
**Probability:** High
**Mitigation:**
- A/B test trigger timing in beta
- Offer optional reward coupon (configurable)
- Use single-tap options (not free text first)
- Optimize copy for friendliness, not interrogation
- **Action before build:** Run paper-prototype on 1 merchant for 2 weeks, measure baseline.

### R2 — Salla Native Feature Overlap
**Risk:** Salla launches similar feature, eroding our value
**Severity:** High
**Probability:** Medium
**Mitigation:**
- Build depth (Doctor rules, variant intelligence) Salla won't replicate quickly
- Partner with Salla early (pitch as complement)
- Monitor Salla product announcements weekly

### R3 — Perceived as "Just Another Popup Tool"
**Risk:** Merchants associate us with PopupSnap, undervaluing
**Severity:** High
**Probability:** Medium
**Mitigation:**
- Strict positioning: "Intent Layer", "Doctor", "Insights" vocabulary
- Demo emphasizes Dashboard, not widgets
- Pricing higher than PopupSnap (signals premium)
- Avoid "popup" in marketing copy

### R4 — PDPL Non-Compliance
**Risk:** Saudi PDPL fines for improper consent
**Severity:** High
**Probability:** Low
**Mitigation:**
- Legal review before launch
- Consent layer in Day 1 design
- Document everything (consent text version, timestamps, IPs)
- Customer-facing consent management URL

### R5 — Salla Theme Compatibility
**Risk:** Our widgets break on various themes
**Severity:** Medium
**Probability:** Medium
**Mitigation:**
- Shadow DOM isolation
- Test on top 10 Salla themes during beta
- Fallback styles for edge cases
- Monitor support tickets for theme issues

### R6 — WhatsApp Business API Restrictions
**Risk:** Meta restricts our notification volume or templates
**Severity:** Medium
**Probability:** Medium
**Mitigation:**
- Pre-approve templates with Meta
- Use Wati or similar BSP (more flexible than direct Meta)
- SMS fallback ready

### R7 — Performance Impact on Stores
**Risk:** Our widget slows down merchant storefronts
**Severity:** High
**Probability:** Low (with discipline)
**Mitigation:**
- Hard performance budget (30KB, 100ms TTI delta)
- Async loading
- Self-hosted CDN with edge caching
- Performance regression tests in CI

---

## 25. Timeline & Milestones

### Week-by-Week 90-Day Plan

#### Phase A: Foundation (Weeks 1-3)

**Week 1: Setup & Architecture**
- Salla developer account + app registration
- Repository setup (frontend, backend, dashboard)
- Database schema implementation
- CI/CD pipeline
- Hosting infrastructure (AWS Riyadh)

**Week 2: Salla Integration Core**
- OAuth flow with Salla
- Webhook receivers (price_updated, product_updated, customer_created, app_installed)
- App snippet registration + injection working on test store
- Basic Twilight hooks tested

**Week 3: Backend Skeleton**
- Public API endpoints (submissions, interest, events)
- Authentication (JWT for merchant dashboard)
- Database access layer
- Rate limiting
- Error handling + logging (Sentry)

#### Phase B: Feature 1 Build (Weeks 4-5)

**Week 4: Hesitation Widget — Frontend**
- Widget rendering (Shadow DOM)
- Exit Intent triggers (desktop + mobile fallback)
- Product Clarity triggers
- Configuration loading from backend
- Submission flow
- Thank you state
- Mobile responsiveness
- Arabic + English

**Week 5: Hesitation Widget — Backend + Dashboard**
- Submission processing
- Storage + indexes
- Basic dashboard view (raw submissions list)
- Widget configuration UI (CRUD)
- Per-widget analytics tab

#### Phase C: Feature 2 Build (Weeks 6-7)

**Week 6: Interest Capture — Frontend**
- "نبهني" button on PDP
- Modal with interest type selection
- Phone validation (Saudi/Gulf)
- PDPL consent layer
- Submission flow

**Week 7: Interest Capture — Backend + Notifications**
- Interest signal storage
- Webhook handlers fire correctly
- WhatsApp Business integration (BSP setup)
- SMS fallback (Unifonic)
- Template approval submitted
- Customer consent management page

#### Phase D: Feature 3 Build (Weeks 8-9)

**Week 8: Intent Dashboard**
- Dashboard home (stats, top reasons, products)
- Variant heatmap
- Date range filtering
- Empty states
- Performance optimization (queries)

**Week 9: Product Doctor**
- Rules engine (5 MVP rules)
- Daily cron job (4 AM Saudi)
- Recommendations CRUD
- Apply action handlers
- Recommendations UI

#### Phase E: Feature 4 + Polish (Week 10)

**Week 10: Analytics + Weekly Digest**
- Widget Analytics dashboard
- Daily aggregation cron
- Weekly digest email template
- Email sender setup (SendGrid)
- First digest test send

#### Phase F: Beta Prep (Weeks 11-12)

**Week 11: Onboarding + Polish**
- 5-step onboarding wizard
- Empty state tours
- Help docs (FAQ pages)
- Privacy Policy template generator
- Loading states everywhere

**Week 12: Internal QA + Bug Bash**
- End-to-end testing on staging
- Performance testing
- Cross-browser testing (Chrome, Safari, Firefox)
- Cross-device testing (iPhone, Galaxy, iPad)
- Theme compatibility testing (top 5 Salla themes)
- Security review
- Closed beta merchants identified + outreach

#### Phase G: Beta + Launch (Weeks 13-15)

**Week 13: Closed Beta Launch**
- 3-5 merchants onboarded with white-glove support
- Daily check-ins
- Bug fixes prioritized

**Week 14: Open Beta + Iteration**
- Expand to 20-30 merchants
- Collect feedback
- Iterate on UX issues
- Refine Doctor rules based on real data

**Week 15: Salla App Store Submission**
- All listing materials prepared
- Demo video recorded
- Submission filed
- Begin reviewing Salla feedback if any

### Critical Path Items
1. Salla developer account approval (Week 1) — can block start
2. WhatsApp Business template approval (Week 7-8) — can block notifications
3. Salla App Store review (Week 15+) — can block launch

---

## 26. Appendix

### A. Glossary

| Term | Definition |
|---|---|
| **Hesitation Capture** | Widget asking customer why they didn't buy |
| **Intent Signal** | Any pre-purchase behavioral data point (hesitation, interest) |
| **Interest Signal** | Customer registering for future notification (price, variant) |
| **Product Doctor** | Rule-based engine recommending fixes per product |
| **Submission** | A customer's response to a hesitation widget |
| **Submission Rate** | Submissions ÷ Widget Views |
| **PDPL** | Saudi Personal Data Protection Law (effective 2023-2024) |
| **Salla Twilight** | Salla's theme engine + JS SDK |
| **App Snippet** | Salla's mechanism for injecting JS/HTML into storefronts |
| **Conditional Webhook** | Salla feature to filter webhooks by rules |

### B. Sample Doctor Rule Configuration (Future Extensibility)

```typescript
// Rules will be database-driven for easy iteration
interface DoctorRuleDb {
  id: string;
  name: string;
  enabled: boolean;
  conditions: ConditionExpression; // composable AND/OR
  recommendation_template: {
    title_template_ar: string; // with {count}, {product_name} placeholders
    title_template_en: string;
    explanation_ar: string;
    explanation_en: string;
    action_type: string;
    action_payload_template: any;
  };
  severity: 'low' | 'medium' | 'high';
  cooldown_days: number; // don't re-recommend within X days
  min_signal_count: number; // threshold
  vertical_filter?: string[]; // only for specific verticals
}
```

### C. Hesitation Reason Taxonomy (Default)

```typescript
const DEFAULT_REASONS = [
  { id: 'price_high', label_ar: 'السعر مرتفع', label_en: 'Price too high', category: 'price' },
  { id: 'shipping_unclear', label_ar: 'الشحن غير واضح', label_en: 'Shipping unclear', category: 'shipping' },
  { id: 'size_unclear', label_ar: 'غير متأكد من المقاس', label_en: 'Unsure about size', category: 'product' },
  { id: 'comparing', label_ar: 'محتار بين منتجات', label_en: 'Comparing products', category: 'decision' },
  { id: 'need_more_info', label_ar: 'محتاج معلومات أكثر', label_en: 'Need more info', category: 'product' },
  { id: 'just_browsing', label_ar: 'فقط أتصفح', label_en: 'Just browsing', category: 'low_intent' },
  // Vertical-specific (added in v2):
  { id: 'ingredients_concern', label_ar: 'قلق من المكونات', label_en: 'Concerned about ingredients', category: 'product', verticals: ['beauty'] },
  { id: 'authenticity', label_ar: 'متشكك في الأصالة', label_en: 'Authenticity concerns', category: 'trust', verticals: ['perfumes', 'fashion'] },
];
```

### D. Sample API Payloads (Detailed)

See section 15 for complete spec. Additional examples:

**Webhook payload from Salla (`product.price.updated`):**
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

**Doctor Recommendation creation:**
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

### E. References

- **Strategic Analysis:** [Smart-Snippet-System-Analysis.md](./Smart-Snippet-System-Analysis.md)
- **Competitive Landscape:** [Competitive-Landscape-Analysis.md](./Competitive-Landscape-Analysis.md)
- **Salla Developer Docs:** https://docs.salla.dev/
- **Salla Webhooks:** https://docs.salla.dev/421119m0
- **Twilight Theme Hooks:** https://docs.salla.dev/422552m0
- **PDPL Compliance:** https://sdaia.gov.sa/en/Research/Pages/DataProtection.aspx

---

## 27. Module 40 + Phase 1/2 Roadmap Specifications

This section adds explicit specs for 20 modules referenced in the Analysis library but not covered in MVP Features 1-4:
- **Module 40** (PDPL Consent Center) — formally MVP-scope requirement
- **8 Phase 1 modules** (Months 4-9)
- **11 Phase 2 modules** (Months 10-18)

Specs are condensed (Description + Top FRs + Salla Integration + Dependencies + Effort). Full UX/edge case treatment will be added when each module enters active development.

---

### 27.1 Module 40 — PDPL Consent Management Center (🟢 MVP — Legal Requirement)

**Description:** Customer-facing self-service portal for managing data, signals, and consent. **Required for PDPL compliance** (already referenced as cross-cutting requirement in Section 11.2; this section formalizes it as a specific feature).

**Functional Requirements:**
- FR-40.1: Accessible via `/v1/public/consent/manage?token=<jwt>`. Token has 30-day expiry, regenerable.
- FR-40.2: Display all interest signals + submissions associated with customer's phone hash.
- FR-40.3: One-click cancel for individual signals (sets `status='cancelled'`).
- FR-40.4: Bulk delete with confirmation prompt (cascade delete + audit log).
- FR-40.5: Consent withdrawal (stops future communications, retains audit record).
- FR-40.6: Data export (CSV/JSON download).
- FR-40.7: Log all actions to `consent_records` table with timestamp, IP, action type.
- FR-40.8: Email confirmation after each major action (delete, withdraw).
- FR-40.9: Arabic + English (RTL support).

**Salla Integration:** None (self-hosted URL).
**Dependencies:** Database schema (`interest_signals`, `consent_records` tables) — already in MVP.
**Effort:** Medium (3-5 days).
**Open Questions:** Should we require phone OTP for full data deletion to prevent token-leak attacks?

---

### 27.2 Phase 1 Modules (Months 4-9)

All Phase 1 modules build directly on MVP data infrastructure. Technically verified, low Salla native overlap.

#### Module 38 — Empty Search Capture (🟡 Phase 1)
**Description:** Captures customer search queries that returned no results. Direct inventory demand signal.
**Key FRs:**
- FR-38.1: Detect empty search state via `.s-search-no-results` CSS class or DOM observation.
- FR-38.2: Inject capture form: pre-filled query + optional phone + PDPL consent.
- FR-38.3: Store in `missed_searches` table with frequency aggregation.
- FR-38.4: Dashboard widget: "Top missed searches" sorted by count.

**Salla Integration:** Twilight `<salla-search>` component customization *(Confirmed)*.
**Dependencies:** PDPL consent layer (MVP).
**Effort:** Small-Medium (2-4 days).

#### Module 39 — First-Time vs Returning Recognition (🟡 Phase 1)
**Description:** Different greeting/widget for new vs returning visitors, with intent pre-tagging.
**Key FRs:**
- FR-39.1: Detect visitor state via cookie + Salla customer login state.
- FR-39.2: First-time: show 3-option intent selector (gift / personal / browse).
- FR-39.3: Returning: show last-viewed product + recently viewed strip.
- FR-39.4: Store intent tag in `visitor_intents` table linked to session.

**Salla Integration:** Twilight SDK for customer state *(Confirmed)*.
**Dependencies:** None (independent feature).
**Effort:** Medium (4-5 days).

#### Module 46 — Vertical Discovery Quiz (🟡 Phase 1)
**Description:** Short quiz building customer preference profile (skin type, style, scent family).
**Key FRs:**
- FR-46.1: Configurable quiz templates per vertical (beauty, fashion, perfumes).
- FR-46.2: 3-5 question flow, < 60 seconds completion.
- FR-46.3: Generate `customer_profile` JSON stored in `customer_profiles` table.
- FR-46.4: Apply profile to product filtering + recommendations.

**Salla Integration:** Products API for filtering.
**Dependencies:** Module 39 (First-Time recognition) for trigger.
**Effort:** Medium-Large (5-7 days).

#### Module 48 — Recently Viewed Memory Strip (🟡 Phase 1 — overlap care)
**Description:** Sticky horizontal strip showing recently viewed products + Dashboard tracking.
**Key FRs:**
- FR-48.1: Store last 20 viewed products in localStorage per visitor.
- FR-48.2: Display sticky strip on PDP/Cart with horizontal scroll.
- FR-48.3: Track view-to-purchase conversion per product in `widget_events`.

**Salla Integration:** Twilight body hooks *(Confirmed)*.
**Dependencies:** Module 35 (Analytics infrastructure).
**Effort:** Small-Medium (3-4 days).
**Note:** Some Salla themes already show "recently viewed" natively. Position our snippet to add tracking value, not duplicate visual.

#### Module 49 — Birthday/Anniversary Capture (🟡 Phase 1)
**Description:** Capture personal dates for triggered campaigns.
**Key FRs:**
- FR-49.1: Form fields: birthday (DD/MM), anniversary (optional, DD/MM).
- FR-49.2: PDPL-compliant consent for date storage.
- FR-49.3: Daily cron checks dates, triggers WhatsApp/Email 3 days before.
- FR-49.4: Dashboard: "Birthdays this month" with campaign launcher.

**Salla Integration:** Customer fields *(verify if natively supported)*.
**Dependencies:** Module 7 (Interest Capture form components).
**Effort:** Small (2-3 days).
**Verification Needed:** Whether Salla `customer` object has birthday/anniversary fields natively.

#### Module 51 — Coming Soon / Pre-Launch Capture (🟡 Phase 1)
**Description:** Capture pre-launch interest for unpublished products.
**Key FRs:**
- FR-51.1: Detect product status="hidden" or custom "coming_soon" tag.
- FR-51.2: Replace standard PDP with pre-launch teaser + email/phone capture.
- FR-51.3: Optional "Early Bird discount" coupon assignment.
- FR-51.4: Auto-notify all subscribers when product status changes to "active".

**Salla Integration:** Products API + status webhooks *(Confirmed)*.
**Dependencies:** Module 8 (Notification infrastructure).
**Effort:** Medium (4-5 days).

#### Module 54 — Influencer Code Capture & Attribution (🟡 Phase 1)
**Description:** Capture influencer-specific traffic, track per-influencer revenue.
**Key FRs:**
- FR-54.1: Parse UTM params + special URL slugs (`/?ref=sara_kn`).
- FR-54.2: Display personalized landing message with influencer name.
- FR-54.3: Auto-apply influencer coupon code at checkout.
- FR-54.4: Dashboard: per-influencer revenue, AOV, conversion rate, CAC.

**Salla Integration:** Coupons API for auto-apply *(Confirmed)*.
**Dependencies:** None.
**Effort:** Medium (4-6 days).

#### Module 55 — Cart Sharing & Save Link (🟡 Phase 1)
**Description:** Generate shareable cart URL for WhatsApp/Email sharing with dual reward.
**Key FRs:**
- FR-55.1: Generate signed JWT containing cart state.
- FR-55.2: Public URL `/cart/share/<token>` reconstructs cart on visit.
- FR-55.3: Track shared cart conversions with referral attribution.
- FR-55.4: Optional 10% discount for both sharer and buyer upon purchase.

**Salla Integration:** Cart API for state reconstruction.
**Dependencies:** Module 22 (Cart-related infrastructure from Phase 1).
**Effort:** Medium (4-5 days).

---

### 27.3 Phase 2 Modules (Months 10-18)

Phase 2 modules require deeper data, technical verification, or careful positioning.

#### Module 37 — Checkout Hesitation Capture (🟠 Phase 2)
**Description:** Capture abandonment reasons specifically on checkout page.
**Key FRs:**
- FR-37.1: Detect exit intent on checkout page (mouseleave / scroll-up / idle).
- FR-37.2: Show 6-option reason selector (shipping, payment, security, etc.).
- FR-37.3: Aggregate in `checkout_hesitations` table separate from PDP hesitations.
- FR-37.4: Trigger different Doctor rules vs PDP hesitations.

**Salla Integration:** Twilight checkout hooks (⚠️ **NEEDS VERIFICATION**).
**Dependencies:** Feature 1 (Hesitation Capture) for shared components.
**Effort:** Medium-Large (5-7 days, contingent on Salla checkout customization).

#### Module 41 — Live Stock Urgency Signal (🟠 Phase 2 — overlap care)
**Description:** Transparent stock count + social proof ("X left + Y customers viewing").
**Key FRs:**
- FR-41.1: Subscribe to `product.quantity.low` webhook *(Confirmed)*.
- FR-41.2: Display badge only when stock ≤ configurable threshold (default 5).
- FR-41.3: Augment with real-time viewing count from analytics events.
- FR-41.4: Skip display if Salla theme already renders stock count (theme detection).

**Salla Integration:** Webhook + Twilight PDP hooks *(Confirmed)*.
**Dependencies:** Webhook handlers from MVP.
**Effort:** Small-Medium (3-5 days).

#### Module 42 — Mobile One-Tap Interest (🟠 Phase 2 — overlap with Salla Wishlist)
**Description:** Anonymous mobile-only interest capture without form. Companion to (not replacement of) Salla Wishlist.
**Key FRs:**
- FR-42.1: Display sticky heart icon on PDP mobile only.
- FR-42.2: Save product ID to cookie + send anonymous event.
- FR-42.3: On return visit, restore from cookie with reminder banner.
- FR-42.4: Aggregate "most anonymous-saved products" for Doctor.

**Salla Integration:** Twilight SDK + mobile detection.
**Dependencies:** Analytics infrastructure (MVP).
**Effort:** Small (2-3 days).
**Kill Criterion:** If incremental volume vs Salla native Wishlist < 2x in pilot, remove from roadmap.

#### Module 43 — Pre-Checkout Confidence Booster (🟠 Phase 2)
**Description:** Trust signals + WhatsApp CTA on checkout page above "Place Order".
**Key FRs:**
- FR-43.1: Inject configurable trust block (shipping, returns, payment security).
- FR-43.2: Optional last-minute WhatsApp support button.
- FR-43.3: Track impression/click-to-WhatsApp conversion.

**Salla Integration:** Twilight checkout hooks (⚠️ **NEEDS VERIFICATION**).
**Dependencies:** Same checkout verification as Module 37.
**Effort:** Small (2-3 days, contingent on hooks).

#### Module 44 — Smart Reorder Timing (🟠 Phase 2)
**Description:** Auto-triggered reorder reminders based on product category timing.
**Key FRs:**
- FR-44.1: Define `reorder_category_timings` config table (e.g., serum=60d, perfume=90d).
- FR-44.2: Daily cron scans completed orders, identifies due reorders.
- FR-44.3: Send WhatsApp reminder with one-click reorder link.
- FR-44.4: Track reorder rate per category for tuning.

**Salla Integration:** Orders API + WhatsApp BSP.
**Dependencies:** WhatsApp infrastructure from MVP.
**Effort:** Medium (5-7 days).

#### Module 45 — Comparison Shopping Detector (🟠 Phase 2)
**Description:** Detect customers viewing 3+ similar products, intervene with help.
**Key FRs:**
- FR-45.1: Track PDP visits per session in real-time (server-side).
- FR-45.2: When session shows 3+ PDPs from same category within 10 minutes, trigger widget.
- FR-45.3: Widget asks: "What's making the decision hard?" with 5 options.
- FR-45.4: Surface insights in Doctor for category-level optimization.

**Salla Integration:** Products API for category matching.
**Dependencies:** Session tracking infrastructure (Module 35 Analytics).
**Effort:** Medium-Large (6-8 days).

#### Module 47 — Customer Bundle Builder (🟠 Phase 2)
**Description:** Customer selects 3+ products to form custom bundle with auto-discount.
**Key FRs:**
- FR-47.1: Configurable rules: min/max products, eligible categories, discount tiers.
- FR-47.2: Bundle UI with selected items, dynamic pricing, "complete bundle" CTA.
- FR-47.3: Apply discount as Salla coupon at checkout.
- FR-47.4: Dashboard: "Top customer-built combinations" to inform official bundles.

**Salla Integration:** Coupons API + Products API.
**Dependencies:** None.
**Effort:** Large (8-10 days).

#### Module 50 — Out-of-Stock Substitute Engine (🟠 Phase 2)
**Description:** Suggest substitutes immediately when product is OOS + capture preference.
**Key FRs:**
- FR-50.1: Detect OOS state via stock = 0 check.
- FR-50.2: Query Products API for similar products (same category, price, attributes).
- FR-50.3: Display 3 alternatives + "wait for original" option.
- FR-50.4: Track substitute conversion rate vs wait rate.

**Salla Integration:** Products API for similarity queries.
**Dependencies:** None.
**Effort:** Medium (5-6 days).

#### Module 52 — Smart Coupon Discovery (🟠 Phase 2)
**Description:** Customer-facing coupon search + capture of searched non-existent codes.
**Key FRs:**
- FR-52.1: Search bar in cart/checkout: "Looking for a coupon?"
- FR-52.2: Suggest available eligible coupons based on cart contents.
- FR-52.3: Capture all searched code names (even non-existent) in `coupon_searches` table.
- FR-52.4: Dashboard: "Searched codes not in system" → uncovers ghost influencer codes.

**Salla Integration:** Coupons API.
**Dependencies:** None.
**Effort:** Medium (4-6 days).

#### Module 53 — Shipping Transparency Calculator (🟠 Phase 2)
**Description:** Pre-checkout shipping cost calculator on PDP/Cart.
**Key FRs:**
- FR-53.1: City/region dropdown with auto-detect from IP.
- FR-53.2: Display shipping options + cost in real-time.
- FR-53.3: "Add X SAR for free shipping" progress bar.
- FR-53.4: Track shipping objection rate vs original cart abandonment.

**Salla Integration:** Shipping API (⚠️ **VERIFY AVAILABILITY**).
**Dependencies:** None.
**Effort:** Medium (5-7 days, contingent on API).

#### Module 56 — Free Sample / Trial Request (🟠 Phase 2)
**Description:** Sample request workflow for high-AOV products (>500 SAR).
**Key FRs:**
- FR-56.1: Eligible product detection (price threshold + sample-eligible tag).
- FR-56.2: Sample request form with address + phone.
- FR-56.3: Create Salla order with sample SKU (custom flow).
- FR-56.4: Track sample-to-purchase conversion + revenue attribution.

**Salla Integration:** Orders API.
**Dependencies:** Order management infrastructure.
**Effort:** Large (8-10 days, includes operational workflow).

---

### 27.4 Roadmap Total Effort Estimate

| Phase | Modules | Total Effort |
|---|---|---|
| MVP (Module 40 explicit) | 1 | 3-5 days |
| Phase 1 (38, 39, 46, 48, 49, 51, 54, 55) | 8 | 25-35 days |
| Phase 2 (37, 41, 42, 43, 44, 45, 47, 50, 52, 53, 56) | 11 | 55-75 days |
| **Total** | **20** | **~80-110 dev days (~16-22 weeks)** |

### 27.5 Critical Path Items

These can block multiple modules:
1. **Salla checkout customization verification** — blocks 37, 43 (potentially 53).
2. **WhatsApp Business API setup** — blocks 44, 49, 51 notifications.
3. **Salla customer fields availability** — blocks 49 (Birthday).
4. **Session tracking infrastructure** — blocks 45 (Comparison Detector).

### 27.6 Out of Scope Notes for Roadmap

- Modules listed are **NOT** part of MVP scope. Building prematurely risks MVP timeline.
- Each module must pass MVP kill criteria before development begins.
- Re-prioritize roadmap quarterly based on real merchant feedback.

---

## Document Sign-Off

| Role | Name | Date | Status |
|---|---|---|---|
| Product Owner | [Founder] | TBD | Pending |
| Engineering Lead | TBD | TBD | Pending |
| Design Lead | TBD | TBD | Pending |
| Legal Review | TBD | TBD | Pending |

---

**نهاية PRD — MVP**

> **التحدي الأكبر:** الانضباط بـ scope الـ MVP. أي feature إضافي = -1 من الأربعة الأساسية.
> **الـ Success:** Submission rate ≥3% + Trial-to-paid ≥15% + 30-day retention ≥70%
> **Timeline:** 15 أسبوع من Day 1 إلى Salla App Store submission.
