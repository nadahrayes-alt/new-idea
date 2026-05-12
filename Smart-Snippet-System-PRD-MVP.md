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
A Customer Intent Intelligence Platform for Salla stores — captures *why* visitors don't buy, *what* they're waiting for, and *what* to fix on each product. Plus 10 additional integrated features covering search insights, influencer attribution, OOS recovery, and lifecycle marketing.

### MVP Scope — Expanded (14 Features)

**Core 4 Features (Customer Intent loop):**
1. **Hesitation Capture Widget** (Why) — Exit intent + Product Clarity surveys
2. **Variant & Price Interest Capture** (Wait) — Multi-dimensional alerts
3. **Intent Dashboard + Product Doctor Lite** (Fix) — Aggregated insights + rule-based recommendations
4. **Widget Analytics** (Measure) — Per-widget performance metrics

**10 Additional MVP Features (added based on strategic value):**
5. **PDPL Consent Center** (Module 40) — Customer-facing data management portal *(legally mandatory)*
6. **Empty Search Capture** (Module 38) — Inventory demand signals from failed searches
7. **Influencer Attribution** (Module 54) — Per-influencer revenue tracking
8. **OOS Substitute Engine** (Module 50) — Conversion recovery on out-of-stock
9. **First-Time vs Returning Recognition** (Module 39) — Pre-tagged intent + personalization
10. **Coming Soon / Pre-Launch Capture** (Module 51) — Pre-launch demand list
11. **Cart Sharing & Save Link** (Module 55) — Social commerce with dual reward
12. **Vertical Discovery Quiz** (Module 46) — Preference profile per vertical
13. **Birthday/Anniversary Capture** (Module 49) — Lifecycle email/WhatsApp campaigns
14. **Smart Reorder Timing** (Module 44) — Category-based repeat purchase automation

### Target Launch (Expanded MVP Timeline)
- **Closed Beta:** Day 90 (was 60)
- **App Store Submission:** Day 140 (was 90)
- **Public Launch:** Day 155 (was 105)

**Note:** Timeline expanded from 15 weeks → 20-22 weeks to accommodate 14 features. Founder + Junior dev assumed.

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

### What's In (Build These 14 Features)

**Core Customer Intent Loop (Features 1-4):**

| # | Feature | Modules Combined | Priority |
|---|---|---|---|
| 1 | Hesitation Capture Widget | M4 + M17 | P0 (Core) |
| 2 | Variant & Price Interest Capture | M7 + M8 (variants/price/follow only, **not restock**) | P0 (Core) |
| 3 | Intent Dashboard + Product Doctor Lite | M32 + M34 | P0 (Core) |
| 4 | Widget Analytics | M35 | P0 (Infrastructure) |

**Additional MVP Features (Features 5-14) — see Section 27 for detailed specs:**

| # | Feature | Module | Priority | Effort |
|---|---|---|---|---|
| 5 | PDPL Consent Center | M40 | P0 (Legal) | 3-5 days |
| 6 | Empty Search Capture | M38 | P0 | 2-4 days |
| 7 | Influencer Attribution | M54 | P0 | 4-6 days |
| 8 | OOS Substitute Engine | M50 | P0 | 5-6 days |
| 9 | First-Time vs Returning | M39 | P0 | 4-5 days |
| 10 | Coming Soon Capture | M51 | P0 | 4-5 days |
| 11 | Cart Sharing | M55 | P0 | 4-5 days |
| 12 | Discovery Quiz | M46 | P0 | 5-7 days |
| 13 | Birthday Capture | M49 | P0 | 2-3 days |
| 14 | Smart Reorder Timing | M44 | P0 | 5-7 days |

**Total Additional Effort:** 38-53 dev days (≈ 8-11 weeks for solo, 4-5 weeks for 2 devs).

### What's Out (Deferred to Phase 1/2)

| Module | Why Out |
|---|---|
| M5 (Ask About Product) | Overlap with Salla Q&A native |
| M8 Restock-only dimension | Overlap with "أعلمني عند التوفر" native |
| M22 (Cart Rescue) | Overlap with Salla abandoned cart |
| M37 (Checkout Hesitation) | Needs Salla checkout verification |
| M41 (Live Stock Urgency) | Theme overlap concerns |
| M42 (Mobile One-Tap) | Salla Wishlist overlap |
| M43 (Pre-Checkout) | Needs Salla checkout verification |
| M45 (Comparison Detector) | Complex session tracking |
| M47 (Bundle Builder) | Large effort (8-10 days) |
| M48 (Recently Viewed) | Theme overlap |
| M52 (Coupon Discovery) | Needs historical search data |
| M53 (Shipping Calc) | Needs Shipping API verification |
| M56 (Sample Request) | Large + operational workflow |
| Modules 1-3, 6, 9-16, 18-21, 23-31, 33, 36 | Phase 1+ / Sister Products |

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

## 27. Detailed Specifications — MVP Features 5-14 + Phase 2 Roadmap

> **SCOPE NOTICE:**
> This section provides **full feature-level specifications** for MVP Features 5-14 (10 modules promoted from Phase 1/2 to MVP per founder decision). Specs match the depth of Features 1-4 (Sections 7-10): description, user flow, functional requirements, UX requirements, configuration, data schema, edge cases, mobile, accessibility, and Salla integration.
>
> Section 27.11 contains condensed roadmap specs for the **10 remaining Phase 2 modules** (37, 41, 42, 43, 45, 47, 48, 52, 53, 56).

---

### 27.1 Feature 5 — PDPL Consent Management Center (Module 40)

#### Description
A customer-facing self-service portal accessed via tokenized URL, allowing data subjects to view all their stored signals, cancel interest signals individually or in bulk, withdraw consent (stopping future communications), and export their data in CSV or JSON format. This module is **required by Saudi PDPL** (effective Sept 2023, mandatory since Sept 2024) and protects against SDAIA fines (48 violation decisions issued since enforcement began).

The portal is accessed via a signed JWT token embedded in every customer-facing email/WhatsApp communication. No login is required — the token IS the proof of identity.

#### User Flow

```
[Customer receives WhatsApp/Email]
     ↓
[Clicks "إدارة بياناتي" / "Manage my data" link]
     ↓
[Token-based URL opens consent portal]
     ↓
[Portal displays:
  - All interest signals (active + triggered)
  - All hesitation submissions (if PII attached)
  - Consent timestamp + version
]
     ↓
[Customer can:
  - Cancel individual signal
  - Bulk delete all data
  - Withdraw consent
  - Export data (CSV/JSON)
]
     ↓
[Confirmation email + audit log entry]
```

