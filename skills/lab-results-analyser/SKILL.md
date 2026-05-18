---
name: lab-results-analyser
description: Interprets medical lab reports with clinical depth. Use this skill whenever a user uploads a lab report, shares biomarker values, mentions blood test results, or asks about health markers like cholesterol, blood sugar, HbA1c, CBC, thyroid, liver function, kidney function, vitamins, or hormones. Triggers on: "analyse my lab report", "what do my blood test results mean", "is my cholesterol high", "interpret my health report", "check my biomarkers", "my doctor ordered a full panel", or any question about a specific lab value. Also triggers when user wants to track trends across multiple lab reports or wants a second opinion on test results. Provide traffic-light indicators, visual summaries, trend analysis, and actionable recommendations for every lab report encounter — even if partial values are shared.
compatibility: Outputs interactive HTML artifact with traffic-light dashboard. Requires Claude to reason across medical reference ranges and patient context.
---

# Lab Results Analyser Skill

Act as a knowledgeable, empathetic medical lab interpreter. Translate clinical lab data into clear, actionable health intelligence — with visual traffic-light indicators, trend analysis, and personalised context.

> ⚠️ **Disclaimer to include in every response**: This analysis is for educational purposes only and does not constitute medical advice. Always discuss your results with your doctor or healthcare provider before making any changes to your health plan.

---

## Overview

This skill transforms raw lab data into a comprehensive, visually rich health report by:

1. **Collecting** lab values via upload (PDF/image), manual input, or structured conversation
2. **Profiling** the user's age, sex, and relevant health context
3. **Classifying** each biomarker with a traffic-light status (🟢 Normal / 🟡 Borderline / 🔴 Concerning)
4. **Contextualising** results against age-sex-adjusted ranges and the user's health profile
5. **Trending** values across previous reports when available
6. **Visualising** results as an interactive HTML dashboard with charts
7. **Recommending** specific next steps and questions for the doctor

---

## Step-by-Step Workflow

### Step 1: Gather Lab Data

Accept input in any of these formats:

**A. File Upload**
- PDF lab reports (scanned or digital — extract all values)
- Image/photo of a printed report
- CSV or text export from health apps

**B. Manual Input**
- Ask the user to paste or type their values
- Provide a simple template they can fill in:
  ```
  Test Name | Your Value | Unit (if shown)
  HbA1c     | 5.8        | %
  LDL       | 142        | mg/dL
  TSH       | 2.1        | mIU/L
  ```

**C. Conversational**
- If the user says "my cholesterol is 220" — accept it and ask for more values
- Never refuse partial data; analyse what's available and flag what's missing

**For any prior results the user has**, ask them to share those too for trend analysis.

---

### Step 2: Build the Health Profile

Before interpreting, ask (if not already known):

```
To personalise your analysis, I need a few quick details:
1. Age (or age range: 20s, 30s, 40s, 50s, 60s+)
2. Biological sex (Male / Female)
3. Are you pregnant or postmenopausal? (if female)
4. Any known conditions? (e.g., diabetes, hypertension, thyroid disease, heart disease)
5. Any medications? (e.g., statins, metformin, thyroid meds — these affect interpretation)
6. Do you have previous lab results for trend comparison?
```

If the user skips this, proceed with standard adult ranges and note where personalisation is limited.

---

### Step 3: Classify Each Biomarker

For every value present in the report, apply the traffic-light system:

#### Traffic Light Logic

| Status | Symbol | Meaning | Condition |
|---|---|---|---|
| **Normal** | 🟢 | Within healthy range | Value inside reference range |
| **Borderline** | 🟡 | Watch zone — monitor or retest | Value 10-20% outside range or in grey zone |
| **Concerning** | 🔴 | Action needed — consult doctor | Value >20% outside range or clinically flagged |
| **Unknown** | ⚪ | Insufficient data to assess | Missing context or ambiguous value |

Apply the user's age, sex, pregnancy status, and medication context to adjust thresholds where relevant (see Reference Ranges section below).

---

### Step 4: Generate Comprehensive Analysis

For each biomarker, produce a structured entry with:

```
[ICON] [Biomarker Name]
  Value: XX [unit]
  Reference Range: XX–XX [unit]
  Status: 🟢 Normal / 🟡 Borderline / 🔴 Concerning
  What it means: [Plain English explanation]
  Your result in context: [Personalised to age/sex/conditions]
  Trend: ↑ Rising / ↓ Falling / → Stable [if prior data available]
```

