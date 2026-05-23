# Company-Specific Interview Profiles

Each lab hires for different signals and tests different things. Tailor your prep accordingly.

---

## Anthropic

**Hiring Signal:** Systems thinking + ability to work on hard, unsolved problems + clear communication

**What they value:**
- Deep reasoning ability, not just implementation
- Understanding safety + alignment implications of system design
- Ability to debug complex multi-component systems
- Evidence of shipping non-trivial projects
- Thoughtfulness about failure modes and edge cases

**What they DON'T care about:**
- Credentials (PhD is not required)
- Flashy optimization tricks without justification
- Generic ML knowledge without systems depth
- Resume length

**Interview Format:**
- 4-5 rounds (45-60 min each)
- Coding: Focus on correct, readable code first. Optimization comes after.
- ML Systems Design: Deep dives into RAG, reasoning, or inference systems
- Research + Product: "Here's a hard problem, think out loud"
- Culture fit: Do you think carefully? Can you change your mind?

**What to Study:**
- Constitutional AI, reasoning traces, chain-of-thought improvements
- How hallucination actually happens and mitigation strategies (not just "use RAG")
- Failure modes in long-form reasoning
- Your own project's failure modes in detail—know them cold
- Papers: Read 3-4 recent Anthropic papers and understand the systems thinking

**Red Flags (Will Eliminate You):**
- Can't explain why you made a choice
- Defensive when questioned
- "I don't know" without follow-up curiosity
- Premature optimization (clever code that sacrifices clarity)

**Company-Specific Questions:**
- "Design an evaluation framework for a reasoning model. What goes wrong?"
- "How would you detect when a model is hallucinating vs. reasoning?"
- "Walk through your biggest shipped project. What broke? What surprised you?"
- "Here's a research paper. How would you implement this? Where are the hard parts?"

---

## OpenAI

**Hiring Signal:** Can think at massive scale + execution speed + thrives in ambiguity

**What they value:**
- Inference speed/cost optimization (critical capability)
- Scaling thinking and systems architecture
- "Get it done fast and iterate" mindset
- Shipping velocity + pragmatism
- Understanding of GPU/hardware constraints

**What they DON'T care about:**
- Perfect code (it can be messy if it works fast)
- Academic rigor without practical application
- Analysis paralysis

**Interview Format:**
- 4-5 rounds (60 min each)
- Coding: Real inference/scaling problems. Speed matters.
- Systems Design: "Design a serving system for 1M concurrent users. Go."
- Product: "What's the biggest bottleneck? What would you attack?"
- Technical depth: Deep on one or two areas only

**What to Study:**
- Inference serving architectures (Triton, vLLM, etc.)
- Hardware: GPU memory, bandwidth, compute balance
- Quantization techniques and their tradeoffs
- Batching strategies and their impact on latency
- Build something that serves models fast. Ship it.
- Papers: Focus on inference optimization (FlashAttention, Paged Attention, etc.)

**Red Flags (Will Eliminate You):**
- "Let me think about it more"—they want fast thinking
- Overcomplicating solutions
- Not knowing GPU memory/bandwidth numbers (order of magnitude)
- No evidence of fast iteration

**Company-Specific Questions:**
- "Design an inference serving system. How do you handle variable batch sizes?"
- "You have a 70B model and 16GB of VRAM. How do you serve it? What's the latency?"
- "Walk me through how you'd optimize model loading time by 10x."
- "If you could add one feature to the model serving stack, what would it be?"

---

## Google DeepMind

**Hiring Signal:** Research-forward + can execute + systems grounding

**What they value:**
- Deep understanding of training at scale (multi-GPU, multi-node)
- Research intuition + ability to implement novel ideas
- Distributed systems thinking
- Papers read and understood deeply
- Evidence of research-quality work (even in projects)

**What they DON'T care about:**
- Non-research work (ops, infra, MLOps)
- Short-term shipping culture
- Implementation tricks without conceptual depth

**Interview Format:**
- 4-5 rounds, mixed technical + research discussion
- Coding: Less emphasized. Usually system design.
- Research Discussion: "Here's a paper. What's next? What's missing?"
- Systems Design: Training infrastructure, distributed algorithms
- Behavioral: "What's a problem you solved that surprised you?"

**What to Study:**
- Multi-GPU training: data parallelism, model parallelism, pipeline parallelism deeply
- Gradient accumulation, communication overlaps
- Training instability and solutions
- Research papers (read at least 5 recent papers on training, inference, or reasoning)
- Be able to critique papers: "What's the limitation? What would you do differently?"
- Your projects should have research flavor—novel idea, not just engineering

**Red Flags (Will Eliminate You):**
- Can't discuss papers at depth
- "I just followed the tutorial"
- No sense of what makes research impactful
- Can't think beyond the immediate problem

**Company-Specific Questions:**
- "Explain distributed training tradeoffs. When would you choose each approach?"
- "Design a training pipeline for a 1T parameter model."
- "Here's a research paper. What's the next experiment?"
- "What's the hardest technical problem you've debugged?"

---

## Perplexity AI

**Hiring Signal:** Product intuition + search/ranking thinking + inference speed optimization

