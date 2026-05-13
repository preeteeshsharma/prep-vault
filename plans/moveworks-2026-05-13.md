# Prep Plan: Moveworks — Senior Software Engineer
**Interview:** 2026-05-20
**Rounds:** sysdesign
**Generated:** 2026-05-13

---

## Day 1 — Conversation Intelligence & Intent Classification

### sysdesign: AI-Powered Conversation Routing System
- **Pattern / goal:** Design a system that ingests support conversations, classifies intent, and routes to appropriate resolution (human agent, knowledge base, or automated action).
- **Approach:**
  - Requirements: 10M messages/day, <500ms P99 latency, multi-language intent classification, fallback to human routing
  - Capacity: ~115 msg/sec peak, 50GB/day logs, need real-time classification + offline batch retraining
  - API design: `POST /route-conversation`, `GET /ticket/{id}/status`, async webhook callbacks
  - Data model: ConversationEvent (user message, timestamp, channel), IntentPrediction (confidence, label, model_version), RoutingDecision (destination, priority)
  - Core components: Message ingestion (Kafka), intent classifier (ML model service), routing engine (rule-based + learned policies), ticket store (SQL + cache), agent dispatcher
  - Deep dive: Intent classifier — cover cold-start (pre-trained model), drift detection (model monitoring), A/B testing new classifiers, fallback to keyword matching
  - Bottlenecks: Model inference latency, retraining frequency, confidence threshold tuning, handling out-of-domain intents
- **Time:** 60 min

---

## Day 2 — Knowledge Graph & FAQ Retrieval

### sysdesign: Semantic FAQ Matching & Self-Service Resolution
- **Pattern / goal:** Build a system that matches user queries against a knowledge base of FAQs/docs, ranks relevant articles, and serves answers with confidence scores—reducing human agent load.
- **Approach:**
  - Requirements: Search across 50k+ internal knowledge articles, <300ms response, multi-language, feedback loop to improve ranking, A/B test article order
  - Capacity: ~2M searches/day (~23 QPS), 5GB knowledge base, embed all articles once per day
  - API design: `POST /search-faq` (query, context, language), returns ranked list with snippets + confidence
  - Data model: Article (title, body, category, embedding, last_updated), SearchQuery (query_text, user_context, timestamp), Feedback (query_id, article_id, helpful_bool, user_id)
  - Core components: Embedding service (dense vector + sparse BM25), vector DB (Pinecone/Weaviate), BM25 index (Elasticsearch), ranking model (learned-to-rank on feedback), cache layer
  - Deep dive: Hybrid retrieval (dense + sparse), cold-start for new articles, measuring embedding quality, feedback loop to retrain ranker, handling domain-specific terminology
  - Bottlenecks: Embedding latency, relevance precision (false positives hurt UX), feedback data sparsity, knowledge base freshness
- **Time:** 60 min

---

## Day 3 — Ticket Lifecycle & State Management

### sysdesign: Support Ticket Management & Escalation System
- **Pattern / goal:** Design a system managing the full lifecycle of support tickets: creation, assignment, escalation rules, SLA tracking, and closure—with audit trails.
- **Approach:**
  - Requirements: 100k tickets/day, SLA alerts (4h response, 24h resolution), auto-escalation if stuck, reassignment logic, closure recommendation, compliance audit logs
  - Capacity: ~1 ticket/sec ingress, 10M active tickets in-flight, ~200 concurrent agents, state transitions every few sec
  - API design: `POST /ticket`, `PATCH /ticket/{id}` (status, assignee, priority), `GET /ticket/{id}` (full history), `GET /tickets?filter=...`, webhook on state change
  - Data model: Ticket (id, status, assignee_id, priority, created_at, updated_at, sla_deadline), TicketEvent (ticket_id, event_type, old_state, new_state, actor, timestamp), Comment (id, ticket_id, author, text, is_internal)
  - Core components: Ticket store (SQL with denorm for fast queries), event log (append-only), SLA monitor (cron job checking deadlines), assignment engine (skill-based + load-balanced), notification service, audit logger
  - Deep dive: Optimistic locking on concurrent updates, event sourcing for audit trail, handling re-assignment chains, SLA calculation across time zones, closure ML model (confidence threshold for recommendation)
  - Bottlenecks: Write amplification (every change fires events + notifications), SLA scan at scale (need indexed deadline column), re-assignment fairness under high churn
- **Time:** 60 min

---

## Day 4 — Automation Workflows & Action Execution

### sysdesign: Intelligent Automation Rules Engine
- **Pattern / goal:** Design a system that learns from resolution patterns and auto-executes routine actions (send email, create ticket, update CRM)—triggered by conversation signals or manual workflows.
- **Approach:**
  - Requirements: Execute 1M automation actions/day, <50ms action latency, support conditional logic (IF intent=refund AND sentiment=angry THEN escalate), audit all executions, no duplicate executions
  - Capacity: ~12 actions/sec peak, 100KB per action record, 10M stored workflows
  - API design: `POST /workflow` (create automation rule), `GET /workflow/{id}`, `POST /execute-action` (async, returns action_id), webhook for completion/failure
  - Data model: Workflow (id, trigger_condition, actions_list, version, enabled), Action (id, type, params, status, retry_count, created_at), ActionLog (action_id, status, error, executed_at)
  - Core components: Rule engine (DSL or low-code builder), workflow store (SQL), action queue (SQS/Kafka), action executor (worker pool), idempotency store (dedupe by action_id), external API client pool
  - Deep dive: Idempotency for external calls (POST to Slack, Salesforce, etc.), handling transient failures (exponential backoff), dead-letter queue for poison actions, version control on workflows (rollback if new version breaks), A/B testing new rules
  - Bottlenecks: External API rate limits (need circuit breaker), action executor throughput (scale workers), idempotency key storage (need fast lookup), workflow complexity → rule explosion
