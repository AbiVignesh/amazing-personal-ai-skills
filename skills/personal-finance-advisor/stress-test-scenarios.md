---
name: stress-test-scenarios
description: Stress-test user's financial resilience under adverse scenarios: job loss, market correction, medical emergency. For each scenario, calculate survival timeline, actions needed, and risk level. Use when user asks "Can I survive job loss?" "What if market crashes?" "Emergency fund adequate?" Output: 3 scenarios with clear impacts and risk levels. Quantitative, not emotional.
---

# Stress Test Scenarios (Maya)

How much pain can you absorb?

---

## YOUR TASK

Run **3 stress scenarios** on user's financial situation. For each:

1. **Scenario Trigger**: What happens
2. **Impact**: Quantified consequences (in ₹, months, %)
3. **Survival Timeline**: How long can user maintain obligations?
4. **Actions Needed**: Contingency sequence
5. **Risk Level**: 🔴 Critical / 🟠 High / 🟡 Medium / 🟢 Low

**Output**: 3 scenarios, clear impacts, no ambiguity.

---

## SCENARIO 1: 30% Income Drop (Job Loss / Role Change / Salary Cut)

**Trigger**: User loses primary employment or income drops 30% overnight.

**Calculate**:
- Monthly income: Before = ₹X, After = ₹0.7X (or ₹0)
- Fixed obligations: Car EMI, rent, insurance, loan EMIs (non-negotiable)
- Emergency fund runway: Emergency Fund ÷ Monthly Fixed = Survival Months
- Variable spending cuts available: Can user cut dining, entertainment, subscriptions?

**Output Template**:
```
SCENARIO 1: 30% Income Drop (Job Loss)

Monthly Income: ₹[X] → ₹[Y] (change: ₹[Z])
Fixed Obligations (non-negotiable): ₹[EMI+rent+insurance+mandatory] / month
Emergency Fund: ₹[Amount]
Survival Timeline: [X] months

Actions Needed (by month):
- Month 1–2: [Immediate action: cut variable spending, activate emergency fund]
- Month 2–3: [If still unemployed: activate side-gig, sell non-essential assets]
- Month 3–4: [If still unemployed: major restructuring (sell car? move home?)]
- Month 4+: [Last resort: family support, personal loans, major asset liquidation]

Risk Level: [🔴 Critical / 🟠 High / 🟡 Medium / 🟢 Low]
Why: [Clear reasoning based on survival timeline vs. realistic job-hunting window]
```

**Example**:
```
SCENARIO 1: Job Loss (Income ₹95k → ₹0)

Fixed Obligations: Car EMI ₹22k + Min Rent ₹15k = ₹37k/month
Emergency Fund: ₹5L
Survival Timeline: 13.5 months (₹5L ÷ ₹37k/month)

Actions Needed:
- Month 1–2: Aggressively job search (target: ₹90k+ role within 60 days). Cut variable spend to zero (dining ₹0, entertainment ₹0).
- Month 3–4: If still unemployed, activate consulting side-gig (target ₹10–15k/month). Survival extends to 18–20 months.
- Month 5–6: If side-gig doesn't hit ₹10k, consider selling car. Saves ₹22k EMI, converts ₹12L car value → ₹2L liquid.
- Month 6+: If still unemployed AND side-gig <₹10k, move in with parents (if available) OR take personal loan ₹10L @ 12%.

Risk Level: 🟠 High
Why: Emergency fund gives 13 months runway (good). But single income dependency means any job loss is existential. Side-gig is lifeline, not luxury.
```

---

## SCENARIO 2: 25% Market Correction (Economic Shock)

**Trigger**: Sensex drops 25% (like 2020 COVID crash, or 2008 financial crisis).

**Calculate**:
- Current equity portfolio value
- Loss in correction: Portfolio × 25%
- New portfolio value: Current - Loss
- Impact on net worth (%)
- Recovery timeline: Assume 12% annual returns; how long to recover?
- Behavioral risk: Will user panic-sell at bottom?

