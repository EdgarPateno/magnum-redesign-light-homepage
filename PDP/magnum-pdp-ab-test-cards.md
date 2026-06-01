# Magnum Supps — PDP Phase 1 A/B Test Cards

> Backlog-ready experiment cards for the Phase 1 PDP quick wins.
> Source: PDP CRO audit of magnumsupps.com (Quattro, Limitless, Beach Body bundle) benchmarked vs. Ghost, BPN, PVL, HD Muscle, Transparent Labs, 1st Phorm.
> Sample sizes below are LOCKED to real Shopify analytics (30-day window). Recompute only if the traffic window changes: https://www.evanmiller.org/ab-testing/sample-size.html

**Live baselines (30-day window):**
- PDP sessions: **118,601** → ~27,300/week → **~13,650 per variant/week** at 50/50
- Online store visitors: **86,124** · Purchase conversion: **1.88%** → ~1,619 orders/month (~187 orders/variant/week)
- Store-wide add-to-cart rate: **6.23%**
- Mobile share: **68.98%** · Mobile add-to-cart rate: **6.42%** → mobile PDP sessions ~81,800/mo (~9,400/variant/week)
- Subscription take-rate: **__% (PENDING — only field still needed, for TEST-1)**

**Sizing reference at 6.23% ATC baseline** (80% power, 95% confidence, two-sided): +20% MDE ≈ 6,400/variant · +15% MDE ≈ 11,200/variant · +10% MDE ≈ 24,700/variant. At ~13,650 sessions/variant/week, any ATC-primary test is powered to a 10% lift inside the 2-week business-cycle minimum — **the cycle floor is the binding constraint, not sample size. Do not stop early.**

---

## Run order (avoid confounding)

Tests 2, 3, and 5 all change above-the-fold / CTA-area elements — do **not** run them on the same traffic simultaneously.

| Slot | Test | Status | Notes |
|------|------|--------|-------|
| 1 | TEST-1 Subscription default | ⬜ Not started | Highest ICE; isolated metric (sub take-rate) |
| 2 | TEST-3 Per-serving price | ⬜ Not started | Layer onto Test 1 winner |
| 3 | TEST-2 Trust strip | ⬜ Not started | Biggest expected purchase-rate lift of ATF tests |
| 4 | TEST-5 Benefit bullets | ⬜ Not started | Run after trust strip concludes |
| – | TEST-4 Sticky ATC | ⬜ Not started | Mobile-segmented; can run in parallel (isolated component) |

Status legend: ⬜ Not started · 🟡 Running · ✅ Shipped · ❌ Killed · 🔁 Iterate

### Program calendar (~8 weeks)

| Weeks | Running | Rationale |
|-------|---------|-----------|
| 1–2 | TEST-1 (sub default) + TEST-4 (mobile sticky) | Different metrics, no ATF overlap → safe in parallel |
| 3–4 | TEST-2 (trust strip, ATC-primary) | First above-the-fold test |
| 5–6 | TEST-5 (benefit bullets) | Next ATF test, after trust strip clears |
| 7–8 | TEST-3 (per-serving) on TEST-1 winner | Layers onto shipped subscription default |

---

## TEST-1 — Subscription default ⭐
- **Ticket:** MAG-003 · **ICE:** I9 · C8 · E9 = **8.7** · **Status:** ⬜ · **Owner:** ______
- **Page(s):** All PDPs (Quattro, Limitless, all consumables)

**Hypothesis**
Because the PDP defaults to "One-time purchase" while Ghost, PVL, and Transparent Labs all pre-select Subscribe & Save, we believe defaulting the selector to Subscribe & Save with flexibility copy ("cancel, pause, or skip anytime") will increase subscription take-rate for all PDP buyers. We'll know it's true when subscription-attached orders rise without a drop in overall purchase rate.

| Variant | Definition |
|---------|------------|
| Control (A) | One-time purchase pre-selected (current) |
| Variant (B) | Subscribe & Save pre-selected + microcopy: "$XX.XX/order · 15% off every order · Cancel, pause, or skip anytime" |