#### Functional Requirements

- **FR-40.1** URL pattern: `/v1/public/consent/manage?token=<jwt>`. JWT contains: customer_phone_hash, merchant_id, issued_at, expires_at (30 days from issue).
- **FR-40.2** Token signed with RS256 using rotated key (90-day rotation). Verify signature server-side on every request.
- **FR-40.3** Display all interest signals where status IN ('active', 'triggered', 'expired') sorted by created_at DESC.
- **FR-40.4** Display all hesitation submissions where customer_phone matches (only if PII was attached).
- **FR-40.5** "Cancel signal" action updates status='cancelled', cancelled_at=NOW(). Removes from notification queue.
- **FR-40.6** "Delete all my data" prompts confirmation modal. Then cascade deletes (audit log retained for legal).
- **FR-40.7** "Withdraw consent" updates consent_records.withdrawn_at=NOW(), stops all future communications.
- **FR-40.8** "Export data" generates CSV/JSON with: signal_id, product_name, interest_type, target_value, created_at, status, notification_history.
- **FR-40.9** All actions logged to `consent_actions` table with: action_type, ip, user_agent, performed_at.
- **FR-40.10** Email confirmation sent after each major action (delete, withdraw) — uses merchant's brand template.
- **FR-40.11** Page available in Arabic + English with auto-detect from token claim or browser locale.
- **FR-40.12** Rate limit: 10 actions/min per token (prevent abuse if token leaked).

#### UX Requirements

**Visual Design:**
- Clean, trust-conveying (NOT marketing-styled)
- Calming colors: white background, dark text, blue accent
- Clear hierarchy: identity → data list → action buttons
- "Last updated" timestamp visible at top

**Page Structure:**
1. Header: "إدارة بياناتي" + masked phone (last 4 visible)
2. Active signals (cards with cancel button)
3. Triggered/expired signals (collapsed)
4. Bulk actions (Export, Delete All, Withdraw Consent)
5. PDPL compliance notice + support contact

**Animation:**
- Action feedback: subtle slide + check mark
- Loading states for async operations
- Toast confirmations (3s auto-dismiss)

**Responsive:** Mobile-first (most access from email links on phone)

#### Configuration

```typescript
interface ConsentCenterConfig {
  tokenExpiryDays: number;         // default 30
  tokenRotationDays: number;       // signing key rotation, default 90
  rateLimitPerMin: number;         // default 10
  emailTemplateAr: string;         // confirmation template
  emailTemplateEn: string;
  brandPrimaryColor: string;       // from merchant settings
  brandLogoUrl: string;
  privacyPolicyUrl: string;
}
```

#### Data Captured

```typescript
interface ConsentAction {
  id: string;                      // UUID
  merchant_id: string;
  customer_phone_hash: string;
  action_type: 'page_view' | 'cancel_signal' | 'bulk_delete' | 'withdraw_consent' | 'export_data';
  signal_ids?: string[];           // if cancel/bulk_delete
  export_format?: 'csv' | 'json';
  ip: string;
  user_agent: string;
  locale: 'ar' | 'en';
  performed_at: timestamp;
}
```

#### Edge Cases

| Edge Case | Behavior |
|---|---|
| Token expired | Show regeneration page: "Enter your phone to receive new link" |
| Token signature invalid | 401 + log security event |
| Customer has 0 signals | Show empty state: "ما عندك بيانات مخزنة معنا" |
| Bulk delete on 1000+ signals | Confirm + batch process (100/batch) |
| Customer already withdrew consent | Show banner with re-enroll option |
| Export request size > 10MB | Send via email instead of direct download |
| Token leaked / suspicious activity | Rate limit + security audit log |
| Merchant uninstalled app | Show "Merchant no longer active" + allow deletion |

#### Mobile, Accessibility & Integration

- **Mobile:** Bottom sheet for confirmation modals, 48px tap targets, single-column, sticky actions
- **A11y:** WCAG AA, screen reader announces results via `aria-live`, focus trap in modals
- **Salla Integration:** No direct integration (self-hosted URL). Link must be in all email/WhatsApp templates.

#### Effort
Medium: **3-5 dev days** (1 backend + 1 frontend)

---

### 27.2 Feature 6 — Empty Search Capture (Module 38)

#### Description
Captures customer search queries that returned no results, converting "invisible inventory misses" into a structured demand signal. When a visitor searches for a product the store doesn't carry, instead of letting them leave silently, we capture the searched term + optional contact info, and surface aggregated insights in the merchant dashboard. This turns search failures into reorder/expansion opportunities.

#### User Flow

```
[Customer searches in Salla store]
     ↓
[Search returns 0 results]
     ↓
[Page detects empty state via .s-search-no-results class]
     ↓
[Smart Snippet capture form injected automatically]
     ↓
[Form pre-fills searched query]
     ↓
[Customer adds phone (optional) + PDPL consent]
     ↓
[Submit → "نخبرك إذا وفرناه"]
     ↓
[Aggregated in missed_searches table]
```

#### Functional Requirements

- **FR-38.1** Detect empty search state via DOM observation: presence of `.s-search-no-results` class OR text content matching "لا توجد نتائج" / "No results".
- **FR-38.2** Inject capture form within 100ms of empty state detection.
- **FR-38.3** Auto-populate search query in form (read-only display + hidden field).
- **FR-38.4** Phone input optional (PDPL consent only required if phone provided).
- **FR-38.5** Store in `missed_searches` table with: merchant_id, query, customer_phone_hash (if provided), session_id, page_url, search_timestamp.
- **FR-38.6** Aggregate identical queries (case-insensitive, normalized whitespace) and increment frequency counter.
- **FR-38.7** Dashboard widget: "Top missed searches" sorted by frequency, time-filterable (7d/30d/all).
- **FR-38.8** Doctor rule: If query frequency > 10 in 30 days → suggest "Consider adding this product/category".
- **FR-38.9** Optional: notify customers if matching product is added later (consent-based).
- **FR-38.10** Anonymous mode: capture query even without phone (high-volume signal).

#### UX Requirements

**Form Style:**
- Minimal, non-intrusive
- Appears below "No results" message with smooth slide-in
- "نريد توفير ما تبحث عنه!" headline
- Single-line phone input + PDPL checkbox + Submit

**Visual Design:**
- Subtle background color (light blue/gray)
- Same border-radius as Salla theme
- Friendly emoji 📩 or 🔍

**Empty State Replacement:**
- Original "No results" message preserved
- Form appears below as enhancement

#### Configuration

