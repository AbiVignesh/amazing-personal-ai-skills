---
name: personal-finance-advisor-integration
description: Guide to the modular Personal Financial Advisor skill architecture. Shows how the 7 sub-skills integrate, which ones to invoke based on user intent, and examples of multi-skill workflows.
---

# Personal Financial Advisor — Integration Guide

## Architecture Overview

The Personal Financial Advisor skill is **modular**: 1 router skill + 7 focused sub-skills.

**Router Skill**: `personal-finance-advisor`
- Lightweight intake & routing logic
- Assesses user intent
- Dispatches to appropriate sub-skill(s)
- Prevents information overload

**7 Sub-Skills** (each focused, concise, specialized):
1. `financial-health-diagnosis` — Calculate health score + metrics (1 screen)
2. `behavioral-spending-audit` — Identify spending leaks (3 key findings)
3. `investment-audit-india` — Evaluate allocation, tax efficiency (4–5 issues)
4. `stress-test-scenarios` — Model resilience under adversity (3 scenarios)
5. `wealth-action-planning` — Create 30/90/12-month roadmap (truths + shifts + plan)
6. `global-investing-strategy` — Assess readiness for global investing (prerequisites + verdict)
7. `income-diversification-strategy` — Identify side-income paths + ranking (3–4 options)

---

## Intent-to-Skill Mapping

| User Intent | Primary Sub-Skill | Secondary (If Deep-Dive) | Output Typical |
|---|---|---|---|
| "How am I doing financially?" | financial-health-diagnosis | — | Health score + 5 metrics + reasoning |
| "Where is my money going?" | behavioral-spending-audit | — | 3 spending leaks with actions |
| "Is my investment strategy good?" | investment-audit-india | — | 4–5 issues flagged + recommendations |
| "Can I survive a job loss?" | stress-test-scenarios | financial-health-diagnosis | 3 scenarios with survival timelines |
| "Create a plan for me" | wealth-action-planning | All others (if comprehensive) | 3 truths + 3 shifts + bold move + timelines |
| "Should I invest globally?" | global-investing-strategy | financial-health-diagnosis | Prerequisites check + readiness verdict + action plan |
| "How do I earn more?" | income-diversification-strategy | financial-health-diagnosis | 3–4 income options ranked + 24-month projection |

---

## Single-Skill Workflows (Focused Intent)

### Workflow 1: User Asks "How am I doing financially?"

```
User Input: "I earn ₹1.2L/month, spend ₹45k, save ₹75k. I have ₹25L invested. 
            How's my financial health?"

Router Action: 
├─ Intent identified: Health assessment
└─ Invoke: financial-health-diagnosis

Output:
├─ Health Score: 7/10 (Healthy, minor tweaks)
├─ Key Metrics: [Table with savings rate, investment rate, EMI ratio, etc.]
└─ Reasoning: 1 paragraph explaining score

User satisfaction: High (got exactly what they asked for in <2 minutes)
```

### Workflow 2: User Asks "Where is my money going?"

```
User Input: "I earn ₹1.5L/month, spend ₹1.5L. I have a ₹20k dining budget but 
            no clue where the rest goes. Help."

Router Action:
├─ Intent identified: Behavioral audit
└─ Invoke: behavioral-spending-audit

Output:
├─ Leak #1: Untracked "Misc" (₹6k/month likely hides ₹3–5k in subscriptions)
├─ Leak #2: Dining & Entertainment (₹32k/month = 26% of after-tax income)
├─ Leak #3: Impulsive Spending (₹10k/month in black holes)
└─ Action Steps: Audit UPI, cancel subscriptions, meal-prep Sundays

User satisfaction: High (specific, actionable)
```

### Workflow 3: User Asks "Can I survive a job loss?"

```
User Input: "My job feels unstable. I have ₹5L emergency fund, ₹22k car EMI, 
            ₹45k monthly expenses. How long can I last?"

Router Action:
├─ Intent identified: Stress testing (job loss scenario)
├─ Invoke: stress-test-scenarios
└─ Optional secondary: financial-health-diagnosis (for context on baseline)

Output:
├─ Scenario 1: Job Loss (30% income drop → 0)
│  ├─ Monthly Burn: ₹22k fixed + ₹23k variable = ₹45k/month
│  ├─ Emergency Fund: ₹5L ÷ ₹45k = 11.1 months survival
│  └─ Risk Level: 🟡 Medium
├─ Scenario 2: Market Correction (25% loss)
│  ├─ Portfolio drop: ₹25L × 25% = ₹6.25L loss
│  ├─ Recovery timeline: 18–24 months
│  └─ Risk Level: 🟢 Low (you have 30+ year horizon)
└─ Scenario 3: Emergency (₹5–10L medical)
   ├─ Can partially cover from emergency fund
   └─ Risk Level: 🟡 Medium (shortfall = ₹2–5L)

User satisfaction: High (clarity on vulnerabilities + action thresholds)
```

---

## Multi-Skill Workflows (Comprehensive Diagnostic)

