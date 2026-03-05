# 90-Day AI Engineer Sprint

> Senior Engineer → AI Engineer  
> Not a curriculum. A targeted upskilling sprint for a 30-year engineer who already thinks in systems.

**OS:** Windows 11 · WSL2 Ubuntu · **Stack:** TypeScript (10+ yrs) · C# (20+ yrs) · Python (learning) · **Target:** Day 75 → first applications · Day 90 → active pipeline

---

## Month-by-Month Breakdown

### Month 1 — Ecosystem Immersion (~90h)
*Python fluency + LLM internals + first real build*

#### Week 1 — ~20h · Python ML idioms + LLM API fundamentals
- Python data structures for ML
- NumPy / Pandas basics (chapters 4–5 only)
- Anthropic + OpenAI SDK (Python & TS)
- Tokens, context, temperature, streaming responses
- Read LangChain docs — map to what you know

🔨 **Build:** first API call — something real, not hello world

**Resources:** Full Stack LLM Bootcamp (Berkeley, free) · Anthropic Python SDK Quickstart · DeepLearning.AI — ChatGPT Prompt Engineering for Devs · Python for Data Analysis — Wes McKinney (ch 4–5)

---

#### Week 2 — ~20h · Embeddings, vector search, RAG theory
- Embeddings as concept + cosine similarity
- pgvector (you know Postgres already)
- Pinecone / Weaviate overview
- Chunking strategies

🔨 **Build:** embed a small corpus, run similarity search

**Resources:** DeepLearning.AI — Building Systems with the ChatGPT API · DeepLearning.AI — LangChain for LLM Application Dev · Pinecone Quickstart + pgvector README · "Chunking strategies for LLM apps" — Pinecone blog (required)

---

#### Week 3 — ~25h · First real RAG system end to end
- Retrieval pipeline design
- Reranking basics
- LangChain / LlamaIndex hands-on

🔨 **Build:** RAG over a real doc set  
🚀 **Ship:** working demo with UI

**Resources:** DeepLearning.AI — Advanced Retrieval for AI with Chroma · Vercel AI SDK — streaming RAG responses

---

#### Week 3+ — ~21h · Enterprise RAG port (P1-CS)
- Provision Azure OpenAI + AI Search
- Semantic Kernel NuGet setup
- Port chunking → Azure AI Search index
- RAG pipeline via SK plugins
- Hybrid search (vector + keyword)
- ASP.NET Minimal API + Swagger

🔨 **Build:** P1 vs P1-CS comparison README  
🚀 **Ship:** 2nd pinned repo — enterprise portfolio piece

---

#### Week 4 — ~25h · Prompt engineering depth + basic evals
- System prompt architecture
- Few-shot, chain-of-thought, structured outputs
- JSON mode / function calling
- Intro to evals: what does "good" mean?

🔨 **Build:** eval harness for your RAG system

**Resources:** Anthropic Prompt Engineering Guide (full read) · DeepLearning.AI — Building and Evaluating Advanced RAG · RAGAS docs

---

