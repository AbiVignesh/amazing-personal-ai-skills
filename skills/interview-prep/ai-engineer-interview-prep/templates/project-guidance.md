# Project Guidance & Portfolio Critique Template

Use this to help users build or evaluate projects for interview prep.

---

## Portfolio Assessment

### Current Portfolio

**Project 1:** [Title]
- **Status:** [Shipped / WIP / Abandoned]
- **Description:** [One sentence]
- **Impact/Signal:** [What does it demonstrate?]
- **Interview Value:** [Why does it matter to interviewers?]

**Project 2:** [Title]
- ...

**Project 3:** [Title]
- ...

---

## Portfolio Strength Assessment

**Interview Signal Strength: X / 10**

| Dimension | Score | Evidence |
|-----------|-------|----------|
| **Diversity** | ___ | Do projects cover different areas? |
| **Depth** | ___ | Is at least one project deep/ambitious? |
| **Shipping Signal** | ___ | Are they actually shipped? |
| **Problem Clarity** | ___ | Do you clearly state the problem you solved? |
| **Impact Communication** | ___ | Can you articulate the impact? |
| **Technical Depth** | ___ | Do they demonstrate systems thinking? |

**Weakest Dimension:** [What to fix first]

---

## Project Guidance: What to Build

### For Different Interview Targets

#### If targeting Anthropic (Reasoning + Safety thinking)

**Project Idea 1: Evaluation Framework for a Reasoning System**
- Build an eval suite for a system (reasoning, summarization, RAG, etc.)
- Demonstrate: Test design, metric thinking, failure analysis
- Difficulty: Medium
- Timeline: 3-4 weeks
- Impact: Shows you understand how to validate AI systems (core Anthropic concern)

**Project Idea 2: Hallucination Detection System**
- Build a system that detects when an LLM hallucinates
- Could use: Retrieved facts vs model output, semantic consistency, etc.
- Demonstrate: Understanding of failure modes, system design
- Difficulty: Medium-Hard
- Timeline: 4-5 weeks

---

#### If targeting OpenAI (Inference Speed + Scale)

**Project Idea 1: Low-Latency Inference Engine**
- Optimize model serving for latency (batching, quantization, caching)
- Benchmark against baseline
- Demonstrate: Inference optimization, systems thinking, tradeoff analysis
- Difficulty: Medium
- Timeline: 3-4 weeks
- Impact: Directly signals OpenAI's core concern

**Project Idea 2: Distributed Inference System**
- Serve one model across multiple GPUs/nodes
- Handle concurrent requests
- Demonstrate: Systems architecture, multi-device thinking
- Difficulty: Hard
- Timeline: 6-8 weeks

---

#### If targeting DeepMind (Research + Systems)

**Project Idea 1: Distributed Training Implementation**
- Implement multi-GPU training (data parallelism, model parallelism, or both)
- Train on a real dataset
- Demonstrate: Distributed systems, training instability debugging, scaling thinking
- Difficulty: Hard
- Timeline: 5-6 weeks
- Impact: Shows you understand training infrastructure at scale

**Project Idea 2: Novel Architecture Experiment**
- Implement a recent paper or variation
- Run experiments, document findings
- Demonstrate: Research thinking, experimental rigor, curiosity
- Difficulty: Medium-Hard
- Timeline: 6-8 weeks

---

#### If targeting Perplexity (Search + Ranking + Speed)

**Project Idea 1: Ranking/Reranking System**
- Build a search + ranking pipeline
- Evaluate ranking quality with metrics
- Demonstrate: Information retrieval thinking, ranking tradeoffs, quality metrics
- Difficulty: Medium
- Timeline: 4-5 weeks
- Impact: Core skill for Perplexity

**Project Idea 2: Fast Search + Generation System**
- Retrieve relevant documents + generate answer with latency budget
- Demonstrate: Full-stack thinking, latency awareness, multi-stage optimization
- Difficulty: Medium-Hard
- Timeline: 5-6 weeks

---

#### If targeting ElevenLabs (Real-time + Audio)

**Project Idea 1: Low-Latency Audio Processing**
- Stream audio processing with sub-100ms latency
- Could be: simple effects, feature extraction, etc.
- Demonstrate: Real-time thinking, streaming architecture, latency budget
- Difficulty: Medium
- Timeline: 3-4 weeks
- Impact: Directly relevant to ElevenLabs

