# Prep Plan: Moveworks — Senior Software Engineer
**Interview:** 2026-05-20
**Rounds:** LLD
**Generated:** 2026-05-13

---

## Day 1 — LLD Foundations & Conversational AI

### LLD: Conversational AI Dialog Engine
- **Pattern / goal:** Design a system that manages multi-turn conversations, intent classification, and response routing for an AI assistant.
- **Approach:**
  - Phase 1 (5 min): Requirements — clarify scope: single user conversations vs. multi-user, persistence, concurrency, intent confidence thresholds, fallback handling
  - Phase 2 (3 min): Data models — define immutable `Message`, `Intent`, `Confidence` value objects; mutable `Conversation`, `DialogState` entities
  - Phase 3 (15 min): Class & interface design — introduce **State pattern** for dialog states (Listening → Processing → Responding); define sealed `Intent` interface with subtypes (HR, IT, Payroll); check that illegal states (e.g., responding before processing) are unrepresentable
  - Phase 4 (10 min): Implement happy path (user utterance → intent classification → response generation); trace edge cases (low confidence, no match, timeout); walk through a concrete support ticket resolution scenario
  - Phase 5 (5 min): Extensibility — show how adding a new intent type (Finance) requires only a new sealed subtype; how swapping the NLP classifier impacts only one component
- **Time:** 38 min

---

## Day 2 — Workflow & Task Management

### LLD: Ticket Routing & Assignment Engine
- **Pattern / goal:** Design a system that receives support tickets, extracts intent, routes to appropriate teams, and manages assignment lifecycle.
- **Approach:**
  - Phase 1 (5 min): Requirements — scope: single/multi-tenant, SLA enforcement, skill-based routing, reassignment, escalation paths, audit trail
  - Phase 2 (3 min): Data models — immutable `Ticket`, `RoutingDecision`, `SLA` value objects; mutable `Assignment`, `TicketState` entities with clear ownership
  - Phase 3 (15 min): Class & interface design — apply **Strategy pattern** for routing logic (skill-based, round-robin, priority-queue); define sealed `TicketStatus` (Open → Assigned → In-Progress → Resolved); use **Builder** for complex Ticket creation; ensure no ticket can be assigned without validation
  - Phase 4 (10 min): Implement: ticket creation → routing decision → agent assignment → SLA tracking; handle reassignment and escalation; trace a concrete high-priority ticket through resolution
  - Phase 5 (5 min): Extensibility — adding a new routing strategy (ML-based) requires only a new Strategy class; adding SLA metrics impacts only the monitoring component
- **Time:** 38 min

---

## Day 3 — Knowledge & Context Management

### LLD: Knowledge Base Search & Retrieval System
- **Pattern / goal:** Design a system that indexes, searches, and ranks knowledge articles to power conversational AI and self-service resolution.
- **Approach:**
  - Phase 1 (5 min): Requirements — scope: indexed article types, full-text search, relevance ranking, caching, multi-language support, update frequency
  - Phase 2 (3 min): Data models — immutable `Article`, `SearchQuery`, `Relevance` value objects; mutable `KnowledgeIndex`, `SearchCache` entities
  - Phase 3 (15 min): Class & interface design — define sealed `IndexStrategy` interface (BM25, TF-IDF, vector similarity); apply **Repository pattern** for data access; use **Decorator pattern** for ranking filters (recency, popularity, category); ensure stale indexes are never returned
  - Phase 4 (10 min): Implement: article indexing → query parsing → ranked search → caching; handle tie-breaking and result pagination; trace a user search for "reset password" returning relevant docs in correct order
  - Phase 5 (5 min): Extensibility — swapping BM25 for semantic search impacts only IndexStrategy; adding a new ranking signal (user feedback) is isolated to the Decorator layer
- **Time:** 38 min

---

## Day 4 — Integration & External Services

### LLD: Webhook Delivery & Retry System
- **Pattern / goal:** Design a system that reliably delivers webhooks to external systems with backoff, dead-lettering, and idempotency.
- **Approach:**
  - Phase 1 (5 min): Requirements — scope: event types, retry limits, backoff strategy, dead-letter queue, idempotency keys, monitoring, delivery guarantee (at-least-once or exactly-once)
  - Phase 2 (3 min): Data models — immutable `Event`, `WebhookPayload`, `DeliveryAttempt` value objects; mutable `WebhookEndpoint`, `RetrySchedule` entities
  - Phase 3 (15 min): Class & interface design — apply **Observer pattern** for event publishing; use **Exponential Backoff Strategy** for retries; define sealed `DeliveryStatus` (Pending → Delivered → Failed → Dead-lettered); idempotency key ensures no duplicate side-effects
  - Phase 4 (10 min): Implement: event creation → webhook registration → retry queue processing → dead-letter handling; trace a failed delivery that succeeds on retry 2; show timeout and exhaustion flows
  - Phase 5 (5 min): Extensibility — adding a new event type requires registering a listener; changing backoff algorithm impacts only the Strategy; adding webhook signing/TLS is isolated to the serialization layer
