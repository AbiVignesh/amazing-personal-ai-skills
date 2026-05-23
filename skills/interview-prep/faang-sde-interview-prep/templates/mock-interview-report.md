# Mock Interview Report Template

Deliver honest, actionable feedback after each mock. Score and identify patterns.

---

## Mock Interview Summary

**Date:** [Date]
**Round Type:** [Coding / System Design / Behavioral / Full interview]
**Difficulty:** [Easy / Medium / Hard]
**Company Focused:** [Google / Amazon / Meta / etc. - optional]
**Duration:** [Minutes]
**Time Limit:** [X minutes]

---

## Score & Performance

**Overall Score:** ___ / 100

**Breakdown by Category:**
- Correctness: ___ / 25
- Code Quality: ___ / 20
- Communication: ___ / 20
- Problem-solving approach: ___ / 20
- Handling pressure: ___ / 15

**Interpretation:**
- 80-100: Would pass this round
- 70-79: Probably pass, some polish needed
- 60-69: Close, but needs improvement
- <60: Not ready yet for this difficulty

---

## What Went Well

✅ **Strengths:**

- [ ] Clear communication: Explained approach before coding
- [ ] Good time management: Finished with time to spare
- [ ] Edge case awareness: Identified and handled edge cases
- [ ] Code quality: Clean, readable code
- [ ] Optimization thinking: Found better approach
- [ ] Debugging: Found and fixed bugs quickly

**Specific examples:**
- "You broke down the problem well: subproblem A, then B"
- "You noticed the optimization when I asked: good thinking"
- "Your code was clean and well-named"

---

## What Broke

❌ **Primary Failure:**

**The Problem:** [What was the biggest issue?]

**Why it matters:** [How would this hurt in real interview?]

**Evidence:** [Where did you show this?]

---

## Detailed Feedback by Dimension

### Correctness (for coding)

- [ ] Solution solves the problem
- [ ] Handles edge cases (null, empty, large)
- [ ] Time complexity is good (not N^3 when N^2 exists)
- [ ] Space complexity is reasonable

**What happened:**
[Describe: Did you get stuck? Wrong approach? Off-by-one error?]

**Specific issue:**
[Example: "Your loop condition was wrong: should be i < n, not i <= n"]

**How to fix:**
[Specific action: "Always write edge cases on whiteboard before coding"]

---

### Code Quality

- [ ] Readable variable names
- [ ] No unnecessary complexity
- [ ] Proper error handling
- [ ] No duplicate logic

**Assessment:**
[Was your code clean or clever? Did you use good style?]

---

### Communication

- [ ] Asked clarifying questions at start
- [ ] Explained approach before coding
- [ ] Thought out loud while coding
- [ ] Discussed tradeoffs and alternatives
- [ ] Summarized at the end

**Assessment:**
[How clear was your communication? Did interviewer understand you?]

**Specific feedback:**
[Example: "You didn't explain your optimization. When you changed the algorithm, say why: 'This reduces time from O(n^2) to O(n log n) by...'"]

---

### Problem-Solving Approach

- [ ] Broke problem into subproblems
- [ ] Started with naive solution
- [ ] Identified bottleneck
- [ ] Optimized step-by-step
- [ ] Validated with examples

**Assessment:**
[Did you think strategically or just code?]

**Specific feedback:**
[Example: "You jumped to optimization without understanding the bottleneck. First identify: what's slow? Then optimize that."]

---

### Handling Pressure

- [ ] Stayed calm when stuck
- [ ] Recovered from mistakes quickly
- [ ] Handled interruptions well
- [ ] Didn't give up
- [ ] Adjusted approach when given hints

**Assessment:**
[Were you cool under pressure or did you panic?]

---

## If This Were Real

**Prediction: [Would you pass?]**

**Reasoning:**
[Be honest. "You'd pass this round but fail the next because X." or "You'd get rejected because Y."]

---

## Company-Specific Feedback

*If mock was company-specific:*

**[Company] Perspective:**

- [Company] values X: You showed this? [Yes / No / Partially]
- [Company] looks for Y: You demonstrated? [Yes / No]
- Red flag for [Company]: [What would concern them?]
- How to improve odds: [Specific action for company]

---

## Comparison to Previous Mocks

| Metric | Mock 1 | Mock 2 | Mock 3 | Trend |
|--------|--------|--------|--------|-------|
| Overall | ___ | ___ | ___ | ↑ / → / ↓ |
| Correctness | ___ | ___ | ___ | |
| Speed | ___ | ___ | ___ | |
| Communication | ___ | ___ | ___ | |

**Pattern:** [Are you improving? Stuck? Regressing?]

---

## Specific Recommendations

### For Next Week

**Priority 1: [Biggest weakness]**
- What to do: [Specific drill]
- Why: [Why this matters most]
- How: [How to practice]
- Success metric: [How you know you've improved]

Example:
- What: "Do 10 similar problems from the same pattern"
- Why: "You struggled with graph traversal, need more reps"
- How: "Solve on LeetCode, time yourself, compare to solution"
- Metric: "Can solve medium graph problem in 30 min"

**Priority 2: [Second weakness]**
- ...

**Priority 3: [Third weakness]**
- ...

### For Next Mock

- **Difficulty:** [Keep same / Increase / Decrease]
- **Focus:** [Practice what to emphasize next time]
- **When:** [Schedule the next mock]

---

## Code Review (if coding round)

**Example issue:**

```python
# What you wrote:
for i in range(len(arr)):  # ← Off by one? Comment why
    if arr[i] > 0:
        result += 1

# Better:
for i in range(len(arr)):  # ← Always explain logic
    # Skip negative numbers, count positives
    if arr[i] > 0:
        result += 1

# Even better (interview level):
for i in range(len(arr)):
    # Edge case: Handle arr[i] == 0? (Yes/No - state clearly)
    if arr[i] > 0:
        result += 1
```

---

## Common Patterns in Your Performance

**If consistently slow:**
- You might be overthinking or not recognizing patterns
- Fix: Do speed drills (10 problems in 2 hours)

**If consistently wrong:**
- Edge cases or implementation bugs
- Fix: Write test cases before coding

**If communication is bad:**
- You might understand but can't explain
- Fix: Record and listen to yourself, practice

**If freezing when stuck:**
- Confidence issue or truly don't know approach
- Fix: Mocks to build confidence, more drilling

---

## Self-Assessment

Ask yourself:

1. **Did I understand the problem?** Yes / No / Sort of
2. **Did I communicate my approach?** Yes / No
3. **Was my code correct?** Yes / No / Partial
4. **Am I faster than last time?** Yes / No / Same
5. **What surprised me?** [Answer]
6. **What would I do differently?** [Answer]

---

## Next Steps

1. **This week:** [Do Priority 1 drill]
2. **Next mock:** [Schedule for date]
3. **Track:** [Measure improvement on Priority 1]

---

## Brutal Honesty

**Real Talk:**

[This is where you give the hard truths.]

Examples:
- "You're not ready for Google yet. Your DSA is weak. Spend 4 weeks drilling before re-interviewing."
- "Your communication is hurting you. Listen to yourself on recording—you ramble. Fix this first."
- "You're close. Just need to be faster. Do speed drills next week."
- "You're ready. Go apply."

---

## Resources for Improvement

**For this weakness:**
- [Specific LeetCode problem set]
- [Specific video / blog]
- [Specific practice drill]

