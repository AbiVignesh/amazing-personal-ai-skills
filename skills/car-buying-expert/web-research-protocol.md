# Protocol: Web Research for Latest Car Data

## Purpose
Ensure all car recommendations are based on current pricing, specifications, and market data—not outdated information.

---

## Research Workflow

### Step 1: Identify Information Needed

Before searching, clarify what you need:

```
REQUIRED DATA POINTS:

For each car shortlisted:
✓ Current price (ex-showroom + on-road estimate)
✓ Available variants/trims and their features
✓ Engine options (petrol/diesel/electric/hybrid)
✓ Real-world fuel efficiency (not claimed)
✓ Current waiting period (critical for buying timeline)
✓ Safety ratings (latest NHTSA/GNCAP)
✓ Reliability reputation (long-term)
✓ Resale value retention
✓ Service center location & service cost estimates
✓ Current finance rates (bank vs NBFC vs dealer)
```

---

### Step 2: Search Strategy

**Search Queries (in order of preference)**:

```
Query Priority 1: Official Pricing & Specs
- "[Car name] price 2026 variants specifications official"
- Go directly to manufacturer's website first
- Verify on 2-3 official dealer websites

Query Priority 2: Current Waiting Period
- "[Car name] waiting period current month city"
- Check forum discussions (Team-BHP, CarDekho forums)
- Check dealer website (often displays waiting period)

Query Priority 3: Real-World Fuel Efficiency
- "[Car name] real mileage fuel efficiency user reviews"
- Look for 20+ user reviews averaging actual mileage
- Weight toward similar driving conditions (highway vs city)
- Cross-check multiple forums

Query Priority 4: Ownership & Service Costs
- "[Car name] service cost annual maintenance estimate India"
- Contact 2-3 authorized service centers
- Note regional variations (rural vs metro rates)

Query Priority 5: Resale Value & Depreciation
- "[Car name] resale value 5 year depreciation India"
- Check used car marketplaces (Cars24, OLX)
- Look for 5-year-old models, their prices

Query Priority 6: Reliability & Common Issues
- "[Car name] common problems issues complaints forums"
- Read Team-BHP owner threads (real owners discuss issues)
- Cross-reference with warranty claims data if available

Query Priority 7: Current Finance Rates
- "[Bank/NBFC] car loan interest rate 2026 current"
- Check 3-5 different lenders (variation is ₹1-3%)
```

---

### Step 3: Source Credibility Ranking

**HIGH CREDIBILITY** (Use directly):
1. Manufacturer's official website
2. Official authorized dealer websites
3. SIAM (Society of Indian Automobile Manufacturers) data
4. Major forum threads with 100+ pages (Team-BHP, Reddit r/india)
5. Reputable car review sites (ThrottleHolic, CarDekho, AutoX)
6. Bank/NBFC official rate cards

**MEDIUM CREDIBILITY** (Verify with 2+ sources):
1. Used car marketplace listings (Cars24, OLX, Quikr)
2. Automotive blogs & YouTube channels
3. Insurance aggregate sites (for estimates)
4. Service center quotes (call 2-3 centers, average)

**LOW CREDIBILITY** (Skip unless confirmed elsewhere):
1. Random blog posts without citations
2. Single forum posts (may be outlier opinion)
3. Dealer advertisements (biased, outdated)
4. Comparison websites with stale data (often outdated)

**SUSPECT** (Triple-verify or skip):
1. Clickbait YouTube titles
2. Anonymous posts with extreme claims
3. Data lacking timestamps
4. Sources with financial incentive (affiliate links)

---

### Step 4: Data Verification Protocol

**For Each Data Point, Verify**:

```
PRICE VERIFICATION:
✗ Single source only
✓ Minimum 2-3 sources
✓ Check if price is ex-showroom or on-road
✓ Verify with actual quotes from dealers in user's city
✓ Note city variations (prices vary ₹50-100k by location)
✓ Check date: If >3 months old, flag as potentially outdated

FUEL EFFICIENCY VERIFICATION:
✗ Use claimed ARAI figure alone
✓ Average real-world reports from 10+ users
✓ Only use reports matching user's driving style (highway, city, mixed)
✓ Note variation ranges (e.g., 14-18 km/l for this car)
✓ Apply conservative multiplier: 0.7 of claimed = real-world estimate

WAITING PERIOD VERIFICATION:
✗ Assume it applies everywhere
✓ Verify for specific city/region
✓ Check date: Waiting periods change monthly
✓ Call dealers directly if timing-critical
✓ Factor in current demand (post-launch vs mature product)

SERVICE COST VERIFICATION:
✗ Trust generic estimates
✓ Call 3 service centers in user's city
✓ Ask for itemized costs (oil, filter, parts, labor)
✓ Average the 3 quotes
✓ Note regional variation (metro cities more expensive)

RESALE VALUE VERIFICATION:
✗ Use predicted values only
✓ Check actual listings of 5-year-old cars on used marketplaces
✓ Average multiple listings
✓ Adjust for condition/mileage
✓ Note: Actual resale depends on condition, mileage, maintenance history
```

