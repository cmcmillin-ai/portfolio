# AI Engineer — Project Arc

*Enterprise .NET Track · 5 Projects + Capstone · 6 Pinned Repos · Two ecosystems. One engineer.*

Five TypeScript projects cover the modern LLM-native stack — RAG, agents, evals, fine-tuning, and a full capstone. One focused C# project in Semantic Kernel + Azure unlocks the enterprise .NET niche. Six pinned repos, two markets.

---

## 01 · Two Ecosystems, One Sprint

### 5 repos · TypeScript
*LLM-Native Track*

P1 → P2 → P3 → P4 → DevMind. Covers the modern AI market: RAG, agents, evals, fine-tuning. Anthropic + OpenAI APIs, Vercel AI SDK, pgvector. This is the core arc.

### 1 repo · C# / Azure
*Enterprise Track*

P1-CS — same RAG architecture, enterprise stack. Semantic Kernel, Azure OpenAI, Azure AI Search. Opens the .NET + AI freelance niche where your 20 years of C# is a genuine moat.

---

## 02 · Project Arc Overview

| Project | Name | Focus |
|---------|------|-------|
| P1 · Day 14 | Code Doc Search | RAG · TypeScript |
| P1-CS · Day 19 | Code Doc Search | RAG · C# / Azure |
| P2 · Day 34 | PR Review Agent | First agent |
| P3 · Day 54 | Debug Assistant | Multi-agent + evals |
| P4 · Day 69 | Fine-tuned Reviewer | Model customisation |
| ⭐ Day 90 | DevMind | Capstone |

> Timeline flexibility: P1-CS sits between P1 and P2. If ahead on P1, P1-CS starts immediately. If P1 runs long, P1-CS compresses — it's a port, not a new concept. The sprint's built-in buffer keeps the Day 90 capstone deadline solid.

---

## 03 · P1-CS Specification — Enterprise RAG Port

**Day 15–19 · ~21 hours · C# / Azure**

The same RAG system built in P1 — reimplemented with Microsoft Semantic Kernel, Azure OpenAI, and Azure AI Search. Proves you can bring AI capabilities into enterprise .NET environments.

**What you build**

- Same codebase/docs ingestion as P1, using Azure AI Search index
- Semantic Kernel orchestration with Azure OpenAI as the LLM
- Azure AI Search for vector + hybrid retrieval (replaces pgvector)
- Minimal ASP.NET API with a clean Swagger endpoint
- Console or Blazor chat interface (functional, not polished)

**What you learn**

- Semantic Kernel plugin architecture and planners
- Azure OpenAI deployment and model management
- Azure AI Search — index creation, hybrid search, semantic ranking
- How enterprise AI orchestration differs from the startup stack
- Cost and latency tradeoffs: Azure managed vs. DIY

**What you skip (intentionally)**

- Polished frontend — API + minimal UI is enough
- Full eval harness — reference P1's eval approach in the README
- Deployment — local + Azure resource provisioning docs suffice
- CI/CD — the TypeScript version has this covered

**What makes the README great**

- Architecture diagram showing Azure service topology
- Side-by-side comparison: TS/pgvector vs. C#/Azure approach
- Cost analysis: Azure AI Search pricing vs. self-hosted vector DB
- "When to choose which" decision framework for clients

**Tech Stack:** `C# / .NET 8` · `Semantic Kernel` · `Azure OpenAI` · `Azure AI Search`

---

## 04 · P1-CS — Day-by-Day Plan

### Day 15 — Setup + Azure

Provision Azure OpenAI + AI Search resources. Scaffold .NET 8 console project. Install Semantic Kernel NuGet packages. Get "hello world" completion from Azure OpenAI working.
*~4h*

### Day 16 — Indexing

Port the chunking logic from P1. Create Azure AI Search index with vector field. Write ingestion script that chunks, embeds (Azure OpenAI embeddings), and pushes to search index.
*~4h*

### Day 17 — RAG pipeline

