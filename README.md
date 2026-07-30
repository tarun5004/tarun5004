<div align="center">

# Tarun Raj Gaur

**Backend-leaning Full-Stack Engineer** — I build systems that stay up, scale predictably, and are easy for the next engineer to reason about.

`MERN` · `FastAPI` · `Docker` · `CI/CD` · `System Design (learning)`

[Portfolio](#) · [LinkedIn](https://www.linkedin.com/in/tarun-raj-gaur-413083270) · [Email](#)

</div>

---

## Why I build what I build

`[FILL: 2-3 sentences connecting your projects — what's the actual thread?]`

I write code assuming someone else has to maintain it without me in the
room. That means tests over cleverness, and explicit tradeoffs over
"it works on my machine."

---

## Master Project

<details open>
<summary><b>ProxiAI — Enterprise AI Gateway & Audit Platform</b> <sub>(design complete · implementation in progress)</sub></summary>

<br>

**Problem:** Organizations using multiple LLM providers (Claude, ChatGPT,
Gemini) across teams have no central visibility into what's being sent,
no audit trail for compliance (SOC 2 / ISO 27001), and no continuity plan
if a provider is suspended or banned — which is not hypothetical: Anthropic's
Fable 5 / Mythos 5 models were taken offline in June 2026 under U.S.
export-control action before being restored July 1, 2026. Any org depending
on a single provider with no fallback loses continuity with zero notice.

**Solution:** A middleware SaaS layer that sits between employees and any
LLM provider — routes requests through infrastructure the org controls,
scores and masks sensitive data before it leaves the perimeter, falls back
automatically when a provider degrades, and gives admins real-time
visibility into cost, usage, and risk.

**Architecture**
```
Employee → SSE connection → Auth (JWT) → Idempotency check (Redis)
  → Rate limiter → PII pipeline (Detect → Classify → Score)
  → Policy Engine (ALLOW / MASK / BLOCK) → Prompt cache (Redis)
  → Routing Engine (intent + budget + latency + health signals)
  → Circuit Breaker + Retry/Backoff → Provider Adapter (Groq/Gemini/Claude/BYOK)
  → SSE stream back to employee
  → [async] request.completed event → BullMQ workers
    (billing, analytics, anomaly, audit) → MongoDB (per retention policy)
```
Full diagram and per-subsystem breakdown: [`/docs`](https://github.com/tarun5004/ProxyAi/tree/main/docs)

**Tech stack:** TypeScript, Node.js/Express, React, MongoDB, Redis, BullMQ,
Docker (multi-stage builds), GCP Cloud Run, Pino, OpenTelemetry, Prometheus/Grafana

**Key engineering decisions**
- **Provider Adapter pattern** — every LLM provider implements the same
  interface (`complete`, `stream`, `healthCheck`, `estimateCost`). Adding a
  new provider means writing one adapter file, zero changes elsewhere —
  Open/Closed Principle applied to a real integration problem, not just
  named in a bullet list.
- **Circuit breaker per provider**, not a global one — a failing provider
  trips independently and the routing engine falls back automatically,
  rather than one bad provider degrading the whole system.
- **Redis Pub/Sub over Kafka at this scale** — deliberately not reaching
  for heavier infrastructure than the problem needs. The event bus sits
  behind a `publish`/`subscribe` interface, so swapping to Kafka later is
  a one-file change if throughput ever justifies it.
- **Retention mode enforced at the write boundary, not after** — a
  No-Storage org's prompt is never constructed into a MongoDB write in the
  first place, rather than written then filtered. Safer by construction,
  not by convention.

**Technical challenges**
- Mid-stream provider fallback: if a provider fails after SSE streaming has
  already started, you can't silently splice in a different model's output
  without a visible glitch — current approach shows an explicit "retrying"
  message and restarts rather than faking continuity.
- Idempotency under flaky connections — a double-click or dropped SSE
  connection shouldn't become two billed LLM calls; handled via `SETNX` on
  a client-generated request ID with a 5-minute TTL.

**Status:** Architecture fully specified across 25 sections (provider
abstraction, policy engine, event-driven side effects, resilience patterns,
audit logging, observability, deployment). Implementation in progress —
this is being built incrementally, not claimed as complete.

💻 [Repo](https://github.com/tarun5004/ProxyAi) · 📐 [Architecture docs](https://github.com/tarun5004/ProxyAi/tree/main/docs) · 🔗 `[Live demo — once deployed]`

</details>

---

## Other Projects

<details>
<summary><b>ChatWave — Real-time chat with Redis pub/sub</b></summary>

<br>

**Problem:** `[FILL]`
**Solution:** `[FILL]`
**Tech stack:** Node.js, Express, Socket.io, Redis, MongoDB, Docker Compose
**Key engineering decisions:** `[FILL]`

💻 `[GitHub repo]` · 🔗 `[Live demo]`

</details>

<details>
<summary><b>PromptCraft — Multi-model prompt testing tool (SSE streaming)</b></summary>

<br>

**Problem:** `[FILL]`
**Solution:** `[FILL]`
**Tech stack:** `[FILL]`
**Key engineering decisions:** `[FILL]`

💻 `[GitHub repo]` · 🔗 `[Live demo]`

</details>

<details>
<summary><b>PersonalOS — Full-stack personal productivity system</b></summary>

<br>

**Problem:** `[FILL]`
**Solution:** `[FILL]`
**Tech stack:** `[FILL]`

💻 `[GitHub repo]` · 🔗 `[Live demo]`

</details>

---

## Tech Stack

<table>
<tr>
<td valign="top" width="33%">

**Languages & Runtime**
- JavaScript / TypeScript
- Python
- Node.js

</td>
<td valign="top" width="33%">

**Backend & Data**
- Express, FastAPI
- MongoDB, PostgreSQL
- Redis

</td>
<td valign="top" width="33%">

**Infra & Tooling**
- Docker, Docker Compose
- GitHub Actions (CI/CD)
- Linux, GCP/Azure

</td>
</tr>
</table>

---

## System Design — Currently Learning

- [ ] Load balancing strategies (round-robin vs. least-connections vs. consistent hashing)
- [ ] Caching layers — invalidation, write-through vs. write-behind
- [ ] Database indexing & query optimization at scale
- [ ] Horizontal scaling for stateful services (WebSocket/SSE specifically)
- [ ] Message queues vs. pub/sub — when each is the right tool

## Development Workflow

`[FILL: how do you actually work? e.g. "Design doc before implementation,
feature branches, self-review against a checklist before merge."]`

## Roadmap

- Finish ProxiAI MVP implementation against the documented architecture
- `[FILL]`
- `[FILL]`

---

<div align="center">
<sub>MCA student @ COER University, building toward backend/full-stack roles.</sub>
</div>