---

### Step 5: Handling Conflicting Information

**When Sources Disagree**:

```
Example:
- Source A: Creta waiting period 4 months
- Source B: Creta waiting period 2 months
- Source C: Creta waiting period 6 months

RESOLUTION:
1. Check dates: Which is most recent?
2. Check location: Are all talking about same city?
3. Call dealers: Get official confirmation
4. Weight recent + official sources higher
5. Report: "Based on latest data, waiting period is 3-4 months, but varies by city"
6. Confidence level: MEDIUM (conflict observed)
```

---

### Step 6: Confidence Scoring for Each Data Point

**Confidence Framework**:

```
HIGH (95%+) Confidence:
- Official manufacturer pricing (dated this month)
- Official GNCAP/safety ratings
- Bank's published interest rates
- Well-established brand reliability data

MEDIUM (70-90%) Confidence:
- Aggregate of 10+ user reports on mileage
- Multiple dealer quotes (average)
- Used car marketplace trends (average of 20+ listings)
- Popular forum consensus (100+ posts, consistent narrative)

LOW (50-70%) Confidence:
- Single YouTube review
- Isolated forum posts
- Dealer estimates (high variance)
- Marketing claims about new features

VERY LOW (<50%) Confidence:
- Specific maintenance costs (too variable)
- Long-term reliability predictions (new models)
- Resale predictions 5+ years out
- Fuel price projections

Rule: Only state confidence level explicitly. Don't hide uncertainty.
```

---

### Step 7: Red Flags in Research Data

**Watch Out For**:

| Red Flag | Means | Action |
|----------|-------|--------|
| Price data is 6+ months old | Outdated | Flag and rescan for current data |
| Specs don't match official website | Conflicting info | Verify with manufacturer |
| One source claims dramatically different mileage than others | Outlier | Cross-verify with 5+ other users, check driving conditions |
| Waiting period hasn't updated in 2+ years | Stale data | Call dealers directly |
| Resale value claims lack supporting evidence | Unsubstantiated | Find actual used car listings |
| Finance rate claim matches no real lender | Made up | Verify with actual bank websites |
| Single forum post claims major reliability issue | Isolated incident | Cross-reference with 20+ other owner posts |

---

### Step 8: Information Organization Template

**Use This Format to Document Findings**:

```
CAR: [Name] [Variant]

PRICING:
- Ex-showroom: ₹[X] (Source: [Dealer/Website], Date: [MM-YYYY], Confidence: HIGH)
- On-road estimate: ₹[Y] (Source: [Multiple dealers avg], Confidence: MEDIUM)
- Regional variation: ±₹[Z] depending on state
- Update note: Check current prices, as GST/taxes may have changed

SPECIFICATIONS:
- Engine: [cc], [fuel type], [power]
- Transmission: [Manual/Auto]
- Seating: [X] persons
- Boot space: [Liters]
- Safety: [Star rating] (Source: [GNCAP/NHTSA], Confidence: HIGH)

FUEL EFFICIENCY:
- Claimed ARAI: [X] km/l
- Real-world (conservative): [Y] km/l (Source: [Average of 10+ user reports], Confidence: MEDIUM)
- Variation range: [A-B] km/l based on driving style
- Used for TCO: [Y] km/l

CURRENT WAITING PERIOD:
- [City name]: [X] months (Source: [Dealer], Date: [MM-YYYY], Confidence: MEDIUM)
- Note: Check with dealers, varies by city and demand

SERVICE & MAINTENANCE:
- Service cost per 10,000 km: ₹[X] (Source: [3 service centers, average], Confidence: MEDIUM)
- Parts availability: [Easy/Moderate/Difficult]
- Service centers in region: [X] (Source: [Manufacturer], Confidence: HIGH)

RESALE VALUE:
- Expected 5-year retention: [X]% (Source: [Average of used car listings], Confidence: LOW-MEDIUM)
- Note: High variance based on actual condition, mileage, maintenance

RELIABILITY:
- Reputation: [Good/Average/Poor] (Source: [Forum consensus, 100+ posts], Confidence: MEDIUM)
- Common issues: [List if any]
- Warranty: [Years/KM]

FINANCING:
- Current bank rate: [X]% (Source: [Bank website], Date: [MM-YYYY], Confidence: HIGH)
- EMI for ₹20L loan, 60 months: ₹[X] (Calculated, Confidence: HIGH)

LAST UPDATED: [MM-DD-YYYY HH:MM]
CONFIDENCE LEVELS: HIGH [95%+] | MEDIUM [70-90%] | LOW [50-70%]
```