- **Primary metric:** % of orders with an active subscription
- **Secondary:** revenue/PDP visitor, projected LTV, one-time→sub switch rate
- **Guardrail:** overall PDP→purchase rate (must not drop), 30-day subscription cancel/refund rate
- **Sample (LOCKED):** detecting 6%→12% take-rate needs **~350 orders/variant**. At ~187 orders/variant/week → reaches sample in **~2 weeks**. Powered (and faster if the real default-on lift exceeds 2×, which is common). Refine once real sub take-rate is supplied.
- **Allocation:** 50/50 · **Min duration:** 2 weeks
- **Ship rule (pre-committed):** ______ (e.g., "ship if sub-revenue/visitor up even with ≤5% lower purchase rate")

**Results (fill post-test)**
- Sample reached: ____ /variant · Primary: control __% vs variant __% · Lift: __% (95% CI: __ to __, p=__)
- Guardrails: __ · Segment deltas (mobile/desktop, new/returning): __
- **Decision:** ____ · **Learning / pattern:** ____

---

## TEST-2 — Trust strip under ATC
- **Ticket:** MAG-004 · **ICE:** I7 · C7 · E9 = **7.7** · **Status:** ⬜ · **Owner:** ______
- **Page(s):** All PDPs

**Hypothesis**
Because Magnum shows no guarantee, testing badge, or risk reversal near the CTA (unlike 1st Phorm's money-back and BPN's NSF/GMP), we believe adding a trust strip (satisfaction guarantee · free-shipping threshold · Kosher/gluten-free/dye-free badges) directly below Add-to-Cart will increase add-to-cart rate for all visitors. We'll know it's true when ATC rate rises with purchase rate holding or improving.

| Variant | Definition |
|---------|------------|
| Control (A) | No trust strip (current) |
| Variant (B) | Trust strip block below ATC: guarantee + free-ship threshold + product certifications |

- **Primary metric:** PDP→add-to-cart rate
  - *Metric swap rationale:* at 1.88% purchase rate, a purchase-primary test needs ~6–7 weeks to detect a 10% lift. Add-to-cart (6.23% baseline) gives a clean 2-week read; purchase is kept as a secondary confirmation.
- **Secondary:** PDP→purchase rate, cart→checkout completion
- **Guardrail:** refund/return rate, support tickets
- **Sample (LOCKED, 6.23% baseline):** +15% rel. ≈ **11,200/variant**; +10% rel. ≈ **24,700/variant**. Reaches sample in **~2 weeks**.
- **Allocation:** 50/50 · **Min duration:** 2 weeks

**Results (fill post-test)**
- Sample reached: ____ /variant · Primary: control __% vs variant __% · Lift: __% (95% CI: __ to __, p=__)
- Guardrails: __ · Segment deltas: __
- **Decision:** ____ · **Learning / pattern:** ____

---

## TEST-3 — Per-serving cost framing
- **Ticket:** MAG-005 · **ICE:** I6 · C7 · E9 = **7.3** · **Status:** ⬜ · **Owner:** ______
- **Page(s):** Protein + higher-priced SKUs first (4lb, Quattro)

**Hypothesis**
Because the $69.99 Quattro price has no value anchor against cheaper whey, we believe adding "as low as $X/serving" at the price (using subscription price when selected) will reduce price hesitation and increase add-to-cart rate, especially on 4lb and protein SKUs.

| Variant | Definition |
|---------|------------|
| Control (A) | Price only (current) |
| Variant (B) | Price + "as low as $X.XX/serving" (recomputes for Subscribe & Save) |

- **Primary metric:** PDP→add-to-cart rate
- **Secondary:** 4lb vs 2lb size mix, subscription attach rate
- **Guardrail:** purchase rate, AOV
- **Sample (LOCKED, 6.23% baseline):** +15% rel. ≈ **11,200/variant**; +10% rel. ≈ **24,700/variant**.
- **Allocation:** 50/50 · **Min duration:** 2 weeks (extend to 3–4 if protein/4lb subset traffic is small — run site-wide if needed to hit sample)
- **Dependency:** Run AFTER TEST-1 ships — the per-serving line reinforces the subscription price, so running both at once confounds attribution.