```typescript
interface EmptySearchCaptureConfig {
  enabled: boolean;
  detectionSelectors: string[];           // CSS selectors for empty state
  detectionTextPatterns: string[];        // Text patterns to match
  capturePhone: boolean;                  // default true
  capturePhoneRequired: boolean;          // default false
  headline_ar: string;
  headline_en: string;
  ctaLabel_ar: string;
  ctaLabel_en: string;
  notifyOnMatch: boolean;                 // notify customer if added later
}
```

#### Data Captured

```typescript
interface MissedSearch {
  id: string;
  merchant_id: string;
  query: string;                          // raw query
  normalized_query: string;               // lowercase, trimmed, deduplicated
  customer_phone_hash?: string;
  customer_email?: string;
  consent_given_at?: timestamp;
  session_id: string;
  page_url: string;
  search_timestamp: timestamp;
  device_type: 'desktop' | 'mobile' | 'tablet';
  notified_at?: timestamp;                // when product was added
  created_at: timestamp;
}
```

#### Edge Cases

| Edge Case | Behavior |
|---|---|
| Empty query (just whitespace) | Don't capture |
| Search by SKU or product code | Capture normally (signal still useful) |
| Customer submits same search twice in session | Update timestamp, don't duplicate |
| Salla theme uses different no-results class | Configurable detection selectors |
| Search returns 1 result but customer leaves | Don't trigger (only on 0 results) |
| Malicious queries (SQL injection attempt) | Sanitize, store, flag for review |
| 1000+ identical queries in 1 day | Throttle aggregation, still log all |
| Customer doesn't submit (leaves page) | Capture query anonymously (no phone) |

#### Mobile, Accessibility & Integration

- **Mobile:** Stack form vertically, large input field, sticky submit button
- **A11y:** Form fields labeled, error messages via `aria-live`, keyboard navigable
- **Salla Integration:** Twilight `<salla-search>` component (Confirmed via docs.salla.dev/422730m0). Uses `.s-search-no-results` CSS hook for detection.

#### Effort
Small-Medium: **2-4 dev days** (1 frontend, mostly DOM observation + form)

---

### 27.3 Feature 7 — Influencer Code Capture & Attribution (Module 54)

#### Description
Captures customer traffic from specific influencers (via UTM params or special URL slugs), displays personalized landing experience, auto-applies the influencer's coupon code at checkout, and tracks per-influencer revenue/AOV/conversion/CAC. Solves the critical problem that merchants spending on influencer marketing have no idea which influencer drives real revenue.

#### User Flow

```
[Influencer posts: "Use code SARA20 — store.sa/?ref=sara_kn"]
     ↓
[Customer clicks → arrives with UTM params or ?ref= slug]
     ↓
[Smart Snippet parses URL, identifies influencer]
     ↓
[Personalized banner shown: "👋 شكرًا لزيارتك من سارة!"]
     ↓
[Customer browses, adds to cart]
     ↓
[At checkout: SARA20 coupon auto-applied]
     ↓
[Order completes → attribution recorded]
     ↓
[Dashboard shows: Sara generated X orders, Y revenue, Z% CVR]
```

#### Functional Requirements

- **FR-54.1** Parse URL on every page load for: `utm_source`, `utm_medium`, `utm_campaign`, `?ref=`, `?influencer=`.
- **FR-54.2** Match against merchant's `influencers` config table (slug, coupon_code, display_name, profile_pic_url).
- **FR-54.3** Store influencer attribution in cookie (30-day window) and session.
- **FR-54.4** Display personalized landing banner with influencer name + photo + welcome message.
- **FR-54.5** Auto-apply influencer's coupon at checkout via Salla Coupons API.
- **FR-54.6** Track every order from influencer-attributed sessions in `influencer_orders` table.
- **FR-54.7** Dashboard: per-influencer table showing orders count, revenue, AOV, conversion rate (if traffic data available), CAC (if merchant tracks).
- **FR-54.8** Influencer management UI in merchant dashboard: add/edit/disable influencers, generate URLs.
- **FR-54.9** Optional: pre-applied coupon stays even if customer clears cart (retains attribution for 30 days).
- **FR-54.10** Multi-influencer support: if customer visits via different influencer, latest attribution wins (configurable: first-touch vs last-touch).

#### UX Requirements

**Landing Banner:**
- Sticky top banner (dismissible)
- Influencer photo + name + welcome message
- "Code automatically applied at checkout" reassurance
- Branded with merchant theme

**Checkout Display:**
- Coupon line item shows: "Discount (Influencer: Sara) -20%"
- Builds trust + transparency

**Merchant Dashboard:**
- Influencer leaderboard sorted by revenue
- Drill-down per influencer: orders, top products purchased
- Export CSV for finance/accounting

#### Configuration

```typescript
interface InfluencerConfig {
  id: string;
  merchant_id: string;
  slug: string;                            // URL identifier (e.g., "sara_kn")
  display_name: string;
  profile_pic_url?: string;
  coupon_code: string;                     // matches Salla coupon
  commission_percent?: number;             // for tracking (informational)
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

| Edge Case | Behavior |
|---|---|
| Customer visits via 2 influencers in same session | Apply attribution_mode rule |
| Influencer coupon already expired in Salla | Show "Code expired" + log alert |
| Influencer disabled mid-session | Honor session, no new attributions |
| Customer manually enters different coupon at checkout | Honor manual entry, log attribution loss |
| Bot traffic with influencer params | Filter by user_agent + behavioral heuristics |
| UTM params changed mid-checkout | Last-applied wins (configurable) |
| Order refunded after attribution | Mark attribution as refunded, deduct from revenue |
| Merchant adds influencer with duplicate slug | Validation error in admin UI |

#### Mobile, Accessibility & Integration

- **Mobile:** Banner is sticky-top with smaller size, dismissible
- **A11y:** Influencer name announced on landing, keyboard-dismissible banner
- **Salla Integration:** Coupons API for auto-apply (Confirmed). Salla webhooks for order tracking. Twilight body hooks for banner injection.

#### Effort
Medium: **4-6 dev days** (parser + dashboard + admin UI)

---

### 27.4 Feature 8 — Out-of-Stock Substitute Engine (Module 50)

#### Description
When a customer lands on a product page where the item is out of stock, instead of just showing "Notify me when available" (which captures latent interest but loses immediate sales), this engine actively suggests 3 similar in-stock products + optionally captures preference for original. Drives substitute conversion (target: 30-40% of OOS traffic recovers as alternative purchase).

#### User Flow

```
[Customer visits PDP for product]
     ↓
[Product detected as OOS (stock = 0)]
     ↓
[Standard "Out of Stock" replaced with substitute panel]
     ↓