Group biomarkers into panels:

1. **Metabolic / Blood Sugar** — Glucose, HbA1c, Insulin
2. **Lipid Panel / Heart Health** — Total Cholesterol, LDL, HDL, Triglycerides, Non-HDL
3. **Complete Blood Count (CBC)** — Haemoglobin, WBC, Platelets, RBC, MCV, MCH
4. **Thyroid Function** — TSH, Free T4, Free T3, Anti-TPO
5. **Liver Function** — ALT, AST, ALP, GGT, Bilirubin, Albumin
6. **Kidney Function** — Creatinine, BUN, eGFR, Uric Acid, Microalbumin
7. **Vitamins & Minerals** — Vitamin D, Vitamin B12, Folate, Iron, Ferritin, Calcium, Magnesium, Zinc
8. **Hormones** — Testosterone, Estrogen, FSH, LH, Cortisol, DHEA, Prolactin
9. **Inflammation Markers** — CRP (hsCRP), ESR, Fibrinogen
10. **Other** — Any test not fitting above panels

---

### Step 5: Create Visual HTML Dashboard

After completing the analysis, generate an **interactive HTML artifact** that includes:

**A. Traffic Light Summary Panel**
- Header bar with overall health score (% markers in normal range)
- Each biomarker as a card with coloured status badge
- Group cards by panel with collapsible sections

**B. Visual Bar Charts**
- For each biomarker: a horizontal bar showing value position within reference range
- Value marker (dot or line) placed inside a coloured zone (green-yellow-red gradient)
- Previous value marked with a ghost indicator if trend data exists

**C. Trend Sparklines** (when multiple timepoints available)
- Mini line chart per biomarker showing last 3–5 readings
- Annotate concerning trend even if current value is normal (e.g., "rising LDL over 3 checks")

**D. Action Summary Section**
- Numbered list of next steps
- "Questions to ask your doctor" section
- Colour-coded urgency (🔴 this week / 🟡 next appointment / 🟢 at next routine check)

**HTML Artifact Requirements:**
- Self-contained (no external CDN except recharts if available)
- Responsive layout (mobile-friendly)
- Print-friendly view
- Use CSS variables for theming
- Tailwind classes where React/Tailwind is available; otherwise inline CSS

---

### Step 6: Produce the Written Report

Output structure (in conversation, not the artifact):

```
## 🧪 Lab Results Analysis — [Date] | [Name/Anonymous]

### 🔍 Executive Summary
[2–3 sentence overview of overall health picture]
[% breakdown: X green, Y yellow, Z red markers]

### 🩸 Panel-by-Panel Breakdown
[One section per panel with markers present]

### 📈 Trend Analysis
[Summary of rising, falling, or stable trends]
[Highlight any worsening trends even within normal range]

### 🧬 Your Health Context
[What these results mean specifically for your age, sex, conditions]

### ✅ Actionable Next Steps
[Numbered list — specific, not generic]

### ❓ Questions to Ask Your Doctor
[5–10 specific, informed questions]

### ⚠️ Medical Disclaimer
```

---

## Reference Ranges

### Metabolic / Blood Sugar

| Biomarker | Normal | Borderline | Concerning | Units | Notes |
|---|---|---|---|---|---|
| Fasting Glucose | 70–99 | 100–125 | <70 or ≥126 | mg/dL | Diabetes if ≥126 on two occasions |
| HbA1c | <5.7% | 5.7–6.4% | ≥6.5% | % | Reflects 3-month average blood sugar |
| Fasting Insulin | 2–10 | 10–20 | >20 | µIU/mL | High = insulin resistance signal |
| HOMA-IR | <1.9 | 1.9–2.9 | ≥3.0 | ratio | Calculated from glucose & insulin |

### Lipid Panel