**What they value:**
- Understanding ranking, relevance, and search quality
- Inference speed and cost (critical for their business model)
- Product sense: "What does the user need?"
- Full-stack thinking (search → ranking → generation → speed)
- Evidence of building consumer products

**What they DON'T care about:**
- Pure research
- Academic credentials
- Offline optimization

**Interview Format:**
- 4-5 rounds, product + technical mixed
- Coding: Often search/ranking related (sorting, indexing, etc.)
- Systems Design: "Design a search + generation system"
- Product: "How would you improve Perplexity's accuracy?"
- Speed: They often ask optimization under constraints

**What to Study:**
- Ranking algorithms, relevance metrics
- Search engines, retrieval basics
- Inference serving (they serve very fast)
- Product metrics for LLMs (accuracy, latency, cost, user satisfaction)
- RAG but with ranking focus
- Build a search product demo (even small)

**Red Flags (Will Eliminate You):**
- Can't explain search quality tradeoffs
- No product thinking ("speed is always good")
- Latency unaware
- Pure ML without business context

**Company-Specific Questions:**
- "Design a search + generation pipeline. How do you ensure quality?"
- "A ranking change improves accuracy by 2% but increases latency by 30ms. What's your decision?"
- "How would you evaluate if a search result is 'better'?"
- "Design a system to serve 10M daily users while keeping latency <100ms."

---

## ElevenLabs

**Hiring Signal:** Audio + inference systems, attention to real-world constraints, shipping

**What they value:**
- Understanding audio/speech (frequency, duration, quality tradeoffs)
- Real-time systems thinking (latency <100ms is critical)
- Inference optimization for edge/streaming
- Product sense for consumer use cases
- End-to-end project shipping

**What they DON'T care about:**
- Academia-only work
- Scale without real-time focus
- Complexity for complexity's sake

**Interview Format:**
- 3-4 rounds
- Coding: Often streaming/real-time problems
- Systems: "Design a low-latency synthesis system"
- Product: "How would you improve voice quality while staying fast?"
- Usually friendlier tone than Anthropic/OpenAI

**What to Study:**
- Audio processing basics (sample rate, bit depth, streaming)
- Real-time inference constraints
- Streaming architectures
- TTS/synthesis model design
- Latency budget thinking
- Build an audio project (even simple voice effect)

**Red Flags (Will Eliminate You):**
- Not aware of latency/real-time constraints
- "We can batch everything"
- Audio knowledge gaps (can't explain sample rate)

**Company-Specific Questions:**
- "Design a real-time voice synthesis system. What's your latency budget?"
- "Walk through your shipping timeline for [your project]. What took longest?"
- "How would you handle streaming input with variable chunk size?"

---

## Sarvam AI

**Hiring Signal:** Multilingual/localization thinking + pragmatism + building for India/Global South

**What they value:**
- Understanding multilingual challenges
- Pragmatic solutions (inference cost matters)
- Building for real constraints (limited infra, internet reliability)
- Product sense for emerging markets
- Evidence of shipping to diverse users

**What they DON'T care about:**
- Scaling thinking without efficiency
- "The US is the only market"
- Overengineering

**Interview Format:**
- 3-4 rounds, often more conversational
- Coding: Pragmatic, efficient solutions
- Systems: Real-world constraints (bandwidth, compute)
- Product: "How does your design work in India?"

**What to Study:**
- Multilingual model considerations
- Inference on limited hardware
- Mobile-first thinking
- Localization, not just translation
- Build something for Indian users/languages

**Red Flags (Will Eliminate You):**
- Dismissing markets outside US
- Not thinking about cost
- "It works on my laptop"

**Company-Specific Questions:**
- "How would you adapt an LLM for [Indian language]? What's hard?"
- "Design an inference system for mobile. Latency budget: 2 seconds."
- "What's the biggest bottleneck for LLMs in emerging markets?"

---

## Universal Red Flags (All Labs)

These will disqualify you at any top lab:

1. **Can't communicate.** Rambling answers, won't be concise, won't explain reasoning
2. **No projects.** Degrees and coursework don't count. Ship something.
3. **Can't handle feedback.** Defensive, dismissive, won't iterate
4. **Premature optimization.** Clever code without clear thinking first
5. **Don't know your own work.** "I followed a tutorial" for your main project
6. **Technology cargo cult.** Reciting facts without understanding
7. **No curiosity about gaps.** When asked something you don't know: "I have no idea" (bad) vs "I don't know, but here's how I'd figure it out" (good)

---

## Universal Green Flags (All Labs)

These make you competitive:

1. **Ship, ship, ship.** 3+ real projects, each with learned lessons
2. **Depth over breadth.** Deep in 2 areas > shallow in 10
3. **Explain your reasoning.** Clear communication about why, not just how
4. **Embrace constraints.** "Here are the tradeoffs I made and why"
5. **Know your failure modes.** "This approach breaks when X. Here's why."
6. **Ask great questions.** Shows you're thinking, not just implementing
7. **Curiosity about hard problems.** "I want to solve X because..."
8. **Iterate on feedback.** "That's a good point. Here's how I'd adjust..."