[Panel shows:
  - "هذا المنتج نفد. هل تجربين بدائل مشابهة؟"
  - 3 alternatives (same category, similar price, similar attributes)
  - "أو احفظ الأصلي للانتظار" button
]
     ↓
[Customer either:
  A) Clicks alternative → goes to PDP → may convert
  B) Saves original → standard back-in-stock flow
  C) Leaves → tracked as "lost despite substitute offer"
]
```

#### Functional Requirements

- **FR-50.1** Detect OOS state via Salla Products API: stock_quantity === 0 OR availability === 'out_of_stock'.
- **FR-50.2** Query Products API for similar products: same category, price within ±30%, similar tags/attributes.
- **FR-50.3** Rank candidates by: same brand (+10), close price (+5), same color/size (+5), best-seller status (+3).
- **FR-50.4** Display top 3 candidates in substitute panel with image, name, price, "View" button.
- **FR-50.5** Replace standard Salla "Out of Stock" message with our substitute panel.
- **FR-50.6** Provide secondary action: "احفظ هذا المنتج" → falls through to Module 8 (Back-in-Stock signal).
- **FR-50.7** Track event when customer clicks alternative (was offered, was clicked, did_convert).
- **FR-50.8** Dashboard metric: "OOS Recovery Rate" = (substitute conversions) / (OOS PDP visits).
- **FR-50.9** Configurable substitute matching: by category only, by attributes, by AI similarity (Phase 3).
- **FR-50.10** Doctor signal: if substitute conversion rate < 15%, suggest improving product taxonomy/tags.

#### UX Requirements

**Substitute Panel Design:**
- Replaces "Out of Stock" badge area on PDP
- Soft empathy: "😔 هذا المنتج نفد حاليًا — إليكِ بدائل قد تعجبكِ"
- 3 product cards horizontal (mobile: vertical scroll)
- Each card: image, name, price, "تصفح" button
- "بدلًا من ذلك، احفظ الأصلي" link below

**Visual:**
- Cards similar to Salla product cards (inherit theme)
- Subtle highlight on hover
- Clear price comparison if alternatives are cheaper

#### Configuration

```typescript
interface OOSSubstituteConfig {
  enabled: boolean;
  numberOfAlternatives: number;            // default 3
  matchingStrategy: 'category_only' | 'attributes' | 'ai_similar';
  priceRangeFactor: number;                // default 0.3 (±30%)
  fallbackToBackInStock: boolean;          // default true
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
  alternatives_shown: string[];            // array of product_ids
  alternative_clicked?: string;            // product_id if clicked
  saved_original: boolean;                 // fell through to back-in-stock
  resulted_in_purchase?: boolean;          // tracked if same session
  purchased_product_id?: string;
  created_at: timestamp;
}
```

#### Edge Cases

| Edge Case | Behavior |
|---|---|
| Product has no similar items in catalog | Hide substitute panel, show back-in-stock only |
| All alternatives also OOS | Filter only in-stock, show fewer if needed |
| Customer was specifically searching this SKU | Lower priority for substitutes (track as searched) |
| Substitute is more expensive | Show price difference clearly, no surprise |
| Substitute conversion vs original restock | Both tracked separately for merchant decision |
| Bot/scraper detected | Skip substitute display (waste of API calls) |
| Merchant disables product mid-display | Auto-refresh, exclude from alternatives |
| Customer dismisses panel | Show back-in-stock CTA instead |

#### Mobile, Accessibility & Integration

- **Mobile:** Vertical scroll for alternatives, larger images
- **A11y:** Each alternative is a focusable button, prices announced
- **Salla Integration:** Products API for similarity queries, Twilight PDP hooks for injection. May require custom event listener if Salla auto-renders OOS message.

#### Effort
Medium: **5-6 dev days** (matching algorithm + UI + tracking)

---

### 27.5 Feature 9 — First-Time vs Returning Recognition (Module 39)

#### Description
Provides a different first-touch experience based on whether the visitor is new (anonymous, no cookie) or returning (recognized via cookie OR Salla customer login). For new visitors, presents a 3-option intent selector (gift / personal / browse). For returning visitors, shows last-viewed product + welcome-back. This produces immediate intent classification for segmentation + better personalized experience.

#### User Flow

```
[Visitor lands on store homepage or category]
     ↓
[Smart Snippet checks: 
  - Cookie: has_visited=true?
  - Salla customer object: logged_in?
]
     ↓
[CASE A: First-time visitor]
     ↓
[Welcome banner: 3 intent options]
     ↓
[Customer taps: "🎁 هدية" / "💄 لي شخصيًا" / "🔍 أتصفح"]
     ↓
[Tag stored in session + cookie set]
     ↓
[Personalized navigation/category prioritization]

[CASE B: Returning visitor]
     ↓
[Welcome-back banner with name (if known)]
     ↓
[Last-viewed product strip]
     ↓
