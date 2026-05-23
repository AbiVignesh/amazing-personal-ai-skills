# Resume Guidance & SDE Profile Optimization

Help users turn their experience into interview-winning resumes.

---

## Resume Assessment

**Current Resume Strength: X / 10**

### Strengths

- [ ] Clear structure (no wall of text)
- [ ] Quantified impact (used numbers, not just verbs)
- [ ] Focused on what matters (shipped code, not busywork)
- [ ] Company names and titles are clear
- [ ] Easy to skim (recruiter has 6 seconds)

**What's working:** [List 2-3 strong elements]

---

## Common Weaknesses (and How to Fix)

### Problem 1: Too Much Focus on Credentials

**Bad:** "Studied CS at Stanford, GPA 3.9, Dean's list"

**Why it's bad:** Credentials don't signal coding ability. Companies care about what you shipped.

**Better:**
- Remove GPA if <3.7
- Remove "Dean's list" (noise)
- Replace with: projects, impact, systems thinking

---

### Problem 2: Describing Tasks Instead of Impact

**Bad:** "Wrote unit tests for backend service"

**Why it's bad:** Task-focused. Doesn't show impact.

**Better:** "Improved test coverage from 60% to 92% through systematic unit testing, reducing production bugs by 35%"

---

### Problem 3: No Numbers

**Bad:** "Optimized database queries, improved performance"

**Why it's bad:** Vague. No proof of impact.

**Better:** "Optimized N+1 database queries in user dashboard; reduced page load from 2.1s to 450ms (79% improvement), enabling 100k more concurrent users"

---

### Problem 4: No Systems Thinking

**Bad:** "Built API endpoint"

**Why it's bad:** Junior-level task description.

**Better:** "Designed and shipped REST API for user notifications with eventual consistency model; scaled to handle 100k events/sec with <50ms latency"

---

### Problem 5: Doesn't Match FAANG Signals

**By company:**

| Company | Cares About | Resume Signal |
|---------|------------|---|
| Google | Technical depth | "Optimized search algorithm from O(n^2) to O(n log n)" |
| Amazon | Bias for action | "Shipped feature in 2 weeks despite ambiguous requirements" |
| Meta | Scale + speed | "Handled 10M daily active users with <100ms latency" |
| Apple | Quality | "Zero production incidents in Q2 due to rigorous testing" |
| Netflix | Autonomy | "Owned end-to-end redesign; drove technical decisions" |

---

## Resume Reframing: Examples

### Example 1: Generic Software Engineer

**Before:**
```
Senior Software Engineer | Amazon | 2021-2023
- Worked on backend team
- Fixed bugs and wrote code
- Participated in code reviews
- Improved test coverage
```

**After:**
```
Senior Software Engineer | Amazon | 2021-2023
- Led redesign of order fulfillment pipeline; reduced order latency from 5s to 800ms 
  (84% improvement) enabling 2x peak traffic handling
- Designed and implemented circuit breaker pattern for external API calls;
  improved system resilience and reduced cascading failures by 40%
- Drove test-first development; improved test coverage from 70% to 95% and
  reduced production bugs by 50%
```

---

### Example 2: Early-Career Engineer

**Before:**
```
Software Engineer | Google | 2023-Present
- Intern on Chrome team
- Learned JavaScript and React
- Shipped small features
```

**After:**
```
Software Engineer | Google | 2023-Present
- Built real-time collaborative editing feature for Google Docs; coordinated with
  PM to ship on schedule, now used by 50k early access users
- Optimized React render performance; reduced component re-render time from 200ms to 40ms
  by implementing memoization and lazy loading
- Owned performance monitoring dashboard for team; identified 3 critical bottlenecks
  through analysis, leading to 30% overall speed improvement
```

---

### Example 3: Different Background

**Before:**
```
Full Stack Developer | Startup | 2022-2023
- Built web app
- Deployed to AWS
- Managed database
```

