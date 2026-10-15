# PAIR — Agentic Dating Lab

A responsive, browser-only prototype for an agent-mediated matchmaking workflow.

## Run locally
Open `index.html` in a browser, or run a static server from this folder:

```bash
python -m http.server 8000
```
Then visit `http://localhost:8000`.

## Features
- 25 clearly labelled fictional seed personas for an end-to-end demo
- Add a participant with LinkedIn and Instagram public-profile URLs plus supplied profile text
- Profile dossier: interest themes, hobbies, potential needs, values/communication notes, confidence and source boundary
- Agent-date simulator: four-turn conversation between two profile agents, surfaced common ground and follow-up questions
- Pairwise compatibility scores and per-person ranked matches
- Search/filter, responsive layout, clickable profile cards and source links
- No backend required; data stays in browser memory for this prototype

## Important implementation boundary
This prototype intentionally does **not** scrape LinkedIn or Instagram, bypass login, or infer sensitive/private traits. The links are stored as references; analysis uses only text entered by the operator. The 25 starter profiles are fictional and must not be represented as real people. For a real-person demo, invite at least 25 consenting participants to submit their own public links and self-authored profile text.

## Scoring
Scores are deterministic exploratory signals based on exact interest overlap and broad theme overlap. They are not scientifically validated compatibility predictions and should not be used to make consequential decisions. The conversation is a transparent simulation, not an actual message sent to a person.

## Suggested production stack
- Frontend: Next.js + TypeScript + Tailwind
- API: Node.js / Fastify
- Storage: PostgreSQL with Prisma
- Agent orchestration: provider-neutral LLM adapter with structured JSON output
- Queue / observability: Redis + OpenTelemetry
- Ingestion: participant-submitted bio text or authorized platform APIs; do not rely on unauthorized scraping
- Deployment: Vercel (frontend) + managed API/database

## Demo video storyboard (under 3 minutes)
1. 0:00–0:20 — Show the 25-person demo pool and explain fictional seed data.
2. 0:20–0:55 — Open one agent dossier; show interests, needs, source boundaries.
3. 0:55–1:45 — Run agent dates and select a conversation; show both agents speaking and the connection/reflection notes.
4. 1:45–2:25 — Change “Rank for” and show personalized rankings with reasons.
5. 2:25–2:50 — Add a consenting participant's two URLs and supplied bio text, then open their dossier.
6. 2:50–3:00 — Explain scoring, data boundary, and next production steps.

## Known limitations
- No automatic extraction from profile URLs.
- New entries are in-memory and reset on reload.
- The seeded people are synthetic and the current agent dialogue is template-driven, not a live LLM.
- No hosted demo, GitHub repository, or YouTube video is created by this package.
