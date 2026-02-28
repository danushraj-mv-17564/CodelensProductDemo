# CodeLens — Product Specification Document

> **Version:** 1.0  
> **Date:** February 27, 2026  
> **Author:** Danush  
> **Status:** Foundation Draft  
> **Classification:** Internal — Confidential

---

## Table of Contents

1. [Vision & Mission](#1-vision--mission)
2. [Product Identity](#2-product-identity)
3. [Core Philosophy](#3-core-philosophy)
4. [Architecture Decisions](#4-architecture-decisions)
5. [Phase 1 — Product Ingestion Engine](#5-phase-1--product-ingestion-engine)
6. [Phase 2 — Continuous Knowledge Evolution Engine](#6-phase-2--continuous-knowledge-evolution-engine)
7. [Phase 3 — Multi-Agent SDLC Orchestration Engine](#7-phase-3--multi-agent-sdlc-orchestration-engine)
8. [Phase 4 — Full SDLC Autonomous Flow](#8-phase-4--full-sdlc-autonomous-flow)
9. [Phase 5 — Automated Apple-Native AI Testing](#9-phase-5--automated-apple-native-ai-testing)
10. [Phase 6 — Self-Improvement Engine](#10-phase-6--self-improvement-engine)
11. [Competitive Landscape](#11-competitive-landscape)
12. [Technical Risks & Mitigations](#12-technical-risks--mitigations)
13. [Build Roadmap](#13-build-roadmap)
14. [Cost Model](#14-cost-model)

---

## 1. Vision & Mission

### Vision

**CodeLens is an Autonomous Product Intelligence Engine that understands, evolves, and builds software products end-to-end.**

Not just code completion. Not just agents. Not just testing automation.

CodeLens becomes:

> The institutional memory + engineering brain + execution engine of a software organization.

### Mission

Replace fragmented development workflows with a single, self-evolving intelligence layer that operates in three modes:

1. **Understand** — Ingest and deeply comprehend any codebase
2. **Construct** — Autonomously translate feature requests into tested, reviewed code
3. **Validate & Evolve** — Continuously test, measure, learn, and improve

### What Makes This Category-Defining

No existing product combines:

- A **persistent, evolving Product Knowledge Graph (PKG)** of a private codebase
- **Role-specialized AI agents** with hierarchical delegation across the full SDLC
- **Autonomous desktop/mobile test execution** pipelines (Apple-native)
- **Cross-release self-improvement** that learns from its own history

Partial attempts exist (Cursor, Devin, Copilot Workspace, Cody), but none achieve this end-to-end.

---

## 2. Product Identity

| Attribute | Value |
|---|---|
| **Product Name** | CodeLens |
| **Platform** | macOS (native SwiftUI application) |
| **Target Ecosystem** | Apple-first — Swift, SwiftUI, Xcode, XCUITest, Core Data, SwiftData, Combine |
| **Distribution** | Developer ID signed (direct download). Not Mac App Store. |
| **Minimum System** | Apple Silicon (M1+), macOS 14 Sonoma+, 16GB RAM |
| **Dependencies** | Xcode 15+, Xcode Command Line Tools |
| **AI Strategy** | Hybrid — Cloud (GPT-4o/Claude) for reasoning & generation, Local (MLX) for embeddings & classification |
| **Data Privacy** | Local-first. All project data stays on-device. Cloud calls send only code snippets, never full repos. |

---

## 3. Core Philosophy

### 3.1 Product-Aware, Not Just Code-Aware

Existing AI tools see code as text. CodeLens sees code as a **product** — with architecture, conventions, history, patterns, fragilities, and intent.

### 3.2 Knowledge Graph as the Backbone

The Product Knowledge Graph (PKG) is the single source of truth. Every agent reads from it, writes to it, and is grounded by it. Without the PKG, agents degenerate into "just another LLM wrapper."

### 3.3 Apple-First Specialization

Every competitor targets polyglot, general-purpose codebases. CodeLens goes **deep** on the Apple ecosystem: SwiftUI view hierarchies, Xcode build system, XCUITest automation, Core Data schemas, Swift Package Manager, Combine pipelines, Accessibility APIs. This depth is the moat.

### 3.4 Incremental Value Delivery

Each phase delivers **standalone value**. Phase 1 alone ("understand any Swift project instantly") is a useful product. No phase requires all other phases to be useful.

---

## 4. Architecture Decisions

### 4.1 Product Knowledge Graph (PKG) Storage

| Decision | Choice | Rationale |
|---|---|---|
| Primary store | **SQLite** | macOS-native, zero-config, battle-tested, supports recursive CTEs for graph traversal |
| Graph queries | Recursive CTEs (`WITH RECURSIVE`) | Path finding, dependency chains, impact analysis |
| Complex graph algorithms | In-memory `Dictionary<NodeID, [Edge]>` | PageRank, community detection, cycle detection — loaded from SQLite on demand |
| Future upgrade path | **Kuzu** (embeddable graph DB) | If Cypher query complexity warrants it |
| Rejected | Neo4j | Requires JVM + server process — wrong for a local macOS app |

**PKG Schema (conceptual):**

```
┌──────────────────────────────────────────────────┐
│                    PKG Layer                      │
├────────────────────┬─────────────────────────────┤
│  Structural Graph  │  Semantic Layer              │
│  (SQLite + FTS5)   │  (Vector embeddings)         │
├────────────────────┼─────────────────────────────┤
│  Node table:       │  Code chunk embeddings       │
│  id, type, name,   │  (768-dim vectors via MLX)   │
│  metadata (JSON)   │  Stored in SQLite BLOB       │
│                    │  + in-memory HNSW index       │
│  Edge table:       │                              │
│  src, dst, type,   │  Enables: "find modules      │
│  weight, metadata  │  related to networking"       │
├────────────────────┼─────────────────────────────┤
│  Temporal layer:   │                              │
│  Snapshots per     │                              │
│  commit hash       │                              │
└────────────────────┴─────────────────────────────┘
```

### 4.2 Multi-Agent Orchestration

| Decision | Choice | Rationale |
|---|---|---|
| Framework | **Custom Swift implementation** | All major frameworks (CrewAI, AutoGen, LangGraph) are Python-only, adding ~200MB, sandboxing issues, and fragility |
| Concurrency | Swift `async/await` + `TaskGroup` | Native, type-safe, perfect for parallel agent execution |
| Agent communication | Shared typed state object | Inspired by LangGraph's `State` model — but native Swift structs |
| Agent streaming | `AsyncStream<AgentOutput>` | Real-time UI updates as agents work |
| Traceability | Append-only SQLite log | Every agent decision, input, output, PKG mutation logged |

**Orchestration Architecture:**

```swift
enum AgentRole: String, CaseIterable {
    case metaOrchestrator, pm, architect, developer, test, reviewer, qa
}

struct AgentOutput {
    let role: AgentRole
    let artifacts: [Artifact]       // PRD, code diff, test file, review comments
    let pkgMutations: [PKGMutation] // Changes to the knowledge graph
    let confidence: Double          // 0.0–1.0
    let traceLog: [TraceEntry]      // Full audit trail
}

protocol Agent {
    var role: AgentRole { get }
    func execute(context: SDLCContext, pkg: PKGStore) async throws -> AgentOutput
}

class SDLCOrchestrator {
    let pipeline: [Agent]
    func run(featureRequest: String) -> AsyncStream<AgentOutput> { ... }
}
```

### 4.3 AI Model Strategy (Hybrid)

| Task | Location | Model | Rationale |
|---|---|---|---|
| AST parsing, graph construction | **Local** | No AI (pure computation) | CPU-bound, fast, private |
| Code embeddings | **Local** | `nomic-embed-text` via MLX | ~100 tokens/ms on M1 Pro |
| Commit classification | **Local** | Phi-3-mini (3B) via MLX | Simple classification, <1s |
| Convention learning | **Local** | Llama 3 8B (QLoRA fine-tuned via MLX) | Style is project-specific |
| Code generation | **Cloud** | Claude Sonnet / GPT-4o | Quality matters most |
| Architecture analysis | **Cloud** | Claude Opus / GPT-4o | Deepest reasoning needed |
| Test generation | **Cloud** | GPT-4o-mini / Claude Haiku | Good quality, low cost |
| PRD writing | **Cloud** | Claude Sonnet | Best structured writing |
| Metric analysis | **Local** | Create ML / Statistical | Pure computation |
| Recommendation text | **Local** | Phi-3-mini via MLX | Convert stats to text |

### 4.4 Distribution & Build

| Decision | Choice | Rationale |
|---|---|---|
| Distribution | Developer ID signed (Notarized) | `xcodebuild`, simulators, and DerivedData access require full disk permissions |
| Sandboxing | Disabled | Sandbox blocks `xcodebuild`, `xcrun simctl`, and project directory access |
| Update mechanism | Sparkle framework | Industry standard for non-App Store macOS apps |
| Xcode integration | Standalone app (reads project files directly) | Xcode Source Editor Extension API is too limited |
| Heavy processing | XPC services | Isolate memory-intensive parsing from main app process |

---

## 5. Phase 1 — Product Ingestion Engine

> **Goal:** Drop in a Swift project → get a deep, structured understanding of the entire codebase

### 5.1 Static Intelligence Extraction

| Capability | Technology | Feasibility |
|---|---|---|
| Parse entire codebase (AST-level) | **SwiftSyntax** (Apple first-party) | Production-ready |
| Module dependency graph | `.pbxproj` / `Package.swift` parser | Production-ready |
| Call graph (function → function) | SwiftSyntax call-site extraction | Production-ready |
| API contract map | SwiftSyntax protocol/function signature extraction | Production-ready |
| Storage schema model | Core Data `.xcdatamodeld` (XML) + SwiftData (SwiftSyntax) | Production-ready |
| UI hierarchy (SwiftUI View tree) | SwiftSyntax `body` declaration parsing | Achievable (~70-80% static coverage) |
| Test coverage mapping | `xccov` JSON export | Production-ready |
| Data flow graph (intra-function) | SwiftSyntax + SIL (`swiftc -emit-sil`) | Achievable |
| Data flow graph (inter-module) | LLM-augmented heuristic analysis | Bleeding-edge |

### 5.2 Semantic Understanding

Using LLM calls (cloud) with AST + dependency graph as context:

- **Architectural patterns:** MVVM, MVC, Clean Architecture, VIPER, TCA
- **Design system usage:** Custom component library detection
- **State management:** Combine, `@Observable`, TCA Store, manual delegates
- **Network abstraction:** URLSession wrappers, Moya/Alamofire, gRPC, GraphQL
- **Persistence patterns:** Core Data, SwiftData, GRDB, UserDefaults, Keychain
- **Error-handling conventions:** Result type, throws, Combine errors, custom error enums
- **Dependency injection:** Protocol-based, Environment, Container patterns

### 5.3 Product Knowledge Graph (PKG) Construction

**Node Types:**

| Node Type | Key Attributes |
|---|---|
| Module | name, type (framework/app/test), dependencies, LOC |
| File | path, module, language, LOC, last_modified |
| Type | name, kind (class/struct/enum/protocol/actor), module, conformances |
| Function | name, signature, type_owner, visibility, complexity |
| View | name, body structure, state properties, navigation targets |
| ViewModel | name, published properties, bound view(s), services used |
| Model | name, properties, persistence layer (Core Data/SwiftData/plain) |
| Service | name, protocols, dependencies, API calls |
| API Endpoint | URL pattern, method, request/response types |
| Database Entity | name, attributes, relationships, migration version |
| Test Case | name, target type, coverage, test kind (unit/integration/UI) |
| Bug (historical) | affected modules, commit hash, severity, resolution |

**Edge Types:**

| Edge Type | Description |
|---|---|
| `DEPENDS_ON` | Module/type dependency |
| `CALLS` | Function call site |
| `CONFORMS_TO` | Protocol conformance |
| `OWNS` | File contains type, type contains function |
| `BINDS_TO` | ViewModel ↔ View binding |
| `FLOWS_DATA` | Data flow between components |
| `TESTS` | Test case targets type/function |
| `PERSISTS_TO` | Model ↔ Database entity mapping |
| `NAVIGATES_TO` | View → View navigation |
| `CHANGED_IN` | Entity modified in commit |
| `CAUSED_BUG` | Change correlated with bug introduction |

### 5.4 Performance Targets

| Project Size | Ingestion Time (Target) | Notes |
|---|---|---|
| Small (50 files) | < 10 seconds | AST only, no LLM |
| Medium (200 files) | < 60 seconds | AST + local embeddings |
| Large (1000+ files) | < 5 minutes | Progressive loading, background LLM |
| Enterprise (5000+ files) | < 15 minutes | Parallelized, XPC service workers |

### 5.5 MVP Deliverable

**Ship in 4-6 weeks:**
- Parse a Swift project using SwiftSyntax → extract all types, functions, protocols, conformances
- Build module dependency graph + call graph → store in SQLite PKG
- Visualize as an interactive force-directed graph in SwiftUI (using Canvas/SpriteKit)
- One-shot LLM call to classify architecture pattern
- Display summary: *"Your project uses MVVM, has 47 views, 23 view models, 15 services, 92% of views have corresponding tests"*

---

## 6. Phase 2 — Continuous Knowledge Evolution Engine

> **Goal:** PKG stays alive — it watches, learns, and evolves with the project

### 6.1 Commit Watching

| Component | Technology |
|---|---|
| File system monitoring | `FSEvents` API (macOS-native, used by Spotlight/Time Machine) |
| Git diff parsing | `libgit2` via SwiftGit2 or `git diff --name-only` |
| Change triggers | On `.swift` file changes → re-parse changed files → compute graph delta |

### 6.2 Incremental Graph Updates

1. Detect changed files via FSEvents
2. Re-parse only changed files with SwiftSyntax
3. Diff old AST vs new AST → compute node/edge additions and removals
4. Apply as a **transactional** PKG update (all-or-nothing per commit)
5. Update embeddings for changed code chunks
6. Propagate edge changes (e.g., function signature change → update all caller edges)

### 6.3 Pattern Learning

| What It Learns | How | Storage |
|---|---|---|
| Recurring bug patterns | Classify commit messages + correlate with affected modules | PKG temporal annotations |
| Coding style & conventions | SwiftLint metrics + LLM summarization | Project conventions document (auto-generated Markdown) |
| Test philosophy | Test-to-source ratio, mocking patterns, assertion density | PKG metadata |
| Module fragility trends | Change frequency × bug rate × coverage inverse | PKG node attributes |
| Developer preferences | Which suggestions get accepted vs rejected | Local preference store |

### 6.4 Background Processing

- `NSBackgroundActivityScheduler` for periodic analysis when app is idle
- `LaunchAgent` option for commit processing even when app isn't running
- Progressive notifications: "3 new commits processed. NetworkModule changed significantly."

### 6.5 MVP Deliverable

**Ship in 2-3 weeks (after Phase 1):**
- Watch git repo for new commits via FSEvents
- Re-parse changed `.swift` files → update dependency graph
- Project health dashboard: bug density by module, test coverage trend, most-changed files
- Display: *"Last 30 days: 14 bug fixes, 60% in NetworkLayer. Coverage: 72% → 68%."*

---

## 7. Phase 3 — Multi-Agent SDLC Orchestration Engine

> **Goal:** Specialized AI agents that collaborate through the PKG to construct software

### 7.1 Agent Definitions

#### Meta-Orchestrator
- **Role:** Oversees entire lifecycle, allocates tasks, tracks progress, handles failures
- **Input:** Feature request (natural language)
- **Output:** Execution plan, agent assignments, progress tracking
- **Model:** Claude Sonnet / GPT-4o

#### Product Manager (PM) Agent
- **Role:** Convert feature description to structured requirements
- **Output:** Requirements doc, acceptance criteria, edge cases, non-functional requirements
- **PKG Reads:** Existing modules, current capabilities, test coverage gaps
- **Model:** Claude Sonnet

#### Architect Agent
- **Role:** Design feature integration plan, predict architectural impact
- **Output:** Integration plan, updated system diagrams, impacted modules list, risk assessment
- **PKG Reads:** Module dependency graph, data flow graph, architectural patterns
- **Model:** Claude Opus / GPT-4o (most critical — needs deepest reasoning)

#### Developer Agent
- **Role:** Write code that adheres to project conventions
- **Output:** Code changes (file diffs), updated documentation
- **PKG Reads:** Conventions, existing code patterns, related modules, API contracts
- **Model:** Claude Sonnet / GPT-4o

#### Test Engineer Agent
- **Role:** Write comprehensive tests for new/changed code
- **Output:** Unit tests, integration tests, snapshot tests, regression tests
- **PKG Reads:** Test patterns, coverage targets, existing test utilities
- **Model:** GPT-4o-mini / Claude Haiku

#### QA Automation Agent
- **Role:** Generate UI automation flows, stress scenarios
- **Output:** XCUITest code, performance test configurations
- **PKG Reads:** View tree, navigation flow, accessibility identifiers
- **Model:** GPT-4o-mini

#### Reviewer Agent
- **Role:** Enforce code quality, architectural compliance, security
- **Output:** Review comments, approval/rejection, suggested fixes
- **PKG Reads:** Conventions, architectural constraints, historical code review patterns
- **Model:** Claude Sonnet

### 7.2 Inter-Agent Communication

```
Feature Request
      │
      ▼
┌─────────────────┐
│ Meta-Orchestrator │──── Creates execution plan
└────────┬────────┘
         │
         ▼
┌────────────────┐     Writes: PRD, acceptance criteria
│    PM Agent    │───→ to shared SDLCContext
└────────┬───────┘
         │
         ▼
┌────────────────┐     Writes: integration plan, impacted modules
│ Architect Agent│───→ to shared SDLCContext
└────────┬───────┘
         │
         ▼
┌────────────────┐     Writes: code diffs
│ Developer Agent│───→ to shared SDLCContext
└────────┬───────┘
         │
         ├─────────────────────┐
         ▼                     ▼
┌──────────────┐     ┌──────────────┐
│  Test Agent  │     │   QA Agent   │   ◄── Can run in parallel
└──────┬───────┘     └──────┬───────┘
       │                    │
       └────────┬───────────┘
                ▼
┌────────────────┐     Writes: approval/rejection, fixes needed
│ Reviewer Agent │───→ to shared SDLCContext
└────────┬───────┘
         │
         ▼
    (If rejected → loop back to Developer Agent, max 3 iterations)
```

### 7.3 Human-in-the-Loop Gates

Configurable approval points:

| Gate | Default | User Can Override To |
|---|---|---|
| After PM Agent (PRD) | Auto-approve | Require human review |
| After Architect Agent (plan) | **Require human review** | Auto-approve |
| After Developer Agent (code) | **Require human review** | Auto-approve |
| After Test Agent (tests) | Auto-approve | Require human review |
| After Reviewer Agent (review) | **Require human review** | Auto-approve |
| Before merge to main branch | **Always require human** | Cannot override |

### 7.4 Cost Per Feature Request

| Scenario | LLM Calls | Estimated Cost |
|---|---|---|
| Simple (single module) | 10-15 calls | $0.30-1.00 |
| Medium (2-3 modules) | 20-30 calls | $1.00-3.00 |
| Complex (5+ modules) | 40-60 calls | $3.00-8.00 |
| Full SDLC with retries | 50-175 calls | $5.00-18.00 |

### 7.5 MVP Deliverable

**Ship in 4-6 weeks (after Phase 1):**
- Implement PM Agent + Developer Agent only
- User types feature request → PM generates acceptance criteria (PKG-grounded) → Developer generates code (convention-aware)
- Side-by-side display: requirements | generated code | diff view
- No auto-execution — human reviews and applies manually

---

## 8. Phase 4 — Full SDLC Autonomous Flow

> **Goal:** Feature request → compiling, tested branch — autonomously

### 8.1 Execution Pipeline

```
Feature Request
      │
      ▼
[Phase 3 Agents produce: PRD + Plan + Code + Tests + Review]
      │
      ▼
┌─────────────────┐
│ Execution Engine │
├─────────────────┤
│ 1. Create git branch (feature/<name>)                    │
│ 2. Write generated files to disk                          │
│ 3. Run: xcodebuild build                                  │
│ 4. If build fails → parse errors → feed to Developer Agent │
│ 5. Developer Agent fixes → write → rebuild                 │
│ 6. Repeat (max 5 iterations)                               │
│ 7. If build succeeds → run: xcodebuild test                │
│ 8. If tests fail → parse failures → feed to Test Agent     │
│ 9. Test Agent fixes → rerun                                │
│ 10. Present results: branch + build log + test results     │
└─────────────────┘
```

### 8.2 Self-Correction Loop

**Key safeguards:**

| Safeguard | Implementation |
|---|---|
| Max iteration cap | 5 build attempts, 3 test fix attempts |
| Oscillation detection | Track all error hashes; if error recurs → bail to human |
| Rollback | Git-based: `git reset --hard` to clean state on failure |
| Partial success | Present working branch even if some tests fail |
| Cost cap | Stop if LLM cost exceeds configurable threshold per feature |

### 8.3 Build System Integration

| Capability | Command | Output |
|---|---|---|
| Build | `xcodebuild build -scheme X -destination 'platform=macOS'` | Build log, errors |
| Test | `xcodebuild test -scheme X -destination 'platform=macOS'` | `.xcresult` bundle |
| Error parsing | Parse `xcodebuild` output + SwiftSyntax `DiagnosticEngine` | Structured error objects |
| Result parsing | `xcresulttool get --format json` on `.xcresult` | Test pass/fail, coverage |
| Incremental build | Default `xcodebuild` behavior (only recompiles changed files) | Faster iteration |

### 8.4 MVP Deliverable

**Ship in 3-4 weeks (after Phase 3):**
- Take Developer Agent output → create git branch → write files
- Run `xcodebuild build` → if fails, parse errors, retry (max 3)
- If succeeds → run `xcodebuild test` → display results
- No auto-merge. Present branch + results to user.

---

## 9. Phase 5 — Automated Apple-Native AI Testing

> **Goal:** AI-generated, PKG-aware test suites for SwiftUI apps

### 9.1 SwiftUI Semantic Understanding

| Analysis | Method | Coverage |
|---|---|---|
| View tree map | SwiftSyntax `body` parsing | ~70-80% (static) |
| Navigation flow graph | Extract `NavigationLink`, `NavigationStack`, `.sheet`, `.fullScreenCover` | ~70% (misses programmatic routing) |
| State mutation graph | Track `@State`, `@Binding`, `@ObservedObject`, `@EnvironmentObject` | ~60% (Combine pipelines are hard) |
| Accessibility identifier map | Extract `.accessibilityIdentifier()` modifiers | 100% of declared identifiers |

### 9.2 XCUITest Generation

| Test Type | Reliability | Approach |
|---|---|---|
| Smoke tests (launch, verify elements) | ~90% | Template-based + accessibility ID map |
| Navigation flow tests | ~70% | PKG navigation graph + LLM |
| Form input + validation | ~80% | LLM with field type inference |
| Complex stateful interactions | ~40% | LLM + state mutation graph |
| Edge cases (memory/network) | ~60% | Template-based simulation |

**The 80/20 rule:** Auto-generate the straightforward 80% of tests. The complex 20% stays human-assisted.

### 9.3 Simulation & Edge Cases

| Scenario | Method |
|---|---|
| Memory pressure | `xcrun simctl spawn <device> memory_pressure critical` |
| Network failure | Mock `URLProtocol` injection via app launch environment |
| Background/foreground | `XCUIDevice.shared.press(.home)` + `app.activate()` |
| Slow network | Network Link Conditioner profile via `simctl` |
| Rotation | `XCUIDevice.shared.orientation = .landscapeLeft` |
| Accessibility audit | Apple's `AXAudit` + LLM review of view hierarchy |

### 9.4 Test Execution Infrastructure

| Component | Technology |
|---|---|
| Local simulator | `xcrun simctl` + `xcodebuild test -destination` |
| Parallel testing | Multiple simulator instances via `xcodebuild test -parallel-testing-enabled YES` |
| Screenshot diffing | `swift-snapshot-testing` (Point-Free) |
| Crash clustering | Parse `.ips` crash files → cluster by stack trace similarity |
| Result reporting | Parse `.xcresult` bundles → structured test report |
| Future: Device farm | AWS Device Farm / BrowserStack (remote execution) |

### 9.5 Accessibility Identifier Auto-Injection

When CodeLens detects views **without** `.accessibilityIdentifier()`:
1. Flag as "untestable views" in the PKG
2. Suggest identifier additions via Developer Agent
3. Optionally auto-add identifiers following naming convention: `<ModuleName>.<ViewName>.<ElementType>.<Description>`

### 9.6 MVP Deliverable

**Ship in 4-6 weeks (can run parallel to Phase 3):**
- Parse SwiftUI views → extract view hierarchy + accessibility identifiers
- User selects a view → CodeLens generates a basic XCUITest (launch, navigate, verify elements)
- Run via `xcodebuild test` → show pass/fail
- No edge case simulation, no screenshot diffing, no device farm — just "auto-smoke-test any view"

---

## 10. Phase 6 — Self-Improvement Engine

> **Goal:** CodeLens gets smarter with every release

### 10.1 Metrics Collection

| Metric | Source | Frequency |
|---|---|---|
| Test coverage per module | `xccov` JSON export | Every test run |
| Bug density (bug-fix commits / total commits) | Git history + commit classification | Every commit |
| Regression frequency | Test pass/fail history across commits | Every test run |
| Change frequency (churn) | Git log per module | Daily |
| Build time per module | `xcodebuild` timing output | Every build |
| Agent success rate | Trace log (feature request → successful merge or not) | Per feature |
| LLM cost per feature | API call logs | Per feature |

### 10.2 Fragility Scoring

```
fragility(module) = (bug_fix_commit_ratio) × (1 - test_coverage) × (change_frequency_z_score)
```

Modules with high fragility scores trigger:
- Reviewer Agent applies stricter review
- Test Agent generates more edge case tests
- Architect Agent flags risky integration plans involving that module
- Dashboard highlights in red

### 10.3 Adaptive Agent Behavior

| Signal | Agent Response |
|---|---|
| Module fragility > 0.7 | Test Agent: increase edge case density by 2× |
| Architecture change correlated with bugs (>3 instances) | Architect Agent: flag pattern and suggest alternative |
| Test coverage dropping trend | Developer Agent: include tests with every code change |
| Specific error type recurring | Developer Agent: pre-apply known-good pattern for that error |
| Agent success rate < 50% for module | Escalate to human: "I struggle with this module — more context needed" |

### 10.4 Cold Start Mitigation

Day one (no history):
- Use **industry heuristics**: high churn + low coverage = high risk
- Apply conservative defaults for all agent strictness levels
- Start collecting data immediately

After 30 days: basic fragility scores become meaningful  
After 90 days: trend analysis becomes reliable  
After 6 months: cross-release learning kicks in

### 10.5 Feedback Loop Stability

To prevent runaway cycles ("fragile → more tests → more bugs found → more fragile → ..."):
- Track **bug introduction rate** (new bugs per change), not total bug count
- Require **statistical significance** (>3 corroborating data points) before adjusting agent behavior
- Hard cap on strictness multipliers (max 3× default)

### 10.6 MVP Deliverable

**Ship in 2-3 weeks (after Phases 2+4):**
- After each test run: collect coverage, pass/fail per module, build time
- Compare vs previous run: "Coverage improved in ModuleA (+5%), Regressed in ModuleB (-3%)"
- Compute fragility score per module
- Dashboard: "Top 5 riskiest modules in your project"

---

## 11. Competitive Landscape

| Capability | Cursor | Devin | Copilot Workspace | Cody (Sourcegraph) | **CodeLens** |
|---|---|---|---|---|---|
| Code completion | Yes | Yes | Yes | Yes | Yes |
| Codebase indexing | Embeddings (RAG) | On-demand (agent loop) | Shallow | SCIP code graph + RAG | **PKG (deep graph)** |
| Persistent knowledge graph | No | No | No | No | **Yes** |
| Semantic understanding (architecture) | No | No | No | Partial | **Yes** |
| Multi-agent orchestration | No | Single agent | Single agent | No | **Full hierarchy** |
| Full SDLC lifecycle | No | Attempted | Plan → code only | No | **Yes (closed loop)** |
| Autonomous build/test cycle | No | Partial | No | No | **Yes** |
| UI test generation | No | No | No | No | **Yes (XCUITest)** |
| Cross-release learning | No | No | No | No | **Yes** |
| Apple ecosystem depth | Generic | Generic | Generic | Generic | **Deep specialization** |

### Unfair Advantages

1. **PKG as institutional memory** — every interaction makes the system smarter
2. **Apple-first depth** — SwiftUI, Xcode, XCUITest, Core Data knowledge is a moat
3. **Closed-loop execution** — not just generating code, but building, testing, and iterating
4. **Self-improvement** — the product gets better over time without user intervention

---

## 12. Technical Risks & Mitigations

| Risk | Severity | Mitigation |
|---|---|---|
| LLM hallucination in architecture changes | **Critical** | Reviewer Agent validates against PKG. Hard gates requiring compilation before proceeding. |
| Infinite correction loops (build/test cycle) | **High** | Max 5 iterations. Oscillation detection (recurring error hash). Cost cap per feature. |
| Context window limitations | **High** | PKG provides focused context retrieval (not entire codebase). RAG + graph query = relevant context only. |
| SwiftUI View tree static analysis incompleteness | **Medium** | Hybrid approach: static (70-80%) + runtime accessibility hierarchy. Document limitations honestly. |
| Inter-module data flow analysis accuracy | **Medium** | LLM-augmented heuristics with confidence scores. Flag low-confidence edges in PKG. |
| Cloud LLM cost at scale | **Medium** | Aggressive caching. Cheaper models for templated tasks. Progressive capability (simple tasks = local, complex = cloud). |
| Runtime cost / memory on M1 16GB | **Medium** | XPC service isolation. Lazy loading. Cap concurrent simulators. Profile aggressively. |
| Swift compilation speed (iteration bottleneck) | **Medium** | Incremental builds. Modular project structure. Cache DerivedData intelligently. |
| Xcode version compatibility | **Low** | Pin supported Xcode range. Test across latest 2 Xcode versions. |

---

## 13. Build Roadmap

```
Month 1-2:   Phase 1 MVP — Product Ingestion + PKG + Visualization
             └─ Value: "Understand any Swift project instantly"

Month 2-3:   Phase 2 MVP — Continuous Knowledge Evolution
             └─ Value: "Living project health dashboard"

Month 3-5:   Phase 3 MVP — PM Agent + Developer Agent
             └─ Value: "Feature request → spec + code draft"

Month 5-6:   Phase 5 MVP — Basic XCUITest Generation
             └─ Value: "Auto-generate smoke tests for any view"

Month 6-8:   Phase 4 MVP — Build + Test Autonomous Loop
             └─ Value: "Feature request → compiling, tested branch"

Month 8-10:  Phase 6 MVP — Self-Improvement Dashboard
             └─ Value: "Quantified, learning project health insights"

Month 10+:   Full agent hierarchy, advanced testing, cross-project
             learning, enterprise features, team collaboration
```

### Why This Order

1. **Phase 1** delivers standalone value and is the **hard prerequisite** for everything (PKG)
2. **Phase 2** is a small incremental step that makes Phase 1 continuously useful
3. **Phase 3** is the first "wow" feature — describe a feature, get code
4. **Phase 5** (testing) before Phase 4 (full loop) because testing infra is needed for the loop
5. **Phase 4** combines Phase 3 + Phase 5 into the closed loop
6. **Phase 6** requires accumulated data from all previous phases

---

## 14. Cost Model

### Development Cost (Solo Developer)

| Phase | Duration | Notes |
|---|---|---|
| Phase 1 MVP | 4-6 weeks | Foundation — invest heavily here |
| Phase 2 MVP | 2-3 weeks | Incremental on Phase 1 |
| Phase 3 MVP | 4-6 weeks | Agent system + LLM integration |
| Phase 5 MVP | 4-6 weeks | Can parallel with Phase 3 |
| Phase 4 MVP | 3-4 weeks | Combines Phase 3 + 5 |
| Phase 6 MVP | 2-3 weeks | Analytics + dashboards |
| **Total to full MVP suite** | **~6-10 months** | |

### Operational Cost (Per User/Month, Active Use)

| Item | Monthly Cost |
|---|---|
| Cloud LLM calls (50 features/month) | ~$400 |
| Local compute (electricity) | ~$10 |
| Optional remote test runners (2 Mac minis) | ~$200 |
| **Total** | **~$600/month** |

### Revenue Model (Future)

| Tier | Price | Includes |
|---|---|---|
| **Indie** | $29/month | Phase 1 + 2 + limited Phase 3 (10 features/month) |
| **Pro** | $99/month | All phases. 50 features/month. |
| **Team** | $49/seat/month | All phases + shared PKG + team insights |
| **Enterprise** | Custom | Self-hosted, unlimited, SLA, SSO |

---

> **Next Document:** `02_APP_WIREFRAMES.md` — Complete macOS application wireframe design

---

*CodeLens — The Autonomous Software Development Intelligence Platform*  
*Built by Danush. Powered by AI. Grounded by knowledge.*