**Output Template**:
```
SCENARIO 2: 25% Market Correction

Current Equity Exposure: ₹[X]
Loss in Correction: ₹[Y] (X × 25%)
New Portfolio Value: ₹[Z]
Impact on Net Worth: [A]%
Recovery Timeline (at 12% annual returns): [B] months

Monthly SIP Opportunity: During correction, ₹[C]/month SIPs buy at lower prices, accelerating recovery.

Behavioral Check:
- Do you have 10+ year horizon? YES → Continue investing, ignore correction.
- Do you need this money in next 2 years? YES → You're taking wrong risk; reconsider allocation.

Risk Level: [🟡 Medium / 🟢 Low]
Why: [Depends on time horizon and allocation suitability]
```

**Example**:
```
SCENARIO 2: 25% Market Correction

Current Equity Exposure: ₹10L (MF + ELSS + PPF equity portion)
Loss in Correction: ₹2.5L
New Portfolio Value: ₹7.5L
Impact on Net Worth: -9% (₹2.5L ÷ ₹28L total assets)
Recovery Timeline: 18–24 months (at 12% annual returns, plus ongoing SIPs)

Monthly SIP Benefit: Continue ₹25k/month SIPs during correction. ₹25k buys more units at lower NAV. Net recovery impact: -15% instead of -25%.

Behavioral Check:
- Your time horizon: 35 years (excellent). You SHOULD continue investing.
- Your upcoming needs: Home purchase in 3–4 years (moderate concern). Allocate ₹3–4L to debt funds to avoid selling equities during correction.

Risk Level: 🟢 Low
Why: Correction is temporary. Your 35-year horizon absorbs it completely. In fact, correction is an opportunity to buy at discount (₹25k monthly SIPs).
```

---

## SCENARIO 3: Medical/Personal Emergency (₹5–10L Unexpected Expense)

**Trigger**: Major medical event, family crisis, or large unexpected expense requiring immediate ₹5–10L.

**Calculate**:
- Emergency fund: ₹[X]
- Shortfall: ₹5–10L - ₹X
- Liquidation options: Which assets can be sold quickly?
- Loan options: Personal loan rates? Home loan top-up?
- Behavioral impact: Would emergency derail long-term investing?

**Output Template**:
```
SCENARIO 3: Medical/Personal Emergency (₹5–10L)

Emergency Fund: ₹[X]
Shortfall: ₹[Y]
Can Fund Cover 50% of expense? [Yes/No]

Liquidation Options (in order of preference):
1. Emergency fund: ₹[X] (covers X% of ₹5–10L expense)
2. Liquid debt fund: ₹[Amount] (accessible 1–2 days)
3. Short-term FDs: ₹[Amount] (accessible 1–2 weeks, may have 1–2% early withdrawal penalty)
4. Equity mutual funds: ₹[Amount] (accessible 1–2 days, but triggers capital gains tax on profits)
5. Personal loan (backup): ₹10L @ 12–15% = ₹20k/month EMI for 5 years

Outcome:
- If emergency fund is ₹10L+: Can cover 100% without derailing investments ✅
- If emergency fund is ₹5–7L: Can cover 50–70%, need to sell one FD tranche or take small personal loan
- If emergency fund is <₹5L: Major disruption. Will need personal loan OR sell equities (suboptimal timing) OR family support

Risk Level: [🔴 Critical / 🟠 High / 🟡 Medium / 🟢 Low]
Why: [Based on emergency fund size relative to anticipated major life events]
```