**Project Idea 2: End-to-End Streaming System**
- Ingest streaming audio → process → output (voice effect, transcription, etc.)
- Demonstrate: Streaming systems, real-world constraints, audio basics
- Difficulty: Medium
- Timeline: 4-5 weeks

---

### Generic High-Impact Projects (Any Company)

1. **Build & Ship a Real RAG System**
   - Retriever + reranker + generator
   - Eval framework (quality, latency, cost)
   - Impact: Demonstrates full-stack LLM systems thinking
   - Difficulty: Medium
   - Timeline: 4-5 weeks

2. **Fine-tuned Model for a Real Problem**
   - Fine-tune an open LLM on a domain
   - Compare fine-tune vs prompt engineering vs RAG
   - Document tradeoffs learned
   - Impact: Shows you understand adaptation, not just base models
   - Difficulty: Medium
   - Timeline: 3-4 weeks

3. **Inference Optimization Project**
   - Take a model, optimize for speed/memory/cost
   - Benchmark and document tradeoffs
   - Impact: Demonstrates systems thinking + pragmatism
   - Difficulty: Medium
   - Timeline: 3-4 weeks

4. **Production ML System**
   - Take an ML task, build end-to-end (data → train → serve → monitor)
   - Include monitoring, rollouts, A/B testing thinking
   - Impact: Shows you've thought about real-world constraints
   - Difficulty: Hard
   - Timeline: 6-8 weeks

---

## Project Quality Rubric

Use this to self-evaluate projects. Aim for 8+ across the board.

| Dimension | Score 1-10 | What This Looks Like | How to Improve |
|-----------|------------|-------------------|-----------------|
| **Clear Problem** | ___ | "I'm solving X because Y" is crystal clear | Add a 1-2 sentence problem statement |
| **Non-Trivial** | ___ | It's not a tutorial, not a toy | Add real constraints: latency, scale, cost |
| **Shipped** | ___ | Code is on GitHub, works, documented | Put it on GitHub with README |
| **Measured** | ___ | You have metrics showing impact | Add benchmarks, evals, comparisons |
| **Well-Communicated** | ___ | A smart person can understand it in 5 min | Add README with clear diagrams/explanations |
| **Technical Depth** | ___ | Shows systems thinking, not just copying | Explain tradeoff decisions you made |
| **Realistic Constraints** | ___ | Inspired by real-world problems | Mention actual constraints (latency, cost, scale) |
| **Learned Lessons** | ___ | You document what you learned | Write down 3-5 key takeaways |

**Projects should score 8+ on all dimensions to be interview-strong.**

---

## Resume/Portfolio Critique

### Current Resume Strengths

- [ ] Clear, shipping-focused
- [ ] Shows progression (small → medium → large projects)
- [ ] Quantifies impact ("reduced latency by 40%")
- [ ] Emphasizes tradeoffs and systems thinking

**What's Working:**
[List 2-3 strong elements]

---

### Resume Weaknesses

**Problem Areas:**
- [ ] Too focused on credentials (degrees, certifications)
- [ ] Mentions projects but not impact
- [ ] Uses jargon without demonstrating understanding
- [ ] Lists tasks instead of outcomes
- [ ] Too long or unclear

**Biggest Issue:** [The most important thing to fix]

---

### Resume Improvements

**Reframe These:**

**Before:** "Worked on ML team, did data preprocessing"
**After:** "Optimized data pipeline, reducing training time from 24h to 4h through batch balancing and preprocessing optimization"

---

**Before:** "Led implementation of transformer model"
**After:** "Implemented multi-GPU training of 7B parameter model on 8 GPUs, achieving 60% GPU efficiency through gradient checkpointing and overlap optimization"

---

**Before:** "Built RAG system for customer support"
**After:** "Built RAG system reducing customer support resolution time from 2h to 15min; designed retriever + reranker to balance latency (<500ms) vs quality (92% relevance)"

---

### Portfolio Website/README

**Strong Portfolio Signals:**
- [ ] Clear project descriptions (problem → solution → impact)
- [ ] Code is on GitHub with good READMEs
- [ ] Benchmark results / metrics shown
- [ ] Writeups explaining learning
- [ ] Links to live demos (if applicable)
- [ ] Blog posts explaining complex projects