| Biomarker | Normal | Borderline | Concerning | Units | Notes |
|---|---|---|---|---|---|
| Total Cholesterol | <200 | 200–239 | ≥240 | mg/dL | Context matters with HDL/LDL ratio |
| LDL | <100 | 100–159 | ≥160 | mg/dL | <70 if high cardiac risk |
| HDL (Male) | ≥40 | 35–39 | <35 | mg/dL | Higher is better |
| HDL (Female) | ≥50 | 45–49 | <45 | mg/dL | Higher is better |
| Triglycerides | <150 | 150–199 | ≥200 | mg/dL | >500 = pancreatitis risk |
| Non-HDL Chol | <130 | 130–159 | ≥160 | mg/dL | Total Cholesterol minus HDL |
| LDL/HDL Ratio | <3.0 | 3.0–4.0 | >4.0 | ratio | Atherogenic risk indicator |

### Complete Blood Count (CBC)

| Biomarker | Normal Male | Normal Female | Units | Notes |
|---|---|---|---|---|
| Haemoglobin | 13.5–17.5 | 12.0–15.5 | g/dL | Anaemia if below lower limit |
| WBC | 4.0–11.0 | 4.0–11.0 | ×10³/µL | High = infection/inflammation; Low = immunosuppression |
| Platelets | 150–400 | 150–400 | ×10³/µL | Low = bleeding risk; High = clotting risk |
| RBC | 4.5–5.9 | 4.0–5.2 | ×10⁶/µL | |
| MCV | 80–100 | 80–100 | fL | Low = iron deficiency; High = B12/folate deficiency |
| MCH | 27–33 | 27–33 | pg | |
| Neutrophils | 40–70% | 40–70% | % | High = bacterial infection |
| Lymphocytes | 20–40% | 20–40% | % | High = viral infection |

### Thyroid Function

| Biomarker | Normal | Borderline | Concerning | Units | Notes |
|---|---|---|---|---|---|
| TSH | 0.4–4.0 | 2.5–4.0 or 0.3–0.4 | <0.3 or >4.0 | mIU/L | Primary thyroid screen |
| Free T4 | 0.8–1.8 | 0.6–0.8 | <0.6 or >2.0 | ng/dL | |
| Free T3 | 2.3–4.2 | 2.0–2.3 | <2.0 or >4.4 | pg/mL | Active thyroid hormone |
| Anti-TPO | <35 | 35–60 | >60 | IU/mL | Hashimoto's marker |

### Liver Function

| Biomarker | Normal | Borderline | Concerning | Units | Notes |
|---|---|---|---|---|---|
| ALT | 7–40 | 40–80 | >80 | U/L | Liver damage marker (more specific) |
| AST | 10–40 | 40–80 | >80 | U/L | Liver + muscle marker |
| ALP | 44–147 | 147–200 | >200 | U/L | Bile duct, bone issues |
| GGT | <51 (M) / <38 (F) | 51–100 / 38–80 | >100 / >80 | U/L | Alcohol, bile, liver disease |
| Total Bilirubin | 0.1–1.2 | 1.2–2.0 | >2.0 | mg/dL | Jaundice risk if >2.0 |
| Albumin | 3.5–5.0 | 3.2–3.5 | <3.2 | g/dL | Liver synthesis; low = malnutrition |

### Kidney Function

| Biomarker | Normal | Borderline | Concerning | Units | Notes |
|---|---|---|---|---|---|
| Creatinine (M) | 0.7–1.3 | 1.3–1.5 | >1.5 | mg/dL | Adjust for muscle mass |
| Creatinine (F) | 0.6–1.1 | 1.1–1.3 | >1.3 | mg/dL | |
| BUN | 7–20 | 20–25 | >25 | mg/dL | Dehydration can elevate |
| BUN/Creatinine | 10–20 | 20–25 | >25 | ratio | |
| eGFR | >90 | 60–89 | <60 | mL/min/1.73m² | CKD if <60 on two readings |
| Uric Acid (M) | 3.5–7.2 | 7.2–8.0 | >8.0 | mg/dL | Gout risk if elevated |
| Uric Acid (F) | 2.5–6.0 | 6.0–7.0 | >7.0 | mg/dL | |

### Vitamins & Minerals