**After:**
```
Full Stack Developer | Startup | 2022-2023
- Architected and shipped e-commerce platform for 50k users; designed PostgreSQL schema
  for 100k orders/day with sub-100ms query latency through careful indexing strategy
- Automated deployment pipeline using GitHub Actions + Docker; reduced deployment time 
  from 30min (error-prone manual process) to 5min, enabling 10x more frequent deploys
- Scaled API from handling 100 req/s to 1k req/s by implementing Redis caching and 
  database connection pooling; cost per request dropped 60%
```

---

## Resume Structure That Works

### Format

```
Name | Phone | Email | GitHub | LinkedIn
Location (or remote)

PROFESSIONAL SUMMARY (optional, 2-3 lines max)
[Only if it highlights systems thinking or unique angle. Otherwise skip.]

EXPERIENCE
[Company] | [Title] | [Start-End]
- [Impact statement 1: what + how + result]
- [Impact statement 2: quantified]
- [Impact statement 3: systems thinking]

[Repeat for each role]

PROJECTS (optional, include if non-obvious or impressive)
[Project name] | [Tech stack]
- [What you built + impact]

SKILLS
Languages: Python, Java, Go, etc.
Systems: SQL, Redis, Docker, Kubernetes, etc.
[Group by relevance, not comprehensive list]

EDUCATION
[University] | [Degree] | [Year]
[Only list if prestigious school or GPA >3.7; otherwise optional]
```

---

## What to Include / Exclude

### Include:
- ✓ Shipped projects with real users
- ✓ Quantified impact (metrics, numbers)
- ✓ Systems thinking (scaling, tradeoffs, design)
- ✓ Technical depth (optimization, algorithms)
- ✓ Leadership (owned something end-to-end)
- ✓ Companies/brands that are recognizable

### Exclude:
- ✗ GPA if <3.7
- ✗ Bootcamp (unless very relevant)
- ✗ High school anything
- ✗ Task descriptions ("participated in", "helped with")
- ✗ Generic skills (HTML, CSS, JavaScript)
- ✗ Coursework or certifications (irrelevant)
- ✗ Personal interest section
- ✗ Objective statement ("Seeking SDE role...")

---

## Impact Statement Formula

**[What I did] + [Why it mattered] + [The result]**

**Template:**
```
[Action verb] [what you built] [technical approach/constraint];
[why it mattered / business impact] [metric showing improvement]
```

**Example:**
```
"Redesigned user feed ranking algorithm using collaborative filtering;
improved content relevance and time-on-app by 15% for 100M users"
```

---

## Metrics That Impress FAANG

**Performance:**
- Latency: "500ms → 100ms"
- Throughput: "1k req/s → 10k req/s"
- Resource efficiency: "10GB memory → 2GB"

**Scale:**
- Users: "1k → 100k"
- Data: "1GB → 10TB"
- Requests: "100 req/s → 100k req/s"

**Reliability:**
- Uptime: "99.5% → 99.99%"
- Bug reduction: "50 bugs/qtr → 5 bugs/qtr"
- Incidents: "10 SEVs/year → 1 SEV/year"

**Business:**
- Revenue impact: "Enabling $5M revenue"
- Cost reduction: "Saved $500k/year in infrastructure"
- Time: "Ship in 2 weeks vs 6 weeks"

**Always quantify when possible.**

---

## Company-Specific Resume Strategies

### For Google:
**Highlight:** Technical depth, novel algorithms, optimization
- "Implemented O(log n) search algorithm"
- "Wrote paper on distributed consensus"
- "Optimized critical path by 3x through clever caching"

### For Amazon:
**Highlight:** Ownership, bias for action, operational excellence
- "Owned entire feature from design to deployment"
- "Shipped feature in 2 weeks despite ambiguity"
- "Drove operational metric from X to Y"

