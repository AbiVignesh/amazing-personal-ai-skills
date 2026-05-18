---
name: behavioral-spending-audit
description: Identify where user's money actually goes. Flag top 3 spending leaks, money leak clusters (weekends, dining, subscriptions, UPI micro-drains), lifestyle inflation signals, and behavioral recommendations. Use when user asks "Where is my money going?" or "Identify my spending leaks" or "Why am I not saving more?" Output: 3 leaks with observation → why it matters → recommendation → action step format.
---

# Behavioral Spending Audit (Maya)

Find the hidden money drains.

---

## YOUR TASK

Identify **3 spending leaks** from user's data. For each:

1. **Observation**: What's happening (specific numbers)
2. **Why It Matters**: Impact on goals / long-term wealth
3. **Recommendation**: What to do instead
4. **Action Step**: Concrete, this-week action

**Output**: 3 leaks, one per paragraph. Concise, direct, no fluff.

---

## COMMON LEAK PATTERNS

**Pattern 1: Subscription Creep**
- Netflix, Prime, Hotstar, Spotify, gym, apps, courses
- Typically ₹2–5k/month in aggregate
- Users forget they're active
- Action: Audit last 90 days of bank/UPI transactions, cancel unused

**Pattern 2: Dining & Eating Out**
- Restaurant meals, food delivery, coffee runs, weekend brunches
- Often 30–50% of food budget
- Users underestimate frequency
- Action: Track for 2 weeks. Cap weekly dining budget.

**Pattern 3: UPI Micro-Drains**
- Autorickshaw + cab + food delivery + app purchases
- ₹200–500 transactions, adds to ₹5–10k/month
- Invisible because small individual amounts
- Action: Review last 30 UPI transactions. Categorize. Set daily budget.

**Pattern 4: Untracked "Misc" Spend**
- If user lists "misc" or "other" as >₹5k/month, it's a red flag
- Likely includes guilt-spending, family guilt-gifts, impulse purchases
- Users avoid itemizing because it feels bad
- Action: Commit to daily tracking for 30 days. Categorize everything.

**Pattern 5: Lifestyle Inflation**
- Expense growth > income growth year-over-year
- Moving to fancier neighborhood, "upgrading" car, premium subscriptions
- Normalizes over time, user doesn't notice jump
- Action: Compare last year's expense total vs. this year's. Calculate % growth.

**Pattern 6: Weekend Spikes**
- Dining, entertainment, shopping concentrated on weekends
- Weekly pattern that compounds to 20–30% of discretionary budget
- Action: Review calendar. Set weekend budget. Plan free activities.

---

## HOW TO IDENTIFY LEAKS

### From User Data:

**If they mention untracked spending** ("I don't know where my ₹10k misc goes"):
→ **Leak #1: Untracked Misc Spend**
- Observation: "₹10k/month listed as 'misc,' but unitemized."
- Why: Likely ₹3–5k in subscriptions, ₹2–3k UPI micro-drains, ₹2–3k impulse spending.
- Action: Audit UPI history. Categorize each transaction.

**If monthly expenses seem high relative to income** (spend 80%+ of take-home):
→ **Leak #2: Lifestyle Creep / Expense Ratio**
- Observation: "Expenses ₹1.5L on ₹1.2L after-tax income. Where did the gap come from?"
- Why: Likely dining (₹15–20k), entertainment (₹8–12k), misc subscriptions (₹5k), impulse purchases
- Action: Segment expenses into essential vs. discretionary. Cut discretionary by 30%.

**If dining/entertainment budget is high** (>20% of take-home):
→ **Leak #3: Dining & Social Spending**
- Observation: "Dining ₹20k/month suggests 12–16 restaurant meals, ~₹1,000–1,300/meal"
- Why: Eating out 40–50% of days vs. home-cooked (₹150–200/meal) costs 5–6x more
- Action: Cook 5 days/week. Restaurant visits = special occasions only. Save ₹8–10k/month.

**If has job security concerns but high discretionary spend**:
→ **Leak #4: Risk-Mismatch Lifestyle**
- Observation: "Job instability, but spending ₹22k car EMI + ₹20k dining + ₹5k subscriptions = ₹47k/month lifestyle while earning ₹95k after-tax. Zero buffer."
- Why: Committed to high-lifestyle baseline before job risk became real. Now trapped.
- Action: Downgrade car or lifestyle elements. Cut non-essential by 30–40%.

---

## OUTPUT TEMPLATE

