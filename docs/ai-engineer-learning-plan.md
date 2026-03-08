# AI Engineer — 90-Day Learning Plan

> **Status:** Not started · **Duration:** 90 days / ~280h · **Pace:** 20h+ per week
> **Goal:** Deepen skills, then decide · **Repos:** 6 pinned · 2 ecosystems · **Start applying:** Day 75

---

## 00 · Your Gap Map

Five gap areas identified — four AI foundations plus enterprise Azure AI. The sprint is front-loaded to close foundations in Month 1, with Azure covered by the P1-CS port.

- **Python / ML idioms** — Closes: Week 1–2
- **LLM APIs & prompt engineering** — Closes: Week 1, 4
- **RAG & vector DBs** — Closes: Week 2–3
- **Agents & orchestration** — Closes: Week 5–7
- **Azure AI / Semantic Kernel** — Closes: Week 3 (P1-CS port)

---

## 01 · Daily Structure

| Time | Activity |
|------|----------|
| Morning · 1.5h | Course / reading theory |
| Midday · 1.5h | Coding / building hands-on |
| Evening · 0.5h | Docs, write-up, commit to GitHub ship |
| Weekend top-up | 6–8h to hit the 20h/week floor. Use for big builds & catch-up. |

---

## 02 · Week-by-Week Plan

### Month 1 — Ecosystem Immersion
*Python fluency · LLM internals · first real build · enterprise port. ~110h total.*

#### Wk 1 · ~20h · Python ML idioms + LLM API fundamentals

- Python data structures for ML
- NumPy / Pandas basics
- Anthropic + OpenAI SDK (Python & TS)
- Tokens, context, temperature
- Streaming responses
- Read LangChain docs
- 🔨 **Build:** First API call — something real, not hello world

**Resources:**

- `Course · Free` Full Stack LLM Bootcamp (Berkeley) — do this week 1 in parallel
- `Docs` Anthropic Python SDK Quickstart
- `Course · Short` DeepLearning.AI — ChatGPT Prompt Engineering for Devs
- `Reference` Python for Data Analysis — Wes McKinney (ch 4–5 only)

#### Wk 2 · ~20h · Embeddings, vector search, RAG theory

- Embeddings as concept + cosine similarity
- pgvector (you know Postgres already)
- Pinecone / Weaviate overview
- Chunking strategies
- 🔨 **Build:** Embed a small corpus, run similarity search

**Resources:**

- `Course · Short` DeepLearning.AI — Building Systems with the ChatGPT API
- `Course · Short` DeepLearning.AI — LangChain for LLM Application Dev
- `Docs` Pinecone Quickstart + pgvector README
- `Blog` "Chunking strategies for LLM apps" — Pinecone blog

#### Wk 3 · ~25h · First real RAG system — end to end

- Retrieval pipeline design
- Reranking basics
- LangChain / LlamaIndex hands-on
- 🔨 **Build:** RAG over a real doc set
- 🚀 **Ship:** working demo with UI

**Resources:**

- `Course · Short` DeepLearning.AI — Advanced Retrieval for AI with Chroma
- `Framework` Vercel AI SDK — streaming RAG responses (TS-first, fits your stack)
- `Docs` LlamaIndex — RAG from scratch guide
- `Reference` LangChain Expression Language (LCEL) docs

#### Wk 3+ · ~21h · Enterprise RAG port — P1-CS

- `Azure` Provision Azure OpenAI + AI Search resources
- `Azure` Semantic Kernel NuGet packages + hello world
- `Azure` Port P1 chunking logic → Azure AI Search index
- `Azure` RAG pipeline via Semantic Kernel plugins
- `Azure` Hybrid search (vector + keyword) — native to Azure AI Search
- `Azure` ASP.NET Minimal API + Swagger endpoint
- 🔨 **Build:** P1 vs P1-CS comparison table + decision framework
- 🚀 **Ship:** GitHub repo with architecture diagram README

**Resources:**