- **Time:** 38 min

---

## Day 5 — Conversational State & Context

### LLD: Multi-Turn Conversation Context Manager
- **Pattern / goal:** Design a system that maintains rich conversation context across multiple turns, preserving user intent, extracted entities, and conversation history.
- **Approach:**
  - Phase 1 (5 min): Requirements — scope: context window size, persistence (session vs. long-term), entity extraction, slots/variables, context expiration, privacy/PII handling
  - Phase 2 (3 min): Data models — immutable `Message`, `Entity`, `ContextSnapshot` value objects; mutable `ConversationContext`, `SlotFiller` entities with explicit ownership
  - Phase 3 (15 min): Class & interface design — apply **Repository pattern** for context storage; use **Memento pattern** to save/restore dialog state; define sealed `ContextType` (Short-term, Long-term, Session); use value objects to enforce immutability of context snapshots
  - Phase 4 (10 min): Implement: message arrival → entity extraction → slot filling → context update; handle context expiration and PII redaction; trace a multi-turn IT ticket scenario (user → AI → clarification → resolution)
  - Phase 5 (5 min): Extensibility — adding a new entity type (phone number) impacts only SlotFiller; changing storage backend (Redis → DB) is isolated to Repository; adding PII detection is a pluggable filter in the extraction pipeline
- **Time:** 38 min

---

## Day 6 — Skills & Quality Assurance

### LLD: Agent Skill Profiling & Quality Assurance System
- **Pattern / goal:** Design a system that tracks agent skills, measures resolution quality, and suggests skill development paths.
- **Approach:**
  - Phase 1 (5 min): Requirements — scope: skill taxonomy, competency levels, quality metrics (CSAT, resolution time, accuracy), coaching recommendations, leaderboards
  - Phase 2 (3 min): Data models — immutable `Skill`, `QualityScore`, `Competency` value objects; mutable `AgentProfile`, `PerformanceMetric` entities
  - Phase 3 (15 min): Class & interface design — define sealed `Metric` interface (CSAT, ResolutionTime, Accuracy); apply **Strategy pattern** for skill assessment; use **Composite pattern** for skill hierarchies (IT > Networks > Switching); ensure competency levels are validated (no jumps from Novice to Expert)
  - Phase 4 (10 min): Implement: skill acquisition → performance measurement → skill-to-ticket matching; trace an agent with IT skills and high CSAT being recommended for escalations; handle certification expiry
  - Phase 5 (5 min): Extensibility — adding a new quality metric requires a new Metric subtype; changing assessment logic impacts only Strategy; adding certification tracking is isolated to the profile entity
- **Time:** 38 min

---

## Day 7 — Capstone & Refinement

### LLD: End-to-End AI Assistant Resolution Pipeline
- **Pattern / goal:** Integrate all prior subsystems into one cohesive end-to-end flow: user query → intent → knowledge retrieval → routing → agent assignment → resolution.
- **Approach:**
  - Phase 1 (5 min): Requirements — restate: high-level flow, SLAs, escalation criteria, analytics, user feedback loop
  - Phase 2 (3 min): Data models — consolidate immutable `Request`, `ResolutionOutcome` value objects; mutable `AssistantSession`, `PipelineState` entities
  - Phase 3 (15 min): Class & interface design — use **Facade pattern** to orchestrate all prior components; define sealed `ResolutionPath` (Self-service → Human → Escalation); apply **Chain of Responsibility** for escalation logic; ensure no request bypasses required validation
  - Phase 4 (10 min): Implement: complete happy path from inbound query to closure; trace branching: auto-resolution via KB vs. human hand-off vs. escalation; handle failures at each stage
  - Phase 5 (5 min): Extensibility — adding a new resolution channel (chatbot → phone) impacts only ResolutionPath; adding feedback collection is a Decorator on the outcome; introducing A/B testing is isolated to a routing interceptor
- **Time:** 38 min

---

## Weak areas to revisit
None identified yet — first session will surface these. After Day 1, review which LLD patterns (State, Strategy, Repository, Builder, Decorator, Facade, Chain of Responsibility) felt less natural, and revisit those with additional problems.