**Month 1 skills acquired:** Python ML idioms · LLM APIs (Py + TS) · Embeddings · Vector DBs · RAG pipelines · Prompt engineering · Basic evals · LangChain / LlamaIndex · Semantic Kernel (C#) · Azure OpenAI · Azure AI Search

**Month 1 deliverable:** Two production-quality RAG systems — one in TypeScript (P1) and one in C#/Azure (P1-CS) — with a comparison README that articulates when to choose each stack. Eval harness runs in CI on the TS version.

---

### Month 2 — Agents, Production & Depth (~90h)
*Multi-step agents · observability · production patterns · flagship project*

#### Week 5 — ~20h · Agent architectures — formal patterns
- ReAct pattern (Yao et al. paper — required reading)
- Tool use / function calling in depth
- Memory types: in-context, external, episodic
- Planning strategies

🔨 **Build:** single agent with 3+ tools

**Resources:** ReAct paper (arXiv:2210.03629) · DeepLearning.AI — Functions, Tools and Agents with LangChain · Anthropic tool use docs

---

#### Week 6 — ~20h · Multi-agent systems + observability
- Orchestrator / specialist patterns
- Agent handoffs + routing
- LangSmith / Langfuse tracing
- Failure modes & recovery

🔨 **Build:** 2-agent orchestration system

**Resources:** LangGraph docs · Langfuse quickstart · DeepLearning.AI — Multi AI Agent Systems with crewAI

---

#### Weeks 7–8 — ~50h · Flagship project
- Pick a problem you genuinely care about
- Full stack: TypeScript backend + UI
- RAG + agents + evals + observability
- Cost optimization + latency profiling
- Safety / guardrails layer

🔨 **Build:** production-grade AI system  
🚀 **Ship:** deployed, public, documented

**Resources:** Designing ML Systems — Chip Huyen (serving + monitoring chapters) · Langfuse cost dashboard · Vercel deployment docs

---

**Month 2 skills acquired:** ReAct agents · Multi-agent systems · LangSmith / Langfuse · Prompt versioning · Cost optimization · Guardrails · Production deployment · Evals in depth

**Month 2 deliverable:** A flagship project that is live, deployed, and documented. Not a demo — a real system with evals, tracing, and a write-up. This is what you lead with in every conversation and interview.

---

### Month 3 — Positioning, Direction & Go-to-Market (~80h)
*Specialise · sharpen the narrative · focused job search*

#### Week 9 — ~20h · Go deep on chosen direction
- Fine-tuning (LoRA / PEFT) if agents track
- MLOps pipelines (DVC, MLflow) if platform track
- Advanced RAG patterns if product track
- Read 3–5 relevant papers (skim first, then deep)

🔨 **Build:** direction-specific mini-project

---

#### Week 10 — ~20h · Narrative, portfolio & positioning
- Write a technical blog post about what you built
- Polish GitHub READMEs
- Craft your "AI Engineer" story (3 decades → AI)
- Update LinkedIn — AI Engineer framing

🚀 **Publish:** blog post + open source anything

---

#### Weeks 11–12 — ~40h · Active job search + interview prep
- Target 10–15 roles (AI-native startups first)
- Prep: system design for AI systems
- Prep: explain RAG, agents, evals from first principles
- Prep: Claude Code background as a narrative
- Keep building — don't stop during applications

🚀 **Apply:** send first 10 applications by Day 75

---

## What You Have by Day 90

| | |
|---|---|
| Full LLM/agent stack | ✅ |
| 2+ shipped projects | ✅ |
| Evals & observability | ✅ |
| Technical writing | ✅ |
| Direction specialisation | ✅ |
| Interview-ready narrative | ✅ |
| Active pipeline | ✅ |

**Day 90 position:** A senior engineer with a compelling AI portfolio spanning two ecosystems (TypeScript + C#/Azure), a clear specialisation narrative, and active applications in flight. 30 years of engineering context is a *feature* — most AI Engineer candidates can't think in systems at this level.

---

## Language, Cloud & LLM Platform Strategy

### Language Stack

Windows + WSL2 gives you the best of both worlds — native C#/.NET and Azure tooling on Windows, full Unix Python/ML environment in WSL2 Ubuntu. TypeScript is your primary production language and runs comfortably in either context.

| Language | Status | Notes |
|---|---|---|
| **TypeScript** | Primary | Vercel AI SDK, Anthropic SDK — all excellent. Build P1–P3 and capstone. 10+ years is a competitive advantage most AI Engineer candidates don't have. |
| **Python** | Learn | Runs exclusively in WSL2 Ubuntu — pyenv 2.6.25 and Python 3.12.3 already installed and confirmed. Never use native Windows Python for ML work. |
| **C# / .NET** | Azure Primary | Semantic Kernel is C#-native. Runs natively on Windows. Current Upwork client is already C#/Azure — this is live client work, not just sprint prep. 20+ years is a genuine differentiator. |

### Cloud Platform

| Platform | Priority | Notes |
|---|---|---|
| **Azure** | Primary | Azure OpenAI is how most enterprise companies deploy GPT-4 in production. C# + Semantic Kernel + Azure is a rare combination. 26% of AI engineer postings, skewed toward senior enterprise roles. Target: AI-102 cert. |
| **AWS** | Secondary | 32.9% of job postings — the broadest market. Know enough to be conversant: SageMaker, Bedrock, core IAM. Skills transfer directly from Azure. |
| **GCP** | Deprioritised | Vertex AI is genuinely strong but smaller pool, no C# leverage. Skip for now. |

### LLM Platforms

**Anthropic / Claude** — Primary reasoning engine. Sonnet for heavy lifting, Haiku for latency-sensitive paths in agent loops. Your Claude Code intuitions are a genuine edge.  
Models: `claude-sonnet-4-6` · `claude-haiku-4-5` (speed)

**OpenAI** — Fine-tuning + routing target. Best fine-tuning API for P4. Use `text-embedding-3-small` for all embeddings. Multi-model routing in P3 (Claude for reasoning, GPT-4o for speed) is a real production pattern worth demonstrating.  
Models: `gpt-4o` · `text-embedding-3-small` · fine-tuning API

**HuggingFace** — Open-source & fine-tuning internals. LoRA/QLoRA for P4. On Windows, use PyTorch + CUDA inside WSL2 — the RTX 5060 is CUDA-native and the entire PEFT ecosystem is built for it. Colab Pro (~£10/month) is the safety valve if 8GB VRAM hits a ceiling.  
Stack: `PEFT / LoRA` · `PyTorch + CUDA (WSL2)` · `RTX 5060 · 8GB VRAM`

> **Tooling decision:** Vercel AI SDK over LangChain as primary TS abstraction. LangChain has a reputation problem in senior engineering circles. Use the Vercel AI SDK (streaming, tool use, multi-model routing in one clean package) and raw Anthropic/OpenAI SDKs where it doesn't reach. "I used the SDK directly to understand the tool-use loop without framework magic" is a strong interview answer.

---

## Hardware & Environment — Confirmed Setup

> No new hardware needed. WSL2 Ubuntu 24.04 set up and confirmed — pyenv, Python 3.12, nvm, Node LTS all installed. VS Code with WSL extension connected. API keys in .env.local. Ready to start.

| Machine | Role | Spec |
|---|---|---|
| **Windows Laptop** | Primary | Intel CPU · RTX 5060 (8GB GDDR7 VRAM) · 32GB RAM · WSL2 Ubuntu for Python/ML · Windows native for C#/.NET/Azure/SQL Server |
| **MacBook Pro M1 Pro 16GB** | Side bet | Fresh macOS install, held in reserve. Free optionality. Ready to set up in an afternoon if needed. |
| **Google Colab Pro** | Safety valve | ~£10/month · A100 (40GB VRAM) · Subscribe at Day 55 when P4 starts. Don't pay for it during P1–P3. |
| **Mac Mini / MacBook M5 Pro** | Deferred | Decision held until P4 if RTX 5060 VRAM ceiling becomes a real blocker. By then M5 Pro will have clear specs. |

> **WSL2 boundary rule — non-negotiable:** All Python and ML work runs inside WSL2 Ubuntu. C#/.NET runs natively on Windows. TypeScript runs either side. Docker Desktop uses WSL2 backend. Crossing this boundary causes dependency conflicts — keep it clean.

---

## Direction Fork — Day 60

By Day 60 you'll have built real systems. Let the work tell you where to go.

| Direction | Focus | Signal |
|---|---|---|
| **Agents & Automation** | Multi-agent systems, autonomous workflows, tool orchestration | Claude Code background is most legible here. Cutting edge, directly relevant, high ceiling. |
| **Product & Integration** | Own AI features end-to-end at a product company | Full-stack + AI + 30yr judgment = rare. Startup-heavy, high ownership, fast feedback. |
| **Platform & Tooling** | Build the infra other AI engineers build on | C# + Azure angle is a genuine differentiator. Infrastructure focus, high leverage. |

---

## Sprint Resources

| Resource | Type | When | Notes |
|---|---|---|---|
| Full Stack LLM Bootcamp (Berkeley) | Course · Free | Week 1 | Full stack end-to-end — do in parallel |
| DeepLearning.AI Short Courses | Course · Paid | Ongoing | Pick 4–6 matching monthly focus. 1–2h each. |
| Designing ML Systems — Chip Huyen | Book | Month 2 | Read serving, monitoring, evals chapters |
| Vercel AI SDK | Framework | Day 1 | First-class TypeScript — streaming + tool use |
| Microsoft Semantic Kernel | Framework | Week 3+ | C#-native, enterprise-grade, underrated |
| LangSmith / Langfuse | Observability | Week 2+ | Add tracing from day 1 |
| ReAct, RAG, Attention papers | Papers | Month 2 | Skim for framing — vocabulary for interviews |
| TLDR AI / The Rundown | Newsletter | Daily | 5 min/day — non-negotiable during sprint |

---

## Certification Roadmap

**Don't cert before you build.** Projects, portfolio, and deployed systems carry more weight in AI Engineer hiring than any badge.

| Timing | Cert | Notes |
|---|---|---|
| Now → Day 90 | Sprint | Build. Ship. Azure hands-on is your cert prep — you just don't know it yet. |
| Month 4–5 | **Azure AI-102** | Primary cert. 4–6 weeks focused study on top of sprint experience. Sit while Azure is fresh. ~£165. |
| Month 6–9 | AWS MLA-C01 | Needs ~1yr hands-on AWS. Build that on the job. ~£240. |
| Year 2+ | Optional | AZ-305, Google ML Engineer, NVIDIA DLI — based on where the role takes you. |

### Azure AI Engineer Associate (AI-102) — Primary

The cert that most directly validates what you'll have built. The 2025 refresh shifted focus toward generative AI and agentic solutions — Azure OpenAI, AI Foundry, AI Search, RAG pipelines, responsible AI governance. Exactly the stack built across P1–P3. **C# exam option is a genuine edge over most candidates.**

**What it covers:** Azure OpenAI Service · Azure AI Search (RAG) · AI Foundry & Agents · Cognitive Services · Responsible AI · Vision, NLP, Speech

**Study path:** Microsoft Learn official AI-102 path (free) → Scott Duffy Udemy (~£15) → Whizlabs practice tests → `kennethleungty/Azure-AI-Engineer-Associate-Notes` (GitHub, free, passed first attempt)

### AWS ML Engineer Associate (MLA-C01) — Secondary

Replaces the retiring AWS ML Specialty (gone March 2026). Engineering-focused — validates ability to productionise ML workloads using SageMaker and AWS ML stack. Needs ~1yr hands-on AWS. Build that on the job.

### Certs to Skip

| Cert | Reason |
|---|---|
| ~~AWS ML Specialty MLS-C01~~ | Retiring March 31, 2026. Don't invest prep time. |
| ~~AWS AI Practitioner AIF-C01~~ | Aimed at business professionals. Below your level. Under-positioning on a senior engineer CV. |
| ~~Azure AI Fundamentals AI-900~~ | Foundational, non-technical. Go straight to AI-102. AI-900 is padding. |

> **Honest cert calculus:** A deployed GitHub project with Langfuse traces and a RAGAS eval suite opens more doors than any cert. AI-102 earns its place for breaking into a new domain without a track record. After that, let the job tell you which cert to chase next.

---

## Visual Timeline

```
Month 1 · Days 1–30    Python + APIs → Embeddings + RAG → Enterprise RAG port (P1-CS)
Month 2 · Days 31–60   Agents → Multi-agent → Flagship build & ship
Month 3 · Days 61–90   Specialisation → Narrative → Applications (Day 75+)
```

*Experience compression is real — a typical engineer spends Month 1 just getting Python comfortable. You'll clear that in Week 1 and be building by Week 2. The time savings go into deeper projects.*