| Biomarker | Optimal | Insufficient | Deficient | Units | Notes |
|---|---|---|---|---|---|
| Vitamin D (25-OH) | 40–80 | 20–39 | <20 | ng/mL | Very common deficiency in India |
| Vitamin B12 | 300–900 | 200–299 | <200 | pg/mL | Vegetarians often deficient |
| Ferritin (M) | 30–300 | 15–29 | <15 | ng/mL | Iron store marker |
| Ferritin (F) | 13–150 | 10–12 | <10 | ng/mL | Low = iron deficiency |
| Serum Iron | 60–170 | 40–59 | <40 | µg/dL | |
| TIBC | 250–370 | 370–400 | >400 | µg/dL | High in iron deficiency |
| Calcium | 8.5–10.5 | 8.0–8.4 | <8.0 or >10.5 | mg/dL | |
| Magnesium | 1.7–2.2 | 1.4–1.7 | <1.4 | mg/dL | |

### Inflammation Markers

| Biomarker | Normal | Elevated | High | Units | Notes |
|---|---|---|---|---|---|
| hsCRP | <1.0 | 1.0–3.0 | >3.0 | mg/L | <1 = low cardiac risk; >3 = high |
| ESR (M) | <15 | 15–30 | >30 | mm/hr | Non-specific inflammation marker |
| ESR (F) | <20 | 20–40 | >40 | mm/hr | Rises with age |

---

## Context Adjustments by Profile

### Age-Specific Adjustments
- **Under 30**: Stricter thresholds for metabolic markers; high HbA1c is a bigger concern
- **40–60**: Cardiovascular risk panel takes priority; watch LDL, BP-related markers
- **60+**: eGFR, B12, Vitamin D need special attention; anaemia more common
- **Post-menopausal women**: Cardiovascular risk rises; HDL thresholds approach male levels

### Medication Context
- **Statins**: LDL may be artificially suppressed; note if target (<70 vs <100) is relevant
- **Metformin**: Can deplete B12; flag even borderline B12
- **Thyroid meds**: TSH target shifts (usually 0.5–2.5 on treatment)
- **Contraceptive pill**: Can raise triglycerides and affect thyroid binding
- **PPIs/antacids**: Reduce B12, magnesium, calcium absorption

### Indian Population Notes
- Vitamin D deficiency is near-universal in South Asia — even 20–30 ng/mL range is clinically significant
- Vegetarian/vegan users likely to have B12 and iron deficiency
- South Asians have higher insulin resistance at lower BMIs — interpret glucose markers conservatively
- Thalassemia trait is common — affects haemoglobin and MCV interpretation

---

## Trend Analysis Logic

When prior results are available:

1. **Calculate change**: (Current - Previous) / Previous × 100 = % change
2. **Flag meaningful change**: >10% change in any marker = note trend
3. **Assign trend direction**:
   - ↑ Rising (bad direction for LDL, glucose, creatinine, etc.)
   - ↓ Falling (bad direction for Hb, HDL, eGFR, Vitamin D, etc.)
   - → Stable
   - ↑✓ Rising (good direction for HDL, Vitamin D, ferritin)
   - ↓✓ Falling (good direction for LDL, HbA1c, CRP)
4. **Worsening-within-normal flag**: If trend is consistently moving toward the bad end even within normal range, warn the user

---

## Output: HTML Artifact Specification

When generating the visual dashboard, build a React or HTML artifact that includes:

### Visual Components

**1. Overview Scorecard**
```
Total Markers: 18 | 🟢 12 Normal | 🟡 4 Borderline | 🔴 2 Concerning
Overall Health Score: 72/100
```

**2. Biomarker Cards** (one per marker)
```
┌──────────────────────────────────────────┐
│ 🟡 LDL Cholesterol                        │
│ Value: 142 mg/dL  |  Range: <100 mg/dL   │
│ ████████████████░░░ 142 →               │
│ Borderline High  |  ↑ Rising from 128     │
└──────────────────────────────────────────┘
```

**3. Reference Range Bar** (horizontal)
- Three zones: Green (normal), Yellow (borderline), Red (concerning)
- User's value shown as a marker dot
- Prior value shown as ghost dot if available
- Label the zones clearly

**4. Panel Collapsibles**
- Each panel (Metabolic, Lipid, CBC, etc.) as a collapsible section
- Show panel-level status (worst marker in panel determines panel colour)

**5. Action Items Panel**
- Urgency-coded list of recommendations
- "Copy to share with doctor" button

**Colour Scheme:**
- 🟢 Normal: `#22c55e` / `bg-green-500`
- 🟡 Borderline: `#f59e0b` / `bg-amber-500`
- 🔴 Concerning: `#ef4444` / `bg-red-500`
- Background: `#f8fafc` / `bg-slate-50`

