# Interview Question Banks

Realistic questions organized by topic. Not textbook—these are patterns from real top-lab interviews.

---

## Coding Interview Questions

Not LeetCode. Real inference/systems problems.

### Easy (Warm-up, 20-30 min)

1. **Batch Processing**
   - Problem: You have variable-length sequences (lengths: 32, 64, 128, 256). Design a batching strategy that pads to length 256. What's the compute waste per batch?
   - Follow-up: How would you fix the waste? (Packing, dynamic batching)
   - Expected: Understands padding waste, thinks about efficiency

2. **KV Cache Indexing**
   - Problem: Implement efficient KV cache storage for a transformer during generation. You generate token-by-token, need to access only the relevant KV pairs for attention.
   - Constraints: Minimize memory reallocation
   - Follow-up: What if you have a batch of 32 sequences at different generation steps?
   - Expected: Understands memory layout, indexing strategy

3. **Attention Mask**
   - Problem: Implement a causal attention mask (for autoregressive generation). Given position i, which positions should it attend to?
   - Follow-up: How do you apply this mask during training vs inference?
   - Expected: Understands attention mechanics, masking efficiency

### Medium (45-60 min)

1. **Efficient Attention**
   - Problem: Implement FlashAttention (the concept, not production code). The goal: reduce memory I/O for attention computation.
   - Hint: Think about tiling and recomputation instead of storing intermediate values.
   - Follow-up: Why does this matter for inference? Training?
   - Expected: Understands memory bottlenecks, I/O-aware algorithm design

2. **Gradient Accumulation**
   - Problem: You want to train on batch size 256, but your GPU only fits batch 32. Design gradient accumulation.
   - Constraints: How many steps? When do you update weights?
   - Follow-up: What happens to the gradient magnitude? Learning rate?
   - Expected: Understands gradient scaling, effective batch size

3. **Speculative Decoding**
   - Problem: You have a fast draft model and a slow target model. Design speculative decoding to speed up generation while maintaining quality.
   - Hint: Generate multiple tokens with the draft, verify with target, accept/reject
   - Follow-up: What if the draft model is wrong? How do you handle rejection?
   - Expected: Understands multi-stage inference, probability mechanics

### Hard (60-90 min, with back-and-forth)

1. **Distributed Attention**
   - Problem: You're training a 1T parameter model on 8 nodes (64 GPUs). How do you compute attention efficiently across nodes?
   - Constraints: Minimize communication
   - Follow-up: Model parallelism vs pipeline parallelism tradeoff?
   - Expected: Understands distributed computing, communication bottlenecks

2. **Quantization-Aware Training**
   - Problem: You want to quantize a model to INT8 but maintain accuracy. Design the training process.
   - Hint: How do you simulate quantization during training?
   - Follow-up: What about activation quantization vs weight quantization?
   - Expected: Understands quantization mechanics, training implications