[Optionally: AI suggestion based on past intent]
```

#### Functional Requirements

- **FR-39.1** Detect visitor state on initial page load: read `ss_returning` cookie + Salla customer.is_logged_in flag.
- **FR-39.2** First-time: show intent banner on homepage and category pages (NOT PDP/cart).
- **FR-39.3** Intent options: configurable per merchant (default 3: gift/personal/browse).
- **FR-39.4** On intent click: set cookie `ss_returning=true` + `ss_intent=<value>`, store in session.
- **FR-39.5** Returning visitor: show personalized banner with stored intent or last activity reference.
- **FR-39.6** If Salla customer logged in: show name from Salla customer object.
- **FR-39.7** Last-viewed product strip uses localStorage cache of recent PDP visits.
- **FR-39.8** Dashboard: visitor intent distribution (% gift, personal, browse) for marketing segmentation.
- **FR-39.9** Doctor rule: if gift intent > 30%, suggest gift-focused homepage section or Gift Finder app.
- **FR-39.10** Optional: pass intent tag to URL params for marketing pixels (Facebook custom audience).

#### UX Requirements

**First-Time Banner:**
- Top of page, dismissible
- Three large tap-friendly buttons
- Emoji + clear label per option
- Subtle, not aggressive

**Returning Banner:**
- More personal: "👋 مرحبًا بعودتك" + name if known
- Shows: last-viewed product card + "متابعة" CTA
- Includes "Continue where you left off" link

**Visual:**
- Different colors for first-time (welcoming blue) vs returning (warm yellow/orange)
- Smooth slide-in animation
- Auto-dismiss after intent selected (first-time)

#### Configuration

```typescript
interface VisitorRecognitionConfig {
  enabled: boolean;
  firstTimePages: string[];                // page types where banner shows
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
  passIntentToPixel: boolean;              // for FB/Google audiences
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
  intent_tag?: string;                     // gift/personal/browse/etc.
  selected_at?: timestamp;
  last_visit_at?: timestamp;
  total_visits: number;
  first_visit_at: timestamp;
  last_intent?: string;                    // from previous session
}
```

#### Edge Cases

| Edge Case | Behavior |
|---|---|
| Customer clears cookies | Treated as first-time again (acceptable) |
| Salla logged-in but no cookie | Use customer ID, set cookie |
| Cookie says returning but Salla logged out | Trust cookie, no name shown |
| Intent selected but customer changes mind | Allow override, log changes |
| Banner dismissed without intent | Log dismissal, no tag |
| Mobile vs desktop different browsers | Independent (acceptable) |
| Bot/crawler traffic | Skip banner entirely (UA detection) |
| Customer with ad blocker | Banner may not render; graceful fallback |

#### Mobile, Accessibility & Integration

- **Mobile:** Stacked button layout, larger tap targets
- **A11y:** Intent options as proper buttons, keyboard navigable, announced
- **Salla Integration:** Twilight SDK for customer state (Confirmed via docs.salla.dev/422610m0)

#### Effort
Medium: **4-5 dev days**

---

### 27.6 Feature 10 — Coming Soon / Pre-Launch Capture (Module 51)

#### Description
For products that are configured but not yet publicly available (status="hidden" or custom "coming_soon" tag), replaces the standard PDP with a pre-launch teaser featuring product photo, expected launch date, and an interest capture form (phone or email). Optionally offers early-bird discount coupon to subscribers. When product status changes to "active", auto-notifies all subscribers via WhatsApp/Email.

This converts pre-launch curiosity into a guaranteed first-day sales list.

#### User Flow

```
[Merchant creates product in Salla with status="hidden" + tag "coming_soon"]
     ↓
[Customer somehow accesses URL (preview link, leaked URL, etc.)]
     ↓
[Smart Snippet detects status, replaces PDP with teaser]
     ↓
[Teaser shows:
  - Product photo (slightly blurred or full)
  - Expected launch date
  - Description teaser
  - "اشتركي لتنبيهك عند الإطلاق" form
  - Optional: "احصلي على 15% خصم Early Bird"
]
     ↓
[Customer submits → added to pre_launch_subscribers table]
     ↓
[When product status → "active":
  - Auto-notify all subscribers
  - Provide early-bird coupon if configured
]
```

#### Functional Requirements

- **FR-51.1** Detect product status from Twilight context: status === 'hidden' OR has tag 'coming_soon'.
- **FR-51.2** Replace default Salla PDP rendering with pre-launch template (via Twilight hooks).
- **FR-51.3** Pre-launch template shows: product images (blurred config option), name, teaser description, expected launch date.
- **FR-51.4** Capture form: phone OR email (at least one required) + PDPL consent + optional early-bird opt-in.
- **FR-51.5** Store in `pre_launch_subscribers` table: customer_phone_hash, product_id, subscribed_at, early_bird_opt_in.
- **FR-51.6** Subscribe to Salla `product.status.updated` webhook.
- **FR-51.7** When status changes to 'active': queue notifications to all subscribers within 5 minutes.
- **FR-51.8** Notification template: includes product link, optional early-bird coupon code (auto-generated single-use).
- **FR-51.9** Track conversion: subscribers → first-day purchases attribution.
- **FR-51.10** Dashboard: per-product pre-launch subscriber count, conversion rate after launch.

#### UX Requirements

**Pre-Launch Page Design:**
- Build anticipation: large product image, teaser tagline
- Countdown timer to launch date (if known)
- "اشترك للحصول على وصول مبكر" CTA
- Trust signals: "X متابع للإطلاق"
- Social share buttons (Twitter/Instagram)

**Visual:**
- Cinematic feel (different from regular PDP)
- Premium typography
- Subtle animation on countdown

**Notification UX:**
- WhatsApp message with product image + "تم الإطلاق!" + early-bird code
- Email version with rich product preview

#### Configuration

```typescript
interface PreLaunchConfig {
  enabled: boolean;
  detectionMethod: 'status_hidden' | 'custom_tag' | 'both';
  customTagName: string;                   // default "coming_soon"
  imageBlur: boolean;                      // default false
  showCountdown: boolean;
  earlyBirdEnabled: boolean;
  earlyBirdDiscountPercent: number;        // default 15
  earlyBirdCouponPrefix: string;           // e.g., "EARLY_"
  notificationChannels: ('whatsapp' | 'email')[];
  notificationDelaySeconds: number;        // default 300 (batch notifications)
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
  purchase_attributed?: string;            // order_id if converted
  subscribed_at: timestamp;
}
```

#### Edge Cases

| Edge Case | Behavior |
|---|---|
| Product status reverts from active → hidden | Don't re-notify, but show "back to pre-launch" for new visitors |
| Subscriber already has account | Match by email/phone, link to existing |
| Launch date passes without status change | Show "delayed" message + invite re-subscribe |
| Customer unsubscribes before launch | Honor immediately, remove from queue |
| Early-bird coupon limits (e.g., first 100 only) | Configurable limit + waitlist |
| Multiple products coming soon, customer subscribes to several | Independent subscriptions per product |
| Merchant deletes product before launch | Notify subscribers of cancellation |
| 1000+ subscribers at launch time | Batch notifications over 1 hour to respect rate limits |

#### Mobile, Accessibility & Integration

- **Mobile:** Full-screen experience, large CTA button at bottom
- **A11y:** Countdown announced periodically, form fields labeled
- **Salla Integration:** Products API for status detection, `product.updated` webhook (Confirmed) for status change events, Twilight PDP override

#### Effort
Medium: **4-5 dev days**

---

### 27.7 Feature 11 — Cart Sharing & Save Link (Module 55)

#### Description
Generates a shareable URL containing the customer's cart state, allowing them to send the cart to friends/family/themselves via WhatsApp, Email, or copy-paste. Optionally rewards both sharer and buyer with discount if shared cart converts. Enables social commerce patterns (gift lists, "look what I want" sharing) that Salla doesn't natively support.

#### User Flow

```
[Customer adds 3-5 items to cart]
     ↓
[Sees "💾 احفظي أو شاركي السلة" button in cart]
     ↓
[Clicks → modal opens with options]
     ↓
[Three options:
  A) Copy link
  B) Share to WhatsApp (deep link)
  C) Send to email
]
     ↓
[Link generated with JWT containing cart state]
     ↓
[Recipient opens link → cart reconstructed in their browser]
     ↓
