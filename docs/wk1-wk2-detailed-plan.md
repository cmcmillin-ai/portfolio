# Wk 1 & 2 — Detailed Theory Catchup Plan

> **10–12h across a few evenings + weekend**  
> Build tasks are done. This is purely reading, watching, and connecting theory to the system already running.  
> Every session below has a code anchor — a specific thing to have open in VS Code while you read.

---

## The approach

You built before you read. That's the right order for an engineer. Every concept below already exists somewhere in your running system — the theory sessions name it, explain the mechanics, and give you vocabulary. The goal isn't to re-learn what you built; it's to be able to explain it precisely under interview pressure and make better decisions in Wk 3+.

**Rule for every session:** open the relevant file in VS Code before you start reading. When the theory matches something you recognize in the code, add a brief inline comment. Those comments are your notes — and they're in the right place to be useful later.

---

## Session Map — 10.5h total

| Session | Topic | Hours | When |
|---------|-------|-------|------|
| 1 | Tokens, context windows, temperature | 1.5h | Evening 1 |
| 2 | Streaming & the Vercel AI SDK v6 model | 1.5h | Evening 2 |
| 3 | LangChain landscape + Python ML idioms | 1.5h | Evening 3 |
| 4 | Embeddings & cosine similarity | 2h | Weekend AM |
| 5 | Chunking strategies (the essential session) | 2h | Weekend midday |
| 6 | pgvector deep dive + retrieval quality | 1.5h | Weekend PM |

---

## Session 1 — Tokens, Context Windows, Temperature
**1.5h · Evening 1**

**Open before you start:** your chat API route (`src/app/api/chat/route.ts` or equivalent) and your `.env.local`.