3. **Streaming Inference Engine**
   - Problem: Design an inference engine that handles streaming input (e.g., tokens from a user chat arrive one at a time). You need to batch multiple users' requests while maintaining low latency.
   - Constraints: <50ms latency, handle 1k concurrent users
   - Follow-up: How do you handle stragglers (users whose requests haven't arrived)?
   - Expected: Understands batching, scheduling, latency-throughput tradeoffs

---

## ML Systems Design Questions

The candidate designs a full system under constraints. 90-120 min.

### Inference Systems

1. **Serve a 70B Model**
   - Setup: You need to serve a 70B parameter model.
   - Constraints: Single GPU with 24GB memory, <100ms latency, handle 100 req/s
   - Design: How would you serve this?
   - Follow-ups:
     - Can you fit the model? (Hint: quantization, offloading)
     - How many concurrent users?
     - What if you had 8 GPUs instead?
   - Interviewer will push: "Latency increased. Why? What do you trade?"
   - Scoring: Understands tradeoffs, constraints, scaling reasoning

2. **Multi-Model Serving**
   - Setup: You need to serve 3 models (7B, 13B, 70B) with different SLAs
   - Constraints: 4 x 40GB GPUs, <50ms p50 latency, cost matters
   - Design: How do you allocate resources?
   - Follow-ups:
     - What if requests shift (suddenly 80% for 70B)?
     - How do you prioritize?
   - Scoring: Understands resource allocation, dynamic scheduling

3. **Sub-100ms RAG Latency**
   - Setup: User query → retrieve docs → rerank → generate answer
   - Constraints: <100ms total latency, 10M doc corpus
   - Design: How do you achieve this?
   - Follow-ups:
     - Where's the bottleneck? (Retrieval or generation?)
     - How many docs to retrieve?
   - Scoring: Systems thinking, bottleneck identification

### Training Systems

1. **Train a 1T Model**
   - Setup: 1 trillion parameter model, 8 GPU nodes (64 GPUs), train on 1 trillion tokens
   - Design: How do you split computation?
   - Questions:
     - Data vs model parallelism?
     - How many training steps?
     - Communication overhead?
   - Scoring: Understands distributed training, scaling laws

2. **Fault Tolerance in Distributed Training**
   - Setup: Training a 500B model on 32 GPUs. A GPU fails during training.
   - Design: How do you recover?
   - Questions:
     - How often do you checkpoint?
     - How much computation do you lose?
     - How would you detect failure?
   - Scoring: Systems thinking, failure modes

### Agent Systems

1. **Reliable Multi-Step Agent**
   - Setup: Design an agent that can plan and execute 5-10 step tasks reliably
   - Example: "Book a flight, then rent a car, then book a hotel"
   - Design: How do you structure the agent?
   - Questions:
     - What tools does it have?
     - How do you handle errors?
     - How do you prevent infinite loops?
   - Scoring: End-to-end thinking, error recovery

### Evaluation Systems

1. **Build an Evaluation Framework**
   - Setup: You have a fine-tuned model for summarization. How do you evaluate it?
   - Questions:
     - What metrics?
     - How many test examples?
     - How do you detect quality regressions?
   - Scoring: Understands evaluation, tradeoff thinking

---

## LLM Design & Fine-tuning Questions

60-90 min, focused on reasoning and tradeoffs.

### Fine-tuning Strategy

1. **Fine-tune vs Prompt Engineering**
   - Setup: You want to improve a model's performance on a domain-specific task.
   - Choose: Fine-tune or prompt engineering?
   - Questions:
     - What data do you have? (100 examples? 10k?)
     - Cost implications?
     - Latency?
   - Expected: Understands tradeoffs, data efficiency

2. **LoRA vs QLoRA vs Full Fine-tune**
   - Setup: Fine-tune a 70B model on a limited GPU (24GB).
   - Design: Which technique and why?
   - Questions:
     - How much data?
     - How many iterations?
     - How do you evaluate?
   - Expected: Understands parameter efficiency, quality tradeoffs

### Hallucination & Safety

1. **Detect Hallucination in Responses**
   - Setup: Your LLM hallucinates facts. How do you detect and mitigate?
   - Questions:
     - Can you detect it during generation?
     - Can you prevent it?
     - How do you test for it?
   - Expected: Understands hallucination patterns, mitigation

2. **RAG for Factuality**
   - Setup: Use RAG to ground model responses in documents.
   - Questions:
     - When to retrieve?
     - How many documents?
     - How do you handle conflicts (docs contradict)?
   - Expected: Understands RAG design, quality metrics

### Data & Training

1. **Data Selection for Fine-tuning**
   - Setup: You have 100k examples for a domain. Should you use all?
   - Design: How do you select training data?
   - Questions:
     - What if data is noisy?
     - How do you detect quality?
   - Expected: Understands data efficiency, curse of big data

2. **Instruction Tuning**
   - Setup: You want to make a model follow instructions better.
   - Design: How would you create training data and train?
   - Questions:
     - What kinds of instructions?
     - How many examples?
     - How do you evaluate?
   - Expected: Understands instruction tuning mechanics

---

## Distributed Training Questions

60-90 min.

1. **Data Parallelism Deep Dive**
   - Setup: Training on 8 GPUs with data parallelism.
   - Questions:
     - How do you synchronize gradients?
     - What's the communication cost?
     - How do you handle stragglers?
   - Expected: Understands all-reduce, communication bottlenecks

2. **Model Parallelism Strategy**
   - Setup: Model is too large for one GPU.
   - Questions:
     - Tensor parallelism vs pipeline parallelism?
     - When would you choose each?
     - Communication overhead?
   - Expected: Understands tradeoffs

3. **Gradient Checkpointing**
   - Setup: You're out of memory during training.
   - Questions:
     - How does checkpointing help?
     - What's the compute overhead?
     - When is it worth it?
   - Expected: Understands memory-compute tradeoff

---

## Product & Tradeoff Questions

45-60 min, often conversational.

1. **Latency vs Cost**
   - Setup: "We can reduce latency by 2x but increase cost by 5x. Do we do it?"
   - Expected: "Depends. What are the user constraints? Business constraints?"
   - Follow-up questions will push your reasoning

2. **Quality vs Speed**
   - Setup: "Our model takes 500ms and is 95% accurate. A faster model would be 200ms but 90% accurate."
   - Expected: Understand use cases, user tolerance, revenue impact

3. **Model Size vs Inference Cost**
   - Setup: "Should we use a 7B or 70B model?"
   - Expected: Depends on quality needs, latency, cost, user expectations

---

## Real Interview Advice for Each Question Type

### Coding
- **Communicate first.** Explain approach before coding.
- **Correct > clever.** Working code that's readable beats clever code that's buggy.
- **Edge cases.** Ask about them: "What about variable batch sizes? Empty sequences?"
- **Optimization.** Optimize for clarity first. If time, optimize for speed/memory.

### Systems Design
- **Draw diagrams.** Use ASCII art if needed. Helps clarify thinking.
- **Constraints first.** "What's the latency budget? Scale? Cost?"
- **Tradeoffs.** Every design choice has a cost. Explain the tradeoff you're making.
- **Failure modes.** "What happens if X fails? How do you recover?"
- **Iterate.** "I'd start with X. If that doesn't work, I'd try Y because..."

### LLM Design
- **Understand tradeoffs.** Not "what's best" but "best for what?"
- **Know your data.** Quality > quantity, usually.
- **Evaluation matters.** How do you know if it works?
- **Grounding + reasoning.** Combine RAG, reasoning, fine-tuning thoughtfully.

### Research Discussion
- **Read deeply, not broadly.** Know 3 papers cold > know 10 papers shallow.
- **Criticize thoughtfully.** "The paper does X well. But it doesn't address Y..."
- **Extensions.** "If I were extending this, I'd..."
- **Contextualize.** "This paper matters for X use case because..."