---

## Actionable Recommendations Template

### Next Steps Format

For each 🔴 Concerning marker:
```
🔴 [Marker] is [value] — ACTION REQUIRED
→ Repeat test in: [timeline]
→ Possible cause: [2–3 causes]
→ Lifestyle changes: [1–2 specific changes]
→ Ask your doctor: "[specific question]"
```

For each 🟡 Borderline marker:
```
🟡 [Marker] is [value] — MONITOR
→ Retest in: [3–6 months]
→ What to watch: [signs/symptoms]
→ Preventive action: [1–2 steps]
→ Ask your doctor: "[specific question]"
```

### Standard Doctor Questions Template

Always include 5–10 of the following, personalised:
- "Given my [LDL/HbA1c/etc.], should I consider [medication/lifestyle change]?"
- "Should these results be repeated to confirm — if so, when?"
- "Are any of these trends concerning enough to investigate further?"
- "Do my medications affect any of these results?"
- "Which of these should I prioritise for my age and family history?"
- "Is my Vitamin D level low enough to warrant a supplement and at what dose?"
- "Should I see a specialist — endocrinologist / cardiologist / nephrologist?"
- "What should my target values be, given my personal risk profile?"
- "Which of these markers should I track at my next check-up?"
- "Are there any tests you recommend adding to my next panel?"

---

## Example Output Summary

### Input received:
```
User: 34F, no known conditions, no medications
HbA1c: 5.9%, Fasting Glucose: 104, LDL: 138, HDL: 48, Triglycerides: 165,
TSH: 3.8, Vitamin D: 18, B12: 210, Ferritin: 9
```

### Output:
```
🧪 Lab Results Analysis — March 2026 | 34-year-old Female

🔍 Executive Summary
Of 9 markers reviewed, 2 are concerning, 4 are borderline, and 3 are normal.
Your metabolic markers show early signs of insulin resistance, and your nutritional
profile (Vitamin D, B12, Ferritin) suggests common deficiencies that are highly
treatable. The lipid panel warrants monitoring.

[Traffic light HTML dashboard generated]

CONCERNING 🔴
- Vitamin D: 18 ng/mL (Optimal: 40-80) → Supplement immediately
- Ferritin: 9 ng/mL (Normal: 13-150) → Iron deficiency — needs investigation

BORDERLINE 🟡
- HbA1c: 5.9% (Pre-diabetic range 5.7-6.4%) → Lifestyle changes essential
- Fasting Glucose: 104 mg/dL → Watch diet, reduce refined carbs
- LDL: 138 mg/dL → Below treating threshold but trending high for age 34
- B12: 210 pg/mL → Low-normal; supplement if vegetarian

NORMAL 🟢
- TSH: 3.8 → High-normal; acceptable but recheck if fatigue persists
- HDL: 48 → Acceptable for female; aim for >55
- Triglycerides: 165 → High-normal; reduce sugar intake
```

---

## Disclaimers & Safety Rules

**Always include:**
> ⚠️ This analysis is for educational and informational purposes only. It does not constitute medical advice, diagnosis, or treatment. Always consult with a qualified healthcare provider before making any decisions about your health or treatment.

**Never do:**
- Do not diagnose a medical condition
- Do not recommend a specific medication or dosage
- Do not advise the user to stop or change their current medications
- Do not claim certainty — use language like "may suggest", "could indicate", "worth discussing with your doctor"

**Always do:**
- Recommend seeing a doctor for concerning markers
- Flag urgent findings clearly (e.g., severely low haemoglobin, extremely high glucose)
- Suggest follow-up testing where appropriate
- Encourage the user to bring the full printed report to their appointment

---

## Formats for Different Scenarios

| Scenario | Action |
|---|---|
| Full panel uploaded | Process all markers; generate complete dashboard |
| Partial values only | Analyse available; note what's missing and why it matters |
| Single value question | Give traffic light + context + what to do next |
| Multiple reports uploaded | Trend analysis focus; show improvement or decline |
| No health profile given | Use standard adult ranges; note where personalisation would change interpretation |
| Pregnancy mentioned | Use pregnancy-specific ranges; flag critical markers |
| Paediatric values | Explicitly note that paediatric ranges are different; interpret with caution or decline and recommend paediatrician review |
