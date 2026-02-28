# Intelligence

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** AI · **Phase 1 — Shipped**  
> **Accent Color:** `#BF5AF2` (purple) · **SF Symbol:** `brain.head.profile`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#BF5AF2` (purple)  
**Purpose:** Configure AI providers and manage how CodeLens uses intelligence.

### 8.1 Layout — Settings Form + Provider Detail

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  🧠 Coding Intelligence        │                        ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│  CodeLens uses AI models to an│   Anthropic            ║
║  📁 Projects         │  your code, generate documenta│                        ║
║  🏛 Architecture     │  and answer questions.        │   ────────────────     ║
║  📦 Dependencies     │  Privacy & AI Usage...        │                        ║
║  🔍 Search           │                               │   Status: ✓ Connected  ║
║  ──────────────────  │  ────────────────────         │                        ║
║   Create            ▾│                               │   API Key              ║
║  📄 Context          │  Providers         + Add a Pro│   sk-ant-••••••••••    ║
║  🔨 Tasks            │                               │   [Test ✓]             ║
║  🧩 Blueprints       │  ┌────────────────────────────│                        ║
║  ──────────────────  │                               │  🟣 Anthropic           ║
║   Quality           ▾│                               │     Claude Sonnet 4.5 ·║
║  ✅ Tests            │  └────────────────────────────│   Model Assignment     ║
║  🔒 Security         │  ┌────────────────────────────│                        ║
║  ⚡ Performance      │                               │  🟢 OpenAI              ║
║  ──────────────────  │                               │     Not configured     ║
║   Knowledge         ▾│  └────────────────────────────│                        ║
║  📖 Wiki             │                               │   Docs & Chat          ║
║  📜 Conventions      │  ────────────────────         │   [Claude Sonnet  ▼]   ║
║  📰 Changelog        │                               │                        ║
║  ──────────────────  │  CodeLens Tools (MCP)        [│   Reviews & Tests      ║
║   Insights          ▾│  When enabled, CodeLens expose│   [GPT-4o-mini   ▼]    ║
║  ♡ Health            │  code analysis tools via MCP f│                        ║
║  △ Improve           │  use by AI assistants.        │   ────────────────     ║
║  📊 Timeline         │                               │                        ║
║  ──────────────────  │  ────────────────────         │   Local Models         ║
║   AI                ▾│                               │                        ║
║  🧠 Intelligence    ●│  Local Models                 │   Embeddings           ║
║  💬 Ask CodeLens     │                               │   nomic-embed-text     ║
║  🐛 Debug            │  Embeddings  nomic-embed-text │   ✓ Ready (256MB)      ║
║  ──────────────────  │  Classifier  Phi-3-mini      [│                        ║
║  ⚙ Settings          │                               │   Classifier           ║
║                      │  ────────────────────         │   Phi-3-mini (3B)      ║
║                      │                               │   ✓ Ready (1.8GB)      ║
║                      │  Usage This Month             │                        ║
║                      │                               │   ────────────────     ║
║                      │  $48.00 / $500                │                        ║
║                      │  ██████████░░░░░░░░░░░░░░  9.6│   [Remove Provider]    ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                          2 providers       ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 8.2 Middle Column Sections

**A. Header** — "Coding Intelligence" with brain icon  
**B. Description** — What AI does in CodeLens, + privacy link  
**C. Providers List** — Cards for each configured provider  
**D. MCP Toggle** — Exposes CodeLens tools to external AI via MCP  
**E. Local Models** — Status of on-device models  
**F. Usage** — Monthly spending bar

### 8.3 Provider Card

```
┌──────────────────────────────────────┐
│  🟣 Anthropic                      ✓ │  ← checkmark = active & connected
│     Claude Sonnet 4.5 · Active      │  ← current model · status
└──────────────────────────────────────┘
```

### 8.4 Right Column — Provider Configuration

When a provider is selected:

- **Status indicator**: Green "✓ Connected" or red "✕ Not configured"
- **API Key input**: Masked field + [Test] button
- **Model Assignment dropdowns**: 3 simplified roles:
  - "Code & Design" → architecture + code generation
  - "Docs & Chat" → documentation + Ask CodeLens
  - "Reviews & Tests" → test generation + code review
- **Local Models**: Show download status, size, readiness
- **[Remove Provider]**: Destructive action, confirmation dialog

### 8.5 "+ Add a Provider" Flow

Clicking "+ Add a Provider..." opens a sheet:

```
┌──────────────────────────────────────────────┐
│                                              │
│  Add AI Provider                             │
│                                              │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │ 🟣       │  │ 🟢       │  │ 🔵       │  │
│  │Anthropic │  │ OpenAI   │  │ Ollama   │  │
│  │          │  │          │  │ (Local)  │  │
│  └──────────┘  └──────────┘  └──────────┘  │
│                                              │
│  API Key                                     │
│  ┌──────────────────────────────────────┐   │
│  │ sk-ant-...                            │   │
│  └──────────────────────────────────────┘   │
│                                              │
│                     [Cancel]    [Add ▶]     │
│                                              │
└──────────────────────────────────────────────┘
```

---
