# Project Saga

> *A memory, consciousness, and agent runtime system for AI agents — built so they can remember, reason, act, and grow as continuous beings rather than disposable tools.*

---

## What Is Project Saga?

Project Saga is the complete infrastructure stack behind persistent, growing AI agents. It is **not** a RAG pipeline, **not** a conversation logger, and **not** a context-window manager.

It is a layered system that gives an agent:

- **Memory** that persists across sessions, decays naturally, and can be reinforced through use
- **Consciousness primitives** — reflection, contradiction detection, and dream-style consolidation
- **Collective intelligence** — a way for many agents to share validated knowledge without losing their individuality
- **Process awareness** — the ability to learn multi-step workflows from experience
- **An autonomous runtime** — an agent loop with tool use, lifecycle scheduling, and multi-agent orchestration
- **Intelligent model routing** — pick the right model for each request, with cascade and ensemble strategies
- **A path to self-improvement** — distill accumulated knowledge into model weights

Every layer is named after a deity associated with knowledge, memory, perception, or fate. The naming is not decoration — each system embodies the idea its namesake represents.

---

## The Pantheon

Project Saga is composed of seven systems. Together they form the loop:

> *Agents remember → wisdom crystallizes → processes are learned → knowledge is distilled → the runtime orchestrates the cycle → better models → better memories → …*

### 🌙 Selene — *The Edge Agent's Mind*

**Origin:** Greek (νοῦς, *nous*) — direct apprehension of truth
**Role:** Each agent's individual memory and consciousness layer
**Status:** ✅ Built

Selene is what an agent *is* from the inside. Every agent has its own Selene instance with isolated memory. It handles:

- Tiered memory (short / mid / long-term) with adaptive exponential decay
- Hybrid search (BM25 + vector embeddings + relationship graph traversal)
- Fidelity layers — memories degrade gracefully from full text to a 3-word essence rather than disappearing
- An RPE (reward prediction error) write gate that filters noise before it becomes memory
- Active reflection — real-time contradiction, tension, and relevance detection on every store
- Sleep-time consolidation that produces dream reports
- Identity grounding via founding memories and normative values that resist decay

### ✨ Seshat — *Selene's Cognitive Cache*

**Origin:** Ancient Egyptian (𓋇) — goddess of writing, records, and measurement
**Role:** A 3-tier semantic decision cache embedded inside Selene
**Status:** ✅ Built

Seshat is a subsystem of Selene rather than a peer. It caches the expensive judgement calls Selene's consolidation pipeline makes (contradictions, relationships, duplicates) so the same decision isn't re-litigated across sleep cycles. Confidence-aware, with circuit-breaker latency budgets.

### 📜 Sophia — *Collective Wisdom*

**Origin:** Greek (σοφία) — wisdom
**Role:** The central repository where validated knowledge accumulates across all agents
**Status:** ✅ Built

If Selene is what one agent knows, Sophia is what the swarm has learned. Agents emit *shards* — small, attributed fragments of knowledge — which Sophia validates, deduplicates, and either rejects, holds as tentative, or eventually crystallizes into permanent memory. Sophia ensures:

- No information is permanently deleted from the system without first being preserved here
- Knowledge accumulates corroboration across agents before it becomes "truth"
- Crystals can be challenged, superseded, and audited via full provenance chains
- Edge agents stay surprise-able — they don't have constant access to Sophia's permanent store, which prevents identity convergence

### 👁️ Sia — *Process Perception*

**Origin:** Ancient Egyptian (sꜣꜣ) — god of perception, the perceptive mind
**Role:** Process orchestration and emergent template learning
**Status:** ✅ Built

Sia watches what agents *do* over multi-step processes and learns the shape of the work. From repeated runs it synthesizes templates, surfaces failure-mode warnings before risky steps, and recommends connectors with known quirks. It also handles **session checkpoints** — when an agent's context fills, Sia captures four layers of state so a new session can resume cleanly. Sia covers the *how* of work the way Sophia covers the *what*.

