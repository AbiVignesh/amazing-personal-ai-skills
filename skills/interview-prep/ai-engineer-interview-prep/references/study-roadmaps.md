# Study Roadmaps for AI Engineer Interview Prep

Choose based on your current level and time available. These are concrete, shipped-focused.

---

## 4-Week Crash Course (Target: Get Interview-Ready)

**For:** Level 2 candidates or Level 3 with specific gaps. Time commitment: 50-60 hours.

**Assumption:** You have shipped at least one project and understand basic ML.

### Week 1: Foundations + Your Strongest Area

**Goal:** Be dangerous in one domain, passable in others.

**Daily (Mon-Fri): 2-3 hours**

- **Mon-Tue:** Review transformers deeply. Read/re-read:
  - "Attention Is All You Need" paper
  - Understand why self-attention > RNN (compute parallelization, long dependencies)
  - Code up attention from scratch (not using PyTorch's built-in)
  
- **Wed-Fri:** Pick your strongest area:
  - *Option A (Inference):* FlashAttention, KV cache mechanics, quantization basics
  - *Option B (Training):* Distributed training (DDP, FSDP), gradient checkpointing
  - *Option C (RAG):* Retrieval ranking, chunking strategies, hallucination patterns
  
  - Read 1-2 papers + code a simple implementation
  - Example: If RAG, implement a basic retriever + ranker

**Weekend:** Mock interview #1 (any topic). Get feedback. Identify biggest gap.

**Output:** 1 working implementation (attention, quant layer, ranker, etc.)

---

### Week 2: Depth in 2 Areas + Coding Drills

**Goal:** Credible in 2 areas. Clear coding under pressure.

**Daily (Mon-Fri): 2-3 hours**

- **Mon-Tue:** Deepest area from Week 1. Read papers, understand failure modes:
  - Can you explain tradeoffs? (not just features)
  - What breaks at scale?
  - Example questions (Week 2): "You have 100ms latency budget. What do you cut?"
  
- **Wed:** Second area (choose from: LLM design, systems, agents):
  - Focus on tradeoffs, not breadth
  - 1 paper + implementation
  
- **Thu-Fri:** Coding drills (90 min each day):
  - Efficient attention implementation (hand-code, no PyTorch tricks)
  - Batching logic with variable lengths
  - Simple ranking algorithm (reranking with cosine similarity)
  - Use `templates/coding-questions.md` (not yet created; will provide concrete examples)

**Weekend:** Mock interview #2 (ML systems design). Time yourself.

**Output:** Coded + debugged implementations. Faster coding (45 min for a working solution).

---

### Week 3: Company-Specific Prep + Mock Interviews

**Goal:** Target your top 2-3 companies. Get real interview feel.

**Daily (Mon-Fri): 2-3 hours**

- **Mon:** Pick target company. Read `company-profiles.md`. Understand:
  - What signals matter for hiring
  - Interview format
  - Real questions (ask on company blogs, look at Blind/Levels.fyi)
  
- **Tue-Wed:** Company-specific deep dive:
  - If Anthropic: Study reasoning traces, hallucination mitigation
  - If OpenAI: Inference speed/scale tradeoffs
  - If DeepMind: Distributed training, research thinking
  - If Perplexity: Search + ranking + speed
  
  - Read/build something company-specific
  
- **Thu-Fri:** Full mock interviews (90 min each)
  - Mock 1: Coding from company question bank
  - Mock 2: ML systems design (company-relevant)
  - Time yourself. Record if possible (hearing yourself helps).

**Weekend:** Write detailed mock feedback (use `templates/mock-interview-report.md`). Identify patterns.

**Output:** 2 full mocks done. Honest assessment of what you'd fail on.

---

### Week 4: Final Polish + Last Mocks

**Goal:** Tighten weaknesses. Feel ready.

**Daily (Mon-Fri): 1.5-2 hours**

- **Mon-Tue:** Attack your biggest interview weakness:
  - If it's coding speed: Do 3 more coding drills
  - If it's systems thinking: Walk through a complex system end-to-end
  - If it's communication: Practice explanations out loud
  
- **Wed:** Resume/portfolio review:
  - Does it tell a coherent story?
  - Do the projects show progression, not just busyness?
  - Can you explain each project in 2 minutes, highlighting signal?
  
- **Thu-Fri:** Final 2 full mocks:
  - Mock 1: Your weakest area
  - Mock 2: Mixed (coding + design)

**Weekend:** Apply aggressively. You're ready.

**Output:** 4+ full mocks done. Sense of where you stand.

---

## 8-Week Deep Dive (Target: Compete with Strong Candidates)

**For:** Level 2 candidates wanting to be competitive. Time commitment: 80-100 hours.

**Weeks 1-2:** Foundations + Depth

- Transformers (detailed): Positional encoding, multi-head attention mechanics, why it scales
- LLMs: GPT-2/3 architecture, scaling laws, why larger models generalize
- Implement from scratch: Attention layer + simple transformer
- Papers: "Attention Is All You Need", "Language Models Are Unsupervised Multitask Learners"

**Weeks 3-4:** Two Deep Areas + Early Mocks

Choose 2 from:
- Inference optimization (quantization, KV cache, speculative decoding)
- Training at scale (distributed training, gradient checkpointing, FSDP)
- RAG systems (retrieval, reranking, hallucination)
- Agents (planning, tool use, error recovery)

For each:
- Read 3-4 papers
- Code a working implementation
- Understand failure modes deeply
- Mock interviews on each topic (Week 4)

**Weeks 5-6:** Systems + Product Thinking

- Systems design: Inference serving, training infrastructure, eval systems
- Product thinking: Tradeoff analysis, user constraints, business metrics
- Full mock interviews (ML systems design)
- Build a small project that integrates multiple concepts

**Weeks 7-8:** Company-Specific Prep + Interviews

- Weeks 7: Pick 2-3 target companies. Deep prep.
- Week 8: Final mocks, resume polish, interview scheduling

**Milestones:**
- Week 2: Transformer implementation working
- Week 4: 4 full mocks done, patterns clear
- Week 6: 1 integration project shipped
- Week 8: Interviewing at target companies

---

## 12-Week Mastery (Target: Stand Out, Multiple Offers)

**For:** Level 2-3 candidates wanting to dominate. Time commitment: 150-180 hours.

### Month 1: Breadth + Depth Foundation

- **Week 1-2:** Transformers, attention, scaling laws (deep dive)
- **Week 3-4:** LLMs + foundation models (study GPT-2/3/4 architecture, understand the full pipeline)
- **Output:** Transformer and small LLM implemented from scratch

### Month 2: Four Deep Areas

Choose 4 areas. Spend 2 weeks per area:

1. **Inference Optimization** (Weeks 5-6)
   - Quantization (INT8, FP8, dynamic, static)
   - KV cache, FlashAttention, Paged Attention
   - Speculative decoding, draft models
   - Papers: FlashAttention v1/v2, Paged Attention, Speculative Decoding
   - Build: Quantized inference system, batching engine

2. **Distributed Training** (Weeks 7-8)
   - Data parallelism, model parallelism, pipeline parallelism
   - Gradient accumulation, communication overlaps
   - FSDP, DeepSpeed
   - Papers: Megatron-LM, ZeRO, FSDP docs
   - Build: Distributed training script on multi-GPU setup

3. **RAG + Retrieval Systems** (Weeks 9-10)
   - Embedding models, vector similarity search
   - Reranking, ranking loss functions
   - Chunk strategies, hybrid search
   - Hallucination detection + mitigation
   - Papers: RAG paper, ColBERT, BGE-M3
   - Build: RAG system with reranking, eval framework

4. **Agents + Tool Use** (Weeks 11-12)
   - Function calling, tool binding
   - Planning algorithms (chain-of-thought, tree-of-thought)
   - Error recovery, retries
   - Cost + latency modeling
   - Build: Multi-step agent with real tools

### Month 3: Systems + Research + Company-Specific

- **Week 13-14:** Systems design deep dives
  - Inference serving at scale (1M concurrent users)
  - Training infrastructure
  - Evals and monitoring
  - Full system designs (5+ mocks)

- **Week 15:** Research thinking + paper reviews
  - Read 10+ recent papers (understand not just results but limitations)
  - Can you critique papers? Suggest next experiments?
  - Attend 1-2 lab seminars or reading groups

- **Week 16:** Company-specific deep prep
  - Pick 3-4 target companies
  - Study their tech blogs, papers, hiring signals
  - Build project that signals fit
  - Final interview preparation

**Milestones:**
- Week 2: Transformer + LLM implemented
- Week 4: First quantization/inference optimization working
- Week 8: Multi-GPU distributed training script
- Week 12: RAG system working
- Week 14: Agent system with tool use
- Week 16: 20+ mocks done, targeting specific companies

---

## Paper Reading Guide

**Essential (read 2-3 times, deeply):**
- Attention Is All You Need
- Language Models Are Unsupervised Multitask Learners (GPT-2)
- Language Models Few-Shot Learners (GPT-3)

**Inference Optimization (pick 3):**
- FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness
- Efficient Memory Management for Large Language Model Serving with PagedAttention
- Accelerating Large Language Model Decoding with Speculative Execution

**Distributed Training (pick 2):**
- Megatron-LM: Training Multi-Billion Parameter Language Models
- ZeRO: Memory Optimizations Toward Training Trillion Parameter Models
- Fully Sharded Data Parallel (FSDP) paper

**RAG (pick 2):**
- Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks
- ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT
- Bge M3-Embedding: Multi-Lingual, Multi-Functionality, Multi-Granularity Text Embeddings

**Recent & Trendy (pick 3):**
- Chain-of-Thought Prompting Elicits Reasoning in Large Language Models
- Tree of Thoughts: Deliberate Problem Solving with LLMs
- Mixture of Experts: Recent Trends and Future Directions (if interested in scaling)

---

## Building Projects (Any Timeline)

Projects matter more than papers. Here's what to build:

**Project 1 (Inference):** Quantized inference system or batching engine
- Constraints: Latency budget, memory limit
- Evaluation: Speed, quality tradeoffs
- Difficulty: Medium
- Time: 3-4 weeks

**Project 2 (RAG):** End-to-end RAG system with reranking
- Constraints: Quality (eval framework), cost
- Build: Retriever + reranker + generator, eval
- Difficulty: Medium
- Time: 4 weeks

**Project 3 (Novel):** Something hard that combines multiple concepts
- Examples:
  - "Build an LLM agent that plans multi-step tasks reliably"
  - "Design a low-latency inference system that handles 1k concurrent users"
  - "Implement distributed training of a small LLM across 8 GPUs"
- Difficulty: Hard
- Time: 6-8 weeks

Ship real things. Not tutorials. Real things that solve problems or answer questions.