[If recipient purchases → both get 10% discount]
     ↓
[Track in cart_shares table]
```

#### Functional Requirements

- **FR-55.1** "Share Cart" button injected into Salla cart page via Twilight hooks.
- **FR-55.2** On click: serialize cart state to JWT (product_ids, quantities, variants, applied coupons).
- **FR-55.3** Generate shareable URL: `/cart/share/<jwt_token>` with 30-day expiry.
- **FR-55.4** Modal shows: copy link, WhatsApp share, email share, optional sharer's note (max 200 chars).
- **FR-55.5** Recipient clicks link → cart state reconstructed in their Salla session (preserving their account).
- **FR-55.6** Recipient sees "هذه السلة من [Sharer]" banner with sharer's note if provided.
- **FR-55.7** Track share-to-purchase attribution: cart_share_id linked to subsequent order.
- **FR-55.8** Dual reward (if configured): apply coupon to recipient at checkout, credit sharer's account.
- **FR-55.9** Dashboard: total shares, share conversion rate, top sharers leaderboard.
- **FR-55.10** Sharing analytics: which channels work best (WhatsApp vs email), avg cart value shared.

#### UX Requirements

**Share Modal:**
- Three large action buttons (copy, WhatsApp, email)
- Preview of shared cart (top 3 items + total)
- Optional note field
- "🎁 كلاكما يحصل على 10% خصم" reassurance

**Recipient Experience:**
- Friendly banner: "👋 [Name] شاركت معك هذه السلة"
- Optional note from sharer prominently displayed
- Items pre-added to recipient's cart
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
    minOrderValue?: number;                // discount eligibility
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
  cart_state: {                            // serialized cart
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

| Edge Case | Behavior |
|---|---|
| Recipient adds items + shared items | Combine into single cart |
| Shared item now out of stock | Show "X is now unavailable" + remove from cart |
| Shared coupon now expired | Show notice, recipient can still buy at regular price |
| Token tampered | 400 + log security event |
| Token expired (>30 days) | Show "This shared cart has expired" + suggest fresh browse |
| Same recipient opens link 10 times | Track unique vs total opens |
| Sharer not logged in (anonymous) | Can still share, attribution stored in cookie |
| Self-share (sharer = recipient) | Allow (legitimate use case: save cart for later) |

#### Mobile, Accessibility & Integration

- **Mobile:** Native WhatsApp share intent, share sheet support on iOS/Android
- **A11y:** All share options keyboard accessible, screen reader announces share confirmation
- **Salla Integration:** Cart API for state reconstruction, Coupons API for dual reward

#### Effort
Medium: **4-5 dev days**

---

### 27.8 Feature 12 — Vertical Discovery Quiz (Module 46)

#### Description
A short interactive quiz (3-5 questions, < 60 seconds) tailored to the merchant's vertical (Beauty / Fashion / Perfumes / Gifts / Other) that builds a `customer_profile` JSON. The profile captures preferences (e.g., skin type, style preference, scent family) that informs product recommendations, email campaigns, and dashboard segmentation. Increases repeat purchase rate by ~2.3x compared to unprofiled customers.

#### User Flow

```
[Customer visits homepage or category page]
     ↓
[First-time + selected "Personal" intent (from Module 39)]
     ↓
[CTA appears: "🌟 اعرفي بشرتك خلال 60 ثانية"]
     ↓
[Customer clicks → quiz modal opens]
     ↓
[3-5 multi-choice questions per vertical template]
     ↓
[Generates profile: e.g., { skin_type: 'oily', concerns: ['acne', 'oiliness'], routine_level: 'intermediate' }]
     ↓
[Shows: "✨ ملف بشرتك جاهز" + 3 recommended products]
     ↓
[Optional: capture phone for personalized recommendations later]
     ↓
[Profile stored, used for filtering + campaigns]
```

#### Functional Requirements

- **FR-46.1** Configurable quiz templates per vertical (default: beauty, fashion, perfumes, gifts).
- **FR-46.2** Each template: 3-5 questions, multi-choice or single-choice, with branching logic.
- **FR-46.3** Quiz UI: progress bar, "Next" / "Back" buttons, "Skip" option.
- **FR-46.4** Generate `customer_profile` JSON with: vertical-specific dimensions (e.g., skin_type for beauty).
- **FR-46.5** Store profile in `customer_profiles` table (linked to phone hash or customer_id).
- **FR-46.6** Apply profile to PDP filtering: highlight products matching profile.
- **FR-46.7** Doctor rule: surface products customers profiled but didn't buy.
- **FR-46.8** Profile-based segmentation in dashboard (e.g., "Customers with dry skin: 234").
- **FR-46.9** Email/WhatsApp campaigns can filter by profile attributes.
- **FR-46.10** Allow profile update/retake.
- **FR-46.11** Show "Recommended for you" badges on products matching profile (subtle UI).
- **FR-46.12** Track quiz completion rate, drop-off question, time-to-complete.

#### UX Requirements

**Quiz Design:**
- Modal that's "fun, not interrogating"
- Visual options with icons/images where helpful
- Smooth transitions between questions
- "Skip" available but discouraged subtly

**Result Screen:**
- "✨ ملف بشرتك جاهز" with profile summary
- 3 recommended products shown immediately
- "احفظي ملفك" CTA (capture phone optional)

**Profile Application:**
- Subtle "Match" badge on products matching profile
- "ملفك" filter chip in category pages

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
  resultMapping: {                         // profile generation logic
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
  profile_data: Record<string, any>;       // flexible per vertical
  quiz_completion_seconds: number;
  questions_answered: number;
  questions_skipped: number;
  completed_at: timestamp;
  updated_at: timestamp;
}
```

#### Edge Cases

| Edge Case | Behavior |
|---|---|
| Customer starts quiz, abandons mid-way | Save partial progress, allow resume |
| Customer takes quiz multiple times | Overwrite profile (with consent confirmation) |
| Quiz template changes after profile saved | Re-prompt to update profile |
| Customer skips all questions | Don't save profile, suggest retake later |
| No products match profile | Fall back to category bestsellers |
| Conflicting answers (e.g., "oily skin" + "dry skin") | Last answer wins, flag for review |
| Profile aging (e.g., customer info from 2 years ago) | Suggest update after 365 days |
| Mobile vs desktop different profiles | Allow sync via email/phone match |

#### Mobile, Accessibility & Integration

- **Mobile:** Full-screen takeover modal, swipe between questions
- **A11y:** All options keyboard-navigable, screen reader friendly
- **Salla Integration:** Products API for filtering/recommendations, Customer object for profile linking