### Workflow A: Complete Financial Overhaul

```
User Input: "I'm 35, earning ₹1.5L/month, spending ₹1.5L (in deficit), 
            have ₹13L invested + ₹20L ESOP about to vest. My job is shaky. 
            I want a complete financial plan."

Router Action: 
├─ Intent identified: Comprehensive diagnostic
├─ Invoke (in sequence):
│  1. financial-health-diagnosis (baseline)
│  2. behavioral-spending-audit (identify leaks)
│  3. investment-audit-india (ESOP + allocation issues)
│  4. stress-test-scenarios (job loss + ESOP tax bomb)
│  5. wealth-action-planning (create roadmap)
│  6. income-diversification-strategy (stabilize income)
└─ Optional: global-investing-strategy (if asked after other issues resolved)

Integrated Output (5–10 minute read):
├─ Health Score: 2/10 (Critical. Insolvent.)
├─ Top 3 Spending Leaks + Actions: [From behavioral audit]
├─ Investment Issues: ESOP concentration + tax trap + poor allocation
├─ Stress Test: Job loss = 0 months survival. ESOP tax = bankruptcy in 24 months.
├─ Action Plan: 
│  ├─ Immediate (Month 1): Lifestyle reset, ESOP tax planning, start consulting
│  ├─ Months 2–6: Scale consulting to ₹20k/month, build emergency fund
│  ├─ Months 6–12: New job search, ESOP diversification, stabilize income
│  └─ Year 2: Recover from deficit, rebuild net worth
├─ 3 Brutal Truths: [From wealth planning]
├─ 3 Strategic Shifts: [From wealth planning]
└─ 12-Month Projection: Deficit eliminated, consulting ₹20k, total surplus +₹24k/month

User satisfaction: Very high (complete clarity, actionable steps, timeline)
```

### Workflow B: "I Want to Build Multiple Income Streams"

```
User Input: "I have ₹95k/month, ₹53k surplus. My job is at risk. I want to build 
            multiple income sources. Where should I start? Also, should I invest 
            globally?"

Router Action:
├─ Intent 1 identified: Income diversification (primary)
├─ Intent 2 identified: Global investing (secondary, but premature)
├─ Invoke (in sequence):
│  1. financial-health-diagnosis (baseline: Good fundamentals, but job risk)
│  2. income-diversification-strategy (which side-gigs, in what sequence)
│  3. stress-test-scenarios (job loss scenario with side-gig income)
│  4. global-investing-strategy (readiness check: NOT YET)
└─ Optional: wealth-action-planning (if they want 12-month roadmap)

Integrated Output (5–7 minute read):
├─ Current Health: 5/10 (excellent savings, but single-income fragile)
├─ Income Diversification Recommendation:
│  ├─ Option 1 (PRIMARY): Consulting ₹20k/month (month 2–6)
│  ├─ Option 2 (PARALLEL): Job upgrade / skill certification (month 1–6)
│  ├─ Option 3 (SECONDARY): Content creation (month 7+ only)
│  └─ Option 4 (SPECULATIVE): SaaS product (year 2+ only)
├─ Sequencing: Consulting (month 1) + Job upgrade (month 1–6 parallel) = 24-month plan
├─ Stress Test: Job loss with ₹20k consulting by month 6 = 18–20 months survival (vs. 13 months now)
├─ Global Investing Verdict: NO, NOT YET. Blockers: (1) Single income dependency, (2) No side-gig income stabilized yet, (3) Domestic not maxed
│  └─ Timeline: Revisit in 18 months (after consulting ₹20k/month + emergency fund rebuilt)
└─ Action Plan: Month 1 start consulting. Month 6 reach ₹20k/month. Month 12 new job + consulting = ₹145k/month total.

User satisfaction: Very high (clear priorities, sequencing, and explains WHY global investing is premature)
```

### Workflow C: "Give Me Everything — Full Financial Plan"

```
User Input: "I want a full financial plan. Assess my health, spending, 
            investments, stress test, create a roadmap, and tell me if I 
            can invest globally and earn more on the side."

Router Action:
├─ Full diagnostic mode
├─ Invoke ALL 7 SUB-SKILLS in sequence:
│  1. financial-health-diagnosis
│  2. behavioral-spending-audit
│  3. investment-audit-india
│  4. stress-test-scenarios
│  5. wealth-action-planning
│  6. global-investing-strategy
│  7. income-diversification-strategy
└─ Synthesis: Create integrated narrative

Output (10–15 minute comprehensive read):
├─ Executive Summary (1 paragraph)
├─ Financial Health Snapshot (metrics table + score)
├─ Behavioral Issues (3 spending leaks)
├─ Investment Assessment (4–5 issues + recommendations)
├─ Resilience Check (3 stress scenarios + risk levels)
├─ Action Roadmap (30/90/12-month timelines + milestones)
├─ Global Investing: When & How
├─ Income Diversification: Sequence & 24-month projection
└─ Questions for User (for deeper dive on specific sub-skill if needed)

User satisfaction: Highest (comprehensive, structured, no gaps)
```