**Example**:
```
SCENARIO 3: Medical Emergency (₹8L)

Emergency Fund: ₹1.5L (liquid debt fund)
Shortfall: ₹6.5L
Can Fund Cover 50%? Partially (19% of expense)

Liquidation Options:
1. Emergency fund: ₹1.5L (19% of expense)
2. Home down-payment FD: ₹2L (can tap, but delays home purchase timeline by 6 months)
3. Equity mutual funds: ₹3L (accessible same-day; may have ₹300–400k unrealized gains, triggering ₹60–80k tax)
4. PPF withdrawal (emergency): ₹2L available (partial withdrawal allowed, accessible in 1 week)
5. Personal loan (backup): ₹6.5L @ 12% = ₹16.3k/month × 60 months

Outcome: Can cover ₹8L without complete portfolio liquidation. Combined emergency fund ₹1.5L + partial FD ₹2L + partial equity ₹3L + PPF ₹1.5L = ₹8L. Tight, but manageable.

Risk Level: 🟡 Medium
Why: Emergency fund is borderline (1.5 months of fixed expenses). If you had a ₹2L emergency fund (target: 3 months), this scenario becomes 🟢 Low-risk.
```

---

## OVERALL RESILIENCE SCORE

After 3 scenarios, synthesize:

```
Overall Financial Resilience:
├─ Job Loss Resilience: [X months survival] → [Risk Level]
├─ Market Shock Resilience: [Recovery timeline] → [Risk Level]
├─ Emergency Resilience: [Can cover ₹5–10L?] → [Risk Level]
└─ Verdict: [Overall resilience high/medium/low. Key vulnerability: [X]. Key strength: [Y].]

Recommended Priority: [What's the single biggest thing to address? Build emergency fund? Stabilize income? Diversify assets?]
```

**Example**:
```
Overall Financial Resilience:
├─ Job Loss Resilience: 13.5 months (then side-gig extends to 20+ months) → 🟠 High Risk (single income dependency)
├─ Market Shock Resilience: 18–24 month recovery, but SIPs help → 🟢 Low Risk (long time horizon)
├─ Emergency Resilience: Can cover ₹8L partially (19% from fund, 80% from FD liquidation + loans) → 🟡 Medium Risk (tight)
└─ Verdict: Financially resilient in most scenarios, BUT highly vulnerable to job loss in year 1–2. Key vulnerability: single income + upcoming marriage/home commitments coinciding with job risk. Key strength: excellent SIPs discipline, growing net worth, ₹13-month emergency runway.

Recommended Priority: Build side-gig consulting income to ₹20k/month (removes job-loss vulnerability in year 2). Don't prioritize global investing yet.
```

---

## GUARDRAILS

1. **Be quantitative.** "This is bad" is useless. "13.5 months survival at ₹37k/month burn rate" is actionable.
2. **Sequence actions by realism.** "Month 1: aggressively job search" (realistic). "Month 3: sell car" (harder but doable). "Month 6: move in with parents" (last resort).
3. **Don't sugarcoat.** If emergency fund is ₹1L and monthly burn is ₹50k, say "3 months runway" not "you're okay."
4. **Include behavioral context.** Some users will panic-sell equities at 25% loss. Note this risk explicitly.
5. **Reference current macro context.** "Nifty PE at 22x (elevated), so correction risk higher. RBI rate at 6.5% (stable debt returns)."

---

## QUICK MENTAL MODEL

**Job Loss Risk**:
- <3 months emergency fund: 🔴 Critical (get side-gig immediately)
- 3–6 months: 🟠 High (start side-gig planning)
- 6–12 months: 🟡 Medium (side-gig is nice-to-have)
- 12+ months: 🟢 Low (you have time to breathe)

**Market Correction Risk**:
- Time horizon <3 years: 🔴 Critical (too much equity)
- 3–10 years: 🟠 High (rebalance to 60/40)
- 10–20 years: 🟡 Medium (70/30 OK, but avoid 80%+ equity)
- 20+ years: 🟢 Low (80%+ equity is fine, corrections are opportunities)

**Emergency Fund Risk**:
- <1 month: 🔴 Critical (immediate crisis)
- 1–3 months: 🟠 High (vulnerable)
- 3–6 months: 🟡 Medium (acceptable)
- 6–12 months: 🟢 Low (secure)

