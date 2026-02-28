# Ask CodeLens

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** AI · **Phase 1 — Shipped**  
> **Accent Color:** `#64D2FF` (teal) · **SF Symbol:** `bubble.left.and.text.bubble.right.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#64D2FF` (teal)  
**Purpose:** Chat with your codebase. Ask questions, get answers grounded in your actual code.

### 9.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  ⚠ No AI provider configured. │                        ║
║  ──────────────────  │                     Extended 🔘│                        ║
║   Explore           ▾│                     Thinking  │                        ║
║  📁 Projects         │                               │                        ║
║  🏛 Architecture     │                               │                        ║
║  📦 Dependencies     │                               │                        ║
║  🔍 Search           │                               │                        ║
║  ──────────────────  │         ┌──────────┐          │                        ║
║   Create            ▾│                               │    💬    │              ║
║  📄 Context          │                               │  (circle)│             ║
║  🔨 Tasks            │         └──────────┘          │                        ║
║  🧩 Blueprints       │                               │                        ║
║  ──────────────────  │       Ask CodeLens            │                        ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests            │  Ask questions about your code│                        ║
║  🔒 Security         │  CodeLens will search your cod│                        ║
║  ⚡ Performance      │  and provide answers.         │                        ║
║  ──────────────────  │                               │                        ║
║   Knowledge         ▾│                               │                        ║
║  📖 Wiki             │                               │                        ║
║  📜 Conventions      │                               │                        ║
║  📰 Changelog        │                               │                        ║
║  ──────────────────  │                               │                        ║
║   Insights          ▾│                               │                        ║
║  ♡ Health            │                               │                        ║
║  △ Improve           │                               │                        ║
║  📊 Timeline         │                               │                        ║
║  ──────────────────  │                               │                        ║
║   AI                ▾│                               │                        ║
║  🧠 Intelligence     │                               │                        ║
║  💬 Ask CodeLens    ●│                               │                        ║
║  🐛 Debug            │                               │                        ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │                               │                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Ask about this codebase...                                         ▶         ║
║  ⊙ Claude Sonnet 4.5                                                          ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 9.2 Active Chat State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                     Extended 🔘│                        ║
║  🏠 Home             │                     Thinking  │   Referenced Sources   ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│                               │   ────────────────     ║
║  📁 Projects         │  ┌───── You ──────────────────│                        ║
║  🏛 Architecture     │                               │ How does the network re║
║  📦 Dependencies     │                               │ logic work in this proj║
║  🔍 Search           │  └────────────────────────────│      NetworkModule     ║
║  ──────────────────  │                               │                        ║
║   Create            ▾│  ┌───── CodeLens ─────────────│   📄 RetryPolicy.swift  ║
║  📄 Context          │                               │                        ║
║  🔨 Tasks            │                               │ The retry logic in **Tr║
║  🧩 Blueprints       │                               │ Companion** is handled ║
║  ──────────────────  │                               │ `RetryPolicy` in       ║
║   Quality           ▾│                               │ `NetworkModule`.       ║
║  ✅ Tests            │                               │                        ║
║  🔒 Security         │                               │ It uses exponential bac║
║  ⚡ Performance      │                               │ with jitter:           ║
║  ──────────────────  │                               │                        ║
║   Knowledge         ▾│                               │ ```swift               ║
║  📖 Wiki             │                               │ func retry<T>(         ║
║  📜 Conventions      │                               │   maxAttempts: Int = 3,║
║  📰 Changelog        │                               │   delay: TimeInterval =║
║  ──────────────────  │                               │ ) async throws -> T    ║
║   Insights          ▾│                               │ ```                    ║
║  ♡ Health            │                               │                        ║
║  △ Improve           │                               │ The policy retries on: ║
║  📊 Timeline         │                               │ - `.timeout` errors    ║
║  ──────────────────  │                               │ - `.serverError(5xx)`  ║
║   AI                ▾│                               │ - `.connectionLost`    ║
║  🧠 Intelligence     │                               │                        ║
║  💬 Ask CodeLens    ●│                               │ It does **not** retry o║
║  🐛 Debug            │                               │ - `.unauthorized`      ║
║  ──────────────────  │                               │ - `.badRequest`        ║
║  ⚙ Settings          │                               │                        ║
║                      │  └────────────────────────────│                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Ask about this codebase...                                         ▶         ║
║  ⊙ Claude Sonnet 4.5                                                          ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 9.3 Chat Design Details

**Message Bubbles:**

| Element | You (user) | CodeLens (AI) |
|---|---|---|
| Alignment | Right-aligned | Left-aligned |
| Background | `#3A3A3C` | `#2C2C2E` |
| Label | "You" — right | "CodeLens" — left, with 💬 icon |
| Text | `Body` | `Body`, with markdown rendering |
| Code blocks | — | Syntax-highlighted, with "Copy" button |

**Input Bar (Bottom):**
```
╠══════════════════════════════════════════════════════════════════════════════╣
║  Ask about this codebase...                                         ▶      ║
║  ⊙ Claude Sonnet 4.5                                                       ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

- Text input: full width, `Body` font, "Ask about this codebase..." placeholder
- Send button (▶): teal circle, appears when text is entered
- Model indicator: small text below input showing current model name
- **Extended Thinking toggle**: top-right of chat area, enables chain-of-thought

**Right Column — Referenced Sources:**

When CodeLens answers, it shows which files/symbols it referenced:

```
Referenced Sources
────────────────

📄 APIClient.swift
   Lines 45-89
   NetworkModule

📄 RetryPolicy.swift
   Lines 12-34
   NetworkModule

────────────────

Related Symbols
· RetryPolicy
· APIClient
· NetworkError

────────────────

[View in Architecture →]
```

Each source is clickable → opens in Xcode or navigates to Architecture graph.

### 9.4 Chat History

The left panel of Ask CodeLens can optionally show chat history (accessible via a disclosure or when inspector is hidden):

```
Previous conversations:

Today
  "How does the retry logic work?"
  "What patterns does DataLayer use?"

Yesterday
  "Why is NetworkModule coverage low?"
```

---