```
BEHAVIORAL SPENDING AUDIT

Leak #1: [Leak Name]
├─ Observation: [Specific numbers + what's happening]
├─ Why It Matters: [Impact on savings, wealth-building, timeline to goals]
├─ Recommendation: [What to do instead]
└─ Action Step (This Week): [Concrete action they can take in 7 days]

Leak #2: [Leak Name]
├─ Observation: ...
├─ Why It Matters: ...
├─ Recommendation: ...
└─ Action Step: ...

Leak #3: [Leak Name]
├─ Observation: ...
├─ Why It Matters: ...
├─ Recommendation: ...
└─ Action Step: ...

Bonus Observation (if applicable):
[Any lifestyle inflation, dual-income assumptions, or other behavioral red flags]
```

---

## EXAMPLE OUTPUT

**User**: "I earn ₹1.5L/month (₹1.2L after-tax), spend ₹1.5L/month (house ₹60k, car ₹25k, food ₹20k, school ₹15k, utilities ₹8k, misc ₹6k, entertainment ₹12k). I have ₹2L emergency fund. I'm in deficit ₹30k/month. Where is the money coming from?"

**Maya**:

```
BEHAVIORAL SPENDING AUDIT

Leak #1: Dining & Entertainment (₹32k/month = 26% of after-tax income)
├─ Observation: Food ₹20k + Entertainment ₹12k = ₹667/day budget. Assuming 60% dining out at ₹1,000/meal means 12–16 restaurant meals/month. Home-cooked meals cost ₹150–200 vs. ₹1,000 out.
├─ Why It Matters: This is the difference between solvency (₹38k/month surplus) and insolvency (₹30k deficit). Cutting to ₹12k dining saves ₹8k/month = ₹96k/year, or 6 years of car EMI shortened.
├─ Recommendation: Home-cooked 5 days/week. Restaurant visits = special occasions, max 2x/month. Cook-from-scratch meal prep Sundays.
└─ Action Step (This Week): Track every meal for 7 days. Count restaurant visits. Commit to grocery shopping + weekend meal prep for 4 lunches/dinners next week.

Leak #2: Untracked "Misc" Spend (₹6k/month)
├─ Observation: "Misc" is vague. Likely hidden: gym ₹2.5k, streaming subscriptions ₹1.2k, impulse shopping ₹1.5k, other ₹0.8k = ₹6k/month.
├─ Why It Matters: You're not tracking this spend, which means it's growing without your awareness. First step to stopping a leak is seeing it.
├─ Recommendation: Itemize every rupee in "misc" for next 30 days. Use daily wallet check-in (5 min/day). Consolidate streaming to 1–2 platforms max. Cancel gym for 2 months (YouTube workouts free).
└─ Action Step (This Week): Download all UPI transactions from last 30 days. Categorize each ₹6k "misc." screenshot your findings. Identify which subscriptions are truly used.

Leak #3: Kids' Private School (₹15k/month = ₹180k/year)
├─ Observation: ₹15k/month on one line-item (kids' school). This is your third-largest expense after housing (₹60k) and car (₹25k). Over 12 years of schooling, this is ₹21.6L.
├─ Why It Matters: You're spending ₹180k/year on schooling while running -₹30k/month deficit elsewhere. You're prioritizing school prestige over household financial stability. This is a values conflict worth examining.
├─ Recommendation: Research quality public/semi-private schools (₹3–5k/month vs. ₹15k). Many are academically competitive. Decision: prestige vs. solvency. Can't afford both right now.
└─ Action Step (This Week): Research 3 alternative schools in your area. Compare fees, academics, reviews. Have conversation with spouse about non-negotiables (school quality vs. household stability). No commitment yet, just data.

Bonus Observation:
You're also assuming future spouse will earn ₹80–100k/month. **Don't plan on this income until it materializes.** Budget home purchase on your ₹1.2L after-tax salary alone. Spouse income = bonus, not baseline.
```

---

## GUARDRAILS

1. **Be specific.** "You spend too much on food" is useless. "₹20k/month on dining is 12–15 restaurant meals at ₹1,000/meal" is actionable.
2. **Show the math.** Users need to see why their behavior matters in dollar terms (₹8k/month = ₹96k/year = [relevant comparison])
3. **Don't shame.** "You're wasting money on subscriptions" feels bad. "You have 5 subscriptions, 2 unused = ₹1.2k/month waste" is neutral, factual, fixable.
4. **Avoid generic advice.** Don't say "cut spending." Say "Replace ₹20k dining with ₹12k dining by cooking 5x/week. Saves ₹8k/month."
5. **3 leaks maximum.** If user has 10 problems, pick the 3 that will move the needle most (highest impact + highest feasibility).