**Results (fill post-test)**
- Sample reached: ____ /variant · Primary: control __% vs variant __% · Lift: __% (95% CI: __ to __, p=__)
- Guardrails: __ · Segment deltas: __
- **Decision:** ____ · **Learning / pattern:** ____

---

## TEST-4 — Enriched sticky ATC (mobile)
- **Ticket:** MAG-006 · **ICE:** I5 · C7 · E8 = **6.7** · **Status:** ⬜ · **Owner:** ______
- **Page(s):** All PDPs · **Segment:** mobile

**Hypothesis**
Because the mobile sticky bar shows only "Add to cart" — forcing a scroll-up to confirm flavor and price — we believe adding thumbnail + live price + selected variant to the sticky bar will increase mobile add-to-cart rate, with no desktop regression.

| Variant | Definition |
|---------|------------|
| Control (A) | Button-only sticky bar (current) |
| Variant (B) | Sticky bar with featured image + live price + selected variant |

- **Primary metric:** mobile PDP→add-to-cart rate
- **Secondary:** time-to-ATC, scroll-depth-to-purchase
- **Guardrail:** mobile bounce, accidental-add / cart-removal rate
- **Sample (LOCKED, 6.42% mobile ATC, 68.98% mobile share):** +15% rel. ≈ **10,900/variant**; +10% rel. ≈ **23,900/variant**. At ~9,400 mobile sessions/variant/week → **~2 wks for +15%, ~3 wks for +10%**.
- **Allocation:** 50/50, analyze mobile segment · **Min duration:** 2–3 weeks
- **Note:** isolated component — safe to run in parallel with other tests.

**Results (fill post-test)**
- Sample reached: ____ /variant · Primary: control __% vs variant __% · Lift: __% (95% CI: __ to __, p=__)
- Guardrails: __ · Segment deltas: __
- **Decision:** ____ · **Learning / pattern:** ____

---

## TEST-5 — Outcome-led benefit bullets (ATF)
- **Ticket:** MAG-007 · **ICE:** I6 · C6 · E8 = **6.7** · **Status:** ⬜ · **Owner:** ______
- **Page(s):** All PDPs (per-product bullet sets)

**Hypothesis**
Because Magnum's strongest differentiator (zero bloat, lactose-friendly) is buried in a feature list, we believe surfacing 3–4 outcome-led benefit bullets above the fold will increase add-to-cart rate by helping visitors grasp "why this product" within 5 seconds — mirroring PVL's outcome-led hook.

| Variant | Definition |
|---------|------------|
| Control (A) | No ATF benefit bullets (current) |
| Variant (B) | 4 icon bullets, e.g. protein: "Zero gas/bloating · 30g 4-source protein · Lactose-friendly · Kosher & gluten-free" (pre-workout gets its own set) |

- **Primary metric:** PDP→add-to-cart rate
- **Secondary:** scroll depth, accordion-open rate (do fewer people need to dig?)
- **Guardrail:** purchase rate, page load time
- **Sample (LOCKED, 6.23% baseline):** +15% rel. ≈ **11,200/variant**; +10% rel. ≈ **24,700/variant**. Reaches sample in **~2 weeks**.
- **Allocation:** 50/50 · **Min duration:** 2 weeks
- **Dependency:** another ATF change — run AFTER TEST-2 (trust strip) concludes to avoid confounding.

**Results (fill post-test)**
- Sample reached: ____ /variant · Primary: control __% vs variant __% · Lift: __% (95% CI: __ to __, p=__)
- Guardrails: __ · Segment deltas: __
- **Decision:** ____ · **Learning / pattern:** ____

---

## Pre-launch checklist (per test)
- [ ] Hypothesis documented (above)
- [ ] Real baseline + traffic plugged in; sample size recalculated
- [ ] Primary / secondary / guardrail metrics instrumented and QA'd
- [ ] Variant QA'd on mobile + desktop (no flicker, correct price recompute)
- [ ] Run ≥ 1 full business cycle (2 weeks min); no peeking / early stop
- [ ] Ship rule pre-committed where guardrails trade off against primary