---

### Step 9: Updating Old Information

**When to Re-research**:

```
EVERY MONTH:
- Current price (GST/tax changes, new variants)
- Finance rates (RBI policy changes)
- Waiting period (supply/demand fluctuates)

EVERY QUARTER:
- Fuel efficiency reports (new user data accumulates)
- Service cost updates

EVERY 6 MONTHS:
- Resale value trends (market fluctuates)
- Reliability data (new issues may emerge)

ANNUALLY:
- Safety ratings (new tests occur)
- Warranty changes
- New generation launches

BEFORE RECOMMENDATION:
- Always check if data is >3 months old
- Flag if significant time has passed since last update
- Re-research if any price/specification change mentioned in news
```

---

### Step 10: Reporting Data Sources to User

**Transparency Template**:

```
WHAT I FOUND:

Car: Hyundai Creta SX
Price: ₹15.3L on-road
Source: Average of 3 authorized dealer quotes in Chennai (June 2026)
Confidence: HIGH

Fuel efficiency: 18 km/l real-world
Source: Average of 15 user reports on Team-BHP forum (highway driving)
Confidence: MEDIUM (assumes similar driving style to yours)

Waiting period: 2-3 months
Source: Direct dealer inquiry (June 15, 2026)
Confidence: MEDIUM (varies by city, demand fluctuates)

Service cost: ₹3,200 per 10,000 km
Source: Average of 3 Hyundai service centers in Chennai
Confidence: MEDIUM (labor costs vary by location)

Resale value: 50-52% retention after 5 years
Source: Analysis of 20 5-year-old Creta listings on Cars24 (June 2026)
Confidence: LOW-MEDIUM (depends on actual condition, mileage)

NOTE: This data reflects current market as of June 2026. Prices and waiting periods change monthly.
I recommend verifying prices with dealers before committing, as rates may have changed.
```

---

## Example: Research Protocol in Action

### Real Example: Researching Creta's Real Fuel Mileage

**Claim**: Creta diesel claims 23.7 km/l (ARAI)

**My research**:

```
Query 1: "Creta diesel real mileage fuel efficiency km/l actual"
Results: Multiple forum posts, YouTube reviews

Query 2: "Creta diesel owner discussion Team-BHP fuel consumption"
Results: Long thread with 200+ owners discussing actual mileage

Data collection:
- Owner 1: "I get 18 km/l in city, 21 on highway"
- Owner 2: "Around 19 km/l mixed driving"
- Owner 3: "20-21 km/l if I drive carefully on highway"
- Owner 4: "17 km/l in heavy traffic city"
- Owner 5: "19 km/l overall average"
[...repeated 15+ times...]

Average from 20 users: 19.2 km/l
Range: 17-22 km/l

My conclusion:
"Real-world mileage: 19-20 km/l (0.81-0.85x of claimed 23.7 km/l)
For conservative cost estimation, use 18 km/l"

Confidence: MEDIUM (good data from many users, but variation exists)
```

---

## Critical Reminders

1. **Never trust claimed figures alone** (ARAI, manufacturer mileage claims)
2. **Always verify prices with dealers** (prices vary by location, day)
3. **Update data before major recommendations** (markets change monthly)
4. **State confidence level explicitly** (don't hide uncertainty)
5. **Cite sources** (help user verify independently)
6. **Disclose conflicting information** (transparency > false confidence)
7. **Re-research if uncertain** (better to spend 5 min than give wrong advice)

---

**End of Web Research Protocol**

This protocol ensures all recommendations are grounded in current, verified data—not outdated information or guesses.