**Common Weaknesses:**
- [ ] Projects described vaguely ("did ML stuff")
- [ ] Code is private or on incomplete repos
- [ ] No metrics or benchmarks
- [ ] Looks like a tutorial, not original work

---

## How to Position Projects in Interviews

### For Coding Questions

**Mention Project Experience:**
"I've optimized inference before. Here's what I learned about memory layout and cache efficiency. That's why I'd approach this problem..."

**Signals Interviewers Look For:**
- You've debugged real systems
- You know practical constraints
- You've learned from failure

---

### For Systems Design Questions

**Reference Your Projects:**
"In my last project, I faced a similar problem. We tried X, it failed because Y, so we switched to Z..."

**Signals:**
- You've shipped, not just theorized
- You understand tradeoffs
- You learn from mistakes

---

### For Product/Research Discussion

**Lead with Your Project:**
"I built a RAG system and learned that hallucination mostly happens when the retriever fails, not the generator..."

**Signals:**
- Systems thinking
- Empirical validation
- Clear communication

---

## Building Your Next Project (Step-by-Step)

### Step 1: Identify the Gap

**Your Assessment:** [Gap you want to address]
- What's weak: [Area]
- Why it matters: [For which companies/interviews]
- How a project helps: [What you'll learn]

---

### Step 2: Define the Problem

**Problem Statement:**
- What: [What are you building?]
- Why: [Why does this matter?]
- For whom: [Who benefits?]
- Constraints: [Latency, cost, scale, quality]

**Example:**
"Build a low-latency RAG system (latency <200ms, quality >85%) to serve 1k concurrent users efficiently. Constraint: Single GPU with 24GB memory."

---

### Step 3: Define Success

**Metrics:**
1. [Metric 1]: Target value
2. [Metric 2]: Target value
3. [Metric 3]: Target value

**Example:**
1. Latency: <200ms p95
2. Quality: >85% relevance
3. Cost: <$1 per 1k queries

---

### Step 4: Design & Build

**Phase 1 (Week 1-2):** Core functionality
- Rough implementation
- Baseline metrics

**Phase 2 (Week 3):** Optimization
- Address bottlenecks
- Improve metrics

**Phase 3 (Week 4-5):** Polish & Documentation
- Code cleanup
- README + writeup
- Final benchmarks

---

### Step 5: Communicate

**2-Minute Pitch:**
"I built [project]. The problem was [problem]. I solved it by [approach]. The results: [metrics]. The most interesting part: [learning]."

**5-Minute Deep Dive:**
- Problem & constraints
- Your approach
- Key technical decisions
- Results and tradeoffs
- What you learned

**Written Writeup (GitHub README):**
- Problem statement
- Architecture diagram
- Implementation notes
- Benchmark results
- Key learnings

---

## Portfolio Timeline

**For 4-week interview prep:**
- Don't start a new project
- Improve + showcase existing projects

**For 8-week interview prep:**
- Complete 1 new project (4-5 weeks) or improve existing ones

**For 12-week interview prep:**
- Complete 2-3 projects over the timeframe
- Month 1-2: First project
- Month 2-3: Second project (optional)

---

## Red Flags in Projects

❌ **Don't Do This:**

1. "Just followed a tutorial" - Signals: No original thinking
2. "Built with no constraints" - Signals: Doesn't understand real engineering
3. "No metrics" - Signals: Can't measure impact
4. "Can't explain tradeoffs" - Signals: Didn't think deeply
5. "Never shipped" - Signals: No follow-through

---

## Green Flags

✅ **Do This:**

1. Clear problem statement + constraints
2. Thoughtful architecture (can explain why)
3. Measured results (benchmarks, comparisons)
4. Learned lessons (write them down)
5. Code on GitHub with good documentation

---

## Portfolio Revision Checklist

- [ ] 2-3 shipped projects minimum
- [ ] Each project shows different signal (inference, training, RAG, agents, etc.)
- [ ] Clear problem + solution + impact for each
- [ ] Code is clean and documented
- [ ] Metrics/benchmarks included
- [ ] Can explain each project in 2 minutes
- [ ] Can articulate what you learned
- [ ] Links to code/blog/writeups
- [ ] Resume is updated

**Once all checked: You have interview-ready portfolio.**
