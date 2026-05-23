# AI Engineer Skill Matrix & Assessment Framework

## Skill Levels

### Level 1: Foundational (Ready in 12+ weeks)
- Basic ML knowledge (gradient descent, backprop, neural networks)
- Comfortable in Python, knows one framework deeply
- Has done one or two small projects
- Understands transformers conceptually but not deeply
- No experience with systems optimization or inference

**Readiness for:** Entry-level roles, internships, junior roles at less competitive labs

### Level 2: Intermediate (Ready in 8 weeks)
- 1-2 years production ML/systems experience
- Shipped at least one meaningful project end-to-end
- Understands transformers, knows attention mechanics, has fine-tuned models
- Familiar with one optimization domain (quantization OR batching OR caching)
- Can reason about tradeoffs (latency vs accuracy, cost vs quality)

**Readiness for:** Mid-level roles, some labs' senior roles (Perplexity, ElevenLabs)

### Level 3: Advanced (Ready in 4 weeks)
- 3+ years with deep ML or systems experience
- Multiple shipped projects with measurable impact
- Deep knowledge in 2+ domains (inference optimization, training at scale, evals)
- Understands distributed systems, failure modes, scaling bottlenecks
- Can think through problems end-to-end with minimal guidance
- Has debugged complex production issues

**Readiness for:** Anthropic, OpenAI, DeepMind interviews

### Level 4: Expert (Niche specialists)
- Research-level depth in specific area (e.g., speculative decoding, mixture of experts)
- Published or shipped major contributions
- Can teach others in their domain
- Rare — most interview candidates are Level 2-3

**Readiness for:** Principal engineer roles, research roles, specialized opportunities

---

## Core Competencies Assessment

Score each 1-5 (1=novice, 5=expert). Identify gaps.

### ML Fundamentals
- [ ] Backpropagation and gradient flow: ___ 
- [ ] Loss functions, optimization, convergence: ___
- [ ] Regularization, overfitting, data quality: ___
- [ ] **Evaluation:** Can you debug a model that's not converging? Do you know why?

### Transformers & Large Language Models
- [ ] Attention mechanisms (self, cross, multi-head): ___
- [ ] Positional encoding, sequence length trade-offs: ___
- [ ] Transformers architecture end-to-end: ___
- [ ] Why transformers scale better than RNNs: ___
- [ ] **Evaluation:** Can you explain why you'd use multi-query attention instead of standard attention?

### Fine-tuning & Adaptation
- [ ] LoRA, QLoRA, full tune trade-offs: ___
- [ ] Instruction tuning, RLHF mechanics: ___
- [ ] Data selection strategies: ___
- [ ] Eval design for fine-tuned models: ___
- [ ] **Evaluation:** When would you NOT fine-tune? What's the threshold?

### Inference Optimization
- [ ] Quantization (INT8, FP8, dynamic vs static): ___
- [ ] KV cache, paged attention, flash attention: ___
- [ ] Batching strategies, token budget planning: ___
- [ ] Speculative decoding, draft models: ___
- [ ] **Evaluation:** You have 100ms latency budget and need 80% throughput. What do you optimize?

### RAG & Retrieval
- [ ] Embedding models, vector similarity search: ___
- [ ] Reranking, ranking loss functions: ___
- [ ] Hallucination detection and mitigation: ___
- [ ] Retrieval-augmented generation pipeline: ___
- [ ] **Evaluation:** Why does naive RAG often fail? What signals tell you it's broken?

### Agents & Tool Use
- [ ] Function calling, tool binding, MCP: ___
- [ ] Planning and reasoning with tools: ___
- [ ] Error recovery, retries, fallbacks: ___
- [ ] Cost and latency of multi-step inference: ___
- [ ] **Evaluation:** Design an agent that reliably completes 10-step tasks. What breaks?

### Distributed Systems for AI
- [ ] Data parallelism, model parallelism, pipeline parallelism: ___
- [ ] Gradient accumulation, all-reduce communication: ___
- [ ] Distributed training scaling laws (throughput, communication overhead): ___
- [ ] Checkpointing, recovery, distributed debugging: ___
- [ ] **Evaluation:** You're training on 8 GPUs and seeing 40% efficiency. Diagnose the bottleneck.

### Systems Thinking & Tradeoffs
- [ ] Latency vs throughput vs cost trade-offs: ___
- [ ] Identifying bottlenecks in complex pipelines: ___
- [ ] Scaling thinking (linear, polynomial, diminishing returns): ___
- [ ] Failure mode analysis, reliability planning: ___
- [ ] **Evaluation:** Design a system where you INCREASE latency to reduce total cost. When is this right?

### Production & DevOps
- [ ] Monitoring, metrics, observability: ___
- [ ] Version control for models and data: ___
- [ ] A/B testing, rollouts, canary deploys: ___
- [ ] Cost modeling, ROI, business constraints: ___
- [ ] **Evaluation:** Your model is 2% more accurate but 50% slower. What information do you need before shipping?

### Coding Under Pressure
- [ ] Algorithm design speed: ___
- [ ] Bug-free code first pass (not perfect, but correct): ___
- [ ] Communicating while coding: ___
- [ ] Testing edge cases, knowing when you're done: ___
- [ ] **Evaluation:** Can you write working code in 45 minutes while explaining your reasoning?

### Communication & Problem Framing
- [ ] Explain complex concepts to non-experts: ___
- [ ] Ask clarifying questions before diving in: ___
- [ ] Handle pushback and criticism: ___
- [ ] Defend design choices with reasoning: ___
- [ ] **Evaluation:** Pitch your current project in 5 minutes. Did you explain the why?

---

## Readiness Rubric

Use this to assess overall interview readiness:

| Dimension | Not Ready | Getting Close | Ready | Strong |
|-----------|-----------|---------------|-------|--------|
| **Technical Depth** | Knows facts, can't explain tradeoffs | Understands core concepts, gaps in systems thinking | Can reason through tradeoffs, knows failure modes | Can teach others, predicts second-order effects |
| **Shipping Signal** | No projects or only tutorials | 1 side project, unfinished | 1-2 shipped projects with real users/impact | 3+ projects, clear progression in complexity |
| **Pressure Performance** | Freezes or goes silent | Slow start, gets there eventually | Clear thinking, asks good questions | Thrives under pressure, improves as mock goes on |
| **Specific Depth** | Broad knowledge, no depth | Deep in 1 area OR basic in 3+ areas | Deep in 2+ areas, basic in others | Expert in 2+ areas, curious about gaps |
| **Growth Velocity** | Slow learning, repeats mistakes | Learning but hitting walls | Picks up new domains quickly | Masters new domains independently |
| **Fit for Company** | Unclear alignment with role | Basic qualifications | Strong fit, clear added value | Exceptional fit, can solve hard problems they care about |

### Readiness Decisions

**Early Stage (Months away, don't interview yet)**
- Level 1-2 candidates with multiple gaps
- Limited shipping signal
- Struggling with basic system design
- Action: Build projects, go deep in 1-2 areas

**Mid Stage (4-8 weeks, start applying)**
- Level 2-3 candidates
- 1-2 areas of genuine depth
- 2+ shipped projects
- Action: Do mocks, get company-specific prep

**Late Stage (Ready now, interview aggressively)**
- Level 3+ candidates
- 2+ areas of expert depth
- 3+ quality projects
- Clear pressure performance
- Action: Polish weaknesses, study company-specific patterns, practice mocks