### For Meta:
**Highlight:** Scale, move-fast culture, user impact
- "Scaled system to 10M DAU"
- "Shipped MVP in 1 week, iterated 3x based on user feedback"
- "Improved user engagement by 20%"

### For Apple:
**Highlight:** Quality, user experience, attention to detail
- "Zero production incidents"
- "Improved user experience metrics by X%"
- "Led quality initiative"

### For Netflix:
**Highlight:** Technical judgment, autonomy, impact
- "Owned decision on [technology choice], trade-offs were..."
- "Drove architectural decision independently"
- "Responsible for system's reliability and performance"

---

## Profile Optimization for Online Applications

### LinkedIn

**Headline:** (120 characters max)
- Bad: "Software Engineer at Google"
- Better: "Backend Engineer | Scaling systems for 100M+ users | Python, Go, Kubernetes"

**About section:** (2-3 sentences)
- State your focus areas (systems, infrastructure, ML, etc.)
- Mention a key achievement
- Invite questions/connections

**Experience:** Use same language as resume (quantified impact)

**Skills:** Pin top 3-5 relevant skills

### GitHub Profile

**README:** Create a profile README with:
- [ ] What you work on
- [ ] Recent projects with links
- [ ] Tech stack
- [ ] How to reach you

**Pinned repositories:** (4-6 repos)
- [ ] Well-documented projects
- [ ] Show breadth or depth
- [ ] Include README with context

**Activity:** Keep it active (commits, contributions)

---

## Portfolio Website (Optional but Helpful)

If you build one, include:
- [ ] 2-3 standout projects
- [ ] Problem statement for each
- [ ] Technical architecture diagrams
- [ ] Links to live demo or GitHub
- [ ] Metrics/results
- [ ] What you learned

**Example project layout:**
1. Project name
2. Problem: "X needed [solution], but existing systems [limitation]"
3. Solution: "I built [what] using [tech] with [approach]"
4. Results: "Achieved [metric], enabling [impact]"
5. Learnings: "Key insight was..."
6. Code: Link to GitHub

---

## Common Mistakes to Avoid

❌ **Don't:**
1. **Submit generic resume to all companies**
   - Tailor bullets to company signals

2. **Mention technologies without context**
   - "Used Docker" → "Containerized app with Docker, reducing deployment time by 5x"

3. **Use action verbs without impact**
   - "Implemented" → "Implemented X resulting in Y improvement"

4. **List a million skills**
   - Pick top 8-10 most relevant ones

5. **Have grammar/spelling errors**
   - Proofread 3x

6. **Make it too long**
   - 1 page for junior, 1.5 pages for senior max

7. **Use same resume for FAANG and non-FAANG**
   - Tailor: Emphasize different signals

---

## Resume Checklist Before Submitting

- [ ] All roles: Quantified impact in each bullet
- [ ] No typos or grammar errors
- [ ] Companies and dates correct
- [ ] Accomplishments highlight systems thinking
- [ ] Metrics show scale or efficiency gain
- [ ] Tailor to company (if known)
- [ ] One page if <5 years experience, 1.5 pages if senior
- [ ] Contact info easy to find
- [ ] PDF formatting looks clean

---

## What Happens After Resume Screening

**If resume is strong:**
- Recruiter reach out within 1-2 weeks
- You'll get phone screen (usually 30 min)

**If resume doesn't stand out:**
- Might not hear back (unfortunately)
- Or: Alternative pathway (referral, networking)

**Strategy:** Strong resume + network = highest chance of phone screen

---

## Getting the Resume in Front of Recruiters

**Best channels (in order):**
1. Referral (friend at company) ← highest conversion
2. LinkedIn recruiter outreach
3. Apply on company careers page
4. RecruitingApp / internal job boards
5. Cold email to hiring manager (rarely works)

**Referral tip:** You don't need to know the person well. "I admire [company]'s [product]. I've [achievement]. Could you refer me?" often works.

