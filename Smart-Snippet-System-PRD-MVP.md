# Smart Snippet System — Product Requirements Document (MVP)

> **Version:** 3.0 — Expanded MVP (4 Core Features + 30 Widgets)
> **Date:** 2026-05-13
> **Last Updated:** Replaced 10 additional features with 30 conversion-focused widgets; full spec per widget
> **Status:** Draft — Ready for Engineering & Design Review
> **Audience:** Engineering + Design + Product
> **Related Docs:**
> - [Smart-Snippet-System-Analysis.md](./Smart-Snippet-System-Analysis.md)
> - [Competitive-Landscape-Analysis.md](./Competitive-Landscape-Analysis.md)
> - [Smart-Snippet-System-Business-Plan.md](./Smart-Snippet-System-Business-Plan.md)

---

## جدول المحتويات

1. [Executive Summary](#1-executive-summary)
2. [Background & Context](#2-background--context)
3. [Goals & Non-Goals](#3-goals--non-goals)
4. [Personas & Roles](#4-personas--roles)
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
25. [Appendix](#25-appendix)
26. [Detailed Specifications — 30 Widgets](#26-detailed-specifications--30-widgets)

---

## 1. Executive Summary

### Vision
A Customer Intent Intelligence Platform for Salla stores — captures *why* visitors don't buy, *what* they're waiting for, and *what* to fix on each product. Combined with a library of 30 plug-and-play conversion widgets covering social proof, urgency, trust, seasonal campaigns, popups, and engagement.

### MVP Scope — Expanded (4 Core Features + 29 Widgets)

**Core 4 Features (Customer Intent loop):**
1. **Hesitation Capture Widget** (Why) — Exit intent + Product Clarity surveys
2. **Variant & Price Interest Capture** (Wait) — Multi-dimensional alerts
3. **Intent Dashboard + Product Doctor Lite** (Fix) — Aggregated insights + rule-based recommendations
4. **Widget Analytics** (Measure) — Per-widget performance metrics

**29 Widgets (grouped by category):**

| Category | Count | Widgets |
|---|---|---|
| Social Proof | 3 | Live Viewer Counter · Today's Buyers Counter · Recent Purchase Toast |
| Urgency | 2 | Low Stock Urgency · Stock Progress Bar |
| Contact | 2 | Floating Marketing Button · Quick Contact |
| UX | 2 | Scroll-to-Top · Sticky Add-to-Cart |
| Timer | 2 | Sale Countdown · Free Shipping Countdown |
| Seasonal | 5 | Ramadan Mode · National Day · White Friday · Eid Widget · Back to School |
| Popup | 5 | Welcome Popup · Exit Intent Popup · Newsletter Signup · Cart Abandonment · Age Verification |
| Trust | 3 | Trust Badges · Shipping Info · Return Policy |
| Engagement | 4 | Wishlist Heart · Recently Viewed · Also Bought · Comparison Button |
| Tool | 1 | Widget Customizer |

**Total MVP items:** 4 core features + 29 widgets = **33 items**

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

## 4. Personas & Roles

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

### Tertiary: The Merchant Team Member

**Name:** Mohammed Al-Qahtani
**Age:** 28
**Role:** Marketing/Operations employee at Sara's store
**Reports to:** Sara (Merchant Owner)
**Tech Literacy:** Medium-high. Familiar with dashboards, content tools, basic analytics.

**Goals:**
- Configure and tune widgets day-to-day on behalf of the merchant
- Respond to customer interest signals (price alerts, contact forms)
- Apply Product Doctor recommendations
- Generate weekly reports for the owner

**Access Needed:**
- Read all customer-submitted data
- Edit widget configurations
- Cannot manage billing or team invites
- Cannot delete data (PDPL audit trail)

**Where Smart Snippet Fits:**
Mohammed logs in daily, triages new interest signals, configures seasonal widgets before campaigns, and prepares a Monday digest for Sara.

### Internal: Platform Admin (Smart Snippet Team)

**Name:** Internal user — Customer Success / Engineering / Support
**Role:** Smart Snippet platform operator
**Tech Literacy:** High.

**Goals:**
- Onboard new merchants
- Resolve support tickets
- Monitor platform health (uptime, webhooks, error rates)
- Manage billing operations (refunds, plan changes, comps)
- Enforce PDPL compliance + audit logs
- Toggle feature flags for staged rollouts
- Approve WhatsApp/SMS templates

**Access Needed:**
- Read access to ALL merchants and ALL data (audit-logged)
- Impersonate any merchant for support
- Manage subscriptions across merchants
- Internal-only dashboards (cron health, webhook queue, error tracker, alerting)

**Where Smart Snippet Fits:**
The admin operates an internal dashboard separate from the merchant dashboard. Every privileged action (impersonation, data access, deletion) is logged for compliance.

### 4.5 Roles & Permissions Matrix

The system supports **5 distinct roles**:

1. **Customer** — End user of the Salla store (anonymous or logged-in)
2. **Merchant Owner** — Account-level admin for one Salla store
3. **Merchant Team — Manager** — Invited team member with operational permissions
4. **Merchant Team — Viewer** — Invited team member with read-only access
5. **Platform Admin** — Smart Snippet internal staff

#### Capability Matrix

| Capability | Customer | Merchant Owner | Team: Manager | Team: Viewer | Platform Admin |
|---|---|---|---|---|---|
| **— Storefront —** |  |  |  |  |  |
| Browse store, see widgets render | ✅ | ✅ | ✅ | ✅ | ✅ |
| Submit hesitation reasons | ✅ | — | — | — | — |
| Subscribe to interest signals (price/variant) | ✅ | — | — | — | — |
| Save items to wishlist | ✅ | — | — | — | — |
| Submit contact form / newsletter | ✅ | — | — | — | — |
| Manage own consent (tokenized URL) | ✅ | — | — | — | — |
| Export / delete own data (PDPL) | ✅ | — | — | — | — |
| **— Merchant Dashboard —** |  |  |  |  |  |
| Log into merchant dashboard | — | ✅ | ✅ | ✅ | ✅ (via impersonation) |
| View Intent Dashboard | — | ✅ | ✅ | ✅ | ✅ |
| View Widget Analytics | — | ✅ | ✅ | ✅ | ✅ |
| Configure widgets (edit) | — | ✅ | ✅ | — | ✅ |
| Publish widget changes | — | ✅ | ✅ | — | ✅ |
| Rollback widget version | — | ✅ | ✅ | — | ✅ |
| Apply Doctor recommendations | — | ✅ | ✅ | — | ✅ |
| Dismiss Doctor recommendations | — | ✅ | ✅ | — | ✅ |
| Export data (CSV/JSON) | — | ✅ | ✅ | — | ✅ |
| View customer submissions list | — | ✅ | ✅ | ✅ | ✅ |
| View interest signals list | — | ✅ | ✅ | ✅ | ✅ |
| Manage Salla integration settings | — | ✅ | — | — | ✅ |
| **— Billing & Team —** |  |  |  |  |  |
| View subscription / plan | — | ✅ | ✅ | — | ✅ |
| Upgrade / downgrade plan | — | ✅ | — | — | ✅ |
| Manage payment method | — | ✅ | — | — | ✅ |
| Invite team members | — | ✅ | — | — | ✅ |
| Remove team members | — | ✅ | — | — | ✅ |
| Assign team roles | — | ✅ | — | — | ✅ |
| **— Internal Admin —** |  |  |  |  |  |
| View all merchants list | — | — | — | — | ✅ |
| Impersonate merchant (audit-logged) | — | — | — | — | ✅ |
| Issue refunds / credits | — | — | — | — | ✅ |
| Toggle feature flags | — | — | — | — | ✅ |
| Approve WhatsApp/SMS templates | — | — | — | — | ✅ |
| View platform-wide analytics | — | — | — | — | ✅ |
| Manage cron / webhook health dashboards | — | — | — | — | ✅ |
| Access audit logs | (own only) | (own store only) | — | — | ✅ (all) |
| Send broadcast announcements | — | — | — | — | ✅ |
| Permanently delete merchant data (PDPL) | — | ✅ (own store) | — | — | ✅ (any store) |

### 4.6 Platform Admin Capabilities (Internal Dashboard)

The Platform Admin operates a separate dashboard from the merchant-facing one. It contains:

| Section | Purpose |
|---|---|
| **Merchants Index** | List of all installed merchants — search, filter by plan/status, sort by activity, MRR contribution |
| **Merchant Detail** | Per-merchant view: subscription, install date, last login, widget count, data volume, support tickets |
| **Impersonation** | Log in AS a merchant for support — all actions audit-logged with reason field |
| **Billing Operations** | Process refunds, issue credits, change plans manually, grant comp trials, manage failed payments |
| **Support Tickets** | Ticket queue (if we run support in-platform; otherwise external like Intercom) |
| **Platform Analytics** | MRR, churn, active stores, total submissions, total interest signals, widget adoption rates |
| **Feature Flags** | Toggle features per merchant or globally for staged rollouts |
| **WhatsApp/SMS Template Approvals** | Review and approve merchant-submitted message templates before Meta/Wati submission |
| **Cron / Webhook Health** | Visibility into batch jobs (Doctor rules, aggregation), webhook queue depth, retry stats |
| **Error / Alerting Dashboard** | Sentry integration, error rate by widget, P0/P1 alerts |
| **Audit Log Search** | Search all admin actions across time + merchant — PDPL compliance trail |
| **PDPL Compliance Center** | Pending data deletion requests, consent withdrawal queue, SDAIA inquiry handling workflow |
| **Broadcast Announcements** | Send in-dashboard banners to all merchants (e.g., "Maintenance window tonight") |

### 4.7 Merchant Team Roles Detail

**Owner (1 per store):**
- Created automatically when merchant installs Smart Snippet from Salla App Store
- Tied to the Salla merchant account (cannot be transferred without admin help)
- Full access including billing, team management, and data deletion

**Manager (multiple per store):**
- Invited by Owner via email
- Can configure widgets, view all data, apply recommendations
- Cannot access billing or invite/remove team members
- Cannot delete data permanently

**Viewer (multiple per store):**
- Invited by Owner via email
- Read-only access to dashboard, analytics, submissions, interest signals
- Cannot edit widgets or apply recommendations
- Suitable for stakeholders (founders, investors, agency partners)

**Invitation Flow:**
1. Owner clicks "Invite Team Member" in dashboard
2. Enters email + selects role (Manager / Viewer)
3. System sends invite email with signed token (24h expiry)
4. Invitee creates account (password or Google SSO) → joins store team
5. Invite logged in audit trail

**Team Size by Plan (suggested):**
| Plan | Owner | Manager Slots | Viewer Slots |
|---|---|---|---|
| Basic (99 SAR) | 1 | 1 | 2 |
| Pro (199 SAR) | 1 | 3 | 5 |
| Business (349 SAR) | 1 | Unlimited | Unlimited |

### 4.8 Customer Self-Service Capabilities

End customers do not have a Smart Snippet account. They interact with the system in two modes:

**Anonymous (no Salla login):**
- Browse storefront, see widgets
- Submit hesitation reasons (no PII required)
- Save items to local wishlist (localStorage)
- Add items to comparison tray (localStorage)
- Track recently viewed (localStorage)

**Logged-in (via Salla customer account):**
- All anonymous capabilities PLUS:
- Wishlist syncs across devices (via Salla customer wishlist API)
- Interest signals tied to customer account
- Newsletter subscription tied to customer email

**Self-Service via Tokenized URL (no login needed):**
Every customer-facing email/WhatsApp contains a signed link to a PDPL consent center where the customer can:
- View all stored data linked to their email/phone
- Cancel individual interest signals
- Withdraw consent (stops all future communications)
- Export their data (CSV/JSON)
- Request permanent deletion

(Note: Full PDPL Consent Center is deferred to Phase 1 — see Section 6 "What's Out". MVP provides unsubscribe links only.)

### 4.9 Authentication & Authorization

| Role | Auth Mechanism | Session | 2FA |
|---|---|---|---|
| Customer (anonymous) | Session cookie | Per-tab | — |
| Customer (logged-in) | Salla customer OAuth | Salla-managed | Salla-managed |
| Merchant Owner | Salla merchant OAuth (install flow) | JWT, 7-day refresh | Optional (recommended) |
| Merchant Team | Email + password OR Google SSO | JWT, 7-day refresh | Optional (recommended) |
| Platform Admin | Internal SSO (Google Workspace) | JWT, 1-day refresh | **MANDATORY** |

**Audit logging requirements:**
- All Platform Admin actions logged: who, when, what, why (reason field required for impersonation and data access)
- Merchant Owner actions affecting data (delete, export) logged within store-scoped audit trail
- Customer self-service actions (consent withdrawal, deletion) logged for PDPL compliance
- Audit logs retained for 7 years per PDPL requirements

**Authorization model:**
- Customer scoping: customer can only access own data via signed token
- Merchant scoping: all merchant API endpoints filter by `store_id` from JWT
- Team scoping: team member role checked on every request; permissions enforced server-side (not just UI)
- Admin scoping: full access but audit-logged; sensitive actions (data deletion, refunds) require secondary confirmation

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

### What's In (Build These: 4 Core Features + 29 Widgets)

**Core Customer Intent Loop (Features 1-4) — see Sections 7-10 for detailed specs:**

| # | Feature | Modules Combined | Priority |
|---|---|---|---|
| 1 | Hesitation Capture Widget | M4 + M17 | P0 (Core) |
| 2 | Variant & Price Interest Capture | M7 + M8 (variants/price/follow only, **not restock**) | P0 (Core) |
| 3 | Intent Dashboard + Product Doctor Lite | M32 + M34 | P0 (Core) |
| 4 | Widget Analytics | M35 | P0 (Infrastructure) |

**29 Widgets — see Section 26 for detailed specs per widget:**

| # | Widget | Category | Complexity |
|---|---|---|---|
| 1 | Live Viewer Counter | Social Proof | Medium |
| 2 | Today's Buyers Counter | Social Proof | Simple |
| 3 | Recent Purchase Toast | Social Proof | Medium |
| 4 | Low Stock Urgency | Urgency | Simple |
| 5 | Floating Marketing Button | Contact | Very Simple |
| 6 | Scroll-to-Top | UX | Very Simple |
| 7 | Sticky Add-to-Cart | UX | Simple |
| 8 | Quick Contact | Contact | Simple |
| 9 | Sale Countdown | Timer | Simple |
| 10 | Free Shipping Countdown | Timer | Simple |
| 11 | Stock Progress Bar | Urgency | Simple |
| 12 | Ramadan Mode | Seasonal | Medium |
| 13 | National Day | Seasonal | Simple |
| 14 | White Friday | Seasonal | Medium |
| 15 | Eid Widget | Seasonal | Simple |
| 16 | Back to School | Seasonal | Simple |
| 17 | Welcome Popup | Popup | Simple |
| 18 | Exit Intent Popup | Popup | Medium |
| 19 | Newsletter Signup | Popup | Simple |
| 20 | Cart Abandonment | Popup | Medium |
| 21 | Age Verification | Popup | Very Simple |
| 22 | Trust Badges | Trust | Very Simple |
| 23 | Shipping Info | Trust | Simple |
| 24 | Return Policy | Trust | Very Simple |
| 25 | Wishlist Heart | Engagement | Medium |
| 26 | Recently Viewed | Engagement | Simple |
| 27 | Also Bought | Engagement | Medium |
| 28 | Comparison Button | Engagement | Medium |
| 29 | Widget Customizer | Tool | Complex |

### What's Out (Deferred to Phase 1/2)

The following modules from the original analysis are deferred outside this MVP scope:

| Module | Why Out |
|---|---|
| M5 (Ask About Product) | Overlap with Salla Q&A native |
| M8 Restock-only dimension | Overlap with "أعلمني عند التوفر" native |
| M22 (Cart Rescue) | Overlap with Salla abandoned cart |
| M37 (Checkout Hesitation) | Needs Salla checkout verification |
| M38 (Empty Search Capture) | Deferred to Phase 1 |
| M39 (First-Time vs Returning) | Deferred to Phase 1 |
| M40 (PDPL Consent Center) | Deferred to Phase 1 (legal review pending) |
| M41 (Live Stock Urgency) | Theme overlap concerns |
| M42 (Mobile One-Tap) | Salla Wishlist overlap |
| M43 (Pre-Checkout) | Needs Salla checkout verification |
| M44 (Smart Reorder Timing) | Deferred to Phase 1 |
| M45 (Comparison Detector) | Complex session tracking |
| M46 (Discovery Quiz) | Deferred to Phase 1 |
| M47 (Bundle Builder) | Large effort (8-10 days) |
| M49 (Birthday Capture) | Deferred to Phase 1 |
| M50 (OOS Substitute Engine) | Deferred to Phase 1 |
| M51 (Coming Soon Capture) | Deferred to Phase 1 |
| M52 (Coupon Discovery) | Needs historical search data |
| M53 (Shipping Calc) | Needs Shipping API verification |
| M54 (Influencer Attribution) | Deferred to Phase 1 |
| M55 (Cart Sharing) | Deferred to Phase 1 |
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

## 25. Appendix

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


## 26. Detailed Specifications — 29 Widgets

> **SCOPE NOTICE:**
> This section provides **full-spec specifications** for all 29 widgets in the MVP scope, matching the depth of Features 1-4 (Sections 7-10). Each widget spec includes: description, user flow, functional requirements, UX requirements, configuration options, trigger logic (where applicable), data captured, edge cases, mobile considerations, accessibility, and Salla integration notes.
>
> Widgets are grouped by category for navigation:
> - 26.1 Social Proof (3)
> - 26.2 Urgency (2)
> - 26.3 Contact (2)
> - 26.4 UX (2)
> - 26.5 Timer (2)
> - 26.6 Seasonal (5)
> - 26.7 Popup (5)
> - 26.8 Trust (3)
> - 26.9 Engagement (4)
> - 26.10 Tool (1)
>
> All widgets MUST comply with the Cross-Cutting Requirements in Section 11 (i18n, PDPL, performance budget, mobile responsiveness, WCAG 2.1 AA, security, browser support) and follow the Design Principles in Section 16.1.

---

### 26.1 Social Proof Widgets

#### 26.1.1 Widget 1 — Live Viewer Counter

##### Description
A small floating badge that displays the number of customers currently viewing a product (PDP) or the store (any page) in near-real-time. Builds social validation by signaling product popularity. Uses session heartbeat events from the snippet — does not require external analytics.

**Two display modes (configurable per merchant):**
- **Mode A: Product-level** — "12 شخص يشاهدون هذا المنتج الآن"
- **Mode B: Store-level** — "47 شخص يتصفحون المتجر الآن"

##### User Flow

```
[Customer lands on PDP / store page]
      ↓
[Snippet fires viewer_heartbeat every 15s]
      ↓
[Backend counts active viewers in last 60s rolling window]
      ↓
[Widget renders with smooth count-up animation]
      ↓
[Counter updates every 10-30s via SSE or polling]
      ↓
[Customer leaves page] → Heartbeat stops → Count decays
```

##### Functional Requirements

**FR-W1.1** Widget MUST render on PDP, Category, and Homepage (configurable per merchant).

**FR-W1.2** Counter MUST display real-time viewer count for the current product (Mode A) or current store (Mode B).

**FR-W1.3** Widget MUST update the counter at minimum every 30 seconds and maximum every 5 seconds.

**FR-W1.4** Widget MUST NOT display if viewer count < `min_viewers_threshold` (default: 3) to avoid showing "1 viewer".

**FR-W1.5** Widget MUST cap displayed count at `max_display_count` (default: 999) to prevent inflated numbers.

**FR-W1.6** Widget MUST use a rolling 60-second window to define "currently viewing" — heartbeat received in last 60s.

**FR-W1.7** Widget MUST debounce heartbeat events server-side (max 1 heartbeat per session per 15s).

**FR-W1.8** Counter MUST animate with smooth count-up/down (no abrupt jumps).

**FR-W1.9** Widget MUST support a "boost" multiplier (default: 1.0) to inflate counts within ethical limits (max 2.0x) — disabled by default.

**FR-W1.10** Widget MUST disable itself automatically if observed count is consistently below threshold for 24h (low-traffic store).

##### UX Requirements

- **Position:** Top-right or bottom-right of product image (PDP), top banner (store-level).
- **Visual:** Soft pulse animation (subtle, not distracting). Eye icon + count + label.
- **Color:** Brand color or neutral (configurable).
- **Size:** Compact pill, 32-40px height.
- **Visibility:** Auto-hides after 10 seconds, reappears on scroll up.
- **Typography:** Numbers bold, label regular weight.
- **Animation:** Fade-in on load (300ms), count-up with cubic-bezier easing.
- **Tap behavior:** No interaction on tap (display-only).

##### Configuration Options (Per Merchant)

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `display_mode` | enum | product | `product` / `store` / `both` |
| `pages` | array | [pdp] | Where widget shows: pdp, category, home, cart |
| `position` | enum | top-right | top-left, top-right, bottom-left, bottom-right |
| `min_viewers_threshold` | int | 3 | Hide if count < this |
| `max_display_count` | int | 999 | Cap displayed value |
| `update_interval_seconds` | int | 15 | Polling/SSE interval |
| `rolling_window_seconds` | int | 60 | "Currently viewing" definition |
| `boost_multiplier` | float | 1.0 | Ethical inflation (max 2.0) |
| `auto_hide_seconds` | int | 10 | Auto-fade after this |
| `label_ar` | string | "شخص يشاهد الآن" | Arabic label |
| `label_en` | string | "viewing now" | English label |
| `icon` | enum | eye | eye, users, fire |
| `color` | string | brand | Hex or "brand" (use store theme) |
| `pulse_animation` | boolean | true | Pulse effect on update |

##### Trigger Logic

- **Heartbeat emission:** Snippet sends `viewer_heartbeat` POST every 15s while page is visible (uses Page Visibility API to pause when tab hidden).
- **Aggregation:** Backend bucket-counts heartbeats per `product_id` (or store) per minute, computes 60s rolling unique session count.
- **Display:** Widget polls `/viewers?product_id=X` every 15s or subscribes via SSE.

##### Data Captured

```typescript
interface ViewerHeartbeat {
  session_id: string;        // anonymous
  store_id: string;
  product_id?: string;       // null for store-level
  page_type: 'pdp' | 'category' | 'home' | 'cart';
  user_agent_hash: string;   // for dedup
  timestamp: timestamp;
}
```

**Aggregated table:**
```typescript
interface ViewerCount {
  store_id: string;
  product_id?: string;
  active_sessions: number;   // current count
  last_updated: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Tab hidden / minimized | Pause heartbeats via Page Visibility API |
| Bot traffic | Filter user-agents matching known bot patterns |
| Same user multiple tabs | Dedup by `session_id` (one count per session) |
| Network failure | Retry heartbeat up to 3x with backoff, fail silently |
| Count below threshold | Hide widget entirely (no "1 viewer") |
| Count exceeds cap | Display as `999+` |
| Server unreachable | Widget renders nothing, no errors visible |
| Same product on 2 stores | Counts isolated per `store_id` |

##### Mobile Considerations

- Smaller size on mobile (24-28px height).
- Position shifts to avoid Sticky Add-to-Cart bar (configurable).
- Disabled by default on screens < 360px wide.

##### Accessibility

- `aria-live="polite"` on the count element so screen readers announce updates without interrupting.
- Contrast ratio ≥ 4.5:1 against background.
- Hidden from screen readers if `prefers-reduced-motion` and update interval < 30s.

##### Salla Integration
- Reads `product_id` from `salla.product.id` Twilight global.
- Reads `store_id` from app context.
- No Salla API calls required.

---

#### 26.1.2 Widget 2 — Today's Buyers Counter

##### Description
A static badge that displays the count of unique buyers (orders placed) for a product or the whole store **today** (Saudi timezone, midnight reset). Pulled from Salla Orders API or webhook stream. Static for the duration of the page view — does not poll.

**Two display modes:**
- **Mode A: Product-level** — "اشترى 23 شخص هذا المنتج اليوم"
- **Mode B: Store-level** — "127 طلب اليوم"

##### User Flow

```
[Customer lands on PDP]
      ↓
[Snippet requests /buyers-today?product_id=X]
      ↓
[Backend returns cached count (refreshed every 5 min)]
      ↓
[Widget renders if count ≥ min_threshold]
      ↓
[No polling — static for session]
```

##### Functional Requirements

**FR-W2.1** Widget MUST display unique buyer count for current product (Mode A) or store (Mode B) for the current day in Saudi timezone (UTC+3).

**FR-W2.2** Counter MUST reset at midnight Saudi time (00:00 KSA).

**FR-W2.3** Widget MUST NOT display if count < `min_threshold` (default: 5).

**FR-W2.4** Count MUST be cached at the backend (TTL: 5 minutes) to avoid hitting Salla Orders API on every page view.

**FR-W2.5** Backend MUST listen to `order.created` webhook from Salla and increment the cached count.

**FR-W2.6** Widget MUST render synchronously with the page (no skeleton flash — either show or hide).

**FR-W2.7** Widget MUST respect a `decay_after_hours` (default: 18) — after this hour of the day, optional fallback to "yesterday" count to avoid showing "1 buyer" at 1am.

**FR-W2.8** Widget MUST support pluralized strings (1, 2, 3-10, 11+) in Arabic.

##### UX Requirements

- **Position:** Below price or near "Add to Cart" button.
- **Visual:** Simple text with shopping bag icon or check-mark.
- **Style:** No animations (static).
- **Color:** Success green for emphasis (configurable).
- **Size:** Body text size (14-16px).
- **Pluralization:** Proper Arabic plural forms (1 شخص / 2 شخصان / 3-10 أشخاص / 11+ شخصاً).

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `display_mode` | enum | product | `product` / `store` |
| `pages` | array | [pdp] | Where widget shows |
| `position` | enum | below_price | below_price, above_atc, below_atc |
| `min_threshold` | int | 5 | Hide if count < this |
| `cache_ttl_minutes` | int | 5 | Backend cache duration |
| `decay_after_hours` | int | 18 | Switch to yesterday count after this hour |
| `show_icon` | boolean | true | Display shopping bag icon |
| `color` | string | success | success, brand, neutral |
| `label_ar_template` | string | "اشترى {count} {plural} اليوم" | Arabic template |
| `label_en_template` | string | "{count} bought today" | English template |
| `include_test_orders` | boolean | false | Include test/sandbox orders |

##### Data Captured

```typescript
interface BuyersTodayCache {
  store_id: string;
  product_id?: string;
  buyer_count: number;       // unique customers
  order_count: number;       // total orders
  date: string;              // YYYY-MM-DD KSA
  last_updated: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| First day of store launch | Show "be the first to buy" if count = 0 (configurable) |
| Order cancelled after counted | Decrement on `order.cancelled` webhook |
| Refunded order | Do NOT decrement (already counted as buyer intent) |
| Midnight transition during session | Refresh on next page navigation, don't update mid-session |
| Salla webhook lag (>5 min) | Acceptable — count is approximate, not real-time critical |
| Product variant orders | Aggregate to parent product |
| B2B bulk orders | Count once per customer, not per unit |
| Test/staging orders | Filter out via Salla order flags |

##### Mobile Considerations
- Same visual treatment, smaller font (13-14px).
- Position fixed below price on mobile PDP.

##### Accessibility
- Plain text content, no special ARIA needed.
- Number announced with label by screen readers.

##### Salla Integration
- Webhook: `order.created`, `order.cancelled` (Section 13.3).
- Fallback: `GET /admin/v2/orders?from_date=<today>` (Salla Orders API).
- Idempotency by `order.id` to avoid double-counting.

---

#### 26.1.3 Widget 3 — Recent Purchase Toast

##### Description
A small notification toast that briefly appears in a corner of the screen, displaying a recent (real or pseudonymized) purchase by another customer. E.g., "أحمد من الرياض اشترى عطر فيراري قبل 5 دقائق". Builds social proof by showing active commerce.

**Privacy-first design:** Only first name + city + product name + relative time. No phone, email, address, or order details exposed.

##### User Flow

```
[Customer lands on store / PDP / category]
      ↓
[After delay_seconds_initial (default 8s)]
      ↓
[Backend returns next eligible recent purchase from queue]
      ↓
[Toast slides in from bottom-left/right]
      ↓
[Visible for visibility_seconds (default 6s)]
      ↓
[Slides out + waits gap_seconds (default 25s)]
      ↓
[Repeat with next purchase, up to max_per_session (default 5)]
```

##### Functional Requirements

**FR-W3.1** Widget MUST display a single recent purchase at a time as a non-blocking toast.

**FR-W3.2** Each purchase MUST include: first name (or alias), city (or region), product name, relative time ("5 دقائق", "ساعة", "اليوم").

**FR-W3.3** Widget MUST NOT display purchases older than `max_age_minutes` (default: 60).

**FR-W3.4** Widget MUST NOT expose customer phone, email, address, or order ID.

**FR-W3.5** Widget MUST support "anonymize" mode: replace real names with random first names from a curated pool (configurable per merchant for full anonymity).

**FR-W3.6** Toast MUST cycle through up to `max_per_session` purchases per session (default: 5).

**FR-W3.7** Customer MUST be able to dismiss the current toast with an X button — dismissal pauses the cycle for the session.

**FR-W3.8** Widget MUST fetch a batch of eligible purchases on page load (avoid per-toast API calls).

**FR-W3.9** Widget MUST NOT show the same purchase to the same session twice.

**FR-W3.10** Widget MUST respect `prefers-reduced-motion` — fade in/out instead of slide.

##### UX Requirements

- **Position:** Bottom-left (LTR) / Bottom-right (RTL Arabic).
- **Size:** 280-320px wide, ~80px tall.
- **Visual:** Card-style with product thumbnail (40px square) + text block + close X.
- **Animation:** Slide-in 400ms, slide-out 300ms. Fade alternative for reduced motion.
- **Background:** White with subtle shadow.
- **Border-radius:** 12px.
- **Text:** Name bold, product regular, time muted.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `pages` | array | [home, pdp, category] | Where toasts show |
| `position` | enum | bottom-start | bottom-start, bottom-end, top-end |
| `delay_seconds_initial` | int | 8 | First toast delay after page load |
| `visibility_seconds` | int | 6 | How long each toast visible |
| `gap_seconds` | int | 25 | Gap between toasts |
| `max_per_session` | int | 5 | Cap per session |
| `max_age_minutes` | int | 60 | Hide purchases older than this |
| `anonymize_mode` | enum | first_name | first_name, alias_pool, full_anon |
| `show_thumbnail` | boolean | true | Include product image |
| `show_city` | boolean | true | Display customer city |
| `allow_dismiss` | boolean | true | Show X button |
| `pause_on_dismiss` | boolean | true | Stop cycle if user dismisses |
| `eligible_pages` | array | [pdp, home, category] | Where to display |
| `excluded_products` | array | [] | Product IDs to never feature |

##### Data Captured

```typescript
interface PurchaseToastEvent {
  store_id: string;
  toast_id: uuid;
  session_id: string;
  shown_purchase_id: string;
  shown_at: timestamp;
  dismissed: boolean;
  dismissed_at?: timestamp;
  clicked_product: boolean;       // if user clicks toast → PDP
}

interface ToastEligiblePurchase {
  purchase_id: string;
  store_id: string;
  display_first_name: string;     // computed (real or anonymized)
  display_city: string;
  product_id: string;
  product_name: string;
  product_thumbnail_url: string;
  purchase_time: timestamp;
  shown_count: number;            // limit reuse
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| No recent purchases | Hide widget entirely, do not show stale data |
| Customer has no first name | Use anonymized alias from pool |
| Customer city not provided | Show country only ("من السعودية") |
| Product deleted after purchase | Remove from queue |
| Product out of stock | Optional flag: skip OOS products (default: skip) |
| Privacy opt-out customer | Exclude from toast eligibility entirely |
| Rapid page navigation | Cancel pending toasts on `beforeunload` |
| Same customer multiple purchases | Show only the most recent per customer |
| Test/staging order | Filter out |
| RTL vs LTR | Position mirrors automatically based on `dir` attribute |

##### Mobile Considerations
- Reduced size on mobile (240px wide).
- Positioned above Sticky Add-to-Cart bar (z-index ordering critical).
- `max_per_session` defaults to 3 on mobile (less screen real estate).

##### Accessibility
- `role="status"` `aria-live="polite"` for screen reader announcement.
- Toast text fully accessible, not embedded in image.
- Dismiss button has `aria-label="إغلاق الإشعار"`.
- Auto-dismiss respects `prefers-reduced-motion`.

##### Salla Integration
- Webhook: `order.created` populates the purchase queue.
- Customer data: `customer.first_name`, `customer.city` from `order.created` payload.
- Product data: cached locally (synced on `product.updated`).

---

### 26.2 Urgency Widgets

#### 26.2.1 Widget 4 — Low Stock Urgency

##### Description
A small inline badge displayed on the PDP near the price or Add-to-Cart button that highlights when inventory is running low. Creates purchase urgency through scarcity messaging, but only when it's truthful (real stock count). E.g., "تبقى 3 قطع فقط!" / "Only 3 left!"

**Trigger:** Inventory level falls below a configurable threshold.

##### User Flow

```
[Customer lands on PDP]
      ↓
[Snippet reads current product stock from page or API]
      ↓
[If stock ≤ threshold AND stock > 0]
      ↓
[Badge renders inline near price/ATC]
      ↓
[Optional pulse animation to draw attention]
      ↓
[Updates on stock change webhook]
```

##### Functional Requirements

**FR-W4.1** Widget MUST display only when current product stock is between `low_threshold` and `out_of_stock_threshold` (exclusive). Default thresholds: 1-10.

**FR-W4.2** Widget MUST NOT display for products with `stock_tracking_disabled` or "unlimited" stock.

**FR-W4.3** Widget MUST display exact stock count if `show_exact_count` is enabled, OR a vague label ("Few left!") otherwise.

**FR-W4.4** Widget MUST update reactively when stock changes (via Salla `product.updated` webhook + cache invalidation).

**FR-W4.5** Widget MUST hide automatically when stock = 0 (handover to OOS state).

**FR-W4.6** Widget MUST support per-product overrides (merchant can force-show or force-hide on specific products).

**FR-W4.7** Widget MUST respect a `min_stock_for_display` (default: 1) — never show "0 left".

**FR-W4.8** Widget MUST cache stock count client-side for 60s to avoid flicker on navigation.

##### UX Requirements

- **Position:** Inline, below or beside price.
- **Visual:** Red/orange background with white text, fire or alert icon.
- **Animation:** Subtle pulse every 3s (configurable, off for accessibility).
- **Size:** Small badge, 24-28px height.
- **Typography:** Bold count, regular label.
- **Color:** Warning red `#DC2626` or orange `#EA580C` (configurable).

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `low_threshold` | int | 10 | Show when stock ≤ this |
| `out_of_stock_threshold` | int | 0 | Hide when stock ≤ this |
| `show_exact_count` | boolean | true | Show "3 left" vs "Few left" |
| `vague_label_ar` | string | "كمية محدودة" | When `show_exact_count=false` |
| `vague_label_en` | string | "Limited stock" | English fallback |
| `position` | enum | below_price | below_price, above_atc, inline_atc |
| `color_scheme` | enum | warning_red | warning_red, warning_orange, brand |
| `icon` | enum | fire | fire, alert, hourglass, none |
| `pulse_animation` | boolean | true | Pulse every 3s |
| `excluded_products` | array | [] | Product IDs to skip |
| `excluded_categories` | array | [] | Category IDs to skip |
| `template_ar` | string | "تبقى {count} فقط!" | Arabic template |
| `template_en` | string | "Only {count} left!" | English template |

##### Trigger Logic

- **Initial check:** On widget mount, read `salla.product.quantity` from Twilight global.
- **Update:** Subscribe to `product.updated` webhook → invalidate cache → re-render.
- **Threshold logic:** `0 < stock ≤ low_threshold` → show. Otherwise → hide.

##### Data Captured

```typescript
interface LowStockImpression {
  store_id: string;
  product_id: string;
  session_id: string;
  stock_at_display: number;
  shown_at: timestamp;
  led_to_atc: boolean;       // user added to cart within session
  led_to_purchase: boolean;  // user completed checkout
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Stock changes from 11 → 9 during session | Re-render to show badge |
| Stock changes from 5 → 0 during session | Hide badge immediately |
| Variant products with different stock | Use selected variant stock, not parent |
| Backordered / preorder products | Hide badge entirely |
| Stock tracking disabled | Hide badge |
| Bundled product stock | Use minimum bundle component stock |
| Merchant edits threshold mid-session | Apply on next page load |
| Reduced motion preference | Disable pulse animation |
| Concurrent ATC at threshold edge | Display count is informational, actual cart logic handles oversell |

##### Mobile Considerations
- Same visual treatment, slightly smaller (22px height).
- Position adjusted to not collide with Sticky ATC.

##### Accessibility
- `aria-live="polite"` for stock updates.
- Color is not the only signal (icon + text).
- Contrast ratio ≥ 4.5:1.

##### Salla Integration
- Reads `salla.product.quantity` and `salla.product.unlimited_quantity`.
- Subscribes to `product.updated` webhook for stock changes.
- Handles variant selection via Twilight events (`variant.changed`).

---

#### 26.2.2 Widget 11 — Stock Progress Bar

##### Description
A horizontal progress bar that visualizes remaining inventory as a percentage. E.g., a bar fills with red as stock depletes — "80% sold!" / "تم بيع 80% — اطلب قبل النفاد". More visual than the text-based Low Stock Urgency widget. Builds urgency through visual depletion.

**Calculation:** `sold_percent = (initial_stock - current_stock) / initial_stock × 100`

##### User Flow

```
[Customer lands on PDP]
      ↓
[Snippet reads initial_stock + current_stock]
      ↓
[Calculate sold percentage]
      ↓
[If percentage ≥ display_threshold (default 50%)]
      ↓
[Progress bar renders with animated fill]
      ↓
[Updates on stock change]
```

##### Functional Requirements

**FR-W11.1** Widget MUST calculate sold percentage based on `initial_stock` (merchant-set baseline) and `current_stock`.

**FR-W11.2** Widget MUST NOT display if `sold_percent < display_threshold` (default: 50%).

**FR-W11.3** Widget MUST NOT display for unlimited-stock products.

**FR-W11.4** Widget MUST animate fill on initial render (300-500ms cubic-bezier).

**FR-W11.5** Widget MUST update the bar when stock changes via webhook.

**FR-W11.6** Widget MUST support gradient color transitions: green (0-50%) → orange (50-80%) → red (80-99%).

**FR-W11.7** Merchant MUST be able to set `initial_stock` per-product or use a daily auto-reset baseline.

**FR-W11.8** Widget MUST cap displayed percentage at 99% (never show 100% — that means OOS, different state).

##### UX Requirements

- **Position:** Below price, above or below Add-to-Cart button.
- **Visual:** Horizontal bar 6-8px tall, full width of container.
- **Label:** "تم بيع {percent}% — أسرع قبل النفاد!" with percentage prominent.
- **Color gradient:** Green → Orange → Red based on % sold.
- **Animation:** Fill animates from 0 to current % on render.
- **Border-radius:** 4px (rounded ends).

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `display_threshold` | int | 50 | Show when sold_percent ≥ this |
| `max_display_percent` | int | 99 | Cap displayed value |
| `baseline_mode` | enum | merchant_set | merchant_set, auto_daily, auto_weekly |
| `default_initial_stock` | int | 100 | When baseline mode = auto and no data |
| `color_low` | string | "#22C55E" | Green for low % |
| `color_mid` | string | "#F59E0B" | Orange for mid % |
| `color_high` | string | "#DC2626" | Red for high % |
| `threshold_mid` | int | 50 | % at which color shifts to orange |
| `threshold_high` | int | 80 | % at which color shifts to red |
| `show_count` | boolean | true | Show "X sold" in addition to % |
| `animate_on_render` | boolean | true | Animate fill |
| `position` | enum | below_price | below_price, above_atc, below_atc |
| `template_ar` | string | "تم بيع {percent}% — أسرع قبل النفاد!" | Arabic |
| `template_en` | string | "{percent}% sold — hurry before it's gone!" | English |

##### Data Captured

```typescript
interface StockProgressConfig {
  store_id: string;
  product_id: string;
  initial_stock: number;        // baseline (merchant or auto)
  current_stock: number;        // updated via webhook
  display_threshold: number;
  last_baseline_reset?: timestamp;
}

interface StockProgressImpression {
  store_id: string;
  product_id: string;
  session_id: string;
  sold_percent_at_display: number;
  shown_at: timestamp;
  led_to_atc: boolean;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| `initial_stock < current_stock` (data error) | Reset baseline = current_stock, hide widget |
| Sold percent = 100% (OOS) | Hide widget — OOS Substitute handles UX |
| Product restocked mid-day (auto_daily baseline) | Use original baseline until next reset |
| Variant products | Per-variant baseline if variants_have_different_stock |
| Unlimited stock product | Hide widget entirely |
| Initial_stock not configured | Don't show OR use `default_initial_stock` (configurable) |
| Stock fluctuates rapidly (refunds) | Smoothing: update only every 60s |
| Merchant changes threshold | Re-evaluate on next page view |

##### Mobile Considerations
- Bar width fills container minus 16px padding.
- Text labels stacked below bar on mobile to save horizontal space.

##### Accessibility
- `role="progressbar"` with `aria-valuenow`, `aria-valuemin=0`, `aria-valuemax=100`.
- Text equivalent of percentage announced.
- `aria-label="مقدار المخزون المُباع"`.

##### Salla Integration
- Reads `salla.product.quantity` for `current_stock`.
- `initial_stock` stored in our DB (merchant config per product).
- Auto-baseline mode: backend cron sets baseline at midnight Saudi time.
- Subscribes to `product.updated` for stock changes.

---

### 26.3 Contact Widgets

#### 26.3.1 Widget 5 — Floating Marketing Button

##### Description
A persistent, fully-configurable floating action button (FAB) anchored to a corner of every page. The merchant chooses the destination — WhatsApp, Instagram, Snapchat, TikTok, Telegram, phone (tel:), email (mailto:), or **any custom marketing URL** (campaign landing page, lead form, booking page, etc.). One configurable button the merchant uses for whichever marketing channel they want to push.

> **Positioning note:** This widget is *not* a "WhatsApp button" — Salla ships a native WhatsApp button by default. This widget is a **flexible marketing CTA** that the merchant can point at any channel/campaign of their choice. If the merchant wants WhatsApp, they configure it that way; if they want Instagram followers, they point it there; if they want to drive traffic to a Black Friday landing page, that works too.

**Built-in channel presets (one-click setup):**
- WhatsApp Chat (wa.me)
- Instagram Profile
- Snapchat Profile / Snap link
- TikTok Profile
- Telegram Channel
- Phone Call (tel:)
- Email (mailto:)
- Custom URL

##### User Flow

```
[Customer browses any page]
      ↓
[FAB visible at bottom corner with merchant's chosen icon]
      ↓
[Customer taps FAB]
      ↓
[Opens merchant's configured destination URL in a new tab/app]
      ↓
[For WhatsApp/Phone: opens app directly. For social/URL: opens link.]
      ↓
[Click event logged in Widget Analytics]
```

##### Functional Requirements

**FR-W5.1** Widget MUST render as a FAB on every configured page type.

**FR-W5.2** Tapping the FAB MUST navigate to the merchant-configured destination URL in a new tab (or trigger native handler for `tel:` / `mailto:`).

**FR-W5.3** Widget MUST support **channel presets** (WhatsApp, Instagram, Snapchat, TikTok, Telegram, Phone, Email, Custom URL) that pre-fill icon + color + URL template.

**FR-W5.4** For channel = WhatsApp: Widget MUST construct `https://wa.me/{phone}?text={url_encoded_message}` with optional context-aware message (product name + URL on PDP).

**FR-W5.5** For channel = Phone: Widget MUST use `tel:{number}` protocol.

**FR-W5.6** For channel = Email: Widget MUST use `mailto:{email}?subject={subject}` protocol.

**FR-W5.7** For channel = Social (Instagram/Snapchat/TikTok/Telegram): Widget MUST navigate to the configured profile/channel URL.

**FR-W5.8** For channel = Custom URL: Widget MUST navigate to any merchant-configured URL (validated as HTTPS).

**FR-W5.9** Widget MUST support custom icon upload (PNG/SVG, max 100KB) in addition to channel presets.

**FR-W5.10** Widget MUST support business-hours mode (optional, useful for WhatsApp/Phone): show "online" / "offline" state based on configured hours.

**FR-W5.11** Widget MUST optionally show a tooltip/balloon (e.g., "تابعنا على إنستجرام" / "احجز موعد") after `tooltip_delay_seconds` (default: 8).

**FR-W5.12** Widget MUST track clicks as a `marketing_button_click` event with `channel` property for analytics segmentation.

**FR-W5.13** Widget MUST NOT show on checkout pages by default.

**FR-W5.14** Widget MUST be dismissible by user, with state persisted in `localStorage` for `dismissal_persistence_hours` (default: 24).

**FR-W5.15** Widget MUST collide-detect with Scroll-to-Top, Sticky ATC, and Recent Purchase Toast (z-index + offset).

**FR-W5.16** Widget MUST support **scheduled activation** (start/end dates) — merchant can configure "show this Instagram CTA only during the campaign window".

##### UX Requirements

- **Position:** Bottom-end (right in LTR, left in RTL).
- **Size:** 56px circle on desktop, 52px on mobile.
- **Visual:** Channel-appropriate color preset (WhatsApp green, Instagram gradient, Snapchat yellow, etc.) — or custom hex if merchant overrides.
- **Icon:** Channel-appropriate icon (preset library) OR custom uploaded icon.
- **Shadow:** Subtle elevation shadow.
- **Animation:** Subtle bounce on first view, hover scale 1.05.
- **Tooltip:** Balloon that appears once after delay, dismissible.
- **Offline state (WhatsApp/Phone only):** Greyed-out FAB with tooltip "نرد على رسائلك خلال {hours}".

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `channel` | enum | whatsapp | whatsapp, instagram, snapchat, tiktok, telegram, phone, email, custom_url |
| `destination_url` | string | (required) | Pre-filled by preset OR fully custom |
| `whatsapp_phone` | string | (if channel=whatsapp) | E.164 without `+` (e.g., `966501234567`) |
| `phone_number` | string | (if channel=phone) | E.164 for tel: |
| `email_address` | string | (if channel=email) | mailto: target |
| `email_subject` | string | (optional) | Pre-filled subject for mailto: |
| `pages` | array | [all_except_checkout] | Where FAB shows |
| `position` | enum | bottom-end | bottom-start, bottom-end |
| `offset_x_px` | int | 16 | Horizontal offset |
| `offset_y_px` | int | 16 | Vertical offset |
| `color_background` | string | (preset) | FAB bg color (preset default, overridable) |
| `icon_source` | enum | preset | preset, custom_upload |
| `icon_preset` | enum | (channel default) | whatsapp, instagram, snapchat, tiktok, telegram, phone, email, link, custom |
| `icon_custom_url` | string | (optional) | Uploaded PNG/SVG URL |
| `icon_color` | string | "#FFFFFF" | Icon color (for preset icons) |
| `show_tooltip` | boolean | true | Show contextual tooltip |
| `tooltip_delay_seconds` | int | 8 | When to show tooltip |
| `tooltip_text_ar` | string | (channel default) | AR tooltip (e.g., "تابعنا على إنستجرام") |
| `tooltip_text_en` | string | (channel default) | EN tooltip |
| `tooltip_dismiss_persistence_hours` | int | 24 | Per-user dismissal duration |
| `business_hours_enabled` | boolean | false | Use business hours logic (WhatsApp/Phone) |
| `business_hours_start` | string | "09:00" | KSA time start (HH:MM) |
| `business_hours_end` | string | "22:00" | KSA time end |
| `business_days` | array | [sun,mon,tue,wed,thu,sat] | Working days |
| `offline_message_ar` | string | "نرد على رسائلك خلال {hours}" | Offline tooltip AR |
| `wa_prefilled_message_pdp_ar` | string | "مرحباً، عندي سؤال حول {product}: {url}" | WhatsApp template |
| `wa_prefilled_message_cart_ar` | string | "مرحباً، عندي سؤال حول طلبي" | WhatsApp template |
| `wa_prefilled_message_generic_ar` | string | "مرحباً، عندي استفسار" | WhatsApp template |
| `wa_prefilled_message_pdp_en` | string | "Hi, I have a question about {product}: {url}" | EN |
| `wa_prefilled_message_cart_en` | string | "Hi, I have a question about my order" | EN |
| `wa_prefilled_message_generic_en` | string | "Hi, I have a question" | EN |
| `allow_dismiss` | boolean | false | Allow user to hide FAB |
| `schedule_start_date` | datetime | (optional) | Auto-activate from this date |
| `schedule_end_date` | datetime | (optional) | Auto-deactivate after this date |
| `utm_append` | boolean | true | Append UTM params for attribution (for custom URLs) |
| `utm_source` | string | "smart_snippet_fab" | UTM source value |
| `utm_medium` | string | "fab" | UTM medium |
| `utm_campaign` | string | (optional) | UTM campaign |

##### Channel Presets (built-in)

| Channel | Default Icon | Default Color | URL Template | Notes |
|---|---|---|---|---|
| WhatsApp | WhatsApp logo | `#25D366` | `https://wa.me/{phone}?text={msg}` | Context-aware message |
| Instagram | Instagram glyph | `#E1306C` (gradient) | `https://instagram.com/{handle}` | Drive followers |
| Snapchat | Snapchat ghost | `#FFFC00` | `https://snapchat.com/add/{handle}` OR Snapcode link | |
| TikTok | TikTok glyph | `#000000` | `https://tiktok.com/@{handle}` | |
| Telegram | Telegram paper plane | `#0088CC` | `https://t.me/{channel}` | |
| Phone | Phone receiver | `#1E88E5` | `tel:{number}` | Direct dial |
| Email | Envelope | `#757575` | `mailto:{email}?subject={subj}` | Pre-filled subject |
| Custom URL | Link icon (or upload) | Brand color | `{any_https_url}` | Free-form marketing |

##### Data Captured

```typescript
interface MarketingButtonClick {
  store_id: string;
  session_id: string;
  customer_id?: string;
  channel: 'whatsapp' | 'instagram' | 'snapchat' | 'tiktok' | 'telegram' | 'phone' | 'email' | 'custom_url';
  destination_url: string;
  page_type: 'pdp' | 'cart' | 'category' | 'home' | 'other';
  product_id?: string;
  is_business_hours?: boolean;     // only for WhatsApp/Phone
  clicked_at: timestamp;
  device_type: 'mobile' | 'desktop' | 'tablet';
  referrer: string;
  utm_campaign?: string;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Required destination field empty | Hide widget entirely, show warning in merchant dashboard |
| Invalid URL format | Validate on save, reject save with error |
| Channel = WhatsApp + invalid phone | Validate on save, reject |
| User on desktop without WhatsApp | wa.me redirects to WhatsApp Web — works fine |
| User on desktop, channel = Phone (tel:) | Some browsers prompt to call via FaceTime/Skype — acceptable |
| Outside business hours (WhatsApp/Phone) | Show offline state, but link still works |
| Custom URL is HTTP (not HTTPS) | Reject on save (security) |
| Custom uploaded icon too large | Reject upload, show error |
| Schedule end_date passed | Auto-deactivate widget |
| Schedule start_date in future | Hide widget until start |
| Page has no product context (WhatsApp template) | Fall back to generic message |
| Customer language mismatch | Use customer's detected language for tooltip/template |
| Click triggers popup blocker | Use direct anchor `<a href>` not `window.open` |
| User dismissed FAB | Respect dismissal up to `dismissal_persistence_hours` |
| Multiple channels enabled (conflict) | Only ONE channel per widget instance — merchant must use Quick Contact (#8) for multi-channel |

##### Mobile Considerations
- Slightly smaller FAB (52px).
- Higher z-index than Sticky ATC's contact icon.
- On mobile, native protocols (`tel:`, `mailto:`, `wa.me`) open the respective app directly.
- Social URLs deep-link to native apps when installed (e.g., `instagram://user?username=X`).

##### Accessibility
- `<a>` element with `aria-label` describing the action (e.g., "تابعنا على إنستجرام", "احجز موعد", "افتح محادثة واتساب").
- Sufficient touch target (56×56 desktop, 52×52 mobile, both ≥44×44 minimum).
- Tooltip dismissible via keyboard (Escape).
- High contrast meets WCAG AA for chosen color combinations.
- For custom icons: alt text required from merchant on upload.

##### Salla Integration
- All configuration stored in our DB (no Salla API needed).
- For WhatsApp channel: product name from `salla.product.name` (Twilight global), page URL from `window.location.href`.
- UTM params appended automatically for analytics attribution (if `utm_append=true`).
- Click events captured in our Widget Analytics (Section 10).

---

#### 26.3.2 Widget 8 — Quick Contact

##### Description
A floating button (or expandable menu) that offers multiple contact methods in one place: WhatsApp, phone call, email, contact form, or store address (Google Maps). Tapping the button opens a small panel listing available contact methods configured by the merchant. Complements (not replaces) the Floating Marketing Button widget when multi-channel contact is desired.

##### User Flow

```
[Customer browses any page]
      ↓
[FAB visible at bottom corner]
      ↓
[Customer taps FAB]
      ↓
[Panel expands listing contact methods]
      ↓
[Customer picks one]
      ├── WhatsApp → opens chat
      ├── Phone → tel: link triggers dialer
      ├── Email → mailto: link
      ├── Form → opens modal with contact form
      └── Map → opens Google Maps link
```

##### Functional Requirements

**FR-W8.1** Widget MUST render as a FAB that expands into a vertical menu on tap.

**FR-W8.2** Widget MUST support up to 5 channels: WhatsApp, Phone, Email, Form, Map.

**FR-W8.3** Each channel MUST be individually toggleable per merchant.

**FR-W8.4** Panel MUST collapse on tap outside, on Escape key, or after channel selection.

**FR-W8.5** Phone channel MUST use `tel:` protocol for direct dialing.

**FR-W8.6** Email channel MUST use `mailto:` protocol with optional pre-filled subject.

**FR-W8.7** Form channel MUST submit to `/contact` endpoint (backend stores in DB + notifies merchant via email/WhatsApp).

**FR-W8.8** Form MUST validate name (≥2 chars), phone (E.164), and message (≥10 chars).

**FR-W8.9** Form submission MUST be rate-limited (max 3 per session, max 10 per hour per IP).

**FR-W8.10** Map channel MUST open Google Maps with merchant address in a new tab.

**FR-W8.11** Widget MUST track per-channel click counts as analytics events.

**FR-W8.12** Widget MUST NOT show on checkout pages.

##### UX Requirements

- **Position:** Same as Floating Marketing Button (bottom-end). MUTUALLY EXCLUSIVE with Floating Marketing Button — one or the other, not both.
- **FAB icon:** Generic "contact" icon (envelope + phone overlay) or "headset".
- **Size:** 56px circle.
- **Expansion:** Vertical stack of mini-FABs (40px each), animated in with stagger (50ms delay each).
- **Channel icons:** WhatsApp (green), Phone (blue), Email (gray), Form (brand color), Map (red).
- **Labels:** Show tooltips on hover (desktop); inline labels on mobile.
- **Form modal:** Centered, max 420px wide, mobile full-sheet.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `pages` | array | [all_except_checkout] | Where FAB shows |
| `position` | enum | bottom-end | Same as WA |
| `channels` | object | {wa:true,phone:false,email:false,form:false,map:false} | Per-channel toggles |
| `whatsapp_phone` | string | (optional) | E.164 |
| `phone_number` | string | (optional) | Display + tel: |
| `email_address` | string | (optional) | mailto: |
| `email_subject_default` | string | "استفسار من المتجر" | Pre-filled subject |
| `form_fields` | array | [name, phone, message] | Form schema |
| `form_recipient_email` | string | (optional) | Where form submissions go |
| `map_address` | string | (optional) | Display address |
| `map_lat_lng` | string | (optional) | Coordinates for Maps URL |
| `expand_direction` | enum | up | up, left (RTL: right) |
| `auto_collapse_seconds` | int | 8 | Collapse if no interaction |
| `fab_icon` | enum | headset | headset, envelope, dots |

##### Trigger Logic

- **Mount:** FAB always visible.
- **Expand:** On tap, panel slides open.
- **Collapse:** Tap outside, Escape, or after action.

##### Data Captured

```typescript
interface QuickContactInteraction {
  store_id: string;
  session_id: string;
  customer_id?: string;
  action: 'expand' | 'collapse' | 'channel_click';
  channel?: 'whatsapp' | 'phone' | 'email' | 'form' | 'map';
  page_type: string;
  product_id?: string;
  timestamp: timestamp;
}

interface ContactFormSubmission {
  store_id: string;
  customer_name: string;
  customer_phone: string;
  customer_email?: string;
  message: string;
  page_url: string;
  product_id?: string;
  status: 'new' | 'read' | 'responded' | 'archived';
  pdpl_consent: boolean;
  submitted_at: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| All channels disabled | Hide widget entirely |
| Only one channel enabled | Render single-action FAB (no panel) |
| Form submitted with invalid phone | Inline error, prevent submit |
| Form submission rate-limited | Show "حاول لاحقاً" / "Try again later" |
| Map address missing | Disable Map channel |
| Email service down | Form still saves to DB, retry email send later |
| User submits form with disabled JS | Server-side validation kicks in |
| Both WA-floating and Quick Contact enabled | Show warning in merchant dashboard, prefer Quick Contact |
| Customer language mismatch | Translate channel labels |

##### Mobile Considerations
- FAB stays 52px.
- Expanded panel shows full labels (not just icons) on mobile.
- Form opens as bottom sheet on mobile, modal on desktop.

##### Accessibility
- FAB has `aria-expanded` + `aria-controls`.
- Panel has `role="menu"` and channel items have `role="menuitem"`.
- Keyboard navigable (Tab through channels, Enter to activate, Escape to close).
- Form fields properly labeled.
- Focus trapped within form modal when open.

##### Salla Integration
- Stores form submissions in our DB (`contact_submissions` table).
- Notifies merchant via email (SendGrid) and/or WhatsApp (Wati).
- Optional: cross-references with `customer.email` for known customers.

---

### 26.4 UX Widgets

#### 26.4.1 Widget 6 — Scroll-to-Top

##### Description
A small floating button that appears after the customer scrolls down a configurable distance, allowing one-tap return to the top of the page. Improves navigation on long pages (category listings, homepages with multiple sections). Smooth scroll animation by default.

##### User Flow

```
[Customer scrolls down past threshold (default 400px)]
      ↓
[Button fades in at bottom corner]
      ↓
[Customer taps button]
      ↓
[Page smoothly scrolls to top (window.scrollTo with behavior: smooth)]
      ↓
[Button fades out once scroll position < threshold]
```

##### Functional Requirements

**FR-W6.1** Widget MUST render only when `window.scrollY ≥ scroll_threshold_px` (default: 400).

**FR-W6.2** On tap, page MUST scroll smoothly to top (use `window.scrollTo({ top: 0, behavior: 'smooth' })`).

**FR-W6.3** Button MUST disappear when scroll position falls below threshold.

**FR-W6.4** Scroll listener MUST be throttled to fire max once per 100ms (performance).

**FR-W6.5** Widget MUST respect `prefers-reduced-motion` — use instant scroll instead of smooth.

**FR-W6.6** Widget MUST collide-avoid with Floating Marketing Button / Quick Contact (stack vertically with 8px gap).

**FR-W6.7** Button MUST be visible on long category pages, homepage, and PDP.

##### UX Requirements

- **Position:** Bottom-end, stacked above Floating Marketing Button / Quick Contact.
- **Size:** 44px circle.
- **Visual:** Up-arrow icon, semi-transparent neutral background.
- **Animation:** Fade-in (200ms) when threshold crossed, fade-out (200ms) otherwise.
- **Hover:** Slight darken / scale 1.05.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `pages` | array | [all] | Where it shows |
| `scroll_threshold_px` | int | 400 | When to show |
| `position` | enum | bottom-end | bottom-end, bottom-start |
| `offset_y_px` | int | 80 | Stacked above WA/Contact FAB |
| `size_px` | int | 44 | Button size |
| `color_background` | string | "rgba(0,0,0,0.6)" | Bg color |
| `icon_color` | string | "#FFFFFF" | Arrow color |
| `smooth_scroll` | boolean | true | Smooth vs instant |
| `excluded_pages` | array | [] | Where to hide |

##### Data Captured

```typescript
interface ScrollToTopClick {
  store_id: string;
  session_id: string;
  page_type: string;
  scroll_position_at_click: number;
  page_height: number;
  clicked_at: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Short page (no scroll possible) | Button never appears |
| Customer keyboard-navigates to button | Standard Tab focus, Enter activates |
| Customer scrolls during smooth-scroll | Cancel animation, respect user input |
| iOS Safari address bar behavior | Account for safe-area-inset-bottom |
| Reduced motion preference | Use instant scroll |
| Page has internal scroll containers | Only scrolls window, not nested scrolls |
| User rapidly scrolls up and down | Throttled listener prevents flicker |

##### Mobile Considerations
- Slightly smaller (40px) on mobile.
- Lower z-index than modal/popup widgets.
- Respects iOS safe-area-inset-bottom.

##### Accessibility
- `<button>` element with `aria-label="العودة إلى الأعلى"`.
- Visible focus ring.
- Activatable via Enter and Space.

##### Salla Integration
- No Salla API calls.
- Pure client-side behavior.

---

#### 26.4.2 Widget 7 — Sticky Add-to-Cart

##### Description
A persistent bar fixed at the bottom of the viewport on PDP that displays the product thumbnail, name, price, variant selector, and a prominent "Add to Cart" CTA. Stays visible as the customer scrolls past the original product header. Significantly increases ATC conversion on long-scroll PDPs.

**Activation:** Appears when the customer scrolls past the original product header / ATC button (so original isn't visible anymore).

##### User Flow

```
[Customer lands on PDP]
      ↓
[Sticky bar hidden initially (original ATC visible)]
      ↓
[Customer scrolls down past original ATC button]
      ↓
[Sticky bar slides up from bottom (300ms)]
      ↓
[Bar displays: thumbnail + name + price + variant (if multi) + ATC button]
      ↓
[Customer can:
  ├── Tap ATC → add to cart (Salla)
  ├── Change variant → reflects new price
  ├── Tap product info → smooth-scrolls back to top
  └── Continue scrolling → bar stays
]
```

##### Functional Requirements

**FR-W7.1** Widget MUST appear only on PDP pages.

**FR-W7.2** Widget MUST become visible when `original_atc_element` is no longer in viewport (use IntersectionObserver).

**FR-W7.3** Widget MUST display: product thumbnail (40-48px), product name (truncated to 1-2 lines), current price, ATC button.

**FR-W7.4** Widget MUST reflect variant selection state — change price/availability when variant changes.

**FR-W7.5** ATC button MUST trigger Salla's `salla.cart.addItem(productId, quantity, options)` API.

**FR-W7.6** If selected variant is out of stock, ATC button MUST be disabled with "نفذت الكمية" / "Out of stock" label.

**FR-W7.7** Widget MUST support quantity selector (optional, configurable per merchant).

**FR-W7.8** Widget MUST slide up smoothly (300ms cubic-bezier) on activation.

**FR-W7.9** Widget MUST collide-avoid with Recent Purchase Toast (toasts move above sticky bar).

**FR-W7.10** On successful ATC, widget MUST show a confirmation state ("✓ تمت الإضافة") for 2s, then return to default.

**FR-W7.11** Widget MUST respect mobile viewport height changes (iOS address bar).

##### UX Requirements

- **Position:** `position: fixed; bottom: 0; left: 0; right: 0`.
- **Height:** 64-72px on desktop, 56-64px on mobile.
- **Background:** White with top shadow.
- **Layout:** Flex row — thumbnail | name+price (flex-grow) | variant selector | ATC button.
- **ATC button:** Brand color, prominent, min-width 120px.
- **Mobile:** Thumbnail may be hidden to save space; bigger ATC button.
- **Animation:** slide-up (translateY) on appear.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `show_thumbnail` | boolean | true | Display product image |
| `show_name` | boolean | true | Display product name |
| `show_price` | boolean | true | Display price |
| `show_quantity_selector` | boolean | false | Quantity stepper |
| `show_variant_selector` | boolean | true | Inline variant picker (for ≤3 options) |
| `cta_text_ar` | string | "أضف للسلة" | ATC button text AR |
| `cta_text_en` | string | "Add to Cart" | EN |
| `cta_color_background` | string | brand | Hex or "brand" |
| `cta_color_text` | string | "#FFFFFF" | Text color |
| `auto_hide_on_atc` | boolean | false | Hide bar 2s after ATC success |
| `trigger_element_selector` | string | ".product-add-to-cart" | Original ATC selector for IntersectionObserver |
| `hide_on_keyboard_open` | boolean | true | Hide on mobile when keyboard appears |

##### Trigger Logic

- **Mount:** Bar rendered hidden.
- **Observe:** IntersectionObserver on original ATC element. When NOT intersecting → show bar.
- **Variant change:** Listen to Twilight `variant.changed` event → update price + thumbnail + stock state.

##### Data Captured

```typescript
interface StickyATCInteraction {
  store_id: string;
  session_id: string;
  customer_id?: string;
  product_id: string;
  variant_id?: string;
  action: 'shown' | 'atc_click' | 'variant_change' | 'name_click';
  price_at_action: number;
  in_stock: boolean;
  timestamp: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Product OOS at page load | Bar shows with disabled ATC button |
| Variant required but not selected | ATC disabled with "اختر المقاس" prompt |
| Multiple ATC buttons on page | Use first/configured selector |
| Page has no clear ATC element | Use scroll-position fallback (`scrollY > 600`) |
| User scrolls back up to original ATC | Sticky bar hides |
| Variant out of stock after selection | Disable ATC, show OOS state |
| iOS safe area | `padding-bottom: env(safe-area-inset-bottom)` |
| Mobile keyboard open | Hide bar (or reduce height) |
| Floating WA / Quick Contact below | Stack: WA above sticky bar, sticky bar above page |
| Sticky bar overlaps content | Apply `padding-bottom` to body equal to bar height |
| Salla cart add fails | Show error toast, keep button enabled |
| Already-added product | Optionally label "✓ في السلة" with quantity |

##### Mobile Considerations
- Compact layout: small thumbnail or no thumbnail; prominent ATC.
- Tappable area for ATC ≥48×48.
- Variant selector becomes a tap-to-open sheet on mobile.
- Body padding-bottom adjustment to prevent content occlusion.

##### Accessibility
- `<button>` for ATC with descriptive `aria-label`.
- Quantity stepper has `aria-valuenow`, `aria-valuemin`, `aria-valuemax`.
- Variant selectors are properly labeled.
- Bar has `role="region"` `aria-label="إضافة للسلة"`.

##### Salla Integration
- Reads `salla.product` (Twilight global) for id, name, price, image, variants.
- Listens to `salla.product.variant-changed` event.
- Calls `salla.cart.addItem(productId, quantity, options)` on ATC tap.
- Listens to `salla.cart.added` event to show success state.

---

### 26.5 Timer Widgets

#### 26.5.1 Widget 9 — Sale Countdown

##### Description
A live countdown timer that displays the remaining time until a sale, offer, or campaign ends. Creates time-based urgency. Shows days/hours/minutes/seconds remaining and supports flexible display formats (compact pill, full banner, inline text). Supports per-product and store-wide modes.

**Modes:**
- **Store-wide:** Global banner showing one campaign timer (e.g., "ينتهي العرض خلال 2د 14س 30د").
- **Product-specific:** Timer next to price for a specific product on sale.

##### User Flow

```
[Customer visits store / PDP]
      ↓
[Snippet reads active campaign config from backend]
      ↓
[If now < campaign_end]
      ↓
[Timer renders showing days/hrs/min/sec remaining]
      ↓
[Timer updates every second client-side]
      ↓
[When countdown reaches 0]
      ↓
[Optional: switch to "Sale ended" state OR hide widget]
```

##### Functional Requirements

**FR-W9.1** Widget MUST display countdown in DD:HH:MM:SS format (configurable to hide leading zeros / units).

**FR-W9.2** Widget MUST count down once per second client-side using `setInterval`, but reconcile with server time on page load to prevent drift.

**FR-W9.3** Widget MUST support multiple simultaneous campaigns (store-wide + product-specific) but render at most one per location.

**FR-W9.4** Timer MUST stop when `now >= campaign_end_timestamp` and either: hide, show "Sale ended", or restart (if recurring).

**FR-W9.5** Widget MUST support timezone awareness — `campaign_end` stored in UTC, displayed in customer's local time.

**FR-W9.6** Widget MUST gracefully handle clock skew (use server time as source of truth, sync on load).

**FR-W9.7** Widget MUST not flicker on second-tick updates (use CSS opacity transition or no animation on tick).

**FR-W9.8** Widget MUST support recurring campaigns (daily flash sale at 6pm KSA, weekly Friday offers).

**FR-W9.9** Widget MUST respect `Page Visibility API` — pause animations when tab hidden, resume on visible.

##### UX Requirements

- **Position:**
  - Store-wide: top banner OR sticky bar below header.
  - Product-specific: inline below price.
- **Visual:**
  - Banner: full-width strip with countdown digits.
  - Inline: small pill with smaller digits.
- **Digit display:** Monospace font for digits to prevent layout shift on tick.
- **Color:** High-contrast warning (red/orange) for urgency, or brand for branding.
- **Animation:** No animation on tick (avoid distraction). Optional pulse every 10s.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `mode` | enum | store_wide | store_wide, per_product, both |
| `campaigns` | array | [] | List of campaign objects |
| `display_format` | enum | dd_hh_mm_ss | dd_hh_mm_ss, hh_mm_ss, mm_ss |
| `show_units_labels` | boolean | true | "د / س / د / ث" labels |
| `hide_leading_zeros` | boolean | true | "5د" not "05د" |
| `expired_behavior` | enum | hide | hide, show_ended_message, restart |
| `expired_message_ar` | string | "انتهى العرض" | When expired |
| `expired_message_en` | string | "Sale ended" | EN |
| `recurring_pattern` | object | null | { type: 'daily'|'weekly', time: 'HH:MM', tz: 'KSA' } |
| `placement` | enum | top_banner | top_banner, sticky_bar, inline_pdp |
| `color_scheme` | enum | warning | warning, brand, neutral |
| `pages` | array | [home, pdp, category] | Where to show |

##### Campaign Object

```typescript
interface Campaign {
  id: uuid;
  name: string;                         // "White Friday 2026"
  start_at: timestamp;                  // UTC
  end_at: timestamp;                    // UTC
  scope: 'store' | 'category' | 'product';
  scope_ids?: string[];                 // category/product IDs
  recurring?: {
    type: 'daily' | 'weekly';
    time: string;                       // "18:00"
    timezone: string;                   // "Asia/Riyadh"
    duration_hours: number;
  };
  message_ar: string;                   // "ينتهي العرض خلال"
  message_en: string;                   // "Sale ends in"
  cta_text_ar?: string;
  cta_link?: string;
  active: boolean;
}
```

##### Data Captured

```typescript
interface CountdownImpression {
  store_id: string;
  session_id: string;
  campaign_id: string;
  page_type: string;
  product_id?: string;
  time_remaining_seconds_at_view: number;
  shown_at: timestamp;
  clicked_cta: boolean;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Server time drift | Sync via `/server-time` endpoint on mount; adjust offset |
| Multiple campaigns active for same scope | Show highest-priority (most recently created or merchant-pinned) |
| Campaign expired during session | Switch to expired state without page reload |
| Campaign start in future | Hide widget until start |
| Recurring campaign in current window | Always treat current window's end as `campaign_end` |
| DST transitions | Use IANA timezone (Asia/Riyadh has no DST, but handle gracefully) |
| Customer clock wrong | Server time is source of truth; ignore client clock |
| Tab in background for long | On visibilitychange, recompute remaining time |
| Campaign deleted while displayed | Next page load hides it |
| 0 days, 0 hours, 0 minutes | Show "{seconds} seconds" with red flash on last 10s |

##### Mobile Considerations
- Banner reduces to single line on mobile.
- Hide labels on small screens (just digits + colon separators).
- Sticky bar variant: top of viewport, doesn't push content.

##### Accessibility
- `aria-live="polite"` updates announced periodically (every 60s, not every second).
- Time properly labeled: "ينتهي العرض خلال يومين وثلاث ساعات وأربع دقائق".
- Sufficient contrast.
- Reduced motion: no pulse animation.

##### Salla Integration
- Campaigns stored in our DB.
- Optional: read Salla Offers/Coupons API to auto-populate campaign endings.
- No direct Salla widget — we render our own.

---

#### 26.5.2 Widget 10 — Free Shipping Countdown

##### Description
A countdown banner that informs the customer how much more they need to add to their cart to unlock free shipping, combined with a real-time progress bar. Shows in cart and on PDP. E.g., "أضف {remaining} للحصول على شحن مجاني" with a fill bar. Excellent AOV booster.

**Triggers and modes:**
- **Cart page:** Banner at top showing current cart subtotal vs threshold.
- **PDP:** Floating bar showing threshold + cart subtotal (read from Salla cart API).
- **Sticky bar:** Always-visible across pages until threshold met.

##### User Flow

```
[Customer adds items to cart]
      ↓
[Snippet reads current cart subtotal from Salla]
      ↓
[Calculate: remaining = threshold - subtotal]
      ↓
[Banner renders with progress bar]
      ↓
[On every cart change (Salla event)]
      ↓
[Bar updates, label updates]
      ↓
[When subtotal ≥ threshold]
      ↓
[Banner switches to "Free shipping unlocked! 🎉"]
```

##### Functional Requirements

**FR-W10.1** Widget MUST read current cart subtotal from `salla.cart.subtotal` or via Salla Cart API.

**FR-W10.2** Widget MUST update on Salla cart events: `cart.added`, `cart.updated`, `cart.removed`.

**FR-W10.3** Widget MUST display: remaining amount, progress bar fill %, currency.

**FR-W10.4** Widget MUST switch to "unlocked" state when `subtotal >= threshold`.

**FR-W10.5** Threshold MUST be merchant-configurable per region/country if multi-region.

**FR-W10.6** Widget MUST respect product exclusions — some products may not qualify for free shipping (configurable list).

**FR-W10.7** Widget MUST format currency properly (SAR localization, RTL number formatting).

**FR-W10.8** Widget MUST hide automatically if no shipping threshold is configured (avoid empty banner).

**FR-W10.9** Widget MUST display amount in customer's preferred currency (if multi-currency store).

##### UX Requirements

- **Position:** Top banner on cart page, sticky top OR PDP inline (configurable).
- **Visual:** Horizontal layout — icon + text + progress bar + amount remaining.
- **Progress bar:** Smooth fill animation on update.
- **Color:** Brand color for progress; success green on unlocked.
- **Icon:** Truck or package emoji/icon.
- **Unlocked state:** Switches to checkmark + celebratory copy.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `threshold_amount` | number | 200 | Min cart value for free shipping (SAR) |
| `currency` | string | "SAR" | Currency code |
| `pages` | array | [pdp, cart, category] | Where to display |
| `position` | enum | top_banner | top_banner, sticky_bar, inline_pdp |
| `excluded_products` | array | [] | Products that don't count toward threshold |
| `template_remaining_ar` | string | "أضف {amount} للحصول على شحن مجاني" | AR |
| `template_remaining_en` | string | "Add {amount} more for free shipping" | EN |
| `template_unlocked_ar` | string | "🎉 لقد حصلتِ على شحن مجاني!" | AR |
| `template_unlocked_en` | string | "🎉 You unlocked free shipping!" | EN |
| `show_progress_bar` | boolean | true | Visual fill bar |
| `progress_color` | string | brand | Bar color |
| `unlocked_color` | string | "#22C55E" | Color when unlocked |
| `hide_after_unlock_seconds` | int | 0 | Auto-hide after unlock (0 = keep showing) |
| `region_overrides` | array | [] | { region: 'SA', threshold: 200 } |

##### Data Captured

```typescript
interface FreeShippingImpression {
  store_id: string;
  session_id: string;
  customer_id?: string;
  page_type: string;
  cart_subtotal_at_view: number;
  threshold: number;
  remaining: number;
  state: 'progress' | 'unlocked';
  shown_at: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Cart empty | Show "أضف منتجات للحصول على شحن مجاني" |
| Cart subtotal includes excluded products | Subtract excluded item totals from subtotal |
| Customer in region with no threshold | Hide widget |
| Threshold = 0 (always free shipping) | Hide widget (no urgency) |
| Cart subtotal exactly = threshold | Show "Unlocked" state |
| Customer removes items, drops below threshold | Switch back to progress state |
| Variant pricing changes mid-session | Recompute remaining on cart event |
| Cart includes gift cards (often excluded) | Per merchant config |
| Customer logged out / cart empty on PDP | Show generic "Add {threshold} for free shipping" without progress |
| Multi-currency store | Use customer's selected currency |

##### Mobile Considerations
- Compact single-row banner on mobile.
- Progress bar takes full width minus padding.
- Position: top banner doesn't push content (use absolute + body padding).

##### Accessibility
- `role="status"` for the banner.
- Progress bar has `role="progressbar"` with `aria-valuenow/min/max`.
- Currency announced properly by screen readers ("مئتا ريال").
- Color is not the only signal (text + icon + bar).

##### Salla Integration
- Reads `salla.cart.subtotal` from Twilight global.
- Listens to `salla.cart.updated` event.
- Falls back to `GET /v2/cart` if Twilight global unavailable.
- Optional: read Salla's shipping zones to auto-detect threshold (Phase 2).

---

### 26.6 Seasonal Widgets

> **SHARED CONTEXT:** All seasonal widgets share a common framework — they activate within a date range, override theme accent colors with seasonal palette, optionally inject themed badges/overlays on PDPs, and surface promo banners. Each widget below specifies its unique behavior, dates, palette, and content. Common implementation lives in a single `SeasonalEngine` core; widgets are configuration variants.

#### 26.6.1 Widget 12 — Ramadan Mode

##### Description
A bundle of seasonal customizations that activates during the Hijri month of Ramadan: themed banner with crescent/lantern motifs, prayer-time-aware promo timing (avoid showing aggressive offers during Iftar/Suhoor), Ramadan greeting modal on first visit, Iftar countdown timer (optional), and curated Ramadan products collection promotion.

**Date logic:** Auto-detects Hijri Ramadan dates (1 - 30 Ramadan) using a Hijri calendar library OR allows merchant to manually set start/end Gregorian dates.

##### User Flow

```
[Date enters Ramadan window]
      ↓
[On first visit during Ramadan]
      ↓
[Optional: Ramadan greeting modal "كل عام وأنتم بخير"]
      ↓
[Theme override applies: banner, accent color]
      ↓
[Iftar countdown timer shows during fasting hours]
      ↓
[Ramadan collection link in nav/banner]
      ↓
[On Iftar time]
      ↓
[Banner switches to "إفطار شهي" message for 30 min]
      ↓
[Aggressive popups paused during 30-min Iftar window]
```

##### Functional Requirements

**FR-W12.1** Widget MUST activate only between `ramadan_start` and `ramadan_end` dates (Hijri or Gregorian).

**FR-W12.2** Widget MUST display a Ramadan-themed banner at the top of all pages with merchant-customizable copy and CTA.

**FR-W12.3** On first visit during Ramadan, widget MUST optionally show a greeting modal (dismissible, max once per user per Ramadan).

**FR-W12.4** Widget MUST pause "aggressive" popups (Exit Intent, Cart Abandonment, Newsletter) during the 30 minutes before Maghrib (Iftar) until 30 minutes after.

**FR-W12.5** Widget MUST optionally display an Iftar countdown timer that pulls Maghrib time from a prayer-time API for the configured city (default: Riyadh).

**FR-W12.6** Widget MUST link to a "Ramadan Collection" landing page if `collection_url` is configured.

**FR-W12.7** Widget MUST support the merchant uploading a custom Ramadan logo overlay (lantern icon).

**FR-W12.8** Widget MUST allow merchant to manually override auto Hijri date detection.

**FR-W12.9** Greeting modal MUST be skippable, with no penalty in user flow.

**FR-W12.10** Widget MUST automatically deactivate on the day after `ramadan_end`.

##### UX Requirements

- **Banner color palette:** Gold `#D4A24C` + deep green `#0F4C3A` + cream `#FAF5EC`.
- **Banner content:** Lantern icon + merchant copy + CTA.
- **Greeting modal:** Soft, celebratory; calligraphy-style greeting; lantern/crescent imagery.
- **Iftar countdown:** Subtle bar, not loud. Auto-disappears when fasting time ends.
- **Iftar moment banner:** Calm "إفطار شهي" green banner for 30 minutes.
- **No aggressive animations** during Iftar window.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `date_mode` | enum | auto_hijri | auto_hijri, manual_gregorian |
| `manual_start_date` | date | — | If date_mode=manual |
| `manual_end_date` | date | — | If date_mode=manual |
| `show_banner` | boolean | true | Top banner |
| `banner_text_ar` | string | "رمضان كريم — تخفيضات حصرية" | Banner copy AR |
| `banner_text_en` | string | "Ramadan Kareem — Exclusive Offers" | EN |
| `banner_cta_text_ar` | string | "تسوق الآن" | AR |
| `banner_cta_url` | string | "/ramadan-collection" | Where CTA goes |
| `show_greeting_modal` | boolean | true | First-visit greeting |
| `greeting_modal_image_url` | string | (default) | Hero image for modal |
| `greeting_modal_text_ar` | string | "كل عام وأنتم بخير" | AR |
| `greeting_modal_text_en` | string | "Ramadan Mubarak" | EN |
| `show_iftar_countdown` | boolean | false | Show countdown to Maghrib |
| `prayer_city` | string | "Riyadh" | City for Maghrib API |
| `pause_popups_around_iftar` | boolean | true | Quiet popups |
| `iftar_quiet_minutes_before` | int | 30 | Pause window before |
| `iftar_quiet_minutes_after` | int | 30 | Pause window after |
| `palette_primary` | string | "#D4A24C" | Gold |
| `palette_secondary` | string | "#0F4C3A" | Deep green |
| `palette_accent` | string | "#FAF5EC" | Cream |
| `logo_overlay_url` | string | (optional) | Custom Ramadan logo |

##### Data Captured

```typescript
interface SeasonalImpression {
  store_id: string;
  widget: 'ramadan' | 'national_day' | 'white_friday' | 'eid' | 'back_to_school';
  session_id: string;
  customer_id?: string;
  shown_at: timestamp;
  greeting_shown: boolean;
  greeting_dismissed: boolean;
  cta_clicked: boolean;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Customer outside Saudi (different Maghrib time) | Use customer's detected city if available, else default city |
| Hijri/Gregorian crossover ambiguity | Use start_of_Ramadan as official by SDAIA or merchant override |
| Prayer-time API failure | Disable Iftar countdown gracefully, log warning |
| Customer already saw greeting | Skip; check `localStorage` key `ramadan_greeted_{year}` |
| Iftar window collides with active popup | Defer popup, fire after Iftar window ends |
| Last day of Ramadan transitions to Eid | Switch handover at Maghrib (officially Eid 1) |
| Merchant disables manually mid-Ramadan | Deactivate immediately |
| Multi-region store | Use store's primary timezone |
| Year changes during deployment | Use auto detection to refresh dates |

##### Mobile Considerations
- Banner reduces to single line on mobile, possibly icon-only CTA.
- Greeting modal full-sheet on mobile.
- Iftar countdown compact (just time, no labels).

##### Accessibility
- Banner text fully accessible.
- Greeting modal trap-focuses + Escape to dismiss.
- Iftar bar uses `role="status"` with periodic announcement (every 5 min, not every second).
- Decorative imagery has `aria-hidden`.

##### Salla Integration
- Reads `salla.store.city` for prayer time API.
- No Salla widget conflicts (we add overlay, don't override theme).
- Optional: tag products with `tag:ramadan` for collection auto-filter.

---

#### 26.6.2 Widget 13 — National Day

##### Description
A bundle of Saudi National Day customizations (annually September 23): themed banner with Saudi green/white palette, "كل عام والوطن بخير" greeting, optional NDP-themed product collection promotion, and patriotic visual elements (flag motifs, palm-and-swords). Activates Sept 20-26 by default (3 days before, 3 days after).

##### User Flow

```
[Date enters National Day window (Sept 20-26 default)]
      ↓
[Theme overlay applies: Saudi green banner + flag motifs]
      ↓
[On Sept 23 only: special "happy national day" greeting modal]
      ↓
[Saudi National Day collection link surfaced]
      ↓
[On Sept 27: auto-deactivate]
```

##### Functional Requirements

**FR-W13.1** Widget MUST activate between Sept 20 and Sept 26 by default (configurable date range).

**FR-W13.2** Widget MUST display a Saudi National Day banner at top of all pages.

**FR-W13.3** On Sept 23 only, widget MUST display the official Saudi National Day greeting modal (once per user per year).

**FR-W13.4** Widget MUST surface "National Day Collection" link if configured.

**FR-W13.5** Widget MUST use official Saudi national colors (green `#006C35` and white `#FFFFFF`).

**FR-W13.6** Widget MUST support uploading the annual official NDP logo (changes each year).

**FR-W13.7** Widget MUST auto-deactivate on Sept 27 (or `manual_end_date + 1`).

##### UX Requirements

- **Banner color:** Saudi green `#006C35` background, white text, palm-and-swords or flag motif on side.
- **Greeting modal:** Patriotic, flag imagery, full of national pride. Bilingual greeting.
- **Subtle flag stripe** across navigation header (optional).

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `start_date` | date | (auto: Sept 20) | Override default start |
| `end_date` | date | (auto: Sept 26) | Override default end |
| `national_day_date` | date | (auto: Sept 23) | Day of the greeting modal |
| `show_banner` | boolean | true | Top banner |
| `banner_text_ar` | string | "كل عام والوطن بخير" | AR |
| `banner_text_en` | string | "Happy National Day" | EN |
| `banner_cta_url` | string | "/national-day-collection" | CTA target |
| `show_greeting_modal` | boolean | true | First-visit on Sept 23 |
| `official_logo_url` | string | (optional) | Annual NDP logo upload |
| `show_flag_stripe` | boolean | true | Header decoration |
| `palette_primary` | string | "#006C35" | Saudi green |
| `palette_accent` | string | "#FFFFFF" | White |

##### Data Captured
Same structure as `SeasonalImpression` with `widget: 'national_day'`.

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Year changes | Auto-update dates to next year |
| Greeting shown twice | Use localStorage key `national_day_greeted_{year}` |
| Saudi National Day moves (unlikely) | Manual override available |
| Non-Saudi customer | Show regardless (greeting is welcoming, not exclusionary) |
| Merchant in non-Saudi region | Disable by default; opt-in setting |

##### Mobile Considerations
- Banner compact on mobile.
- Greeting modal full-sheet.

##### Accessibility
- All decorative SVGs `aria-hidden`.
- Greeting modal focus-trapped.
- High contrast for green/white meets AAA.

##### Salla Integration
- No Salla API calls.
- Pure overlay/theme.

---

#### 26.6.3 Widget 14 — White Friday

##### Description
A high-stakes seasonal widget for "Black Friday" (rebranded "White Friday" in Saudi/Gulf markets). Activates during the last week of November (configurable), displays dramatic banners, integrates with Sale Countdown (Widget 9), and surfaces a curated discount collection. Designed for high-intensity, time-pressured sale weekends.

**Note:** Often called "White Friday" in Saudi Arabia (الجمعة البيضاء) to avoid negative connotation of "black". The widget supports both labels.

##### User Flow

```
[Date enters White Friday window]
      ↓
[Top banner overrides default theme with dramatic black/white/gold]
      ↓
[Sale Countdown integration: timer counts down to weekend end]
      ↓
[On weekend (Friday 00:00 to Sunday 23:59 KSA)]
      ↓
[Banner switches to "Sale is LIVE" state with stronger visual]
      ↓
[White Friday collection link surfaced]
      ↓
[On Sunday 23:59]
      ↓
[Switch to "Sale ended" or auto-deactivate]
```

##### Functional Requirements

**FR-W14.1** Widget MUST activate between configurable `start_date` (default: 4th Monday of November) and `end_date` (default: following Sunday).

**FR-W14.2** Widget MUST integrate with Sale Countdown widget — auto-create a campaign for White Friday if no campaign exists.

**FR-W14.3** Banner MUST switch between "Coming soon" (pre-Friday) and "LIVE" (Friday-Sunday) states.

**FR-W14.4** Widget MUST surface a "White Friday Collection" link if configured.

**FR-W14.5** Widget MUST support both "Black Friday" and "White Friday" labels per merchant preference.

**FR-W14.6** Banner palette MUST be dramatic: black `#000`, white `#FFF`, gold `#D4AF37`.

**FR-W14.7** Widget MUST auto-deactivate on Monday after the sale weekend.

**FR-W14.8** Widget MUST escalate banner visual intensity on the final day (e.g., flashing edge, "LAST CHANCE" overlay).

##### UX Requirements

- **Pre-event banner:** "الجمعة البيضاء قادمة!" with countdown to start.
- **Live banner:** Bold dramatic "الجمعة البيضاء — تخفيضات حتى 70%".
- **Final-day banner:** Pulsing border, "آخر فرصة!" prefix.
- **Visual:** Black + white + gold accents.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `label_variant` | enum | white | white, black |
| `start_date` | date | (auto: 4th Mon Nov) | Sale start |
| `end_date` | date | (auto: Sun after) | Sale end |
| `pre_event_window_days` | int | 7 | Banner days before |
| `banner_text_pre_ar` | string | "الجمعة البيضاء قادمة" | AR |
| `banner_text_live_ar` | string | "الجمعة البيضاء — تخفيضات حتى 70%" | AR |
| `banner_text_final_ar` | string | "آخر فرصة!" | AR |
| `banner_cta_url` | string | "/white-friday" | CTA target |
| `auto_create_countdown_campaign` | boolean | true | Auto-link to Widget 9 |
| `discount_text` | string | "حتى 70%" | Configurable copy |
| `palette_primary` | string | "#000000" | Black |
| `palette_secondary` | string | "#FFFFFF" | White |
| `palette_accent` | string | "#D4AF37" | Gold |
| `final_day_intensity` | enum | medium | low, medium, high |

##### Data Captured
Same structure as `SeasonalImpression` with `widget: 'white_friday'`.

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Customer visits before sale starts | Show pre-event banner with countdown |
| Customer visits in last hour | Show flashing final-day banner |
| No discount actually applied to products | Banner still shows (merchant content responsibility) |
| Sale extended manually | Update end_date, widget re-activates |
| Conflict with Ramadan/National Day if dates overlap | White Friday wins (rare; merchant alert) |
| Customer dismissed pre-event banner | Re-show on Friday morning |
| Time-zone customer | Use KSA time for "weekend" definition |

##### Mobile Considerations
- Banner reduces to single line.
- Countdown timer compact.
- Final-day intensity reduced on mobile (no flashing border) for performance.

##### Accessibility
- Final-day pulse respects `prefers-reduced-motion`.
- Banner text fully accessible.
- Gold color ensures sufficient contrast against black.

##### Salla Integration
- Auto-creates a Sale Countdown campaign (Widget 9).
- No direct Salla API integration.

---

#### 26.6.4 Widget 15 — Eid Widget

##### Description
A bundle that activates during Eid al-Fitr and Eid al-Adha. Themed banner with celebratory gold/blue palette, "عيد مبارك" greeting modal (once per Eid), optional Eid gift collection link, and increased trust messaging (delivery dates, gift-wrap availability). Two yearly activations.

**Auto-detection:** Uses Hijri calendar.
- Eid al-Fitr: 1-3 Shawwal (3 days)
- Eid al-Adha: 10-13 Dhu al-Hijjah (4 days)

##### User Flow

```
[Date enters Eid window]
      ↓
[Theme overlay: gold + soft blue + cream]
      ↓
[On first visit during Eid period: "Eid Mubarak" greeting modal]
      ↓
[Eid Collection link surfaced]
      ↓
[Gift-related messaging on PDP (gift-wrap, delivery before Eid)]
      ↓
[Last day of Eid: switch to soft "happy holidays" tone]
      ↓
[Auto-deactivate on day after]
```

##### Functional Requirements

**FR-W15.1** Widget MUST detect Eid al-Fitr and Eid al-Adha automatically via Hijri calendar.

**FR-W15.2** Widget MUST display Eid-themed banner during the 3-4 day window.

**FR-W15.3** Widget MUST display greeting modal on first visit per Eid (once per Eid per user).

**FR-W15.4** Widget MUST optionally surface gift-related PDP enhancements: "Gift-wrap available", "Order before X for delivery before Eid".

**FR-W15.5** Widget MUST support both Eids with different palettes (configurable but defaults shared).

**FR-W15.6** Widget MUST allow merchant manual override for date precision (Eid sighting often last-minute).

**FR-W15.7** Widget MUST auto-deactivate 1 day after Eid end.

##### UX Requirements

- **Banner color:** Soft gold `#E5B748` + cream `#FAF5EC`.
- **Greeting modal:** Celebratory, family-warm imagery, calligraphy "عيد مبارك".
- **Gift-wrap badge** on PDP: subtle ribbon/gift icon.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `eid_fitr_enabled` | boolean | true | Activate during Eid al-Fitr |
| `eid_adha_enabled` | boolean | true | Activate during Eid al-Adha |
| `date_mode` | enum | auto_hijri | auto_hijri, manual_gregorian |
| `manual_eid_fitr_start` | date | — | Manual override |
| `manual_eid_fitr_end` | date | — | Manual override |
| `manual_eid_adha_start` | date | — | Manual override |
| `manual_eid_adha_end` | date | — | Manual override |
| `show_banner` | boolean | true | Top banner |
| `banner_text_ar` | string | "عيد مبارك — تخفيضات العيد" | AR |
| `banner_text_en` | string | "Eid Mubarak — Special Offers" | EN |
| `banner_cta_url` | string | "/eid-collection" | CTA target |
| `show_greeting_modal` | boolean | true | First-visit greeting |
| `show_gift_wrap_badge` | boolean | false | PDP gift-wrap indicator |
| `gift_wrap_message_ar` | string | "متوفر تغليف هدية" | AR |
| `palette_primary` | string | "#E5B748" | Gold |
| `palette_accent` | string | "#FAF5EC" | Cream |

##### Data Captured
Same structure as `SeasonalImpression` with `widget: 'eid'` and `eid_type: 'fitr' | 'adha'`.

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Eid date uncertainty (moon sighting) | Allow manual start/end override; default to government announcement |
| Customer celebrated different day | Banner is general; not date-shaming |
| Eid al-Adha overlaps with Hajj period | Handle both peacefully, no conflict |
| Two Eids in same year occasional | Each activation independent |
| Customer dismissed greeting last Eid | Reset per Eid (different `localStorage` keys for `eid_fitr_{year}`, `eid_adha_{year}`) |
| Last day of Eid | Soft transition to "Eid blessings" tone |
| Activated during Hajj week (Eid Adha) | Plays well with religious tone |

##### Mobile Considerations
- Banner compact on mobile.
- Greeting modal full-sheet.

##### Accessibility
- All decorative imagery `aria-hidden`.
- Calligraphy has text equivalent.

##### Salla Integration
- No Salla API needed.
- Optional: tag products `tag:eid-gift` for collection auto-filter.

---

#### 26.6.5 Widget 16 — Back to School

##### Description
A seasonal widget activated during the Back to School period (early August through mid-September for Saudi school year start). Themed banner with school supplies imagery, family-friendly palette, and a curated Back-to-School product collection promotion.

##### User Flow

```
[Date enters Back to School window (Aug 1 - Sept 15 default)]
      ↓
[Top banner overlay: school motifs + parent-friendly tone]
      ↓
[Back to School Collection link surfaced]
      ↓
[Family/kids categories highlighted]
      ↓
[On Sept 16: auto-deactivate]
```

##### Functional Requirements

**FR-W16.1** Widget MUST activate between `start_date` (default Aug 1) and `end_date` (default Sept 15).

**FR-W16.2** Widget MUST display a Back to School banner on all pages.

**FR-W16.3** Widget MUST link to a Back to School collection if configured.

**FR-W16.4** Widget MUST use family-friendly palette: blue `#4A90E2` + yellow `#F5C518` + white.

**FR-W16.5** Widget MUST auto-deactivate on Sept 16 (or `end_date + 1`).

**FR-W16.6** Widget MUST escalate intensity in final week with discount-focused messaging.

##### UX Requirements

- **Banner color:** Blue `#4A90E2` background with yellow `#F5C518` accents.
- **Icons:** Pencil, book, backpack motifs (subtle).
- **Tone:** Helpful and family-warm (not aggressive sale).

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `start_date` | date | (auto: Aug 1) | Override start |
| `end_date` | date | (auto: Sept 15) | Override end |
| `show_banner` | boolean | true | Top banner |
| `banner_text_ar` | string | "العودة إلى المدارس — كل ما يحتاجه طفلك" | AR |
| `banner_text_en` | string | "Back to School — Everything your child needs" | EN |
| `banner_cta_url` | string | "/back-to-school" | CTA target |
| `final_week_message_ar` | string | "آخر أسبوع للتجهيز!" | AR |
| `palette_primary` | string | "#4A90E2" | Blue |
| `palette_accent` | string | "#F5C518" | Yellow |
| `target_categories` | array | [kids, school_supplies, stationery] | Categories to highlight |

##### Data Captured
Same structure as `SeasonalImpression` with `widget: 'back_to_school'`.

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Store doesn't sell school items | Widget can be disabled; otherwise plays as generic seasonal |
| School year changes (rare) | Manual override available |
| University students (later start) | Banner is generic enough to cover |
| Mid-year school start (private intl schools) | Currently single window; merchant can adjust dates |
| Customer is not parent | Banner is opt-in feel, not aggressive |

##### Mobile Considerations
- Compact banner; full-sheet greeting if any.

##### Accessibility
- Decorative imagery `aria-hidden`.
- Banner text accessible.
- Sufficient contrast for yellow accents on blue.

##### Salla Integration
- Optional: tag products `tag:back-to-school`.
- No Salla API needed.

---

### 26.7 Popup Widgets

> **SHARED CONTEXT:** All popup widgets share a common popup engine with: trigger logic, frequency capping, dismissal persistence, A/B variant support, A11y focus trapping, mobile bottom-sheet vs desktop centered modal. Each popup spec below details its trigger conditions, content, and unique behavior.

#### 26.7.1 Widget 17 — Welcome Popup

##### Description
A first-impression modal that greets new visitors with a welcome message, often paired with an introductory offer (discount code, newsletter signup incentive, or free shipping promo). Fires once per user, with configurable delay and dismissal persistence.

##### User Flow

```
[New visitor lands on store]
      ↓
[After delay_seconds (default 5s) on first page]
      ↓
[Modal slides in / fades in centered]
      ↓
[Content: welcome image + headline + offer + CTA]
      ↓
[Customer can:
  ├── Tap CTA (claim offer / continue) → log conversion
  ├── Tap X / outside → dismiss
  └── Tap "remind later" → snooze 1 day
]
      ↓
[Modal closes, never shown again unless config = recurring]
```

##### Functional Requirements

**FR-W17.1** Popup MUST trigger only for new visitors (no `visited_before` cookie) by default.

**FR-W17.2** Popup MUST appear after `delay_seconds` (default: 5s) of being on the first page.

**FR-W17.3** Popup MUST NOT show on checkout or thank-you pages.

**FR-W17.4** Popup MUST be dismissible via X button, Escape key, or backdrop click.

**FR-W17.5** Popup MUST persist dismissal in `localStorage` (key: `welcome_popup_dismissed`) for `dismiss_persistence_days` (default: 30).

**FR-W17.6** Popup MUST capture: shown, dismissed, CTA_clicked, snoozed events.

**FR-W17.7** Popup MUST support a discount code reveal: clicking CTA copies code + redirects.

**FR-W17.8** Popup MUST be mobile bottom-sheet style, desktop centered modal.

**FR-W17.9** Popup MUST respect a global `popup_quiet_period_seconds` shared across all popup widgets (no two popups within 30s of each other).

##### UX Requirements

- **Desktop:** Centered modal, 480px wide, 60% backdrop opacity.
- **Mobile:** Bottom sheet, full-width, peeking image at top.
- **Image:** Hero image (configurable).
- **Headline:** Large, bold welcome message.
- **Offer:** Highlighted card with code or benefit.
- **CTA:** Primary button.
- **Animation:** Fade-in 300ms, scale-up from 0.95.
- **Close:** X button top-right, Escape, backdrop click.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `target_audience` | enum | new_visitors | new_visitors, all_visitors, returning_visitors |
| `delay_seconds` | int | 5 | Delay after landing |
| `pages_excluded` | array | [checkout, thank_you, account] | Where not to show |
| `dismiss_persistence_days` | int | 30 | Re-show after this |
| `snooze_persistence_days` | int | 1 | "Remind me later" duration |
| `headline_ar` | string | "مرحباً بكِ في متجرنا!" | AR |
| `headline_en` | string | "Welcome to our store!" | EN |
| `subhead_ar` | string | "احصلي على خصم 10% على أول طلب" | AR |
| `subhead_en` | string | "Get 10% off your first order" | EN |
| `discount_code` | string | (optional) | Auto-copy on CTA |
| `cta_text_ar` | string | "استلمي الكود" | AR |
| `cta_text_en` | string | "Claim My Code" | EN |
| `cta_url` | string | "/" | Redirect after click |
| `hero_image_url` | string | (default) | Modal image |
| `show_snooze_button` | boolean | true | "Remind me later" |
| `recurring` | boolean | false | Re-show after dismiss period |
| `frequency_cap_per_session` | int | 1 | Max shows per session |

##### Data Captured

```typescript
interface PopupEvent {
  store_id: string;
  popup_widget: 'welcome' | 'exit_intent' | 'newsletter' | 'cart_abandonment' | 'age_verification';
  popup_variant?: string;        // for A/B
  session_id: string;
  customer_id?: string;
  action: 'shown' | 'dismissed' | 'cta_clicked' | 'snoozed' | 'submitted';
  page_url: string;
  trigger_reason: string;
  metadata?: object;             // popup-specific (e.g., code claimed, email entered)
  timestamp: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Returning visitor with cookie | Skip popup |
| User dismissed before, persistence active | Skip |
| User clicked CTA already (claimed) | Skip in future sessions |
| Discount code expired | Hide popup or show new offer |
| Page is checkout / account | Skip per `pages_excluded` |
| Another popup just shown (within quiet period) | Defer trigger |
| Mobile viewport very small (< 320px) | Reduce padding, ensure dismissable |
| User has `prefers-reduced-motion` | No scale animation |
| Concurrent popups same page | Only one wins; quiet period blocks others |
| Brand wants ASAP (delay 0) | Allowed, but warn merchant of UX impact |

##### Mobile Considerations
- Bottom sheet variant (swipe-down to dismiss).
- Hero image clipped to 30% of modal.
- Larger tap targets (CTA min 48px tall).

##### Accessibility
- Focus moves into modal on open; traps within.
- `role="dialog"` `aria-modal="true"` `aria-labelledby="..."` `aria-describedby="..."`.
- Escape key closes.
- Backdrop click closes (with `aria-label`).
- Returns focus to triggering element on close.

##### Salla Integration
- Optional: create coupon via Salla Coupons API (Phase 2).
- For MVP, code is static string copied to clipboard.

---

#### 26.7.2 Widget 18 — Exit Intent Popup

##### Description
A high-conversion popup that fires when a customer signals intent to leave the page (mouse leaves toward browser chrome on desktop; aggressive scroll-up + idle on mobile). Designed to recapture abandoning visitors with a "wait, here's an offer" message. Distinct from the Hesitation Capture Widget (Feature 1) — this widget makes a sales offer; Hesitation Capture asks "why".

**Mutually exclusive with Hesitation Capture on the same page** — only one triggers per session.

##### User Flow

```
[Customer browsing, signals exit intent]
      ├── Desktop: mouseleave toward top of viewport
      └── Mobile: rapid scroll up + idle 3s
      ↓
[Popup fires (if not within quiet period)]
      ↓
[Content: "Wait!" + offer / value prop + CTA]
      ↓
[Customer:
  ├── Claims offer → log conversion, close popup
  ├── Dismisses → close, fire once per session max
  └── Continues exit → popup closes
]
```

##### Functional Requirements

**FR-W18.1** Popup MUST trigger on `mouseleave` event when `event.clientY < 0` (toward top of viewport, desktop).

**FR-W18.2** Popup MUST have a mobile fallback trigger: rapid scroll-up direction + 3s idle.

**FR-W18.3** Popup MUST fire at most once per session (sessionStorage).

**FR-W18.4** Popup MUST NOT fire if Hesitation Capture Widget already fired in same session (mutual exclusion).

**FR-W18.5** Popup MUST NOT trigger on checkout pages.

**FR-W18.6** Popup MUST NOT trigger within first `min_dwell_seconds` (default: 10s) on a page.

**FR-W18.7** Popup MUST persist dismissal for `dismiss_persistence_days` (default: 7).

**FR-W18.8** Popup MUST support A/B variants (different headlines, offers).

**FR-W18.9** Popup MUST capture: shown, dismissed, cta_clicked, page_type, time_on_page_at_trigger.

##### UX Requirements

- **Position:** Centered modal, desktop. Bottom sheet, mobile.
- **Size:** 480px wide desktop; full-width mobile.
- **Headline:** Pattern-interrupt — large, attention-grabbing.
- **Offer:** Discount code, free shipping, free trial, etc.
- **CTA:** Strong primary button.
- **Secondary action:** Small "no thanks" link (low contrast).
- **Animation:** Fast fade-in 250ms.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `min_dwell_seconds` | int | 10 | Min time on page before trigger |
| `pages_excluded` | array | [checkout, thank_you] | Where not to show |
| `mutually_exclusive_with` | array | [hesitation_capture] | Other widgets to defer to |
| `dismiss_persistence_days` | int | 7 | Re-show after this |
| `mobile_trigger_enabled` | boolean | true | Use scroll-up fallback |
| `headline_ar` | string | "انتظري لحظة!" | AR |
| `headline_en` | string | "Wait! Don't go yet!" | EN |
| `subhead_ar` | string | "احصلي على خصم 15% — لفترة محدودة" | AR |
| `subhead_en` | string | "15% off — limited time" | EN |
| `discount_code` | string | (optional) | Auto-copy |
| `cta_text_ar` | string | "احصلي على الخصم" | AR |
| `cta_text_en` | string | "Get My Discount" | EN |
| `cta_url` | string | "/" | Redirect after click |
| `variants` | array | [] | A/B variants |
| `frequency_cap_per_session` | int | 1 | Once per session |

##### Trigger Logic

```javascript
// Desktop
document.addEventListener('mouseleave', (e) => {
  if (e.clientY < 0 && timeOnPage > minDwell && !sessionDismissed) trigger();
});

// Mobile fallback
let scrollHistory = [];
window.addEventListener('scroll', () => {
  scrollHistory.push({ y: window.scrollY, t: Date.now() });
  // detect rapid upward scroll → idle 3s → trigger
});
```

##### Data Captured
Same structure as `PopupEvent` with `popup_widget: 'exit_intent'`.

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Customer moves to switch tab (not exit) | Trigger anyway (mouseleave doesn't distinguish) — acceptable |
| Customer goes to nav bookmark | Likely triggers — acceptable trade-off |
| Mobile: customer pulls down for refresh | Don't confuse with exit intent |
| Customer on slow connection | Popup might delay; load script async |
| Multiple windows open | Track per-tab via sessionStorage |
| Hesitation Capture already showed | Skip Exit Intent (mutual exclusion) |
| Popup rapidly toggled (mouse flickers above) | Debounce 500ms after dismissal |
| User has popup blocker browser extension | Our popup is in-page DOM, not native — not blocked |

##### Mobile Considerations
- Use scroll-up + idle fallback (mousels doesn't fire on mobile).
- Bottom sheet variant.
- Larger CTA tap target.

##### Accessibility
- Same modal A11y as Welcome Popup.
- Focus management correctly handled.

##### Salla Integration
- Optional: create one-time coupon via Salla API (Phase 2).
- For MVP, code is static.

---

#### 26.7.3 Widget 19 — Newsletter Signup

##### Description
A popup that invites customers to subscribe to the merchant's newsletter, often in exchange for a discount or content (early access, lookbook, etc.). Captures email and optionally phone (for WhatsApp/SMS). Integrates with Salla customer database or external ESP.

##### User Flow

```
[Customer browses for > delay_seconds OR triggered by exit/scroll]
      ↓
[Popup shows with newsletter benefit + form]
      ↓
[Customer enters email (+ optional phone)]
      ↓
[Submits → backend validates + stores]
      ↓
[Success state: "Subscribed! Check your email for the code"]
      ↓
[PDPL consent confirmed]
      ↓
[Popup closes after 3s]
```

##### Functional Requirements

**FR-W19.1** Popup MUST trigger via one of: time on page (default 30s), exit intent, or scroll depth (50% of page).

**FR-W19.2** Form MUST require valid email (RFC-compliant regex).

**FR-W19.3** Form MUST optionally accept phone (E.164 Saudi/Gulf validation).

**FR-W19.4** Form MUST include PDPL consent checkbox (required, unchecked by default).

**FR-W19.5** Backend MUST validate email format + check for existing subscriber (dedupe).

**FR-W19.6** On success, popup MUST show confirmation state + auto-close after 3s.

**FR-W19.7** Form MUST be submittable via Enter key.

**FR-W19.8** Popup MUST persist dismissal for `dismiss_persistence_days` (default: 14).

**FR-W19.9** Popup MUST NOT show to already-subscribed customers (check via email or cookie).

**FR-W19.10** Subscriber data MUST sync to merchant's Salla customer database AND optional external ESP (Mailchimp, Klaviyo).

##### UX Requirements

- **Format:** Modal or slide-in box (configurable).
- **Hero image:** Optional newsletter-themed image.
- **Form:** Email input, optional phone, consent checkbox, CTA button.
- **Trust:** Privacy note, unsubscribe link mention.
- **Success state:** Checkmark + thank-you message.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `trigger_mode` | enum | time | time, exit_intent, scroll_depth |
| `trigger_value` | int | 30 | Seconds OR depth % |
| `format` | enum | modal | modal, slide_in_box |
| `position_slide_in` | enum | bottom-end | Position if slide_in |
| `pages_included` | array | [home, pdp, category] | Where it shows |
| `pages_excluded` | array | [checkout, thank_you, account] | Where not |
| `headline_ar` | string | "اشتركي في النشرة" | AR |
| `headline_en` | string | "Join our newsletter" | EN |
| `subhead_ar` | string | "احصلي على خصم 10% + إشعارات بالعروض" | AR |
| `subhead_en` | string | "Get 10% off + exclusive offers" | EN |
| `collect_phone` | boolean | false | Include phone field |
| `phone_required` | boolean | false | If collected, required |
| `consent_text_ar` | string | "أوافق على استلام الرسائل التسويقية وفقاً لنظام حماية البيانات" | AR |
| `consent_text_en` | string | "I agree to receive marketing communications (PDPL)" | EN |
| `cta_text_ar` | string | "اشتركي الآن" | AR |
| `cta_text_en` | string | "Subscribe" | EN |
| `success_message_ar` | string | "تم الاشتراك! تحققي من بريدك" | AR |
| `success_message_en` | string | "Subscribed! Check your inbox" | EN |
| `dismiss_persistence_days` | int | 14 | Re-show after |
| `esp_provider` | enum | salla | salla, mailchimp, klaviyo, none |
| `esp_list_id` | string | (optional) | External list ID |
| `discount_code_on_signup` | string | (optional) | Code emailed after signup |

##### Data Captured

```typescript
interface NewsletterSignup {
  store_id: string;
  subscriber_id: uuid;
  email: string;
  phone?: string;
  consent_pdpl: boolean;
  consent_timestamp: timestamp;
  consent_version: string;
  source: 'newsletter_popup' | 'inline_form' | 'checkout';
  page_url_at_signup: string;
  esp_provider: string;
  esp_external_id?: string;
  created_at: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Email already subscribed | "You're already subscribed — check inbox for code" |
| Invalid email format | Inline error, prevent submit |
| Disposable email detected (e.g., 10minutemail) | Optional block via regex/list |
| Customer dismisses consent | Cannot submit form (PDPL hard block) |
| ESP API failure | Save to our DB, queue for retry |
| Customer also has account on Salla | Match by email; merge profiles |
| Unsubscribe attempts later | Honor via Consent Center (Phase 2) |
| Submission rate-limited | "Too many attempts, try later" |
| Customer enters phone without consent for SMS | Save phone, but only email gets used |

##### Mobile Considerations
- Bottom sheet for modal mode.
- Slide-in box adjusted for mobile width.
- Phone field uses `tel` input type.

##### Accessibility
- Form fields properly labeled.
- Email field `type="email"` `autocomplete="email"`.
- Phone field `type="tel"` `autocomplete="tel"`.
- Consent checkbox programmatically associated.
- Inline errors announced via `aria-live`.

##### Salla Integration
- Default: post subscriber to Salla `customers` API as marketing subscriber.
- Optional: forward to external ESP (Mailchimp, Klaviyo).
- Triggers a separate post-signup email via SendGrid template.

---

#### 26.7.4 Widget 20 — Cart Abandonment

##### Description
A popup that fires when a customer with items in cart shows exit intent, idle behavior, or attempts to navigate away from the cart page. Reminds them of their items and offers an incentive to complete the purchase. Distinct from Salla's native abandoned cart emails (which fire post-session). This widget fires in-session.

**Note:** Salla has native abandoned cart features. This widget is in-session only; we do NOT replace post-session emails.

##### User Flow

```
[Customer has items in cart]
      ↓
[Exit intent OR cart-page idle 60s OR ATC then no checkout 2min]
      ↓
[Popup fires: "Don't lose your items!"]
      ↓
[Content: cart preview + offer + CTA "Complete Order"]
      ↓
[Customer:
  ├── Clicks CTA → /checkout
  ├── Dismisses → close, mark session-shown
  └── Continues exit → close anyway
]
```

##### Functional Requirements

**FR-W20.1** Popup MUST trigger only when cart has ≥ 1 item.

**FR-W20.2** Popup MUST fire on one of: exit intent, cart-page idle (60s), or post-ATC-no-checkout (2 min).

**FR-W20.3** Popup MUST display: cart item count, subtotal, optional discount offer, CTA to checkout.

**FR-W20.4** Popup MUST fire max once per session (configurable).

**FR-W20.5** Popup MUST NOT fire on checkout pages.

**FR-W20.6** Popup MUST persist dismissal for `dismiss_persistence_hours` (default: 24).

**FR-W20.7** Popup MUST display first item thumbnail (or up to 3 thumbnails stacked).

**FR-W20.8** Popup MUST link to Salla checkout URL.

**FR-W20.9** Popup MUST update reactively if cart changes after popup is open (rare).

##### UX Requirements

- **Format:** Modal centered (desktop), bottom sheet (mobile).
- **Image:** Stacked product thumbnails (max 3).
- **Headline:** "لا تنسي طلبك!" / "Don't forget your cart!"
- **Subhead:** "{count} منتج بانتظارك في السلة"
- **CTA:** "أكملي الشراء" / "Complete Order".
- **Offer (optional):** Small discount or free shipping reminder.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `trigger_modes` | array | [exit_intent, cart_idle] | Which triggers |
| `cart_idle_seconds` | int | 60 | Cart page idle threshold |
| `post_atc_no_checkout_seconds` | int | 120 | Wait after ATC before trigger |
| `pages_excluded` | array | [checkout, thank_you] | Where not |
| `dismiss_persistence_hours` | int | 24 | Re-show after |
| `frequency_cap_per_session` | int | 1 | Max shows |
| `headline_ar` | string | "لا تنسي طلبك!" | AR |
| `headline_en` | string | "Don't forget your cart!" | EN |
| `subhead_template_ar` | string | "{count} منتج بانتظارك" | AR |
| `subhead_template_en` | string | "{count} item(s) waiting" | EN |
| `show_subtotal` | boolean | true | Display total |
| `show_thumbnails` | boolean | true | Item thumbs |
| `max_thumbnails` | int | 3 | Cap thumbnails |
| `discount_code` | string | (optional) | Incentive code |
| `cta_text_ar` | string | "أكملي الشراء" | AR |
| `cta_text_en` | string | "Complete Order" | EN |
| `cta_url` | string | "/checkout" | Redirect |
| `disable_if_salla_abandonment_active` | boolean | false | Coordinate with native |

##### Data Captured

```typescript
interface CartAbandonPopup {
  store_id: string;
  popup_event_id: uuid;
  session_id: string;
  customer_id?: string;
  cart_id?: string;
  cart_subtotal: number;
  cart_item_count: number;
  trigger_reason: 'exit_intent' | 'cart_idle' | 'post_atc';
  action: 'shown' | 'dismissed' | 'cta_clicked';
  led_to_checkout: boolean;
  led_to_purchase: boolean;
  timestamp: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Cart emptied between trigger and display | Cancel popup |
| Cart updated while popup open | Refresh content; recalculate subtotal |
| Customer logged out (anonymous cart) | Still trigger; use session-bound cart |
| Customer already at checkout | Suppress |
| Customer dismissed within hours | Skip per persistence |
| Discount code overlap with cart-applied | Show offer with note: "discount applies at checkout if eligible" |
| Salla native abandonment also configured | Setting to disable our widget if native is on |
| Cart contains digital products only | Standard behavior — popup works |
| Cart contains restricted items (age-gated) | Standard behavior |

##### Mobile Considerations
- Bottom sheet.
- Smaller thumbnails (40px).

##### Accessibility
- Modal a11y standard.
- Subtotal announced.
- CTA clearly labeled.

##### Salla Integration
- Reads cart via `salla.cart` Twilight global or `GET /v2/cart`.
- CTA redirects to Salla checkout `/checkout`.
- Does NOT replace Salla post-session abandonment emails.

---

#### 26.7.5 Widget 21 — Age Verification

##### Description
A blocking modal that prompts the customer to confirm their age before browsing the store, required for age-restricted product categories (vape, perfume with alcohol content, certain cosmetics, etc.). Stores confirmation in cookie/localStorage. Mandatory disclaimer pattern in some Saudi categories.

##### User Flow

```
[Customer lands on store (first visit OR cookie expired)]
      ↓
[Full-screen modal blocks all content]
      ↓
[Question: "Are you over 18?"]
      ↓
[Customer:
  ├── Confirms Yes → cookie set, modal dismisses, store visible
  ├── Selects No → redirect to "minors-not-allowed" page OR generic site
  └── Cannot dismiss without choosing
]
```

##### Functional Requirements

**FR-W21.1** Modal MUST block all page interaction until age is confirmed.

**FR-W21.2** Modal MUST NOT be dismissible by Escape, backdrop click, or X — only by choosing Yes/No.

**FR-W21.3** Confirmation MUST persist in cookie `age_verified=1` for `cookie_lifetime_days` (default: 365).

**FR-W21.4** "No" selection MUST redirect to a merchant-configured URL (default: blank page with explanation).

**FR-W21.5** Modal MUST be the ABSOLUTE TOP popup — overrides any other popup quiet periods.

**FR-W21.6** Modal MUST support custom age threshold (18, 21) per merchant.

**FR-W21.7** Modal MUST allow merchant to add a disclaimer body (regulatory text).

**FR-W21.8** Modal MUST work on all pages — not bypassable via direct URL to a product.

**FR-W21.9** Modal MUST be the only widget shown on first visit (suppresses Welcome Popup until age confirmed).

##### UX Requirements

- **Format:** Full-screen modal, no close button.
- **Backdrop:** Solid (not transparent) — full coverage.
- **Content:** Logo + question + two large buttons + disclaimer text.
- **Buttons:** Yes (primary), No (secondary).
- **Visual:** Professional, somber, not playful.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `age_threshold` | int | 18 | 18 or 21 |
| `question_ar` | string | "هل عمرك 18 سنة أو أكثر؟" | AR |
| `question_en` | string | "Are you 18 or older?" | EN |
| `yes_button_text_ar` | string | "نعم" | AR |
| `yes_button_text_en` | string | "Yes" | EN |
| `no_button_text_ar` | string | "لا" | AR |
| `no_button_text_en` | string | "No" | EN |
| `no_redirect_url` | string | (default minors page) | Where No goes |
| `disclaimer_text_ar` | string | (regulatory text) | AR |
| `disclaimer_text_en` | string | (regulatory text) | EN |
| `cookie_lifetime_days` | int | 365 | Persistence |
| `show_logo` | boolean | true | Display store logo |
| `pages_excluded` | array | [] | Pages to skip (rare) |

##### Data Captured

```typescript
interface AgeVerification {
  store_id: string;
  session_id: string;
  customer_id?: string;
  response: 'yes' | 'no';
  ip_address_hash: string;        // for compliance audit, hashed
  user_agent: string;
  timestamp: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Customer disables cookies | Modal shows on every page; not a blocker, just persistent prompt |
| Customer answers No, returns later | Cookie set `age_verified=0`; redirect to no_redirect_url on every load until cleared |
| Cookie expires | Modal re-prompts on next visit |
| Customer uses incognito | Modal shows fresh each session |
| Direct URL deep-link | Modal still blocks until age confirmed |
| Bot crawlers (SEO) | Bypass modal via user-agent detection (configurable allowlist) |
| Customer too young by self-declaration | Honor No redirect; do NOT capture personal info |
| Customer dismisses via dev tools | Out of scope — can't prevent technically savvy users |

##### Mobile Considerations
- Full-screen on mobile (no escape).
- Large tap targets for buttons (min 56px tall).
- Disclaimer text scrollable if long.

##### Accessibility
- `role="dialog"` `aria-modal="true"`.
- Focus trapped inside.
- High contrast.
- Screen reader announces full question and button labels.
- Returns focus to body on close.

##### Salla Integration
- No Salla API needed.
- Cookie-based, client-side.
- Backend logs verification events for compliance audit.

---

### 26.8 Trust Widgets

> **SHARED CONTEXT:** Trust widgets are passive informational displays designed to reduce friction at decision points (PDP, cart, checkout). They share a common rendering engine that places badge groups in configurable positions and reads from a shared `trust_config` per merchant. No customer interaction tracking beyond impression events.

#### 26.8.1 Widget 22 — Trust Badges

##### Description
A row of badges/icons displayed on PDPs and the cart page that visually communicate trust signals: secure checkout, money-back guarantee, customer support availability, authentic products, etc. Configurable per merchant from a curated icon library + custom upload.

##### User Flow

```
[Customer browses PDP or cart]
      ↓
[Badge row renders at configured position (default: below ATC)]
      ↓
[Each badge shows icon + short label]
      ↓
[On hover (desktop) → tooltip with longer description]
      ↓
[Static display, no interaction required]
```

##### Functional Requirements

**FR-W22.1** Widget MUST display up to 6 badges in a horizontal row (responsive: stacks on mobile).

**FR-W22.2** Each badge MUST consist of: icon (24-32px) + label (max 30 chars).

**FR-W22.3** Each badge MUST support an optional tooltip (max 150 chars) on hover.

**FR-W22.4** Merchant MUST choose from a library of 20+ pre-designed badges OR upload custom (PNG/SVG, max 100KB).

**FR-W22.5** Widget MUST render on PDP, cart, and optionally checkout (where Salla allows).

**FR-W22.6** Badges MUST be selectable per page (different sets for PDP vs cart).

**FR-W22.7** Widget MUST gracefully degrade if more than 6 badges configured (show first 6).

**FR-W22.8** Custom uploaded images MUST be optimized server-side (resized, compressed).

##### UX Requirements

- **Layout:** Flex row, justified evenly. Wraps to 2 rows on narrow screens.
- **Icon style:** Outline icons (default library), consistent stroke width.
- **Spacing:** 16px gap between badges.
- **Label:** Small text below icon (12-14px).
- **Tooltip:** Small dark tooltip on hover (desktop only).

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `pages` | array | [pdp, cart] | Where to show |
| `position` | object | { pdp: below_atc, cart: above_total } | Per-page placement |
| `badges` | array | [] | List of badge objects |
| `max_badges_per_row` | int | 6 | Cap |
| `icon_style` | enum | outline | outline, filled |
| `show_tooltips` | boolean | true | Hover tooltips |
| `badge_size_px` | int | 32 | Icon size |

##### Badge Object

```typescript
interface TrustBadge {
  id: uuid;
  icon: string;              // library key OR uploaded URL
  label_ar: string;
  label_en: string;
  tooltip_ar?: string;
  tooltip_en?: string;
  pages: ('pdp' | 'cart')[];
  order: number;
}
```

**Pre-built badge library:**
- Secure Checkout / دفع آمن
- Money-Back Guarantee / ضمان الاسترداد
- Free Shipping / شحن مجاني
- Fast Delivery / توصيل سريع
- Authentic Products / منتجات أصلية
- 24/7 Support / دعم متواصل
- 30-Day Returns / إرجاع خلال 30 يوم
- Verified Seller / بائع موثوق
- SSL Encrypted / تشفير SSL
- Quality Assured / جودة مضمونة
- (+10 more in MVP)

##### Data Captured

```typescript
interface TrustBadgeImpression {
  store_id: string;
  session_id: string;
  page_type: string;
  product_id?: string;
  badge_ids_shown: string[];
  shown_at: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Zero badges configured | Hide widget entirely |
| All badges have invalid icons | Render with placeholder + warning to merchant |
| Custom upload too large | Reject upload, show error |
| Custom upload wrong format | Convert to PNG server-side OR reject |
| Mobile narrow screen | Wrap to 2 or 3 rows |
| RTL layout | Mirror order |
| Tooltip cut off at viewport edge | Reposition automatically |

##### Mobile Considerations
- Wraps to multiple rows.
- Tooltips disabled (no hover); tap-to-show is awkward — defer to label.
- Smaller icons (24px) on very narrow screens.

##### Accessibility
- Each badge has descriptive `aria-label` (icon + label combined).
- Tooltips have `role="tooltip"` and `aria-describedby` association.
- Decorative icons have `aria-hidden`; semantic ones have labels.
- Sufficient contrast for icons and labels.

##### Salla Integration
- No Salla API.
- Custom uploads stored in our CDN.

---

#### 26.8.2 Widget 23 — Shipping Info

##### Description
A compact info card displayed on PDP and cart that summarizes shipping options: estimated delivery time, shipping cost (or "free above X"), and supported regions. Reduces purchase hesitation by answering "when will I get this?" upfront.

##### User Flow

```
[Customer browses PDP]
      ↓
[Shipping card renders near price/ATC]
      ↓
[Card displays:
  - Estimated delivery: "2-4 days to Riyadh"
  - Cost: "Free above 200 SAR" OR "15 SAR flat"
  - Regions: "Ships to all of KSA"
]
      ↓
[Customer can tap "Details" to expand → list of cities with delivery times]
```

##### Functional Requirements

**FR-W24.1** Widget MUST display estimated delivery time, shipping cost summary, and supported regions.

**FR-W24.2** Widget MUST detect customer's city via IP geolocation OR Salla customer profile (if logged in).

**FR-W24.3** Widget MUST show city-specific delivery estimate if available; otherwise generic.

**FR-W24.4** Widget MUST support expand/collapse — collapsed default, expanded shows full city list.

**FR-W24.5** Widget MUST pull shipping data from merchant config (manual entry MVP; Salla Shipping API Phase 2).

**FR-W24.6** Widget MUST update if customer changes location/city.

**FR-W24.7** Widget MUST gracefully hide if no shipping config exists.

##### UX Requirements

- **Format:** Card with icon + 3-line text + expand toggle.
- **Icon:** Truck or package.
- **Color:** Neutral or success green (subtle).
- **Expanded state:** Table or list of city → delivery time.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `pages` | array | [pdp, cart] | Where to show |
| `position` | object | { pdp: below_price, cart: above_total } | Placement |
| `delivery_estimates` | object | { Riyadh: "2-4 days", default: "3-7 days" } | City → time |
| `default_shipping_cost_text_ar` | string | "شحن مجاني للطلبات فوق 200 ر.س" | AR |
| `default_shipping_cost_text_en` | string | "Free shipping above 200 SAR" | EN |
| `flat_rate_amount` | number | 15 | If not free, this amount |
| `regions_supported_text_ar` | string | "نشحن لجميع مدن المملكة" | AR |
| `regions_supported_text_en` | string | "Ships across all KSA" | EN |
| `expandable` | boolean | true | Show "Details" toggle |
| `expanded_default` | boolean | false | Auto-expand |
| `auto_detect_city` | boolean | true | Use IP geo or customer profile |
| `excluded_cities` | array | [] | Cities not shipped to |

##### Data Captured

```typescript
interface ShippingInfoView {
  store_id: string;
  session_id: string;
  page_type: string;
  customer_city_detected: string;
  delivery_estimate_shown: string;
  expanded_clicked: boolean;
  shown_at: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| IP geo fails | Use default estimate, generic regions text |
| Customer in unsupported city | Show "may not ship to {city}" warning + contact link |
| Free shipping threshold variable by region | Use region-specific config |
| BNPL or installment doesn't include shipping | No widget impact (separate config) |
| International shipping (rare for Saudi stores) | Show "International shipping available — contact" |
| Salla Shipping Zones change | Refresh on `store.settings.updated` (Phase 2) |
| Product is digital (no shipping) | Hide widget |
| Same-day delivery options | Display badge "نفس اليوم" if eligible |

##### Mobile Considerations
- Compact card on mobile.
- Expand becomes bottom sheet.

##### Accessibility
- Expandable section uses `<details>`/`<summary>` or proper ARIA disclosure pattern.
- Truck icon decorative, `aria-hidden`.
- All text accessible.

##### Salla Integration
- MVP: merchant manually enters delivery estimates per city.
- Phase 2: read from Salla Shipping API.
- Reads `customer.city` if available; falls back to IP geo.

---

#### 26.8.3 Widget 24 — Return Policy

##### Description
A compact card on PDP, cart, and footer that surfaces the merchant's return policy in a digestible format. Builds confidence at the point of decision. Links to the full policy page for full text. Typical content: "30-day returns, free pickup, full refund".

##### User Flow

```
[Customer browses PDP / cart / footer]
      ↓
[Card renders with key policy summary]
      ↓
[Card content: icon + headline + 1-2 bullets]
      ↓
[Customer can tap "Full Policy" → opens policy page]
```

##### Functional Requirements

**FR-W25.1** Widget MUST display a brief return policy summary (max 3 lines).

**FR-W25.2** Widget MUST link to the merchant's full return policy page (URL configurable).

**FR-W25.3** Widget MUST support per-product overrides (some products non-returnable).

**FR-W25.4** Widget MUST display "Non-returnable" badge if product is in `non_returnable` list.

**FR-W25.5** Widget MUST be configurable bilingually.

**FR-W25.6** Widget MUST gracefully hide if no policy configured.

##### UX Requirements

- **Format:** Small card with icon + text.
- **Icon:** Refresh/undo arrow.
- **Color:** Neutral.
- **Link:** "Full Policy" text-link to dedicated page.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `pages` | array | [pdp, cart, footer] | Where to show |
| `position` | object | { pdp: near_atc, cart: above_total, footer: end } | Placement |
| `policy_summary_ar` | string | "إرجاع خلال 30 يوم — استرداد كامل" | AR |
| `policy_summary_en` | string | "30-day returns — full refund" | EN |
| `policy_url` | string | "/return-policy" | Full policy link |
| `non_returnable_products` | array | [] | Product IDs |
| `non_returnable_categories` | array | [] | Category IDs |
| `non_returnable_text_ar` | string | "هذا المنتج غير قابل للإرجاع" | AR |
| `non_returnable_text_en` | string | "This product is non-returnable" | EN |
| `show_icon` | boolean | true | Display icon |

##### Data Captured

```typescript
interface ReturnPolicyView {
  store_id: string;
  session_id: string;
  page_type: string;
  product_id?: string;
  policy_link_clicked: boolean;
  product_non_returnable: boolean;
  shown_at: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Policy URL invalid | Inline-display extended policy text (configurable longer body) |
| Non-returnable product in cart with returnable items | Show note "Some items non-returnable" |
| Customer in different region with different policy | Show region-specific copy (if configured) |
| Used items policy differs | Out of MVP — single policy |
| Merchant updates policy text | Cache busted on next page load |

##### Mobile Considerations
- Single-line summary truncated.
- "Full Policy" link prominent.

##### Accessibility
- Link text descriptive ("View full return policy") not just "Click here".
- Icon decorative, `aria-hidden`.

##### Salla Integration
- Policy URL is merchant-configured (often `/page/return-policy` on Salla).
- No Salla API needed.

---

### 26.9 Engagement Widgets

#### 26.9.1 Widget 25 — Wishlist Heart

##### Description
A heart-shaped icon on product cards and PDPs that customers can tap to save a product to a personal wishlist. Persists across sessions (for logged-in customers) or per-device (for anonymous users via localStorage). Wishlist accessible from a dedicated page or dropdown.

**Note:** Salla has a native wishlist. Our widget enhances UX with: optimistic toggling, mini-counter badge, "Move to cart" bulk action, and analytics.

##### User Flow

```
[Customer browses product card or PDP]
      ↓
[Heart icon visible (empty if not in wishlist)]
      ↓
[Customer taps heart]
      ↓
[Optimistic toggle: heart fills + count badge increments]
      ↓
[Backend stores wishlist item (Salla API + our DB)]
      ↓
[On wishlist page: customer sees all saved items]
      ↓
[Customer can remove, share, or move to cart]
```

##### Functional Requirements

**FR-W26.1** Widget MUST render heart icon on product cards (category, search, related) and PDP.

**FR-W26.2** Tap on heart MUST toggle wishlist state with optimistic UI (no spinner).

**FR-W26.3** Wishlist state MUST persist:
- Logged-in users: backend (Salla customer wishlist API)
- Anonymous users: localStorage (max 50 items)

**FR-W26.4** Widget MUST display a global wishlist counter badge in header/nav (count of items).

**FR-W26.5** Customer MUST be able to access wishlist page at `/wishlist` (or merchant's URL).

**FR-W26.6** Wishlist page MUST list items with: image, name, price, "Remove" button, "Add to Cart" button.

**FR-W26.7** Wishlist page MUST support "Move All to Cart" bulk action.

**FR-W26.8** If anonymous customer logs in, anonymous wishlist MUST merge into account wishlist.

**FR-W26.9** Widget MUST handle Salla API errors gracefully — keep local state, retry sync.

**FR-W26.10** Widget MUST integrate with Salla native wishlist (read/write same data source).

##### UX Requirements

- **Icon style:** Outline heart (empty) → filled heart (active).
- **Position:** Top-right of product card, top-right of PDP image gallery.
- **Animation:** Bounce/pulse on toggle (200ms).
- **Color:** Brand red `#DC2626` when filled, neutral gray when empty.
- **Counter badge:** Small circle on header heart icon with count.
- **Wishlist page layout:** Grid (desktop) / list (mobile) of items.

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `show_on_cards` | boolean | true | Heart on product cards |
| `show_on_pdp` | boolean | true | Heart on PDP |
| `show_header_counter` | boolean | true | Global count badge |
| `header_counter_position` | enum | top-right | Position in nav |
| `max_anonymous_items` | int | 50 | localStorage cap |
| `merge_on_login` | boolean | true | Merge anon → account |
| `wishlist_page_url` | string | "/wishlist" | Page location |
| `enable_bulk_move_to_cart` | boolean | true | Bulk action |
| `enable_sharing` | boolean | true | Share wishlist link |
| `share_link_pattern` | string | "/wishlist/{token}" | Public share URL |
| `icon_style` | enum | outline_to_filled | outline_to_filled, filled_to_outline |
| `heart_color_active` | string | "#DC2626" | Filled color |
| `heart_color_inactive` | string | "#9CA3AF" | Empty color |

##### Data Captured

```typescript
interface WishlistItem {
  id: uuid;
  store_id: string;
  customer_id?: string;       // null for anonymous
  session_id?: string;        // for anon merging
  product_id: string;
  variant_id?: string;
  added_at: timestamp;
  source_page: string;        // pdp, category, search
  removed_at?: timestamp;
}

interface WishlistEvent {
  store_id: string;
  event: 'added' | 'removed' | 'viewed_page' | 'moved_to_cart' | 'shared';
  customer_id?: string;
  session_id?: string;
  product_id?: string;
  timestamp: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Anonymous user reaches max items | Show "Sign in to save more" prompt |
| Customer logs in with overlapping items | Merge, dedupe by product_id |
| Product deleted from store | Mark wishlist item as unavailable, gray out on page |
| Product out of stock | Show "Notify when back" CTA (cross-link Feature 2) |
| Salla wishlist API down | Keep local state, sync when API recovers |
| Customer logs out | Wishlist becomes anonymous (localStorage); on next login, merge again |
| Multiple devices same account | Sync via backend; conflict resolution = union |
| Customer shares wishlist | Public read-only view via signed link |
| Wishlist page accessed without items | Empty state with "Browse products" CTA |
| Variant added then variant deleted | Hide variant-specific item, optionally suggest parent |

##### Mobile Considerations
- Larger tap target on heart (44×44).
- Bounce animation more subtle on mobile.
- Wishlist page is single-column list.

##### Accessibility
- Heart is `<button>` with `aria-label="إضافة للمفضلة"` / "Remove from wishlist" (dynamic).
- State change announced via `aria-live`.
- Toggle activatable via Enter and Space.
- Color is not the only signal — outline → filled is visual + aria-pressed state.

##### Salla Integration
- Read/write Salla customer wishlist via `GET/POST/DELETE /v2/customer/wishlist`.
- For anonymous: our DB + localStorage; merge on login.
- Cross-references with Feature 2 (Variant & Price Interest) for OOS products.

---

#### 26.9.2 Widget 26 — Recently Viewed

##### Description
A horizontal carousel of products the customer has recently viewed (last 10-20 items). Helps customers re-find products they liked, increasing return-visit conversion. Displays on homepage, PDP (when scrolled past main content), and a dedicated section in the customer account area.

**Note:** Salla theme M48 has a similar feature; this widget is more polished and provides analytics.

##### User Flow

```
[Customer views PDPs over time]
      ↓
[Each PDP view stored in localStorage (anonymous) or backend (logged in)]
      ↓
[On homepage / PDP / account]
      ↓
[Carousel renders showing last X recently viewed]
      ↓
[Customer scrolls horizontally + taps to revisit]
```

##### Functional Requirements

**FR-W27.1** Widget MUST track product views in: localStorage (anonymous), backend (logged-in).

**FR-W27.2** Widget MUST store last 10-20 viewed products (configurable, FIFO eviction).

**FR-W27.3** Carousel MUST render on homepage and PDP (configurable per page).

**FR-W27.4** Each card MUST display: thumbnail, name, price, wishlist heart (if Wishlist widget enabled).

**FR-W27.5** Cards MUST be horizontally scrollable (touch-swipe on mobile, mouse drag on desktop, arrow buttons).

**FR-W27.6** Widget MUST exclude the current product on PDP (don't show "you viewed THIS product").

**FR-W27.7** Widget MUST hide if fewer than `min_items_to_display` items (default: 3).

**FR-W27.8** Widget MUST sync between anonymous and account on login (merge).

**FR-W27.9** Customer MUST be able to clear recently viewed history (button in widget or settings).

**FR-W27.10** Widget MUST exclude deleted or unpublished products.

##### UX Requirements

- **Layout:** Horizontal carousel, 4-5 cards visible on desktop, 1.5-2 on mobile (peek).
- **Card size:** 200×280 desktop, 140×220 mobile.
- **Navigation:** Arrow buttons on desktop, swipe + dots on mobile.
- **Section title:** "شاهدتِ مؤخراً" / "Recently Viewed".

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `pages` | array | [home, pdp, account] | Where to show |
| `position_on_pdp` | enum | below_description | Where in PDP layout |
| `max_items_stored` | int | 20 | History cap |
| `min_items_to_display` | int | 3 | Hide if fewer |
| `cards_visible_desktop` | int | 5 | Carousel width |
| `cards_visible_mobile` | float | 1.5 | Carousel width |
| `exclude_current_product` | boolean | true | Skip current PDP |
| `show_wishlist_heart` | boolean | true | Integrate with Wishlist widget |
| `section_title_ar` | string | "شاهدتِ مؤخراً" | AR |
| `section_title_en` | string | "Recently Viewed" | EN |
| `clear_history_button` | boolean | true | Show clear button |

##### Data Captured

```typescript
interface RecentlyViewedHistory {
  id: uuid;
  store_id: string;
  customer_id?: string;
  session_id?: string;
  product_ids: string[];      // ordered, most recent first
  last_updated: timestamp;
}

interface RecentlyViewedEvent {
  store_id: string;
  customer_id?: string;
  session_id?: string;
  event: 'viewed' | 'reclicked' | 'cleared';
  product_id?: string;
  source_page: string;        // home, pdp, account
  timestamp: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Customer clears localStorage | History empty, widget hides |
| Product deleted from store | Remove from history silently |
| Product variant — track parent | Store parent_product_id |
| Same product viewed multiple times | Update position to top (most recent) |
| Anonymous customer logs in | Merge anon history into account, dedupe |
| Customer has private browsing mode | History only persists in tab session |
| Customer on multiple devices | Synced via backend (logged-in only) |
| Customer scrolls right past last card | No additional cards to load |
| Widget loaded before product views logged | Hide until data available |

##### Mobile Considerations
- Touch-swipe carousel.
- Smaller cards.
- Section title persists at top.

##### Accessibility
- Section has `<h2>` heading.
- Carousel has `role="region"` `aria-label`.
- Arrow buttons have `aria-label="Next/Previous"`.
- Swipe doesn't break keyboard navigation (Tab + arrow keys).

##### Salla Integration
- Reads `salla.product.id` from Twilight global on PDP visit.
- Optional: store history on Salla customer's `metadata` field for sync (Phase 2).

---

#### 26.9.3 Widget 27 — Also Bought

##### Description
A horizontal carousel on PDP titled "Customers also bought" or "Frequently bought together" that displays products commonly purchased alongside the current product. Drives cross-sell. Algorithm uses co-purchase history from Salla orders.

**MVP algorithm:** Simple co-occurrence: products that appeared in the same orders as the current product, ordered by frequency.

##### User Flow

```
[Customer views PDP]
      ↓
[Backend returns top-N co-purchased products]
      ↓
[Carousel renders below main content]
      ↓
[Customer taps a recommended product → navigates to its PDP]
      ↓
[Cross-sell impression logged]
```

##### Functional Requirements

**FR-W28.1** Widget MUST display 4-12 recommended products per PDP.

**FR-W28.2** Recommendations MUST be based on co-purchase frequency from Salla orders.

**FR-W28.3** Algorithm MUST run as a daily batch job (precomputed) — NOT real-time.

**FR-W28.4** Widget MUST exclude the current product from recommendations.

**FR-W28.5** Widget MUST exclude out-of-stock products by default (configurable).

**FR-W28.6** Each card MUST display: thumbnail, name, price, ATC button.

**FR-W28.7** Inline ATC MUST add product without leaving current PDP.

**FR-W28.8** Widget MUST fall back to "Same category" or "Popular products" if no co-purchase data.

**FR-W28.9** Widget MUST exclude products tagged as `not_recommended` by merchant.

**FR-W28.10** Widget MUST handle stores with insufficient order history (< 50 orders) — fall back to popularity.

##### UX Requirements

- **Layout:** Horizontal carousel (same shape as Recently Viewed).
- **Cards include ATC button** (small, inline).
- **Section title:** "اشترى الآخرون أيضاً" / "Customers also bought".
- **Optional bundle CTA:** "Add all to cart" button (bundle UX).

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `max_recommendations` | int | 8 | Cap |
| `min_recommendations` | int | 3 | Hide if fewer |
| `exclude_oos` | boolean | true | Skip OOS products |
| `fallback_algorithm` | enum | popular | popular, same_category, none |
| `inline_atc` | boolean | true | Allow ATC without nav |
| `show_bundle_cta` | boolean | false | "Add all" button |
| `bundle_discount_percent` | float | 0 | Bundle discount if used |
| `section_title_ar` | string | "اشترى الآخرون أيضاً" | AR |
| `section_title_en` | string | "Customers also bought" | EN |
| `excluded_products` | array | [] | Never recommend |
| `algorithm_min_co_occurrence` | int | 3 | Min co-purchases to qualify |

##### Algorithm (MVP)

```
1. Query Salla orders (last 180 days)
2. For each order, generate all pairs of products
3. Count co-occurrence per pair
4. For each product, rank companions by co-occurrence count desc
5. Cache results per product (TTL 24h)
6. On PDP load → fetch from cache
```

##### Data Captured

```typescript
interface AlsoBoughtRecommendation {
  store_id: string;
  source_product_id: string;
  recommended_product_id: string;
  co_occurrence_count: number;
  computed_at: timestamp;
}

interface AlsoBoughtEvent {
  store_id: string;
  session_id: string;
  source_product_id: string;
  recommendation_ids_shown: string[];
  action: 'shown' | 'clicked' | 'atc' | 'bundle_add';
  clicked_product_id?: string;
  timestamp: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| New product (no co-purchase data) | Fall back to same-category |
| Store has < 50 orders | Fall back to popular products |
| All recommended products OOS | Show fallback or hide widget |
| Customer already has recommended product in cart | Suppress that recommendation |
| Recommendations include current product | Filter out |
| Inline ATC fails (Salla API error) | Show error toast |
| Bundle CTA selected | Add all visible recommendations + current to cart |
| Algorithm cache stale (>24h) | Use stale cache; recompute async |
| Variant-level recommendations | Recommend at parent product level |

##### Mobile Considerations
- Carousel scrollable.
- Cards smaller; ATC button compact.
- Bundle CTA prominent on mobile.

##### Accessibility
- Section heading proper.
- Each card focusable.
- ATC button labeled.
- Bundle CTA describes action ("Add all 4 items to cart").

##### Salla Integration
- Reads Salla orders via `GET /admin/v2/orders` (paginated, last 180 days).
- Posts ATC via `salla.cart.addItem`.
- Precomputed nightly cron.

---

#### 26.9.4 Widget 28 — Comparison Button

##### Description
A "Compare" button on product cards and PDPs that adds the product to a comparison tray. Customer can compare up to 4 products side-by-side in a dedicated comparison view, showing attributes like price, specifications, ratings, and availability. Decision-support widget for considered purchases.

##### User Flow

```
[Customer browses product cards or PDPs]
      ↓
[Compare button on each card/PDP]
      ↓
[Customer taps "Compare" on Product A]
      ↓
[Floating tray appears at bottom showing 1 product]
      ↓
[Customer taps "Compare" on Product B, C, D]
      ↓
[Tray shows 4 products, button "Compare All" enabled]
      ↓
[Customer taps "Compare All"]
      ↓
[Comparison view opens: side-by-side table]
      ↓
[Customer can remove products, ATC, or close]
```

##### Functional Requirements

**FR-W29.1** Widget MUST display "Compare" button on product cards and PDP.

**FR-W29.2** Customer MUST be able to add up to `max_comparison_items` (default: 4) products to comparison.

**FR-W29.3** Comparison state MUST persist in localStorage (anonymous) or backend (logged in).

**FR-W29.4** Floating tray MUST appear at bottom when ≥1 item added, listing thumbnails + remove buttons.

**FR-W29.5** Tray MUST have a "Compare All" CTA enabled when ≥2 items.

**FR-W29.6** Comparison view MUST display a table with rows for: image, name, price, key attributes (5-10 configurable), availability, ATC button.

**FR-W29.7** Key attributes MUST be configurable per category (e.g., perfume vs cosmetic vs fashion).

**FR-W29.8** Customer MUST be able to add to cart directly from comparison view.

**FR-W29.9** Widget MUST exclude items that cannot be compared (different categories) OR allow cross-category with warning.

**FR-W29.10** Comparison view MUST highlight differences (e.g., best price highlighted).

##### UX Requirements

- **Compare button on cards:** Small icon + text, secondary action.
- **Floating tray:** Fixed bottom, 80px tall, horizontal scroll if 4 items.
- **Comparison view:** Modal or dedicated page, table layout.
- **Differences highlighted:** Best/worst values bolded or colored.
- **Mobile:** Stack vertically, no side-by-side (or 2-column max).

##### Configuration Options

| Setting | Type | Default | Description |
|---|---|---|---|
| `enabled` | boolean | true | Master toggle |
| `show_on_cards` | boolean | true | Compare btn on cards |
| `show_on_pdp` | boolean | true | Compare btn on PDP |
| `max_comparison_items` | int | 4 | Cap |
| `comparable_attributes` | array | [price, brand, key_specs] | Default columns |
| `category_attributes` | object | { perfume: [scent, size, ml], fashion: [size, color, material] } | Per-category |
| `allow_cross_category` | boolean | false | Allow disparate items |
| `cross_category_warning_ar` | string | "تختار منتجات من فئات مختلفة" | AR |
| `tray_position` | enum | bottom | bottom only (for MVP) |
| `compare_view_format` | enum | modal | modal, page |
| `highlight_best_price` | boolean | true | Highlight in view |
| `clear_button` | boolean | true | "Clear all" in tray |
| `share_comparison_link` | boolean | false | Generate shareable URL (Phase 2) |

##### Data Captured

```typescript
interface ComparisonSession {
  store_id: string;
  session_id: string;
  customer_id?: string;
  product_ids: string[];
  added_at: timestamp;
  comparison_view_opened: boolean;
  led_to_purchase: boolean;
}

interface ComparisonEvent {
  store_id: string;
  session_id: string;
  event: 'product_added' | 'product_removed' | 'view_opened' | 'atc_from_compare' | 'cleared';
  product_id?: string;
  timestamp: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Customer adds 5th item (max 4) | Show "max reached, remove one to add more" |
| Compared item out of stock | Show "نفذت" badge + disable ATC |
| Compared item deleted | Auto-remove from comparison |
| Cross-category items | Show warning, allow if config permits |
| Anonymous customer logs in | Merge localStorage comparison into account |
| Customer reloads page | Comparison persists |
| Customer clears localStorage | Comparison reset |
| Attribute not available on product | Show "—" or "غير متوفر" |
| Mobile: 4 items in side-by-side | Switch to vertical stack layout |
| Customer adds variants of same product | Treat as separate compare items |

##### Mobile Considerations
- Floating tray: smaller, 60px tall.
- Comparison view: vertical accordion or 2-column max.
- ATC button per row, large.

##### Accessibility
- Compare button is `<button>` with `aria-pressed` state.
- Tray is `role="region"` `aria-label="مقارنة المنتجات"`.
- Comparison table is proper `<table>` with `<th>` for product names.
- Highlight differences via screen-reader-friendly text ("Best price: ...") not just color.

##### Salla Integration
- Reads product attributes from `salla.product` Twilight global OR `GET /v2/products/{id}`.
- ATC via `salla.cart.addItem`.

---

### 26.10 Tool Widget

#### 26.10.1 Widget 29 — Widget Customizer

##### Description
The most complex item in the MVP — a merchant-facing visual editor that lets merchants configure, preview, and deploy any of the 28 customer-facing widgets with a no-code interface. Built into the merchant dashboard. Replaces JSON config editing with a polished UI featuring forms, color pickers, live preview, and one-click publish.

**The Widget Customizer is the central control plane for the entire widget library.**

**Key sub-features:**
1. Widget gallery (browse all available widgets)
2. Per-widget configuration UI (forms generated from widget config schema)
3. Live preview (iframe of storefront with widget rendered)
4. Bilingual content editor (AR + EN side-by-side)
5. Theme customization (colors, typography, spacing)
6. Page targeting rules
7. A/B variant editor
8. Versioning + rollback
9. Publishing workflow (draft → preview → publish)
10. Performance estimation (loading impact)

##### User Flow

```
[Merchant logs into dashboard]
      ↓
[Navigates to "Widgets" section]
      ↓
[Widget gallery shows all 28 widgets organized by category]
      ↓
[Merchant clicks "Configure" on Live Viewer Counter]
      ↓
[Customizer opens:
  Left panel: configuration form (sections for triggers, content, design, etc.)
  Right panel: live preview iframe of storefront with widget rendered
]
      ↓
[Merchant edits values; preview updates real-time]
      ↓
[Merchant clicks "Preview on Live Store" → opens new tab with debug param]
      ↓
[Merchant clicks "Publish" → confirmation modal]
      ↓
[Widget goes live (or scheduled for future activation)]
      ↓
[Versioning: prior config retained; rollback button available]
```

##### Functional Requirements

**FR-W30.1** Widget gallery MUST list all 28 customer-facing widgets, organized by 9 categories (Section 26.1-26.9).

**FR-W30.2** Each widget card MUST show: name, category, status (active/draft/disabled), preview thumbnail, complexity rating.

**FR-W30.3** Customizer MUST render configuration forms dynamically based on widget's config schema.

**FR-W30.4** Form sections MUST include: General (enabled, pages), Triggers (where applicable), Content (text, bilingual), Design (colors, spacing), Advanced (frequency, exclusions).

**FR-W30.5** Color picker MUST support hex, RGB, brand presets, and accessibility contrast warnings.

**FR-W30.6** Bilingual editor MUST show AR + EN side-by-side with auto-translation suggestions (Phase 2; MVP is manual).

**FR-W30.7** Live preview MUST render the widget in an iframe simulating the merchant's storefront.

**FR-W30.8** Preview MUST support device toggle: mobile, tablet, desktop.

**FR-W30.9** Preview MUST update within 500ms of config change (debounced).

**FR-W30.10** Customizer MUST support draft saving (auto-save every 30s).

**FR-W30.11** Customizer MUST require explicit "Publish" action to apply changes to live storefront.

**FR-W30.12** Customizer MUST keep version history (last 10 versions per widget).

**FR-W30.13** Merchant MUST be able to rollback to a previous version with one click.

**FR-W30.14** Customizer MUST support widget-level disable (turn off without deleting config).

**FR-W30.15** Customizer MUST validate config server-side before publish; block invalid configs with inline errors.

**FR-W30.16** Customizer MUST estimate performance impact (extra KB, render time) for current config and warn if combined widgets exceed budget (Section 11.3).

**FR-W30.17** Customizer MUST support A/B variant creation: define 2 versions, set traffic split (50/50 default), track conversion separately.

**FR-W30.18** Customizer MUST support scheduled publishing: "Publish on {date+time}" for seasonal/campaign widgets.

**FR-W30.19** Customizer MUST support import/export of widget configs as JSON (for sharing between stores or backups).

**FR-W30.20** Customizer MUST detect and warn about conflicting widget combinations (e.g., enabling both Floating Marketing Button and Quick Contact).

##### UX Requirements

- **Dashboard layout:**
  - Left sidebar: widget categories navigation.
  - Main area:
    - Gallery view: grid of widget cards.
    - Detail view: split-pane (form left, preview right).
- **Form sections:** Accordion or tabs to group related settings.
- **Live preview:**
  - Sticky in right pane.
  - Device toggle: mobile / tablet / desktop.
  - Page selector: home / PDP / cart / category.
  - Debug mode toggle.
- **Save/Publish:**
  - Auto-save badge: "Saved 3 seconds ago".
  - Sticky bottom bar with "Discard", "Save Draft", "Publish" actions.
- **Versioning UI:**
  - "History" tab showing previous versions with timestamps.
  - Rollback button per version.

##### Customizer Sub-Components

1. **Widget Gallery**
   - Filterable by category, complexity, active status.
   - Search bar.
   - Per-widget: status indicator (Active/Draft/Disabled), Edit button.

2. **Configuration Form Engine**
   - Renders forms from JSON schema per widget.
   - Field types: text, textarea, number, boolean, enum (dropdown), color, file (upload), array (repeatable), object (group), date, time.
   - Validation: required fields, format checks, range limits.
   - Inline errors and warnings.

3. **Bilingual Editor**
   - Two columns: AR (RTL) | EN (LTR).
   - Per-field language pair.
   - Auto-detect required language fields.

4. **Theme Editor**
   - Color picker with contrast checker (vs background).
   - Font size, weight, family selectors.
   - Spacing controls (padding, margin).
   - Border radius slider.

5. **Page Targeting**
   - Multi-select: home, pdp, cart, category, search, account.
   - Per-category filters (e.g., "only show on category X").
   - Per-product overrides (include/exclude product IDs).
   - URL pattern matching (regex).

6. **A/B Variants**
   - "Add Variant" button on widget detail.
   - Each variant has its own config + share of traffic.
   - Min sample size before showing significant winner.
   - Variant performance shown in Widget Analytics (Section 10).

7. **Versioning**
   - On each publish, snapshot current config as a version.
   - Version label (auto: "v1, v2"; custom optional).
   - Diff view: side-by-side comparison of two versions.
   - Rollback: copies version to current draft.

8. **Performance Estimator**
   - Sums byte sizes of enabled widgets.
   - Estimates render time per page based on widget complexity.
   - Shows budget bar: "Current 38KB / Budget 50KB" green/orange/red.

9. **Conflict Detector**
   - Static rules: "Floating Marketing Button + Quick Contact = pick one".
   - Position collision detection: "Multiple widgets requested bottom-right".
   - Page placement clashes.

10. **Live Preview Iframe**
    - Loads merchant's storefront (with auth bypass via signed JWT).
    - Injects current draft widget config as URL param.
    - Updates on config change (postMessage to iframe).
    - Device toggle adjusts iframe dimensions + viewport meta.

##### Configuration Options (Meta-Config for the Customizer itself)

| Setting | Type | Default | Description |
|---|---|---|---|
| `auto_save_interval_seconds` | int | 30 | Draft auto-save frequency |
| `max_versions_retained` | int | 10 | Version history cap |
| `preview_debounce_ms` | int | 500 | Preview update debounce |
| `enable_ab_variants` | boolean | true | Allow variants |
| `enable_scheduled_publish` | boolean | true | Allow scheduled |
| `enable_import_export` | boolean | true | JSON I/O |
| `performance_warn_threshold_kb` | int | 40 | Soft warning |
| `performance_block_threshold_kb` | int | 60 | Hard block |
| `default_preview_device` | enum | mobile | Initial preview device |

##### Data Captured

```typescript
interface WidgetConfig {
  id: uuid;
  store_id: string;
  widget_type: string;          // e.g., 'live_viewer_counter'
  config_data: object;          // schema per widget
  status: 'draft' | 'active' | 'disabled' | 'scheduled';
  scheduled_publish_at?: timestamp;
  version: number;
  created_at: timestamp;
  updated_at: timestamp;
  published_at?: timestamp;
  variants?: WidgetVariant[];
}

interface WidgetConfigVersion {
  id: uuid;
  widget_config_id: uuid;
  version: number;
  config_snapshot: object;
  published_at: timestamp;
  published_by: string;         // merchant user
}

interface WidgetVariant {
  id: uuid;
  widget_config_id: uuid;
  variant_name: string;
  config_overrides: object;
  traffic_share_percent: number;
  metrics: {
    impressions: number;
    conversions: number;
    conversion_rate: float;
  };
}

interface CustomizerActivity {
  store_id: string;
  user_id: string;
  widget_type: string;
  action: 'opened' | 'saved_draft' | 'published' | 'rolled_back' | 'preview_viewed' | 'variant_added';
  config_changes: object;       // diff
  timestamp: timestamp;
}
```

##### Edge Cases

| Edge Case | Behavior |
|---|---|
| Merchant publishes invalid config | Server validates; block + show errors inline |
| Two users editing same widget | Last-save-wins with warning ("X was editing this widget") |
| Auto-save fails (server down) | Show "offline" indicator; retain in localStorage; sync on reconnect |
| Iframe preview fails to load | Show error placeholder with "Try again" button |
| Preview iframe has CORS issue | Use proxy with signed token |
| Merchant changes language mid-edit | Field state preserves both AR + EN values |
| Config schema changes (post-deploy) | Backward-compatible migrations; default values fill gaps |
| Variant with 0% traffic split | Allowed; effectively disabled variant |
| Scheduled publish conflicts with manual publish | Manual publish overrides scheduled |
| Rollback to deleted widget version | Restore + warn that prior version may behave differently |
| Performance budget exceeded | Block publish; force merchant to disable some widgets first |
| Export contains sensitive data (API keys) | Strip before export |
| Import malformed JSON | Validate; show field-level errors |
| Two conflicting widgets enabled | Show warning banner in gallery + block publish |

##### Mobile Considerations
- **Customizer is desktop-first** — phone/tablet display is read-only summary.
- On mobile, merchant can view widget status, enable/disable, and see analytics, but cannot edit detailed configs.
- "Edit on desktop" banner shown on mobile.

##### Accessibility
- All form fields properly labeled (`<label for>`).
- Tab order logical: gallery → detail → form sections → preview.
- Color picker accessible (hex input as alternative to visual picker).
- Bilingual editor properly directional (RTL for AR field, LTR for EN).
- Validation errors announced via `aria-live`.
- Preview iframe has descriptive `aria-label`.
- All buttons have descriptive labels (not just icons).
- Keyboard shortcuts: `Cmd+S` save draft, `Cmd+Shift+P` publish, `Esc` close detail.

##### Salla Integration
- Customizer is part of our merchant dashboard (separate from Salla admin).
- Widget configs are stored in our DB.
- Configs are injected into storefront via our App Snippet (Section 13.6).
- For live preview: load merchant's Salla storefront in iframe with `?ssw_preview_token={JWT}` URL param.
- Snippet detects preview mode and uses draft config instead of published.

##### Performance & Scaling
- Form rendering is lazy: schema loaded on widget click.
- Preview iframe loads once, updates via postMessage (no full reload).
- Auto-save debounced; backend writes batched.
- Config versions stored separately, only last 10 retained per widget.
- Schema validation is fast (< 50ms); UI doesn't block.

##### Onboarding
- **First-time use:** Guided tour highlighting gallery → click → form → preview → publish workflow.
- **Per-widget hints:** Tooltips on first-time configuration of each widget.
- **Templates:** Pre-configured "starter" configs per widget (one-click apply).

---

### 26.11 Cross-Widget Interactions Matrix

Many widgets interact with each other in important ways. This table summarizes the key interactions to consider during implementation:

| Widget A | Widget B | Interaction |
|---|---|---|
| Floating Marketing Button | Quick Contact | Mutually exclusive — only one |
| Floating Marketing Button | Scroll-to-Top | Stack vertically (Scroll-to-Top above WA) |
| Floating Marketing Button | Sticky ATC | WA z-index higher; both visible |
| Recent Purchase Toast | Sticky ATC | Toasts position above ATC bar |
| Hesitation Capture (Feature 1) | Exit Intent Popup | Mutually exclusive per session |
| Welcome Popup | Age Verification | Age Verification fires first; Welcome waits |
| Low Stock Urgency | Stock Progress Bar | Both can show; merchant chooses |
| Sale Countdown | White Friday | White Friday can auto-create Countdown campaign |
| Free Shipping Countdown | Cart Abandonment | Cart Abandonment can include shipping incentive |
| Wishlist Heart | Recently Viewed | Recently Viewed cards include wishlist heart |
| Wishlist Heart | Also Bought | Recommendation cards include wishlist heart |
| Comparison Button | Also Bought | Compare button on recommendation cards |
| All Popups | Each other | Global quiet period (30s) between popups |
| Ramadan Mode | Other Popups | Aggressive popups paused during Iftar window |
| Newsletter Signup | Welcome Popup | If welcome has signup → suppress newsletter popup |

---

### 26.12 Shared Implementation Notes

**Snippet bundle structure (high-level):**
- Core runtime: ~12 KB (event bus, config loader, A11y helpers)
- Per-widget bundles loaded lazily: 2-6 KB each
- Total budget for active widgets: ≤ 50 KB gzipped (Section 11.3)

**Configuration loading:**
- On page load, fetch consolidated widget config: `GET /widgets/active?store_id=X&page_type=Y`
- Backend returns: array of active widget configs filtered by current page type
- Client renders each widget independently inside Shadow DOM

**Cross-widget event bus:**
- Pub/sub pattern: e.g., `cart.updated`, `widget.shown`, `popup.fired`
- Allows quiet-period coordination, mutual exclusion, and analytics consistency

**Analytics:**
- All widget impressions/interactions captured per Widget Analytics (Section 10)
- Per-widget conversion rate tracking
- A/B variant performance tracking

**Internationalization:**
- All user-facing strings stored per-widget config in `_ar` and `_en` fields
- Customer-language detection: Salla customer profile > browser Accept-Language > store default

**PDPL compliance:**
- Widgets that capture PII (Newsletter Signup, Quick Contact form, etc.) MUST include explicit consent
- Consent terms link to Privacy Policy (managed by merchant)
- Customer can revoke via tokenized consent management URLs in emails

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

> **التحدي الأكبر:** الانضباط بـ scope الـ MVP. أي إضافة بعد الـ 33 item = scope creep.
> **الـ Success:** Submission rate ≥3% + Trial-to-paid ≥15% + 30-day retention ≥70%
> **النطاق:** 4 features أساسية + 29 widget = 33 item قابلين للتسليم.
