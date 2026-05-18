# Personal Financial Advisor — Architecture Diagram

## System Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                    ROUTER SKILL                                   │
│         personal-finance-advisor (Intake & Dispatch)            │
└─────────────────┬───────────────────────────────────────────────┘
                  │
                  │ Routes to sub-skills based on user intent
                  │
        ┌─────────┼─────────┬─────────┬──────────┬──────────┬─────────┐
        │         │         │         │          │          │         │
        ▼         ▼         ▼         ▼          ▼          ▼         ▼
     ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐  ┌──────┐   ┌──────┐   ┌──────┐
     │  1   │ │  2   │ │  3   │ │  4   │  │  5   │   │  6   │   │  7   │
     │HEALTH│ │SPEND │ │INVEST│ │STRESS│  │ACTION│   │GLOBAL│   │INCOME│
     │ DX   │ │AUDIT │ │AUDIT │ │TEST  │  │PLAN  │   │INVEST│   │DIV   │
     └──────┘ └──────┘ └──────┘ └──────┘  └──────┘   └──────┘   └──────┘
        │         │         │         │          │          │         │
        └─────────┼─────────┴─────────┴──────────┴──────────┴─────────┘
                  │
                  │ Synthesis (Multi-Skill Workflows)
                  │
        ┌─────────▼──────────────────────────────────┐
        │                                             │
        │  Integrated Output (If User Asks "Everything")
        │  ├─ Health Score + Metrics                 │
        │  ├─ Top Spending Leaks                     │
        │  ├─ Investment Issues                      │
        │  ├─ Stress Test Results                    │
        │  ├─ 30/90/12-Month Action Plan            │
        │  ├─ Global Investing Readiness            │
        │  └─ Income Diversification Path            │
        │                                             │
        └─────────────────────────────────────────────┘
```

---

## Intent-to-Skill Routing Tree

```
User provides financial data / asks a question
        │
        ▼
    ┌─────────────────┐
    │ Assess Intent   │
    └────────┬────────┘
             │
    ┌────────┴────────┬────────┬────────┬──────────┬──────────┬──────────┐
    │                 │        │        │          │          │          │
    ▼                 ▼        ▼        ▼          ▼          ▼          ▼
