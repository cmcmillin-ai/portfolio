# AI Engineer — Tech Stack Quick Reference

> Compiled from: Learning Plan · 90-Day Sprint · Project Arc  
> **Languages:** TS · Python · C# · **Cloud:** Azure primary / AWS secondary · **OS:** macOS (Apple Silicon)

---

## Status Legend

| Badge | Meaning |
|---|---|
| `PRIMARY` | Use throughout the sprint |
| `SECONDARY` | Know well, use where needed |
| `LEARN` | Acquire during sprint |
| `AZURE` | Enterprise track |
| `CERT` | Certification target |
| `AWARE` | Know it exists, don't deep-dive |
| `SKIP` | Explicitly deprioritised |

---

## 01 · Languages

### TypeScript — `PRIMARY`
10+ years depth. Primary language for P1, P2, P3 and the DevMind capstone. Vercel AI SDK, Anthropic SDK, LangChain.js all first-class. Competitive advantage vs Python-only AI engineers.  
**Used:** All projects · Sprint-wide

### Python — `LEARN`
Required for ML ecosystem: HuggingFace, PEFT, LoRA fine-tuning (P4), evals with RAGAS. Closes in ~1 week given background. Use pyenv on macOS — never system Python. Syntax gap only, not a cognitive gap.  
**Used:** Wk 1–2 ramp · P4 fine-tuning · RAGAS evals

### C# / .NET 8 — `AZURE` `PRIMARY`
20+ years depth. Used in P1-CS (Enterprise RAG Port). Semantic Kernel is C#-native. The combination of C# + Azure + Semantic Kernel is a niche with very few competitors. VS Code and Rider both run well on macOS.  
**Used:** P1-CS · Day 15–19 · Enterprise track

> **Runtime setup (macOS):** `nvm` for Node/TS · `pyenv` for Python (never system Python) · `dotnet sdk` via Homebrew for C# · All managed independently, no conflicts.

---

## 02 · LLM APIs & Models

### claude-sonnet-4-6 — `PRIMARY`
Default reasoning engine. Multi-step agents, code understanding, careful judgment, long context. Workhorse for P1–P3 and capstone.  
**Used:** All projects · Anthropic API

### claude-haiku-4-5 — `SECONDARY`
Latency-sensitive paths within agent loops. Classification, routing decisions, fast extraction. Swap with one line in Vercel AI SDK.  
**Used:** P2 · P3 agent loops · routing layer

### gpt-4o — `SECONDARY`
~60% of job postings mention OpenAI. Multi-model routing in P3 (Claude for reasoning + GPT-4o for speed) is a real production pattern worth demonstrating. Baseline for fine-tuning comparison in P4.  
**Used:** P3 multi-model routing · P4 benchmark baseline

### text-embedding-3-small — `PRIMARY`
Default embedding model for all vector search. Cheap, fast, excellent quality. Don't overthink this choice.  
**Used:** P1 · P1-CS · any RAG project

### Azure OpenAI — `AZURE` `PRIMARY`
Managed GPT-4o / embedding deployment via Azure. How most enterprise companies consume LLMs in production.  
**Used:** P1-CS · enterprise track

### Mistral-7B / CodeLlama-7B — `LEARN`
Open-source models for P4 LoRA fine-tuning. Run locally on macOS via mlx-lm (Apple Silicon optimised) or on Colab Pro for heavier runs. Fine-tuned specialist model vs GPT-4o cost comparison is the P4 punchline.  
**Used:** P4 · fine-tuning · local inference

> **Routing logic:** Sonnet for reasoning-heavy → Haiku for speed-sensitive → fine-tuned 7B for narrow domain tasks at low cost. Demonstrating this in P3/P4 is production thinking.

---

## 03 · Cloud Platforms & Services

### Azure OpenAI Service — `AZURE` `PRIMARY`
Managed LLM endpoint (GPT-4o, embeddings). 26% of AI engineer job postings, skewed toward senior enterprise.  
**Used:** P1-CS · enterprise track