Build the retrieval + generation pipeline using Semantic Kernel. Wire up Azure AI Search as a retrieval plugin. Implement the hybrid search (vector + keyword) that Azure AI Search provides natively.
*~5h*

### Day 18 — API + UI

Expose as ASP.NET Minimal API with Swagger. Add a simple console or Blazor chat interface. Test against the same queries you used in P1 to compare results.
*~4h*

### Day 19 — README + polish

Architecture diagram (Azure topology). Write P1 vs P1-CS comparison table. Cost analysis. Decision framework. Clean up code, push to GitHub, pin the repo.
*~4h*

---

## 05 · P1 vs P1-CS — Side by Side

| Component | P1 — TypeScript | P1-CS — C# / Azure |
|-----------|-----------------|---------------------|
| Language | TypeScript | C# / .NET 8 |
| LLM Provider | Anthropic Claude (direct API) | Azure OpenAI (managed deployment) |
| Orchestration | Vercel AI SDK / LangChain.js | Microsoft Semantic Kernel |
| Vector Store | pgvector (self-hosted) | Azure AI Search (managed, hybrid) |
| Embeddings | OpenAI text-embedding-3-small | Azure OpenAI text-embedding-3-small |
| Frontend | Next.js chat UI (polished) | Console / Blazor (functional) |
| Deployment | Vercel | Local + Azure provisioning docs |
| Eval harness | Full suite in CI | Reference P1's approach, manual runs |
| Target client | Startups, SaaS, AI-native companies | Enterprise, .NET shops, Azure customers |
| Portfolio signal | "I build modern AI applications" | "I bring AI into your existing .NET stack" |

---

## 06 · What This Unlocks — Market Coverage

### Modern AI / LLM-Native Market
*Covered by P1–P4 + DevMind (existing)*

Startups, SaaS companies, AI-native products. TypeScript/Python stack. Direct API integration. The larger, more competitive market — but your 30yr engineering depth is the differentiator.

`RAG systems` · `AI agents` · `LLM integration` · `Fine-tuning` · `Multi-agent` · `Evals`

### Enterprise .NET + AI Market
*Unlocked by P1-CS (new)*

Enterprise companies, .NET shops, Azure customers. Lower competition, higher trust threshold, longer contracts. Your 20 years of C# is a genuine moat — most AI freelancers can't enter this market.

`Azure OpenAI integration` · `Semantic Kernel` · `.NET AI copilots` · `Enterprise RAG` · `Data analysis + AI`

> **The combined signal:** The combined signal: When a client sees your GitHub profile with both P1 (TypeScript) and P1-CS (C#/Azure) pinned, they see someone who understands AI engineering at the architectural level — not just in one framework. That's rare. Most AI freelancers are Python-only. Most .NET devs haven't touched AI. You're credibly both.

---

## 07 · Sprint Timeline

| Days | Project | Description | Duration |
|------|---------|-------------|----------|
| Day 1–14 | P1 · Code Doc Search | RAG foundation in TypeScript. Vercel AI SDK, pgvector, Anthropic. Full eval harness. | ~14 days |
| Day 15–19 | P1-CS · Enterprise RAG Port | Same RAG architecture in C#. Semantic Kernel, Azure OpenAI, Azure AI Search. | ~5 days |
| Day 20–34 | P2 · PR Review Agent | First agent. Tool use, structured output, GitHub API integration. Days 20–28 front-load setup and tool-use fundamentals; formal agent architecture study (Wk 5, ~Day 29) arrives mid-build and deepens the work already in progress. | ~15 days |
| Day 35–54 | P3 · Debug Assistant | Multi-agent orchestration. Full eval suite. Langfuse observability. | ~20 days |
| Day 55–69 | P4 · Fine-tuned Reviewer | Model customisation. Benchmark report. Cost analysis. | ~15 days |
| Day 70–90 | ⭐ DevMind Capstone | Full system integration. Blog post. Portfolio polish. Profile setup. | ~21 days |