### What to read/watch
- **Anthropic docs — [Models overview](https://docs.anthropic.com/en/docs/about-claude/models)** — 15 min  
  Focus on the context window sizes for claude-sonnet-4-6. Note the input vs output token limits.
- **DeepLearning.AI — ChatGPT Prompt Engineering for Devs** — ~45 min  
  Lessons 1–2 only (Introduction + Guidelines). Skip the Python setup — you know the concepts, you just need the vocabulary.
- **Anthropic docs — [Token counting](https://docs.anthropic.com/en/docs/build-with-claude/token-counting)** — 15 min

### What to come away knowing

**Tokens:** Not words, not characters — roughly 4 chars of English per token. Your pgvector chunks are sized in characters; now you can convert that to approximate tokens and understand where the context limit pressure comes from.

**Context window:** claude-sonnet-4-6 has a 200K token context window. In your RAG pipeline, every query sends: system prompt + retrieved chunks + conversation history + user question. Each of those eats tokens. You made chunking decisions — now you understand why those decisions have a ceiling.

**Temperature:** You probably left it at the default (1.0) or didn't set it. Know what happens at 0 (deterministic, same answer every time — good for evals), 0.7 (balanced), and 1.0+ (more creative/varied). Your RAG system should probably use a low temperature — retrieval-grounded answers benefit from determinism.

### Code anchor
After reading, find where you pass model parameters in your chat route. Add a comment noting what temperature you're using and whether it's the right choice for a document Q&A system. If you didn't set it explicitly, that's worth noting too.

---

## Session 2 — Streaming & the Vercel AI SDK v6 Model
**1.5h · Evening 2**

**Open before you start:** your chat route — specifically the section with `toUIMessageStreamResponse()` and `convertToModelMessages()`. This is the code you debugged hardest on Day 1.

### What to read/watch
- **Vercel AI SDK docs — [Overview](https://sdk.vercel.ai/docs/introduction)** — 20 min  
  Read the "Why AI SDK" section and the core concepts. You'll recognise everything.
- **Vercel AI SDK docs — [streamText](https://sdk.vercel.ai/docs/reference/ai-sdk-core/stream-text)** — 20 min  
  Read the API reference for `streamText`. Map every parameter to what you have in your code.
- **Vercel AI SDK docs — [Migration guide v4 → v5/v6](https://sdk.vercel.ai/docs/migration-guides)** — 20 min  
  Read the breaking changes. You hit `toDataStreamResponse()` → `toUIMessageStreamResponse()` and `convertToModelMessages()` on Day 1 without knowing why. Now you will.
- **Anthropic docs — [Streaming](https://docs.anthropic.com/en/api/streaming)** — 15 min  
  Read the raw streaming format. This is what the SDK is abstracting for you — knowing what's underneath is the interview-level answer.

### What to come away knowing

**Why streaming matters:** The LLM starts returning tokens immediately. Without streaming, the user waits for the entire response before seeing anything. Your UI feels fast because of streaming — it's not an optional enhancement, it's a UX requirement for chat.

**What `convertToModelMessages()` actually does:** Transforms the Vercel AI SDK message format (which includes UI metadata) into the raw format the Anthropic API expects. This is why v6 requires it — v4 did this transformation invisibly, v6 makes it explicit so you understand what's going into the API call.

**What `toUIMessageStreamResponse()` actually does:** Converts the raw Anthropic stream into the Vercel AI SDK's wire format (a special data stream protocol the `useChat` hook on the frontend knows how to consume). Without this, your frontend wouldn't know how to parse the chunks as they arrive.

### Code anchor
In your chat route, add a comment above `convertToModelMessages()` explaining what it does. Add one above `toUIMessageStreamResponse()` explaining what format it produces and why the frontend needs it. These are the two things you'll be asked about in a technical screen.

---

## Session 3 — LangChain Landscape + Python ML Idioms
**1.5h · Evening 3**

**Open before you start:** nothing specific — this is the most conceptual session. Have a browser tab open on the [LangChain.js docs](https://docs.langchain.com/oss/javascript/langchain/overview) for reference.

### What to read/watch
- **LangChain.js docs — [Overview](https://docs.langchain.com/oss/javascript/langchain/overview)** — 15 min  
  Don't build anything. Read to map the concepts: chains, retrievers, document loaders, text splitters. You've built all of these manually — LangChain just names them and gives you pre-built implementations.
- **LangGraph.js docs — [Overview](https://docs.langchain.com/oss/javascript/langgraph/overview)** — 15 min  
  The conceptual/orchestration content has largely moved here. Skim for the mental model — you'll go deep on LangGraph in Wk 6.
- **Andrej Karpathy — [Intro to Large Language Models](https://www.youtube.com/watch?v=zjkBMFhNj_g)** — 1h (watch at 1.25x = ~48 min)  
  The clearest first-principles explanation of how LLMs work. Covers inference, training, finetuning into an assistant, tool use, and the LLM-as-OS mental model. From the co-founder of OpenAI and former Tesla AI director. The fundamentals are fully current — focus on Parts 1 and 2 (first ~42 min); Part 3 on security is interesting but optional for this session.
- **Python for Data Analysis (Wes McKinney) — Chapter 4 intro** — 15 min  
  Skim only. The goal is recognising NumPy array operations when you see them in ML code, not becoming a NumPy practitioner. You'll use this in Week 4's eval harness work and in P4.

### What to come away knowing

**The LangChain mental model:** LCEL (LangChain Expression Language) is a pipe operator for AI components — `retriever | prompt | model | parser`. Your RAG pipeline does exactly this, just wired manually. You don't need LangChain, but you need to recognise the abstraction in code reviews and conversations.

**Why you didn't use LangChain for P1:** Not an oversight — a deliberate choice. "I built the retrieval and generation pipeline manually so I understand every step without framework magic" is a strong answer that distinguishes you from engineers who reach for the framework before understanding what it does.

**Python idioms to recognise:** list comprehensions, `zip()`, `enumerate()`, broadcasting in NumPy. You won't write production Python for a while, but you'll read it constantly in model documentation, eval frameworks, and research code.

---

## Session 4 — Embeddings & Cosine Similarity
**2h · Weekend AM**

**Open before you start:** your ingestion script — specifically the section where you call the OpenAI embeddings API and store results in pgvector.

### What to read/watch
- **DeepLearning.AI — Building Systems with the ChatGPT API — Lesson 1** — 30 min  
  The first lesson covers the embedding concept clearly. Skip the Python execution, focus on the explanation.
- **OpenAI docs — [Embeddings guide](https://platform.openai.com/docs/guides/embeddings)** — 20 min  
  Read "What are embeddings" and "How to get embeddings". Skim the use cases. Pay attention to the dimensionality section — `text-embedding-3-small` outputs 1536-dimensional vectors. That's what's stored in your pgvector column.
- **[Jay Alammar — The Illustrated Word2Vec](https://jalammar.github.io/illustrated-word2vec/)** — 40 min  
  The best visual explanation of what embedding space actually is. You don't need to understand the training mechanics — focus on the spatial intuition: similar meanings are close together, and "close" is measured by cosine similarity.
- **pgvector docs — [Distance functions](https://github.com/pgvector/pgvector#distance)** — 10 min  
  Three options: `<->` (L2/Euclidean), `<=>` (cosine), `<#>` (inner product). Know which one you used and why cosine is the right choice for normalised embedding vectors from OpenAI.

### What to come away knowing

**What an embedding actually is:** A 1536-dimensional vector (for text-embedding-3-small) where the position encodes semantic meaning. Documents about similar topics will have vectors that point in similar directions in this 1536-dimensional space.

**Why cosine similarity and not Euclidean distance:** Cosine measures the angle between vectors, not the distance between their endpoints. For text, two chunks that say the same thing in different lengths should be "close" — cosine handles this correctly, Euclidean distance gets confused by vector magnitude.

**What `text-embedding-3-small` actually is:** A 1536-dimension model trained on a massive text corpus. OpenAI also offers `text-embedding-3-large` (3072 dimensions, higher quality, higher cost). For your use case, small is the right default — the quality difference rarely justifies 4× the cost.

**The retrieval step demystified:** Your pgvector query converts the user's question into an embedding, then finds the chunks whose embeddings are most similar (smallest cosine distance) to the question's embedding. The semantic matching happens entirely in embedding space — no keyword matching.

### Code anchor
In your ingestion script, find the embeddings API call. Add a comment noting the model, the output dimension, and that the result is stored in pgvector using cosine distance (`<=>`). In your retrieval query, add a comment explaining what the similarity threshold or `LIMIT` clause is doing in embedding space terms.

---

## Session 5 — Chunking Strategies (The Essential Session)
**2h · Weekend Midday**

**Open before you start:** your ingestion script — specifically the chunking logic. This is the session where theory most directly improves your existing code.

### What to read/watch
- **[Pinecone — Chunking strategies for LLM applications](https://www.pinecone.io/learn/chunking-strategies/)** — 60 min  
  Read every section. This is the single most important read of both catchup weeks. Take notes. Read it with your chunking code open.
- **[Greg Kamradt — 5 Levels of Text Splitting](https://github.com/FullStackRetrieval-com/RetrievalTutorials/blob/main/tutorials/LevelsOfTextSplitting/5_Levels_Of_Text_Splitting.ipynb)** — 30 min  
  View the notebook on GitHub — you don't need to run it. The five levels (character, recursive character, document structure, semantic, agentic) give you a clear taxonomy for the interview conversation.
- **LangChain docs — [Text splitters](https://js.langchain.com/docs/concepts/text_splitters/)** — 20 min  
  See how the framework implements what you built manually. `RecursiveCharacterTextSplitter` is the most commonly used — identify what strategy yours corresponds to.

### What to come away knowing

**Fixed-size vs semantic chunking:** Fixed-size splits on character count with overlap. Semantic splits on meaning boundaries (paragraphs, sections). You almost certainly did fixed-size — that's fine and correct for a first implementation, but know the tradeoff: fixed-size can split a sentence mid-thought; semantic chunks are more coherent but harder to implement.

**The overlap parameter:** You set a chunk overlap (e.g., 200 characters). This means consecutive chunks share content at their boundaries. Without overlap, a retrieval query that falls between two chunks finds nothing. With overlap, the relevant content appears in at least one chunk. Know what value you chose and why.

**Chunk size tradeoffs:**
- Too small → high precision but loses context (a chunk about "the function returns X" with no surrounding context is useless)
- Too large → low precision, too much irrelevant content in the retrieved chunk, uses more tokens per retrieval
- The sweet spot for code documentation (your P1 use case): 500–1000 characters with ~100 character overlap

**What to do with this knowledge:** Look at your chunk size and overlap settings. Are they appropriate for your document type? This is a concrete improvement you can make to P1 before Wk 3+ — and "I reviewed my chunking strategy against the literature and adjusted the parameters for my document structure" is a strong thing to say about a project.

### Code anchor
After reading, annotate your chunking code with: the strategy name (e.g., "fixed-size with overlap"), your chunk size, your overlap size, and a one-line note on why those values are appropriate (or what you'd change now that you've read the theory). This annotation makes the retrieval quality conversation in Wk 4's eval harness much easier.

---

## Session 6 — pgvector Deep Dive + Retrieval Quality
**1.5h · Weekend PM**

**Open before you start:** your database schema (wherever you define the pgvector table) and your retrieval query.

### What to read/watch
- **pgvector README — [full read](https://github.com/pgvector/pgvector)** — 30 min  
  You've used it. Now read all of it. Focus on: index types (IVFFlat vs HNSW), the `lists` parameter, and when to use each. The HNSW index is the right default for most workloads — know why.
- **Supabase blog — [Fewer dimensions are better](https://supabase.com/blog/fewer-dimensions-are-better-pgvector)** — 20 min  
  Counterintuitive result: sometimes reducing embedding dimensions improves retrieval performance. The "why" here deepens your understanding of what the embedding space is doing.
- **[Anthropic cookbook — Contextual retrieval](https://github.com/anthropic-ai/anthropic-cookbook/blob/main/skills/contextual-retrieval/guide.md)** — 30 min  
  Anthropic's approach to improving RAG retrieval quality. Introduces the concept of prepending context to each chunk before embedding — a concrete improvement you can apply to P1.

### What to come away knowing

**IVFFlat vs HNSW:** IVFFlat partitions the vector space into clusters and searches only the nearest clusters — fast at scale but needs training (the `lists` parameter sets cluster count). HNSW builds a hierarchical graph — better recall, faster queries, but more memory. For your current scale (small corpus), no index at all is fine. For production scale, HNSW is the modern default.

**Why retrieval quality matters more than generation quality:** If the wrong chunks are retrieved, even the best LLM gives a bad answer. "Garbage in, garbage out" applies directly. The eval harness in Wk 4 measures this — retrieval quality (are the right chunks coming back?) is a separate metric from answer quality (is the generated response correct?).

**Contextual retrieval (the Anthropic approach):** Instead of embedding a raw chunk, prepend a brief description of where it came from: *"This chunk is from the authentication module documentation, describing the JWT validation flow."* The chunk then has context that helps the embedding model place it more accurately in the semantic space. This is a genuine quality improvement worth applying to P1 before you add the eval harness.

### Code anchor
In your schema definition, add a comment noting the distance function your index uses. In your retrieval query, add a comment noting how many results you're fetching (`LIMIT k`) and what the downstream effect of that number is (more results = more context tokens, slower generation, potentially better recall).

---

## End-of-week checkpoint

By the end of Session 6 you should be able to answer all of these without notes:

- What is a token? Roughly how many tokens is a typical paragraph?
- What does `convertToModelMessages()` do and why did v6 require it?
- What is an embedding? Why is cosine similarity the right distance metric for them?
- What is `text-embedding-3-small` and what does "1536 dimensions" mean?
- What chunking strategy did you use in P1, and what are the tradeoffs vs alternatives?
- What's the difference between IVFFlat and HNSW indexes in pgvector?
- What is contextual retrieval and how does it improve on naive RAG?

If you can answer those, Wk 1 and Wk 2 are closed. You're ready to move into Wk 3+ (P1-CS) and Wk 4 (evals) with the right foundations underneath the system you've already built.
