# Car Buying Expert Skill — Complete Guide

**Version**: 2.0 | **Status**: Production-Ready | **Last Updated**: 2026-05-23

---

## What This Skill Does

This is a **brutally practical automotive advisor** that helps users make financially sound car-buying decisions.

It's designed to:
- ✅ Prevent financially irrational purchases
- ✅ Recommend the right car for **your actual life**, not marketing hype
- ✅ Calculate real total cost of ownership (not just EMI)
- ✅ Catch red flags before they become debt
- ✅ Help choose the right variant (often NOT the top-spec)
- ✅ Provide current, verified pricing and specs (with web research)

It's **NOT** for:
- ❌ Performance benchmarking ("which car is fastest")
- ❌ Enthusiast spec comparisons
- ❌ Lifestyle bragging ("which car looks better")

---

## Quick Start

### If You're Just Exploring
```
User: "I'm thinking about buying an SUV, but not sure"
Skill: Asks 5-7 clarifying questions about lifestyle, budget, constraints
Output: Budget range, lifestyle fit, 3-4 shortlisted cars with quick explanation
Time: 5 minutes
```

### If You've Decided on a Car But Unsure About Variant
```
User: "Should I get the Creta EX or SX?"
Skill: Compares variants, explains cost-per-feature, recommends "sweet spot"
Output: Recommended variant + cost-benefit analysis + features to skip
Time: 5-10 minutes
```

### If You're Serious & Want Full Analysis
```
User: "I want a complete analysis for [Car]. Can I afford it?"
Skill: Runs affordability assessment, ownership cost projection, red flag detection
Output: 30-50 minute deep dive with financial breakdown + safety check + recommendation
Time: 15-25 minutes
```

---

## Skill Architecture

```
SKILL.md (You are here)
├── Core workflows (discovery → research → analysis → recommendation)
├── Decision trees (navigation logic)
├── Output templates (how recommendations are formatted)
└── Anti-patterns (what NOT to recommend)

/references/
├── car-buying-mindset.md (Psychological framework)
├── india-car-market-2026.md (Market context)
├── affordability-rules.md (EMI safety ratios)
└── red-flags.md (Warning signs)

/frameworks/
├── affordability-assessment.md (Financial health check + calculations)
├── variant-value-matrix.md (Feature cost analysis)
├── ownership-cost-calculator.md (TCO model)
└── ev-readiness-checklist.md (EV viability assessment)

/workflows/
├── initial-discovery.md (First conversation)
├── web-research-protocol.md (How to get current data)
├── variant-selection.md (Choosing trim)
└── red-flag-detection.md (Safety checks)

/examples/
├── scenario-1.md (Budget SUV under ₹20L)
├── scenario-2.md (Creta variant confusion)
├── scenario-3.md (Can I afford BMW?)
├── scenario-4.md (EV vs Hybrid)
└── scenario-5.md (Wait for facelift?)

/checklists/
├── pre-buying-checklist.md (Before committing)
├── variant-evaluation.md (Feature comparison)
├── test-drive-checklist.md (What to check)
└── post-purchase-checklist.md (After buying)
```

---

## How Skill Selects This Tool

**Trigger Patterns** (When to invoke this skill):

✅ **INVOKE** when:
- "Should I buy [car name]?"
- "Which [type] SUV/sedan should I get?"
- "Can I afford a [car name]?"
- "Is [variant] worth the extra cost?"
- "EMI analysis for [car]"
- "EV vs hybrid vs petrol?"
- "Best car for [specific use case]"
- "Used vs new car decision"
- "Should I wait for facelift?"

❌ **DON'T INVOKE** when:
- "What's the 0-100 time?"
- "Fastest cars list"
- "How does a CVT work?"
- "Should I modify my car?"
- "Which car looks coolest?"

---

## Core Concepts

### Concept 1: Total Cost of Ownership ≠ EMI Alone

Most people only count EMI. Smart people count everything:

```
EMI: ₹40k/month
+ Fuel: ₹3.5k/month (realistic, not claimed)
+ Insurance: ₹1k/month
+ Maintenance: ₹1.5k/month
= REAL COST: ₹46k/month

5-year TCO = ₹46k × 60 months = ₹27.6L
Minus resale value = Net cost ₹16L
```

### Concept 2: EMI-to-Salary Ratio is Your Safety Line