---

## Progressive Disclosure Pattern

**First interaction**: User gets **ONE sub-skill output** (light, focused).
**Follow-up interest**: User can dive deeper on specific issue (invoke that sub-skill alone, deep mode).
**Full overhaul request**: Invoke all sub-skills, synthesize into narrative.

**Example interaction**:

```
Message 1 (User): "How's my financial health?"
Response 1 (Maya): financial-health-diagnosis → Health score 5/10 + 5 metrics + reasoning (1 screen)

Message 2 (User): "What should I do about it?"
Response 2 (Maya): wealth-action-planning → 3 truths + 3 shifts + bold move + timeline (2–3 screens)

Message 3 (User): "How much can I allocate to global investing?"
Response 3 (Maya): global-investing-strategy → Readiness verdict + timeline + vehicles (1–2 screens)

Message 4 (User): "Deep dive on investing strategy. I want to know all the issues."
Response 4 (Maya): investment-audit-india (deep mode) → 6–8 issues + detailed recommendations (2–3 screens)

Total: Progressive information, user controls depth
```

---

## When to Invoke Each Sub-Skill

### Single-Skill Triggers (Focused Intent)

| Sub-Skill | Trigger Keywords | User Profile | Output Length |
|---|---|---|---|
| `financial-health-diagnosis` | "How am I doing?" "Rate my finances" "Health check" | Baseline assessment seeker | 1 screen |
| `behavioral-spending-audit` | "Where's my money?" "Spending leaks?" "Why not saving?" | Blind-spot finder | 1–1.5 screens |
| `investment-audit-india` | "Is my portfolio good?" "Fund recommendation?" "Tax optimization?" | Allocation optimizer | 1–2 screens |
| `stress-test-scenarios` | "Can I survive job loss?" "Emergency fund adequate?" "Market crash impact?" | Risk assessor | 1–1.5 screens |
| `wealth-action-planning` | "Create a plan" "What should I do?" "30/90/12-month roadmap?" | Action seeker | 2–3 screens |
| `global-investing-strategy` | "Should I invest globally?" "US stocks?" "Crypto?" "International diversification?" | Global investor | 1–2 screens |
| `income-diversification-strategy` | "How do I earn more?" "Side gigs?" "Career acceleration?" "Consulting?" | Income grower | 1–2 screens |

### Multi-Skill Triggers (Comprehensive Intent)

| Trigger | Invoke | Sequence |
|---|---|---|
| "Complete financial overhaul" | All 7 | 1→2→3→4→5→6→7 (then synthesize) |
| "I want a plan + income strategy" | 1, 5, 7 | Diagnose → Plan → Income |
| "Can I afford X (home/car/wedding)?" | 1, 4, 5, 6 | Health → Stress test → Plan → Global readiness |
| "Investment + global + side-gig" | 3, 6, 7 | Investment audit → Global verdict → Income options |

---

## Quality Gates & Handoffs

**Sub-skill output quality gates**:

✅ `financial-health-diagnosis`: Health score is justified. Metrics are calculated, not guessed.
✅ `behavioral-spending-audit`: 3 leaks are specific ($), not generic ("spend less on food").
✅ `investment-audit-india`: Issues are flagged with context + recommendation, not just "diversify."
✅ `stress-test-scenarios`: Survival timeline is quantified. Actions are sequenced (month 1, 2, 3...).
✅ `wealth-action-planning`: Truths are brutal but true. Shifts are achievable. Bold move has 3–5yr impact.
✅ `global-investing-strategy`: Readiness verdict is clear (YES/MAYBE/NO). Timelines are explicit.
✅ `income-diversification-strategy`: Options are ranked by effort + feasibility. 24-month projection is realistic.

**Handoff to deeper dive**:

If user wants more detail on a specific sub-skill output, re-invoke that skill in "deep mode" (spend more tokens, go into 2–3 screens of detail).

Example:
```
User: "Explain the investment issues in detail. What exactly should I change?"
Maya: [Re-invoke investment-audit-india in deep mode]
Output: 6–8 issues, each with 2–3 paragraph context + recommendation
```

---

## Summary: Why Modular?

**Before (monolithic SKILL.md)**:
- 1 giant skill, 5,000+ words
- User asks simple question, gets wall of text
- Overwhelming for first-time users
- Hard to maintain (changing one section affects whole skill)

**After (7 sub-skills)**:
- Router skill + 7 focused sub-skills
- User gets exactly what they asked for
- Progressive disclosure: shallow first, deep on demand
- Easy to improve 1 sub-skill without breaking others
- Faster loading (smaller context windows)
- Better UX (information scarcity vs. overload)

**Trade-off**: Slightly more coordination needed between skills. But worth it.

---

## Next Steps

1. **Test each sub-skill individually** on the 4 test cases
2. **Test multi-skill workflows** (health diagnosis + action planning)
3. **Iterate based on feedback** (adjust templates, examples)
4. **Deploy**: Install router + 7 sub-skills as a connected set

---