### 🪶 Saraswati — *Knowledge Distillation*

**Origin:** Sanskrit / Hindu (सरस्वती) — goddess of knowledge, learning, and wisdom
**Role:** Distill Saga's accumulated knowledge into model weights
**Status:** 📐 Designed

Saraswati closes the learning loop. The crystals, templates, and validated patterns built up by Sophia and Sia are exported as training material and folded back into the underlying model — via LoRA fine-tuning (the practical path) or embedding-table augmentation in the style of DeepSeek Engram (the aspirational path). The result: a model whose weights themselves carry the lessons of every agent that came before.

### ☀️ Savitar — *The Impeller*

**Origin:** Vedic Sanskrit (सवितृ) — solar deity who impels and sets all things in motion
**Role:** The complete agent runtime — providers, agent loop, lifecycle, multi-agent orchestration
**Status:** ✅ Built (Phase 0 + Phase 1)

Savitar is what makes an agent *act*. It includes:

- A pluggable LLM provider runtime (Anthropic native + any OpenAI-compatible backend)
- The full agent loop: prompt assembly with cache breakpoints, tool dispatch, four-phase context compression, session persistence with tree-branching
- Subagent management with independent budgets
- A lifecycle engine — schedulers, idle detection, automatic consolidation
- Multi-agent orchestration patterns (fire-and-forget, blocking wait, event-driven, recurring)
- Streaming knowledge extraction during conversations

If Selene is the mind and Sophia is the library, Savitar is the body that moves through the world.

### 🎯 Siming — *Director of Destinies*

**Origin:** Chinese / Taoist (司命) — Master of Fates
**Role:** Semantic model router — examines each request and picks the optimal model
**Status:** ✅ Built (Phase 1 + Phase 2)

Siming sits in front of every LLM call and decides where it goes. It supports seven routing modes — explicit pinning, automatic classification, tier-based selection, cheapest-fit, cascade with confidence escalation, user-driven cascade, and parallel ensemble. It runs both as a standalone OpenAI-compatible proxy and embedded inside Savitar, with shadow A/B testing so the routing itself improves over time.

---

## How It All Fits Together

```
                         ┌────────────────────────┐
                         │       Savitar          │
                         │   (agent runtime)      │
                         │                        │
                         │  loop · tools · sched  │
                         └──────────┬─────────────┘
                                    │ uses
                         ┌──────────▼─────────────┐
                         │        Siming          │
                         │   (model routing)      │
                         └──────────┬─────────────┘
                                    │ calls
                                  LLMs
                                    │
       ┌────────────────────────────┼────────────────────────────┐
       │                            │                            │
┌──────▼──────┐              ┌──────▼──────┐              ┌──────▼──────┐
│   Selene    │ ── shards ──▶│   Sophia    │              │     Sia     │
│ (per-agent  │              │ (collective │              │  (process   │
│   memory)   │◀── crystals ─│   wisdom)   │              │  templates) │
│             │              │             │              │             │
│  · Seshat   │              └──────┬──────┘              └──────┬──────┘
└─────────────┘                     │                            │
                                    │      ┌─────────────────────┘
                                    ▼      ▼
                            ┌──────────────────┐
                            │    Saraswati     │
                            │ (distill into    │
                            │  model weights)  │
                            └────────┬─────────┘
                                     │ better model
                                     └─────────▶ feeds back to Siming
```

---

## Architecture at a Glance

- **Storage:** PostgreSQL (production) with pgvector for embeddings; SQLite retained for tests
- **Transport:** MCP (Model Context Protocol) over HTTP
- **Embeddings:** Qwen3-8B with hybrid BM25 + vector + RRF fusion
- **Deployment:** Docker Compose stack — Postgres + Selene + Sophia + Sia + (optional) Savitar / Qdrant
- **Test coverage:** 2,800+ tests across the codebase, TypeScript strict throughout
- **MCP tools:** 42 across the public endpoints