#### Effort
Medium-Large: **5-7 dev days** (quiz engine + 3 vertical templates + profile filtering)

---

### 27.9 Feature 13 — Birthday/Anniversary Capture (Module 49)

#### Description
Captures personal dates (birthday, wedding anniversary, etc.) from customers via opt-in forms (post-checkout or in account section), then triggers personalized WhatsApp/Email campaigns 3 days before the event with a gift code or special offer. Birthday campaigns historically achieve 3-4x higher CTR than generic emails and build emotional loyalty.

#### User Flow

```
[Trigger Point A: Post-checkout success page]
     ↓
[Banner: "🎉 لنحتفل بكِ! أخبرينا متى عيد ميلادك (اختياري)"]
     ↓
[Customer fills DD/MM (year optional)]
     ↓
[Stored in birthday_subscribers table with PDPL consent]

     ────────────────────────────

[Trigger Point B: Daily cron at 8 AM Saudi time]
     ↓
[Finds all subscribers with birthday in 3 days]
     ↓
[Queue WhatsApp/Email with personalized gift code]
     ↓
[Customer receives: "🎂 عيد ميلاد سعيد! هدية لكِ: code BIRTHDAY20"]
```

#### Functional Requirements

- **FR-49.1** Form fields: birthday (DD/MM required, YYYY optional), anniversary (DD/MM optional).
- **FR-49.2** PDPL-compliant consent: explicit checkbox, documented.
- **FR-49.3** Two trigger points configurable: post-checkout, account section, both.
- **FR-49.4** Daily cron at 8 AM Saudi time scans `birthday_subscribers` for dates matching today + 3.
- **FR-49.5** Queue notification with: personalized greeting, gift code (auto-generated single-use), expiry (14 days).
- **FR-49.6** Gift code amount configurable per merchant (default 20% off, max value).
- **FR-49.7** Track campaign metrics: sent, opened, clicked, redeemed.
- **FR-49.8** Dashboard: "Birthdays this month" calendar view, campaign performance.
- **FR-49.9** Optional: anniversary campaigns same logic with different message.
- **FR-49.10** Year-of-birth not required (respect privacy); use date only.

#### UX Requirements

**Capture Form:**
- Friendly: "🎉 لنحتفل بكِ"
- Two date inputs (DD/MM dropdowns, large touch targets)
- Year optional with note
- Consent checkbox clear

**Notification Design:**
- Festive WhatsApp template with emoji + image
- Personalized name if known
- Clear CTA: "استخدمي الكود قبل [date]"

**Dashboard:**
- Calendar view showing upcoming birthdays
- Campaign creator with template preview

#### Configuration

```typescript
interface BirthdayCaptureConfig {
  enabled: boolean;
  triggerPoints: ('post_checkout' | 'account_section' | 'banner')[];
  captureAnniversary: boolean;
  notificationDaysBefore: number;          // default 3
  giftCode: {
    discountType: 'percent' | 'fixed';
    discountValue: number;                 // 20 (%)
    maxValue?: number;                     // cap
    expiryDays: number;                    // default 14
    codePrefix: string;                    // e.g., "BIRTHDAY_"
  };
  channels: ('whatsapp' | 'email')[];
  messageTemplate_ar: string;              // with {{name}}, {{code}}
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
  birthday_year?: number;                  // optional
  anniversary_day?: number;
  anniversary_month?: number;
  consent_given_at: timestamp;
  last_notified_at?: timestamp;
  last_redemption_at?: timestamp;
  subscribed_at: timestamp;
}
```

#### Edge Cases

| Edge Case | Behavior |
|---|---|
| Feb 29 birthday | Notify on Feb 28 in non-leap years |
| Customer enters past date for "anniversary" | Accept, treat as past anniversary |
| Multiple subscribers same phone | Use last submission (likely typo correction) |
| Customer unsubscribes before birthday | Honor immediately, no notification |
| Birthday today (no 3-day buffer) | Send same-day greeting (no gift code expiring) |
| Channel fails (WhatsApp blocked) | Fallback to email |
| Gift code already used | Show "Already redeemed" + offer regular discount |
| Merchant disables campaign mid-cycle | Stop future notifications, honor in-progress |

#### Mobile, Accessibility & Integration

- **Mobile:** Native date picker, optimized form layout
- **A11y:** Date fields labeled, year-optional clearly indicated
- **Salla Integration:** Possible Salla customer.birthday field — verify if natively supported. Coupons API for gift code generation. WhatsApp/Email infrastructure from MVP.

#### Effort
Small: **2-3 dev days**

---

### 27.10 Feature 14 — Smart Reorder Timing (Module 44)

#### Description
Auto-triggered reorder reminders based on product category timing (e.g., serum=60 days, supplement=30 days, perfume=90 days). After customer purchases, system tracks expected depletion based on product category, then sends a WhatsApp reminder with one-click reorder link. Drives 22-35% reorder rate increase without manual merchant effort.

#### User Flow

```
[Customer purchases Vitamin C Serum (30ml)]
     ↓
[Product mapped to category: "serum" (60-day reorder timing)]
     ↓
[Daily cron at 8 AM scans orders 55-65 days old]
     ↓
[Finds matching orders, queues WhatsApp]
     ↓
[Customer receives:
  "مرحبًا [Name] 👋
  طلبتي Vitamin C Serum قبل 60 يوم تقريبًا.
  عادة يخلص في هذا الوقت.
  
  طلب جديد بنقرة واحدة؟
  [Reorder] [Remind later]"
]
     ↓
[Customer clicks Reorder → cart auto-populated, ready for checkout]
     ↓
[Track conversion in reorder_reminders table]
```

#### Functional Requirements

