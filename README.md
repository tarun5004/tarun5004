<div align="center">

# Tarun Raj Gaur

**Backend-leaning Full-Stack Engineer** — I build systems that stay up, scale predictably, and are easy for the next engineer to reason about.

`MERN` · `FastAPI` · `Docker` · `CI/CD` · `System Design (learning)`

[Portfolio](#) · [LinkedIn](https://www.linkedin.com/in/tarun-raj-gaur-413083270) · [Email](#)

</div>

---

## Why I build what I build

Most of my projects start from a specific operational annoyance, not a tutorial.
`[FILL: 2-3 sentences — what's the actual thread connecting ChatWave / ProxiAI /
PromptCraft? E.g. "I keep building infra-adjacent tools — a proxy, a chat
system, a testing harness — because I'm more interested in the plumbing than
the UI."]`

I write code assuming someone else (or future me) has to maintain it without
me in the room. That means tests over cleverness, and explicit tradeoffs over
"it works on my machine."

---

## Featured Projects

<details open>
<summary><b>ChatWave — Real-time chat system with Redis pub/sub</b></summary>

<br>

**Problem:** `[FILL: what specific problem — e.g. "Standard WebSocket chat
implementations don't handle horizontal scaling; a message sent to a socket
on server A never reaches a client connected to server B."]`

**Solution:** `[FILL: how Redis pub/sub solves this — the actual mechanism,
not just "used Redis"]`

**Architecture**
```
[FILL: ASCII or linked diagram — client → load balancer → N app servers →
Redis pub/sub → MongoDB. Even a rough box diagram beats no diagram.]
```

**Tech stack:** Node.js, Express, Socket.io, Redis, MongoDB, Docker Compose

**Key engineering decisions**
- `[FILL: e.g. "Chose Redis pub/sub over a message queue because chat needs
  fan-out, not work distribution — a queue would let only one consumer
  process each message."]`
- `[FILL: another real decision + the alternative you rejected and why]`

**Technical challenges**
- `[FILL: something that actually broke or was hard — e.g. reconnect logic,
  message ordering, presence detection]`

**Proof**
- Docker containers: `[FILL: N]` · REST/WS endpoints: `[FILL: N]` · Test coverage: `[FILL: N%]`

📹 `[Demo GIF placeholder]` · 🔗 `[Live demo]` · 💻 `[GitHub repo]` · 📐 `[Architecture diagram]`

</details>

<details>
<summary><b>ProxiAI — Enterprise AI proxy & audit middleware</b></summary>

<br>

**Problem:** `[FILL: what does an org actually need this for — cost control?
compliance logging? rate limiting across teams calling an LLM API?]`

**Solution:** `[FILL: what ProxiAI actually intercepts/logs/enforces]`

**Architecture**
```
[FILL: client → ProxiAI middleware → provider API, with audit log sink,
rate limiter, and auth layer shown]
```

**Tech stack:** `[FILL: your actual stack — FastAPI? Node middleware?]`

**Key engineering decisions**
- `[FILL]`
- `[FILL]`

**Technical challenges**
- `[FILL: e.g. streaming response passthrough while still logging, or
  handling provider-specific rate limit headers generically]`

**Proof**
- API latency overhead added: `[FILL: Xms]` · Requests/sec tested: `[FILL]` · Test coverage: `[FILL]`

📹 `[Demo GIF placeholder]` · 🔗 `[Live demo]` · 💻 `[GitHub repo]` · 📐 `[Architecture diagram]`

</details>

<details>
<summary><b>PromptCraft — Multi-model prompt testing tool (SSE streaming)</b></summary>

<br>

**Problem:** `[FILL: comparing model outputs side-by-side is slow/manual —
what specifically was painful before this existed?]`

**Solution:** `[FILL: how SSE streaming improves the actual UX/workflow]`

**Architecture**
```
[FILL: client → backend → parallel calls to N model APIs → SSE stream
back to client as each token/response arrives]
```

**Tech stack:** `[FILL]`

**Key engineering decisions**
- `[FILL: why SSE over websockets or polling — a real reason, e.g.
  "one-directional stream, no need for bidirectional complexity"]`

**Technical challenges**
- `[FILL: e.g. handling partial failures when one model API times out
  while others are still streaming]`

**Proof**
- Concurrent model calls tested: `[FILL]` · Lighthouse score: `[FILL]` · CI status: `[FILL: badge]`

📹 `[Demo GIF placeholder]` · 🔗 `[Live demo]` · 💻 `[GitHub repo]` · 📐 `[Architecture diagram]`

</details>

<details>
<summary><b>PersonalOS — Full-stack personal productivity system</b></summary>

<br>

**Problem:** `[FILL]`

**Solution:** `[FILL]`

**Tech stack:** `[FILL]`

**Key engineering decisions**
- `[FILL]`

**Technical challenges**
- `[FILL]`

📹 `[Demo GIF placeholder]` · 🔗 `[Live demo]` · 💻 `[GitHub repo]`

</details>

> ⚠️ **Action item:** Every `[FILL]` above needs a real, specific answer before
> this goes live. A recruiter or engineer who clicks "expand" and finds
> placeholders is worse off than one who never expanded it. Fill these from
> memory of what you actually built — the goal is precision, not polish.

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
- Linux, Azure

</td>
</tr>
</table>

---

## System Design — Currently Learning

- [ ] Load balancing strategies (round-robin vs. least-connections vs. consistent hashing)
- [ ] Caching layers — cache invalidation, write-through vs. write-behind
- [ ] Database indexing & query optimization
- [ ] Horizontal scaling patterns for stateful services (WebSocket/chat specifically)
- [ ] Message queues vs. pub/sub — when each is the right tool

## Engineering Principles I Apply

`SOLID` · `DRY` (without over-abstracting) · `KISS` · dependency injection over
tight coupling · tests written against behavior, not implementation.
`[FILL: one real example from a project where you actually applied one of
these — e.g. "Split ProxiAI's rate limiter into its own module so it could be
tested independently of the HTTP layer."]`

## DevOps Skills

- Containerizing multi-service apps with Docker Compose
- CI pipelines via GitHub Actions — `[FILL: what does your pipeline actually
  run? lint, test, build, deploy?]`
- Basic cloud deployment on Azure/Vercel — `[FILL: which projects, and what
  the deploy process looks like]`

## Development Workflow

`[FILL: how do you actually work? e.g. "Feature branches → PR → self-review
against a checklist → merge. I write the README before the first line of
implementation code so I'm forced to define scope up front."]`

## Roadmap

- `[FILL: e.g. "Add integration tests to ChatWave — currently unit-tested
  only"]`
- `[FILL: e.g. "Contribute a small fix to an open-source project I actually
  use"]`
- `[FILL: e.g. "Write up ProxiAI's rate-limiting design as a technical
  article"]`

## Open Source Contributions

`[FILL — if none yet, be honest: "No external contributions yet — actively
looking for a first issue to pick up." This is a better line than silence,
and far better than a fabricated one.]`

## Technical Writing

`[FILL: link if you have any — a design writeup, a blog post, even a detailed
README counts as a starting point]`

---

<div align="center">

<sub>Currently: MCA student @ COER University, building toward backend/full-stack roles.</sub>

</div>