### Azure AI Search — `AZURE` `PRIMARY`
Managed vector + keyword hybrid search. Replaces pgvector in Azure environments. Native semantic ranking. AI-102 core exam topic.  
**Used:** P1-CS · Wk 3+ · AI-102 exam topic

### Azure AI Foundry — `AZURE` `LEARN`
Azure's unified AI platform — model deployment, agent orchestration, prompt flow, responsible AI. Central to AI-102 (2025 refresh).  
**Used:** AI-102 prep · Month 4–5

### Azure Cognitive Services — `AZURE` `LEARN`
Vision, NLP, Speech, Language APIs on Azure. AI-102 exam breadth. Awareness rather than depth during sprint.

### Azure.Identity / RBAC — `AZURE` `LEARN`
`DefaultAzureCredential` pattern for P1-CS. Managed identities, service principals, key vault integration.  
**Used:** P1-CS · enterprise security pattern

### AWS Bedrock — `SECONDARY`
Managed LLM access on AWS. 32.9% of AI engineer job postings. Conversancy, not mastery.

### AWS SageMaker — `SECONDARY`
MLOps on AWS. Most enterprise ML infrastructure runs here. Build on the job after landing a role.

### GCP / Vertex AI — `AWARE`
Genuinely strong AI platform. Smaller job pool, no C# leverage. Don't invest sprint time here.