"How am I    "Where's my  "Is my  "Can I    "Create a   "Should I   "How do I
 doing?"     money?"   portfolio   survive a  plan for    invest      earn
             "Identify   good?"   job       me?"         globally?"   more?"
             leaks"     "Evaluate  loss?"  "What       "Global      "Multiple
             │          allocation  │     should I   diversi-     income
             │                       │     do?"      fication"     streams"
             │                       │     │         │             │
             │                       │     │         │             │
             ▼                       ▼     ▼         ▼             ▼
        Behavioral-          Investment- Stress-   Global-     Income-
        Spending-            Audit-      Test-     Investing-  Diversi-
        Audit                India       Scenarios  Strategy    fication-
                                                               Strategy
             │                       │     │         │             │
             │                       │     │         │             │
             └───────────────────────┼─────┼─────────┼─────────────┘
                                     │     │         │
                      ┌──────────────┘     │         │
                      │                    │         │
                      ▼                    ▼         ▼
              Financial-Health-      Wealth-Action-
              Diagnosis              Planning
              (Often First)          (Often Synthesizes Others)
                      │                    │
                      └────────┬───────────┘
                               │
                               ▼
                    Integrated Output
                    (User's complete plan)
```

---

## Sub-Skill Details: Input → Output

```
┌─────────────────────────────────────────────────────────────┐
│ SUB-SKILL 1: financial-health-diagnosis                    │
├─────────────────────────────────────────────────────────────┤
│ INPUT:  Income, expenses, assets, liabilities              │
│ CALC:   5 metrics (savings %, investment %, EMI ratio, etc)│
│ OUTPUT: Health score (1–10) + metrics + reasoning           │
│ TIME:   1–2 screens, 2–3 minutes                           │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ SUB-SKILL 2: behavioral-spending-audit                     │
├─────────────────────────────────────────────────────────────┤
│ INPUT:  Expense breakdown, lifestyle patterns              │
│ AUDIT:  Identify 3 spending leaks                          │
│ OUTPUT: Leak 1: [Observation] → [Why] → [Action]          │
│         Leak 2: [same structure]                           │
│         Leak 3: [same structure]                           │
│ TIME:   1 screen, 2–3 minutes                              │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ SUB-SKILL 3: investment-audit-india                        │
├─────────────────────────────────────────────────────────────┤
│ INPUT:  Current portfolio, tax situation                   │
│ AUDIT:  Flag 4–5 investment issues                         │
│ OUTPUT: Issue 1: [Context] + [Recommendation]              │
│         Issue 2: [same]                                    │
│         ...up to 5 issues                                  │
│ TIME:   1–2 screens, 3–5 minutes                          │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ SUB-SKILL 4: stress-test-scenarios                         │
├─────────────────────────────────────────────────────────────┤
│ INPUT:  Income, expenses, assets, job stability            │
│ MODEL:  3 scenarios (job loss, market crash, emergency)    │
│ OUTPUT: Scenario 1: Impact → Timeline → Risk Level        │
│         Scenario 2: [same]                                 │
│         Scenario 3: [same]                                 │
│ TIME:   1–2 screens, 3–5 minutes                          │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ SUB-SKILL 5: wealth-action-planning                        │
├─────────────────────────────────────────────────────────────┤
│ INPUT:  All previous diagnostics (health, leaks, etc)      │
│ CREATE: 3 truths + 3 shifts + 1 bold move + timelines     │
│ OUTPUT: Brutal truths, strategic shifts, action roadmap    │
│         ├─ 30-day plan (week-by-week)                     │
│         ├─ 90-day plan (month-by-month)                   │
│         └─ 12-month projection (metrics table)             │
│ TIME:   2–3 screens, 5–7 minutes                          │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ SUB-SKILL 6: global-investing-strategy                     │
├─────────────────────────────────────────────────────────────┤
│ INPUT:  Current portfolio, income stability, job risk      │
│ CHECK:  5 prerequisites for global investing               │
│ OUTPUT: Prerequisites checklist (✅/⚠️/❌)                 │
│         Readiness verdict (YES/MAYBE/NO)                   │
│         Vehicle recommendations (if ready)                 │
│         Tax implications + timeline                        │
│ TIME:   1–2 screens, 3–5 minutes                          │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ SUB-SKILL 7: income-diversification-strategy               │
├─────────────────────────────────────────────────────────────┤
│ INPUT:  Current income, job risk, goals                    │
│ RANK:   3–4 income options by feasibility                  │
│ OUTPUT: Option 1: [Effort] [Timeline] [Year 1 Potential]  │
│         Option 2: [same]                                   │
│         Option 3: [same]                                   │
│         +24-month projection if sequenced correctly        │
│ TIME:   1–2 screens, 3–5 minutes                          │
└─────────────────────────────────────────────────────────────┘
```

---

## Multi-Skill Workflow Examples

### Workflow A: "How am I doing?" (Focused)

```
User asks: "How am I doing financially?"
        │
        ▼
Router: Detects intent = health check
        │
        ▼
Invoke: financial-health-diagnosis
        │
        ▼
Output: Health score (1–10) + 5 metrics + reasoning
        │
        ▼
User satisfied in 2–3 minutes
```

### Workflow B: "Create a plan" (Medium)

```
User asks: "Create a plan for me"
        │
        ▼
Router: Detects intent = action planning (+ baseline health)
        │
        ▼
Invoke: financial-health-diagnosis (baseline)
           ↓
        wealth-action-planning (main)
        │
        ▼
Output: Health score → Brutal truths → Shifts → Plan (30/90/12)
        │
        ▼
User satisfied with roadmap in 5–7 minutes
```

### Workflow C: "Full overhaul" (Comprehensive)

```
User asks: "Assess everything and create a complete plan"
        │
        ▼
Router: Detects intent = comprehensive diagnostic
        │
        ├─→ financial-health-diagnosis (1)
        ├─→ behavioral-spending-audit (2)
        ├─→ investment-audit-india (3)
        ├─→ stress-test-scenarios (4)
        ├─→ wealth-action-planning (5)
        ├─→ global-investing-strategy (6)
        └─→ income-diversification-strategy (7)
        │
        ▼
Synthesize: Integrated narrative tying all insights
        │
        ▼
Output: Executive summary + 7 diagnostic sections
        │
        ▼
User has complete financial plan in 10–15 minutes
```

---

## Data Flow: Health Diagnosis → Full Plan

```
User Financial Data
        │
        ├─→ financial-health-diagnosis
        │   └─ Output: Health score, metrics
        │
        ├─→ behavioral-spending-audit  
        │   └─ Output: Top 3 leaks
        │
        ├─→ investment-audit-india
        │   └─ Output: 4–5 issues
        │
        ├─→ stress-test-scenarios
        │   └─ Output: 3 scenarios, survival timelines
        │
        └─→ wealth-action-planning
            └─ Input: Outputs from 1-4
            └─ Output: Integrated plan + timelines

Final Output: Comprehensive financial plan
            ├─ Health diagnosis
            ├─ Behavioral insights
            ├─ Investment recommendations
            ├─ Resilience assessment
            └─ Action roadmap (30/90/12 months)
```

---

## Single Skill: Anatomy of financial-health-diagnosis

```
Input:
  - Monthly gross income: ₹X
  - Monthly after-tax income: ₹Y
  - Monthly expenses: ₹Z
  - Current assets/liabilities breakdown
  - Time horizon
        │
        ▼
Calculations:
  - Savings Rate = (Y - Z) / Y × 100
  - Investment Rate = (Invested / Savings) × 100
  - EMI-to-Income = (Monthly EMIs / X) × 100
  - Liquidity Buffer = Emergency Fund / Monthly Fixed Expenses
  - Asset Allocation = [Equity%, Debt%, Gold%, Cash%]
        │
        ▼
Mapping to Health Score:
  - 9–10: Optimized (Savings >40%, Investment >80%, EMI <30%, etc.)
  - 7–8: Healthy (Savings 30–40%, Investments 70–80%, EMI 30–40%, etc.)
  - 5–6: Concerning (Savings 15–25%, Investments 40–70%, EMI 40–50%, etc.)
  - 3–4: Dangerous (Savings <15%, Investments <40%, EMI >50%, etc.)
  - 1–2: Critical (Negative savings, zero investments, EMI >70%, etc.)
        │
        ▼
Output:
  ┌────────────────────────────────────┐
  │ HEALTH SCORE: 5/10                 │
  │ STATUS: Concerning                 │
  │                                    │
  │ Key Metrics:                       │
  │ ├─ Savings Rate: 28% ✅ Good      │
  │ ├─ Investment Rate: 85% ✅ Good   │
  │ ├─ EMI-to-Income: 56% 🔴 Warning │
  │ ├─ Liquidity: 5.2 months ✅ OK   │
  │ └─ Allocation: Good, diversified  │
  │                                    │
  │ Reasoning: [1 paragraph]           │
  │ Your savings rate is excellent, but│
  │ your EMI-to-income is elevated...  │
  └────────────────────────────────────┘
```

---

## Time & Complexity Matrix

```
                 Effort to Invoke
                    LOW  MED  HIGH
        ┌────────────┬───┬───┬───┐
        │ Health Dx  │ ▓ │   │   │
        │ Spend Audit│ ▓ │   │   │
TIME    │ Invest Audit  │ ▓ │   │   │
TO      │ Stress Test   │ ▓ │   │   │
RUN     │ Action Plan   │   │ ▓ │   │
        │ Global Invest │   │ ▓ │   │
        │ Income Div    │   │ ▓ │   │
        │ ALL 7 (Full)  │   │   │ ▓ │
        └────────────┴───┴───┴───┘

▓ = Time: 2–7 minutes | Complexity: Easy

Typical use:
  - Single skill (quick Q): 2–5 minutes
  - Multi-skill (comprehensive): 10–15 minutes
```

---

## Success Criteria: Sub-Skill Output Quality

```
✅ financial-health-diagnosis
   - Health score is justified by metrics
   - All calculations shown (no guessing)
   - Reasoning connects score to user's actual situation

✅ behavioral-spending-audit
   - 3 leaks are specific (₹X amounts)
   - Each leak has "why it matters" (impact quantified)
   - Each leak has clear action step

✅ investment-audit-india
   - 4–5 issues flagged (not vague)
   - Each issue has context + recommendation
   - Tax context is Indian-specific

✅ stress-test-scenarios
   - 3 scenarios are distinct (not overlapping)
   - Survival timelines are quantified
   - Actions are sequenced (month 1, 2, etc.)

✅ wealth-action-planning
   - 3 brutal truths are true (not motivational)
   - 3 shifts are achievable (not fantasy)
   - Bold move has 3–5 year impact
   - Timelines have specific deliverables

✅ global-investing-strategy
   - Prerequisites are clear (✅/⚠️/❌)
   - Readiness verdict is explicit (YES/MAYBE/NO)
   - Timelines are specific (not vague)

✅ income-diversification-strategy
   - Options are ranked by feasibility
   - Timeline to first $ is realistic
   - Effort scores (1–10) are honest
   - 24-month projection is data-driven
```

---

## File Structure at a Glance

```
personal-finance-advisor-skill-v2/
│
├─ README.md
│  └─ Quick start, principles, evaluation criteria
│
├─ SKILL.md (Router)
│  └─ Intake, intent routing, progressive disclosure
│
├─ INTEGRATION_GUIDE.md
│  └─ How sub-skills work together, multi-skill workflows
│
├─ TRANSFORMATION_SUMMARY.md
│  └─ v1 (monolithic) vs v2 (modular) comparison
│
├─ Sub-Skill 1: financial-health-diagnosis.md
├─ Sub-Skill 2: behavioral-spending-audit.md
├─ Sub-Skill 3: investment-audit-india.md
├─ Sub-Skill 4: stress-test-scenarios.md
├─ Sub-Skill 5: wealth-action-planning.md
├─ Sub-Skill 6: global-investing-strategy.md
├─ Sub-Skill 7: income-diversification-strategy.md
│
└─ test_cases.json
   └─ 4 test scenarios with expected outputs

Total: 12 files, ~4,000 lines of well-organized content
```

---

## Next: Ready to Test 🎯

Each sub-skill is ready to be tested independently with Test Cases 1–4.
Then test multi-skill workflows.
Then refine based on feedback.

Then deploy!