- **FR-44.1** `reorder_category_timings` config table maps product categories or product tags to expected depletion days.
- **FR-44.2** Default timings: serum 60d, shampoo 45d, perfume 90d, supplement 30d, vitamin 55d (configurable).
- **FR-44.3** Daily cron at 8 AM Saudi time scans orders aged [timing-5, timing+5] days.
- **FR-44.4** For each matching order, check if customer hasn't reordered same product yet.
- **FR-44.5** Send WhatsApp reminder via merchant's template (Meta-approved).
- **FR-44.6** Reorder link reconstructs cart with original products + applied default shipping.
- **FR-44.7** Track outcomes: reminder_sent, reminder_clicked, resulted_in_reorder.
- **FR-44.8** Dashboard: reorder reminder funnel (sent → clicked → converted).
- **FR-44.9** Doctor rule: if reorder rate < 15% for a category, suggest re-evaluating timing.
- **FR-44.10** Throttle: max 1 reminder per customer per product (don't spam).
- **FR-44.11** Customer can opt out via WhatsApp reply or consent center.

#### UX Requirements

**WhatsApp Message:**
- Personalized: name + product
- Clear value: "حان وقت إعادة الطلب"
- Two options: Reorder now / Remind later
- Unsubscribe link in footer

**Merchant Dashboard:**
- "Reorder Reminders" section
- Funnel chart: sent → clicked → converted
- Per-category breakdown
- Revenue attributed to reminders

#### Configuration

```typescript
interface ReorderTimingConfig {
  enabled: boolean;
  categoryTimings: Map<string, number>;    // category_id → days
  productTagTimings: Map<string, number>;  // tag → days
  defaultTiming: number;                   // fallback, default 60
  scanRangeDays: number;                   // default 5 (timing ± this)
  reminderTemplateAr: string;
  reminderTemplateEn: string;
  channels: ('whatsapp' | 'email')[];
  maxRemindersPerCustomerPerProduct: number; // default 1
  throttlePerDay: number;                  // max reminders sent per day per merchant
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

| Edge Case | Behavior |
|---|---|
| Customer already reordered before reminder | Skip, don't send |
| Customer bought multiple of same product | Adjust expected depletion (e.g., 2x quantity = 2x timing) |
| Product no longer available | Suggest alternative or skip |
| Customer changed phone number | Use latest known via Salla customer object |
| Category timing unknown for new product | Use default timing |
| Customer opted out | Honor, no future reminders |
| Reminder failed (WhatsApp error) | Retry once, then mark as failed |
| Customer reorders after reminder but separately | Track as converted (attribution window 7 days) |

#### Mobile, Accessibility & Integration

- **Mobile:** WhatsApp deep link to merchant store with cart pre-populated
- **A11y:** Email version available for screen reader users
- **Salla Integration:** Orders API to scan orders (Confirmed), WhatsApp BSP for messaging, Cart API for reconstructing cart

#### Effort
Medium: **5-7 dev days**

---

### 27.11 Phase 2 Roadmap (10 Remaining Modules)

These 10 modules remain in Phase 2 roadmap (Months 10-18 post-MVP launch). Specs condensed.

#### Module 37 — Checkout Hesitation Capture
**Description:** Capture abandonment reasons on checkout page specifically.
**Key FRs:** Exit intent detection on checkout, 6-option reason selector, separate analytics from PDP hesitations.
**Salla Integration:** Twilight checkout hooks (⚠️ NEEDS VERIFICATION).
**Effort:** Medium-Large (5-7 days).

#### Module 41 — Live Stock Urgency Signal
**Description:** Transparent stock count + viewing count badge.
**Key FRs:** `product.quantity.low` webhook subscription, threshold-based display, theme overlap detection.
**Effort:** Small-Medium (3-5 days).

#### Module 42 — Mobile One-Tap Interest
**Description:** Anonymous mobile interest capture (Salla Wishlist complement).
**Key FRs:** Sticky heart icon, cookie-based tracking, no PII required.
**Kill Criterion:** If volume < 2x Salla native Wishlist, remove.
**Effort:** Small (2-3 days).

#### Module 43 — Pre-Checkout Confidence Booster
**Description:** Trust signals + WhatsApp CTA above "Place Order".
**Key FRs:** Configurable trust block, WhatsApp support button, conversion tracking.
**Salla Integration:** Twilight checkout hooks (⚠️ NEEDS VERIFICATION).
**Effort:** Small (2-3 days).

#### Module 45 — Comparison Shopping Detector
**Description:** Detect 3+ PDPs in same category, intervene with help widget.
**Key FRs:** Session tracking, category matching, "What's making decision hard?" widget.
**Effort:** Medium-Large (6-8 days).

#### Module 47 — Customer Bundle Builder
**Description:** Customer selects 3+ products → custom bundle with auto-discount.
**Key FRs:** Configurable rules (min/max, eligible categories, tiers), Coupons API for discount.
**Effort:** Large (8-10 days).

#### Module 48 — Recently Viewed Memory Strip
**Description:** Sticky strip of recently viewed products + Dashboard tracking.
**Key FRs:** localStorage cache, view-to-purchase tracking.
**Effort:** Small-Medium (3-4 days).

#### Module 52 — Smart Coupon Discovery
**Description:** Cart-side coupon search + capture of searched non-existent codes.
**Key FRs:** Coupons API integration, capture searched-but-not-found codes.
**Effort:** Medium (4-6 days).

#### Module 53 — Shipping Transparency Calculator
**Description:** Pre-checkout shipping cost calculator on PDP/Cart.
**Key FRs:** City/region detection, real-time shipping calc, "add X for free shipping" progress.
**Salla Integration:** Shipping API (⚠️ VERIFY AVAILABILITY).
**Effort:** Medium (5-7 days).

#### Module 56 — Free Sample / Trial Request
**Description:** Sample request workflow for high-AOV products (>500 SAR).
**Key FRs:** Eligibility detection, sample order creation, conversion tracking.
**Effort:** Large (8-10 days, includes operational workflow).

---

### 27.12 Expanded MVP Total Effort Estimate

| Phase | Modules | Total Effort |
|---|---|---|
| **MVP Features 5-14** | 10 | 41-51 dev days |
| Phase 2 Roadmap (remaining 10) | 10 | 51-69 dev days |
| **Total Roadmap** | 20 | **~92-120 dev days (~18-24 weeks)** |

**With 2 devs (founder + junior) working in parallel:** ~20-22 weeks total MVP timeline.

### 27.13 Critical Path Items

Items that can block multiple modules:
1. **Salla checkout customization verification** — blocks Phase 2 Modules 37, 43, potentially 53.
2. **WhatsApp Business API setup** — blocks MVP Features 13 (Birthday), 14 (Smart Reorder), 10 (Coming Soon).
3. **Salla customer.birthday field availability** — affects MVP Feature 13.
4. **Salla Shipping API availability** — blocks Phase 2 Module 53.
5. **Session tracking infrastructure** — needed for Phase 2 Module 45.

### 27.14 Risks and Mitigations for Expanded MVP

| Risk | Mitigation |
|---|---|
| Timeline extends beyond 22 weeks | Strict scope discipline. Cut features 12-14 if timeline at risk. |
| Cash runway insufficient for 6 months | Raise pre-seed or reduce burn aggressively. |
| Quality suffers from breadth | Mandatory QA week before each feature launch. |
| Feedback delayed (no MVP feedback until Month 5) | Run paid customer interviews monthly during build. |
| Engineering bandwidth | Hire junior dev by Month 2 to support founder. |
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