> **Decision:** Azure PRIMARY (C# + SK + Azure = rare combination) · AWS SECONDARY (broadest market, post-sprint depth) · GCP SKIP

---

## 04 · Frameworks, SDKs & Orchestration

### Vercel AI SDK — `PRIMARY`
Primary TypeScript AI abstraction. Streaming, tool use, multi-model routing in one clean package. Swap providers with one line. Use from Day 1.  
**Used:** P1 · P2 · P3 · capstone · Day 1

### Anthropic SDK — `PRIMARY`
Raw SDK for anything Vercel AI SDK doesn't cover. Python and TypeScript. "I used the SDK directly to understand the tool-use loop without framework magic" is a strong interview answer.  
**Used:** Sprint-wide

### OpenAI SDK — `SECONDARY`
Raw SDK for GPT-4o calls, embeddings, and fine-tuning API (P4).  
**Used:** P3 multi-model · P4 fine-tuning API

### Semantic Kernel — `AZURE` `PRIMARY`
C#-native AI orchestration from Microsoft. Plugin architecture maps 1:1 to LangChain concepts you'll have just built. Mature, enterprise-grade, underrepresented in candidate pool.  
**Used:** P1-CS · Wk 3+ · C# enterprise track

### LangGraph — `LEARN`
Stateful agent orchestration via state machines. More structured than LangChain — cleaner mental model for complex agent flows.  
**Used:** Wk 6 · P3 multi-agent

### LangChain.js / LangChain — `AWARE`
Know the concepts and read the docs (Wk 1). Use sparingly — reputation problem in senior engineering circles. LangSmith observability is still worthwhile.  
**Used:** Wk 1 docs read only · LangSmith ok

### LlamaIndex — `LEARN`
RAG-focused framework. Better document ingestion and retrieval abstractions than LangChain for pure RAG. Python-first.  
**Used:** Wk 3 · P1 RAG pipeline

### FastAPI — `LEARN`
Python backend for AI services where TS isn't the right tool. Clean async API, auto-generated docs. Native on macOS.  
**Used:** Wk 8 flagship · Python backend option

### ASP.NET Minimal API — `AZURE`
Backend for P1-CS enterprise RAG. Exposes SK RAG pipeline as REST endpoint with Swagger. 20yr C# background means trivial overhead.  
**Used:** P1-CS · Day 18

### Next.js — `PRIMARY`
Frontend for P1 and capstone chat UI. Pairs with Vercel AI SDK natively. Use App Router.  
**Used:** P1 UI · capstone DevMind

### Zod — `PRIMARY`
TypeScript schema validation for structured LLM output. Prevents silent failures in agentic systems.  
**Used:** P2 · P3 · structured output validation

> **Decision:** Vercel AI SDK over LangChain as primary TS abstraction · Semantic Kernel for C# · Raw SDKs where frameworks add more friction than value.

---

## 05 · Vector Stores & Data Infrastructure

### pgvector — `PRIMARY`
Postgres extension for vector search. Already know Postgres — low-friction entry point. Production-viable for most scales.  
**Used:** P1 · Wk 2

### Azure AI Search — `AZURE` `PRIMARY`
Managed hybrid (vector + keyword) search. Enterprise RAG for P1-CS. Native semantic ranking.  
**Used:** P1-CS · enterprise track · AI-102 topic

### Supabase (pgvector) — `SECONDARY`
Hosted Postgres + pgvector. Free tier covers sprint projects. Good DX with TypeScript SDK.  
**Used:** P1 hosted option · fast deploy

### Pinecone / Weaviate / Chroma — `AWARE`
Industry-standard for interview conversations about vector infrastructure choices. Know the landscape, don't go deep.  
**Used:** Wk 2 landscape overview only

> **Chunking matters:** Pinecone blog "Chunking strategies for LLM apps" is Wk 2 required reading. Reranking covered in Wk 3 — Azure AI Search provides semantic ranking natively.

---

## 06 · Observability, Evals & Quality

### Langfuse — `PRIMARY`
Open-source LLM observability. Tracing, prompt versioning, A/B testing, cost dashboards. Add from Day 1 of building — evals without observability is flying blind.  
**Used:** Wk 7 setup · all projects from P1

### LangSmith — `SECONDARY`
LangChain's tracing platform. Use if the project uses LangGraph — the integration is native. Either LangSmith or Langfuse; pick one per project.  
**Used:** Wk 7 · LangGraph projects (P3)

### RAGAS — `LEARN`
Open-source RAG eval framework. Faithfulness, answer relevancy, context recall. Eval harness in CI on P1.  
**Used:** Wk 4 · P3 full eval suite

### W&B (Weights & Biases) — `LEARN`
ML experiment tracking. Used in P4 to log LoRA training runs, compare model versions, build the benchmark report.  
**Used:** P4 fine-tuning track

### CI / GitHub Actions — `PRIMARY`
Eval harness runs in CI on P1 TypeScript version. Automated quality gate on every commit. Shows production engineering discipline.  
**Used:** P1 CI evals · all shipped repos

> **The signal:** A GitHub repo with Langfuse traces, a RAGAS eval dashboard, and CI-gated evals signals more credibility to senior engineers than most certs. Start tracing from day one.

---

## 07 · ML Tooling & Fine-Tuning

### HuggingFace PEFT — `LEARN`
LoRA/QLoRA implementation for P4. Python-native via pyenv on macOS. Use mlx-lm for local Apple Silicon runs, Colab Pro for heavier training jobs.  
**Used:** Wk 9 · P4 fine-tuning track

### mlx-lm — `PRIMARY`
Apple's ML framework for Apple Silicon. Optimised for unified memory — outperforms PyTorch/MPS for local fine-tuning on M-series Macs. Run Mistral-7B or CodeLlama locally for inference and fine-tuning. Python-native via pyenv.  
**Used:** P4 local fine-tuning · Apple Silicon

### OpenAI Fine-Tuning API — `LEARN`
Best fine-tuning API for P4. Mature tooling, JSONL dataset format. Fine-tuned GPT-4o-mini specialist vs full GPT-4o — cost/performance comparison is the P4 punchline.  
**Used:** P4 · Day 55–69

### Google Colab Pro — `SECONDARY`
Cloud GPU fallback for heavy LoRA runs that push past 16GB unified memory on the M1 Pro. ~£10/month. A100 with 40GB VRAM. Most practitioners use cloud for heavy fine-tuning regardless of local hardware. Subscribe at Day 55 — don't pay for it during P1–P3.  
**Used:** P4 heavy training runs · safety valve

### NumPy / Pandas — `LEARN`
Python data manipulation basics. Wk 1 (chapters 4–5 only). Enough to prepare fine-tuning datasets and parse eval outputs.  
**Used:** Wk 1 ramp · dataset prep for P4

### MLflow / DVC — `AWARE`
MLOps pipeline tooling. Only if taking the Platform track at the Day 60 direction fork.  
**Used:** Wk 9 Platform track only

> **P4 punchline:** A fine-tuned specialist model at 10% of GPT-4o cost, with a benchmark report showing it outperforms GPT-4o on the narrow task. That's the artefact that shows real ML engineering, not just API wrangling.

---

## 08 · Infrastructure & Deployment

### Vercel — `PRIMARY`
Deployment for Next.js frontend projects (P1, capstone). Zero-config, Git-connected. Free tier covers sprint projects.  
**Used:** P1 · capstone · frontend deploy

### Railway / Render — `SECONDARY`
Backend service hosting. Faster DX than AWS for sprint-pace deployment.  
**Used:** Wk 8 flagship · backend hosting

### Docker — `LEARN`
Containerisation for P1-CS Azure deployment and Wk 8 flagship. Native on macOS — no Docker Desktop friction. Used in P1-CS to package the ASP.NET API.  
**Used:** P1-CS · Wk 8 · containerised services

### GitHub / GitHub Actions — `PRIMARY`
6 pinned repos are the portfolio. GitHub Actions for CI eval harness. Clean commit history and descriptive READMEs are the interview artefact.  
**Used:** All projects · CI evals · portfolio

### GitHub API — `LEARN`
Used in P2 (PR Review Agent) to fetch PR diffs, comments, file trees. Real external tool integration in an agentic context.  
**Used:** P2 · PR Review Agent · tool use

### Homebrew + zsh — `PRIMARY`
macOS package manager. Manages git, nvm, pyenv, dotnet, docker, and all dev tooling. Clean setup, not migration — install fresh from Homebrew, zero cruft.  
**Used:** Mac setup · Day 0

### VS Code — `PRIMARY`
Primary IDE for TypeScript and Python work. macOS native. Extensions: Pylance, ESLint, Prettier, GitHub Copilot, REST Client. Rider is an alternative for C# if preferred.  
**Used:** Sprint-wide · all languages

---

## 09 · OS, Hardware & Local Environment

### macOS (Apple Silicon) — `PRIMARY`
Native Unix environment. Python tooling, Docker, HuggingFace, every tutorial — all work without workarounds. No WSL, no path hacks, no platform friction. The right OS for this sprint.

### MacBook Pro M1 Pro 16GB — `PRIMARY`
Current machine. Fully capable for Projects 1–3 — all API-based work, no local GPU required. P4 fine-tuning is workable with mlx-lm and quantised models; Colab Pro is the safety valve for heavier runs. Don't let hardware be a reason to delay starting.

### MacBook Pro (upgrade) / Mac Mini M4 Pro — `FUTURE`
Either a MacBook Pro upgrade or a Mac Mini M4 Pro (48GB) would meaningfully expand local fine-tuning headroom post-sprint — 13B models unquantised, 7B with room to breathe, two models simultaneously. Not needed for the sprint. Worth revisiting after Day 90 based on where the work takes you.

### Metal / mlx unified memory — `LEARN`
Apple Silicon GPU acceleration via unified memory architecture. mlx-lm is optimised for this — outperforms PyTorch/MPS for local fine-tuning on M-series. Running Mistral-7B locally is realistic on 16GB with quantisation.

### Homebrew + zsh — `PRIMARY`
macOS package manager. Homebrew → nvm → pyenv → dotnet → Docker → VS Code. Clean setup, not migration. Half a day, zero cruft.

> **Memory note:** 16GB is tight for P4 fine-tuning but workable with 4-bit/8-bit quantised models. Colab Pro (~£10/month, A100 40GB) is the safety valve for any run that needs more. Subscribe at Day 55 — don't pay for it during P1–P3.

---

## 10 · Key Concepts & Patterns to Master

| Concept | When | Notes |
|---|---|---|
| **RAG** | Month 1 | Embedding → index → retrieve → rerank → generate. Two implementations: TS/pgvector (P1) and C#/Azure AI Search (P1-CS). |
| **ReAct Pattern** | Wk 5 | Reason + Act loop. Foundation of P2. Yao et al. paper required reading. Build from scratch before using a framework. |
| **Tool Use / Function Calling** | Wk 4 | LLM decides when and how to call external tools. Core to all agentic systems. |
| **Multi-Agent Orchestration** | Wk 6 | Orchestrator / subagent pattern. P3. LangGraph state machine for coordination. |
| **Structured Outputs / JSON Mode** | Wk 4 | Zod schemas for TypeScript validation. Critical for production reliability. |
| **Embeddings & Cosine Similarity** | Wk 2 | Foundation of RAG. Understand *why* text-embedding-3-small, not just how. |
| **Chunking Strategies** | Wk 2–3 | Fixed-size, semantic, hierarchical. Overlap strategies. Pinecone blog is the reference. |
| **Reranking** | Wk 3 | Cross-encoder second-pass to improve retrieval precision. Azure AI Search provides this natively. |
| **Evals Framework Design** | Wk 4 | Faithfulness, relevancy, groundedness. RAGAS metrics. Eval harness in CI. |
| **Agent Memory Types** | Wk 5 | In-context, episodic, semantic. Memory management is a production concern. |
| **Token Economics** | Month 2 | Input vs output pricing. Cost dashboards in Langfuse. Routing Haiku vs Sonnet for cost control. |
| **LoRA / QLoRA** | Wk 9 | Low-Rank Adaptation — efficient fine-tuning without full model retraining. P4. |
| **Hybrid Search** | P1-CS | Vector + keyword combined. Azure AI Search provides this natively. |
| **Guardrails / Safety Layers** | Wk 8 | Input validation, output filtering. Production AI systems need explicit safety layers. |
| **Responsible AI** | AI-102 | Microsoft's RAI framework. Enterprise customers require documented responsible AI posture. |
| **Semantic Kernel Plugin Pattern** | P1-CS | Maps 1:1 to LangChain tools concept. C#-native. LangChain knowledge from P1 makes this a translation exercise. |
| **MLOps / Model Serving** | Month 2 | Deploying, monitoring, versioning models. Chip Huyen "Designing ML Systems" is the reference. |

---

## 11 · Certifications

### Azure AI Engineer Associate (AI-102) — `CERT` `PRIMARY` · Month 4–5 · ~£165
The cert that most directly validates what you'll have built. 2025 refresh shifted focus to generative AI and agentic solutions — Azure OpenAI, AI Foundry, AI Search, RAG pipelines, responsible AI governance. Exactly the stack built across P1–P3. **C# exam option is a genuine edge.**

**What it covers:** Azure OpenAI Service · Azure AI Search · AI Foundry & Agents · Cognitive Services · Responsible AI · Vision, NLP, Speech

**Study path:** MS Learn official AI-102 path (free) → Scott Duffy Udemy (~£15) → Whizlabs practice tests → `kennethleungty/Azure-AI-Engineer-Associate-Notes` (GitHub, free)

---

### AWS ML Engineer Associate (MLA-C01) — `CERT` `SECONDARY` · Month 6–9 · ~£240
Replaces retiring ML Specialty. Engineering-focused — productionising ML workloads via SageMaker and AWS ML stack. Needs ~1yr hands-on AWS. Build that on the job.

---

### Certs to Skip

| Cert | Reason |
|---|---|
| ~~AWS ML Specialty MLS-C01~~ | Retiring March 31, 2026. Don't invest prep time. |
| ~~AWS AI Practitioner AIF-C01~~ | Aimed at business professionals. Under-positioning on a senior engineer CV. |
| ~~Azure AI Fundamentals AI-900~~ | Non-technical foundational cert. Go straight to AI-102. |

> **Honest cert calculus:** A deployed GitHub repo with Langfuse traces and a RAGAS eval suite opens more doors than any cert. AI-102 earns its place for breaking into a new domain without a track record. After that, let the job tell you which cert to chase next.

---

*AI Engineer Tech Stack Reference · Compiled from Learning Plan + 90-Day Sprint + Project Arc*