- **Time:** 60 min

---

## Day 5 — Agent Assist & Real-Time Suggestions

### sysdesign: Real-Time Agent Assistance & Suggestion Engine
- **Pattern / goal:** Build a system that watches agent–customer conversations in real-time, suggests relevant FAQs, next-best actions, and draft responses to accelerate resolution.
- **Approach:**
  - Requirements: Live suggestions within 2s of each customer message, <100ms latency to agent UI, support 5k concurrent agents, personalize by agent skill/history, measure impact (CSAT, handle time)
  - Capacity: ~500 concurrent conversations, 100k suggestions/day, embedding + ranking model inference at scale
  - API design: `POST /conversation-stream/{conversation_id}/message` (agent+customer turn), `GET /suggestions/{conversation_id}` (blocking or webhook), suggestion types: faq_links, next_action, draft_response
  - Data model: ConversationTurn (speaker, text, timestamp), SuggestionRequest (conversation_id, context_window), Suggestion (type, content, rank, confidence, clicked, helpful), AgentProfile (agent_id, skill_tags, resolution_rate)
  - Core components: Message stream processor (Kafka), context assembler (extract last N turns + ticket state), multi-model inference service (retrieve FAQ + predict action + generate draft), ranking model (personalized), cache (recent conversations in Redis), A/B test framework
  - Deep dive: Low-latency inference (use smaller model + caching, batch across agents), handling out-of-context intents (fallback suggestions), measuring drift (did model suggestions hurt quality?), personalization (agent skill tags), draft response generation (prompt engineering + guardrails)
  - Bottlenecks: Model serving latency (inference costs), ranking relevance (too many false positives clutter UI), draft quality (hallucinations), personalization data sparsity (new agents)
- **Time:** 60 min

---

## Day 6 — Analytics & Performance Monitoring

### sysdesign: Support Operations Analytics & Predictive Metrics
- **Pattern / goal:** Build analytics infrastructure tracking key metrics (resolution rate, CSAT, first-contact resolution) and predict SLA misses/escalations before they happen.
- **Approach:**
  - Requirements: 100M events/day from tickets + conversations, sub-minute dashboards, predict SLA miss 30 min before deadline, breakdown by agent/category/lang, detect anomalies, ad-hoc querying
  - Capacity: 1,000 events/sec, 50GB/day raw logs, ~100 concurrent dashboard users, 10TB historical warehouse
  - API design: `POST /analytics-event` (batch or stream), `GET /dashboard/{dashboard_id}`, `GET /metric/{metric_name}?filters=...&granularity=minute`, `GET /prediction/sla-miss/{ticket_id}`
  - Data model: AnalyticsEvent (ticket_id, event_type, dimension_tags, timestamp, value), Metric (metric_name, dimensions, value, timestamp), Prediction (ticket_id, sla_deadline, miss_probability, predicted_at)
  - Core components: Event ingestion (Kafka + Kinesis), stream processor (Spark/Flink, compute rolling metrics), data warehouse (Snowflake/BigQuery, batch + real-time), metrics store (TimescaleDB or ClickHouse), ML pipeline for SLA prediction (XGBoost on ticket features)
  - Deep dive: Metric definition (ensure consistency), handling late events, backfill missing data, SLA prediction model (feature eng: agent_load, ticket_complexity, category, time_of_day), alert thresholds (tuned by business)
  - Bottlenecks: Late-arriving events (out-of-order logs), dashboard query latency over large time ranges, prediction model retraining frequency, data drift in feature distributions
- **Time:** 60 min

---

## Day 7 — Mock Interview & Weak Area Review

### sysdesign: Full System Interview Simulation
- **Pattern / goal:** Simulate a full 60-minute sysdesign interview with a peer or structured self-assessment covering all aspects of Moveworks' core challenges.
- **Approach:**
  - Mock interview problem: **"Design the core routing + resolution engine for an AI support platform: conversations → intent classification → FAQ match OR escalation → ticket → agent assist. Handle 10M messages/day, 100k concurrent tickets, <500ms latency. How would you evolve this to add predictive insights?"**
  - Structure: Start with clarifying requirements (5 min) → API design (5 min) → data model (5 min) → architecture diagram (10 min) → drill one subsystem in depth (20 min) → discuss tradeoffs & bottlenecks (10 min) → extensibility for new requirements (5 min)
  - Focus areas from this plan: How to integrate intent classifier + FAQ retrieval, idempotency in downstream actions, real-time SLA monitoring, A/B testing automation rules, analytics-driven improvements
  - After mock: Review your notes on areas where you stumbled (latency assumptions? Scale math? Tradeoff justification?). These become focus areas for final prep.
- **Time:** 60 min

---

## Weak areas to revisit
None identified yet — first mock interview (Day 7) will surface gaps. Likely candidates post-mock: real-time ranking (latency vs. quality), idempotency patterns at scale, or multi-tenant isolation if the interviewer probes it.