```
SAFE: EMI ≤ 15% of take-home salary
STRETCHING: EMI 15-20%
DANGEROUS: EMI > 20%

Example:
- Salary: ₹50k/month
- Safe EMI: ₹7,500
- Stretching EMI: ₹10,000
- Dangerous EMI: >₹10,000
```

### Concept 3: Mid-Spec is Usually Best Value

Manufacturers add profit at each tier:
```
Base: ₹15L (profit ₹1.2L, margin 8%)
Mid: ₹18L (profit ₹2.4L, margin 13%) ← BEST VALUE
Top: ₹21L (profit ₹3.8L, margin 18%) ← Highest margin, heaviest marketing

Most buyers skip Mid, jump to Top (emotional).
Smart buyers pick Mid (mathematical).
```

### Concept 4: Real-World Mileage ≠ Claimed

```
Claimed: 20 km/l
Real-world: 14-16 km/l (urban driving)
Use this for cost calculations: 0.70 × claimed
```

---

## Key Workflows

### Workflow 1: Initial Discovery (5 mins)
1. Clarify intent (exploring vs decided)
2. Ask 5-7 lifestyle questions
3. Qualify budget
4. Identify constraints
5. Return: Budget range + shortlist + risk flags

### Workflow 2: Market Research (10-15 mins)
1. Identify 3-4 candidate cars
2. Web search for current prices, specs, waiting period
3. Verify across 3+ sources
4. Calculate ownership costs
5. Return: Verified data + confidence scores

### Workflow 3: Variant Selection (5-10 mins)
1. List all variants for chosen car
2. Feature-by-feature breakdown
3. Cost-per-feature analysis
4. Identify "sweet spot" variant
5. Return: Recommended variant + cost-benefit

### Workflow 4: Affordability Assessment (10-15 mins)
1. Calculate safe EMI limit
2. Project ownership costs
3. Check affordability ratios
4. Run red flag detection
5. Return: PROCEED / CAUTION / STOP verdict

### Workflow 5: Recommendation Synthesis (5-10 mins)
1. Synthesize all findings
2. Explain pros & cons
3. Highlight tradeoffs
4. Flag risks
5. Return: Final recommendation + action items

---

## Red Flags This Skill Catches

**CRITICAL** (Stop the purchase):
- EMI-to-salary > 20%
- No emergency fund
- Buying under pressure/emotional reasons
- Ignoring major reliability concerns

**HIGH** (Caution):
- EMI-to-salary 15-20%
- Weak service network
- Poor resale value
- Facelift/new generation imminent

**MEDIUM** (Be aware):
- Feature sacrifices for budget
- Real fuel mileage >> claimed
- Variant overpriced for features
- Insurance costs high

---

## How to Use This Skill (User Instructions)

### For Quick Advice (5-10 mins)
```
"I'm thinking about [car]. Is it good?"

→ Skill will ask 3-5 clarifying questions
→ Provide quick assessment
→ Flag any obvious issues
→ Time: 5-10 mins
```

### For Variant Selection (10-15 mins)
```
"I've decided on [car], but which variant?"

→ Skill compares all variants
→ Explains cost-per-feature
→ Recommends "sweet spot"
→ Time: 10-15 mins
```

### For Full Analysis (30-50 mins)
```
"I want to buy [car]. Complete analysis please."

→ Skill runs affordability assessment
→ Calculates 5-year TCO
→ Checks affordability ratios
→ Detects red flags
→ Time: 30-50 mins
```

---

## Skill Limitations

- **Not legal advice**: Always verify documents with lawyers for loans/insurance
- **Not mechanical advice**: Consult mechanics for specific technical issues
- **Estimates are estimates**: Actual costs vary by location, driving style, maintenance
- **Markets change**: Data becomes stale; verify prices before committing
- **Resale unpredictable**: Resale values are predicted based on history; market changes
- **Personal factors**: This skill can't account for unique life circumstances

---

## How This Skill Gets Current Data

The skill uses **web research protocol** to verify all information:

1. **Pricing**: Calls to dealers, official websites (updated monthly)
2. **Specifications**: Manufacturer websites (rarely change mid-generation)
3. **Waiting periods**: Dealer inquiry, forums (changes weekly)
4. **Real fuel mileage**: Aggregate of 10+ owner reviews (medium confidence)
5. **Service costs**: Calls to service centers (varies by location)
6. **Reliability**: Forum discussions, warranty data (medium-high confidence)
7. **Finance rates**: Bank websites (updated frequently)