- `Framework` Microsoft Semantic Kernel — Getting Started (C#)
- `Docs` Azure AI Search — Create index + vector search quickstart
- `Docs` Azure OpenAI — Deployment + model management
- `Sample` Semantic Kernel RAG sample (GitHub: microsoft/semantic-kernel)

> Why this week exists. Same RAG architecture, enterprise stack. Your 20yr C# depth means this is a translation exercise — you already understand every concept from P1. This one repo unlocks the entire .NET + AI freelance niche where most AI engineers can't compete.

#### Wk 4 · ~25h · Prompt engineering depth + basic evals

- System prompt architecture
- Few-shot, chain-of-thought, structured outputs
- JSON mode / function calling
- Intro to evals: what does "good" mean?
- 🔨 **Build:** Eval harness for your RAG system

**Resources:**

- `Docs` Anthropic Prompt Engineering Guide (full read)
- `Course · Short` DeepLearning.AI — Evaluating & Debugging Generative AI
- `Tool` RAGAS — open-source RAG eval framework
- `Blog` Hamel Husain — "Your AI Product Needs Evals"

**Skills locked in:**

`Python ML idioms` · `LLM APIs (Py + TS)` · `Embeddings` · `Vector DBs` · `RAG pipelines` · `Prompt engineering` · `Basic evals` · `LangChain / LlamaIndex` · `Semantic Kernel (C#)` · `Azure OpenAI` · `Azure AI Search`

> **Deliverable —** Two production-quality RAG systems — one in TypeScript (P1), one in C# / Azure (P1-CS) — with a comparison README that articulates when to choose each stack. Both go on GitHub immediately. Eval harness runs in CI on the TS version. The C# version is your calling card for enterprise .NET clients.

### Month 2 — Agents, Production & Depth
*Multi-step agents · observability · production patterns · flagship project. ~90h total.*

#### Wk 5 · ~20h · Agent architectures — formal patterns

> *P2 (PR Review Agent) starts Day 20 and front-loads setup, tool-use wiring, and GitHub API integration — work that doesn't require deep agent theory. This week's formal study of ReAct, memory types, and planning strategies arrives mid-build (~Day 29) and applies directly to the P2 work already in progress.*

- ReAct pattern — reason + act loop
- Tool use / function calling in depth
- Memory types: in-context, episodic, semantic
- Planning agents vs reactive agents
- 🔨 **Build:** Build a simple ReAct agent from scratch (no framework)

**Resources:**

- `Paper` ReAct: Synergizing Reasoning and Acting in LLMs (Yao et al.)
- `Course · Short` DeepLearning.AI — AI Agents in LangGraph
- `Docs` Anthropic Tool Use guide + cookbook examples
- `Blog` Lilian Weng — "LLM Powered Autonomous Agents" (lilianweng.github.io)

#### Wk 6 · ~22h · Multi-agent systems + orchestration

- Orchestrator / subagent pattern
- LangGraph for stateful agents
- CrewAI overview
- Inter-agent communication
- 🔨 **Build:** Two-agent pipeline: planner + executor

**Resources:**

- `Course · Short` DeepLearning.AI — Multi AI Agent Systems with crewAI
- `Docs` LangGraph — state machines for agents
- `Blog` Anthropic — "Building Effective Agents" (anthropic.com/research)

#### Wk 7 · ~23h · Observability, tracing & cost control

- LangSmith / Langfuse setup
- Prompt versioning & A/B testing
- Latency profiling
- Token cost dashboards
- Guardrails / safety layers
- 🔨 **Build:** Add tracing to your Month 1 RAG system

**Resources:**

- `Tool` Langfuse — open-source LLM observability
- `Tool` LangSmith — LangChain's tracing platform
- `Book` Designing ML Systems — Chip Huyen (serving & monitoring chapters)

#### Wk 8 · ~25h · Flagship project — full system build

- Pick a problem you genuinely care about
- Full stack: FastAPI or TS backend + UI
- RAG + agents + evals + observability
- Safety / guardrails layer
- 🔨 **Build:** Production-grade AI system
- 🚀 **Ship:** deployed, public, documented

**Resources:**

- `Framework` Vercel AI SDK or FastAPI for backend
- `Hosting` Railway / Render for fast deploy
- `Template` Full-stack Next.js + Langchain template (GitHub)

**Skills locked in:**

`ReAct agents` · `Multi-agent systems` · `LangSmith / Langfuse` · `Prompt versioning` · `Cost optimization` · `Guardrails` · `Production deployment` · `Evals in depth`

> **Deliverable —** A flagship project that is live, deployed, and documented. Not a demo — a real system with evals, tracing, and a write-up. This is what you lead with in every conversation, interview, or proposal.

### Month 3 — Positioning, Direction & Go-to-Market
*Specialise · sharpen narrative · run a focused search — job or freelance. ~80h total.*

#### Wk 9 · ~20h · Go deep on your chosen direction

- Fine-tuning (LoRA / PEFT) if agents track
- MLOps pipelines (DVC, MLflow) if platform track
- Advanced RAG patterns if applied AI track
- 🔨 **Build:** Third project: niche-specific, positioned for market

**Resources:**

- `Course · Short` DeepLearning.AI — Finetuning LLMs (if agents track)
- `Course · Short` DeepLearning.AI — MLOps Specialisation intro (if platform track)

#### Wk 10 · ~20h · Narrative, portfolio & presence

- LinkedIn profile — AI engineer framing
- GitHub polish: READMEs, 6 pinned repos, architecture diagrams
- Write your story: from 30-yr engineer to AI engineer
- Upwork profile setup (if freelance track)
- `Azure` Enterprise .NET angle in Upwork profile — separate service offering

#### Wk 11–12 · ~40h · Active search — job applications or first freelance proposals

- Both tracks in parallel is valid — let the market decide
- Interview prep: system design + LLM-specific questions
- `Azure` Target both AI-native and enterprise .NET + AI postings
- 🔨 **Build:** Continue building — momentum matters
- 🚀 **Ship:** 10–15 full-time applications (if job track)
- 🚀 **Ship:** 10–15 Upwork proposals (if freelance track)

> **Deliverable —** A decision made with data: full-time, freelance, or both. A GitHub profile with 6 pinned repos spanning two ecosystems (TypeScript + C#/Azure). Active conversations in progress. Your C# / TypeScript depth positions you for both the modern AI market and the enterprise .NET niche — very few candidates credibly cover both.

---

## 03 · Resource Bank

### Full Stack LLM Bootcamp
`Course · Free` · *Week 1 — Priority*

Berkeley course. Covers the full LLM app stack end-to-end. Do this in Week 1 alongside your API exploration.

### DeepLearning.AI Short Courses
`Course Platform · Paid` · *Ongoing*

Pick 4–6 courses matching your month's focus. RAG, agents, evals, LangChain. 1–2h each — fit around building time.

### Designing ML Systems — Chip Huyen
`Book · Must Read` · *Month 2*

The production ML bible. Read serving, monitoring, and evals chapters in Month 2. Everything else is a bonus.

### Vercel AI SDK
`Framework · TS-First` · *Week 1 onwards*

First-class TypeScript. Build your Month 1 project with this. React + streaming + tool use — productive in hours given your TS depth.

### Azure AI Engineer Associate (AI-102)
`Certification · Target` · *Post-sprint*

Primary cert target. Month 4–5 post-sprint, once Azure AI hands-on is fresh. C# exam option is a genuine edge. P1-CS gives you real Azure AI Search + Azure OpenAI experience before you sit it.

### Microsoft Semantic Kernel
`Framework · C# Enterprise` · *Week 3+ (P1-CS)*

C#-native AI orchestration. Plugin architecture maps to LangChain concepts you'll already know. The enterprise alternative to LangChain — and your 20yr C# makes it natural territory.

### Azure AI Search
`Service · Azure` · *Week 3+ (P1-CS)*

Managed vector + keyword hybrid search. Enterprise-grade RAG infrastructure. Replaces pgvector in Azure environments. Native semantic ranking saves you building reranking yourself.

### Lilian Weng — LLM Powered Agents
`Blog · Essential` · *Before Wk 5*

The clearest conceptual overview of agent architectures. Read before Week 5. lilianweng.github.io

---

## 04 · Gap Closure Tracker

Revisit at the end of each month. Update status as gaps close.

- **Python / ML idioms** — Not started
- **LLM APIs & prompting** — Not started
- **RAG & vector DBs** — Not started
- **Agents & orchestration** — Not started
- **Azure AI / Semantic Kernel** — Not started