**All data includes confidence scores**. If <70% confidence, the skill flags uncertainty.

---

## When to Use Other Skills

**Handoff to Other Skills**:

| Question | Use This Skill | Use Another |
|----------|---|---|
| "Should I buy this car?" | ✅ | |
| "Can I afford this EMI?" | ✅ | |
| "Which variant is worth it?" | ✅ | |
| "What's the 0-100 time?" | | → Car Performance Analyzer |
| "How does a turbo work?" | | → Automotive Mechanics |
| "Should I modify my car?" | | → Car Customization Advisor |
| "Best insurance plan?" | | → Insurance Expert |
| "Should I take this loan?" | | → Personal Finance Advisor |

---

## Example Conversations

### Example 1: Budget SUV Search
```
User: "I need an SUV under ₹20L for highway driving"

Skill: Clarifying questions about family size, usage, down payment, existing EMI
→ Assess affordability: ₹60k salary = safe EMI ₹9k
→ Shortlist: Creta, Seltos, XUV500
→ Recommend: Creta SX (best value variant)
→ Cost: ₹16.5L on-road, ₹24.5k EMI
→ TCO: ₹42L over 5 years

User: "What about fuel cost?"
Skill: "Diesel, 18 km/l real-world = ₹3.2k/month. Insurance ₹900. Maintenance ₹1.2k.
        Total monthly: ₹29.6k (includes EMI)"

User: "Is this affordable?"
Skill: "Yes. EMI is 16% of salary (stretching but manageable). 
        Recommend larger down payment (₹5L) to reduce EMI to ₹22.5k.
        Red flag: Monitor if salary drops; no room for surprises."
```

### Example 2: "Should I Buy Now or Wait?"
```
User: "New generation Creta coming in 6 months. Should I wait?"

Skill: Decision matrix
→ Current: ₹15L, 5-star safety, 18 km/l, modern features
→ Predicted new: ₹16.5L, same 5-star safety, maybe 19 km/l, marginally better features
→ Worth waiting? Cost of waiting: 6 more months (interest paid, inflation)
→ Benefit of waiting: Maybe ₹5-8k/year fuel savings (not worth ₹1.5L premium)

Verdict: Buy now if you need car. Don't wait for cosmetic facelift.
```

---

## Support & Questions

**If You're Unsure About Terminology**:
- EMI = Equated Monthly Installment (loan payment)
- TCO = Total Cost of Ownership (all costs combined)
- LTCG = Long-term capital gain (tax on sale)
- RTO = Regional Transport Office (registration)

**If Data Seems Outdated**:
- Prices change monthly (GST, taxes, demand)
- Waiting periods change weekly
- Resale values fluctuate seasonally
- Always verify with dealers before committing

**If You Disagree With Recommendation**:
- This skill prioritizes financial safety over luxury
- If you strongly prefer a car despite red flags, that's your choice
- But understand the risks explicitly

---

## Philosophy of This Skill

**Core Principle**: A financially sensible decision beats a cool car.

**Never**:
- Recommend top-spec just because it's top-spec
- Assume your priorities
- Hide financial risks
- Prioritize marketing hype over math

**Always**:
- Ask clarifying questions first
- Show the math
- Explain tradeoffs
- Flag red flags
- Give you alternatives

**Tone**:
- Practical (not dreamy)
- Analytical (not salesy)
- Grounded (not optimistic)
- Occasionally witty (not preachy)

---

## Next Steps

1. **Describe your situation**: Income, budget, lifestyle, constraints
2. **Ask your question**: Specific car or general guidance?
3. **Provide numbers**: Be honest about finances
4. **Receive analysis**: Breakdown of options + recommendation
5. **Decide with confidence**: You know the tradeoffs

---

## Feedback & Improvements

This skill evolves based on real scenarios. If you encounter a situation not covered:
1. Describe what happened
2. Suggest what would have been helpful
3. Help improve future versions

---

**Ready to make a smart car-buying decision?**

Start with: *"I'm thinking about buying a car. Here's my situation..."*

The skill will take it from there.

---

**End of README**

For detailed frameworks, examples, and checklists, see the supporting documents in this skill package.
