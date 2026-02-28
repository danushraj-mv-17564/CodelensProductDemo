# Blueprints / Module Generator

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Create · **Phase 2**  
> **Accent Color:** `#FFD60A` (yellow) · **SF Symbol:** `puzzlepiece.extension.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#FFD60A` (yellow)  
**SF Symbol:** `puzzlepiece.extension.fill`  
**Purpose:** Describe a module in plain English. CodeLens generates the entire scaffolding — protocols, implementations, tests, documentation, DI registration. Not just a file template — an architecture-aware module factory.

> **Sidebar group:** Create

### 15.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │                               │     ┌──────────┐       ║
║  ──────────────────  │         ┌──────────┐          │     │    🧩    │        ║
║   Explore           ▾│                               │    🧩    │              ║
║  📁 Projects         │                               │  (circle)│             ║
║  🏛 Architecture     │         └──────────┘          │                        ║
║  📦 Dependencies     │                               │   No Blueprint         ║
║  🔍 Search           │     Module Blueprints         │   Selected             ║
║  ──────────────────  │                               │                        ║
║   Create            ▾│  Describe a module and CodeLen│   Select a blueprint   ║
║  📄 Context          │  generates protocols, implemen│   to see its files     ║
║  🔨 Tasks            │  tests, docs, and DI wiring.  │   and configuration.   ║
║  🧩 Blueprints      ●│                               │                        ║
║  ──────────────────  │      [⊕ New Blueprint]        │                        ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests            │                               │                        ║
║  🔒 Security         │                               │                        ║
║  ⚡ Performance      │                               │                        ║
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
║  💬 Ask CodeLens     │                               │                        ║
║  🐛 Debug            │                               │                        ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │                               │                        ║
║                      │                               │                        ║
╚══════════════════════╧═══════════════════════════════╧════════════════════════╝
```

### 15.2 New Blueprint — Description Form

```
┌──────────────────────────────────────────────────────────┐
│                                                          │
│  What module do you need?                                │
│                                                          │
│  ┌──────────────────────────────────────────────────┐   │
│  │ A caching layer that stores API responses        │   │
│  │ locally using SwiftData, with TTL-based          │   │
│  │ expiration and automatic cache invalidation      │   │
│  │ when the data model changes.                     │   │
│  └──────────────────────────────────────────────────┘   │
│                                                          │
│  Architecture:  [MVVM ▾]    ← detected from project     │
│  DI Pattern:    [Protocol ▾] ← detected from project    │
│  Test level:    [Unit + Integration ▾]                   │
│                                                          │
│  ☑ Generate protocols                                    │
│  ☑ Generate implementations                              │
│  ☑ Generate unit tests                                   │
│  ☑ Generate documentation                                │
│  ☑ Generate DI registration                              │
│  ☐ Generate SwiftUI previews                             │
│                                                          │
│                                      [✦ Generate Module] │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

**Key insight:** The dropdowns for Architecture and DI Pattern are **pre-filled** based on CodeLens's analysis of the existing project. This is the moment the viewer realizes: "It learned my patterns."

### 15.3 Populated State — Blueprint List + Generated Preview

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  🔍 Filter blueprints...       │  CacheModule           ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│  ┌────────────────────────────│  6 files · 342 lines   ║
║  📁 Projects         │                               │ ✓ CacheModule          ║
║  🏛 Architecture     │                               │   3m ago · $0.80       ║
║  📦 Dependencies     │  └────────────────────────────│                        ║
║  🔍 Search           │  ┌────────────────────────────│  📁 CacheModule/        ║
║  ──────────────────  │                               │ ✓ NetworkRetryModule   ║
║   Create            ▾│                               │   Yesterday · $0.60    ║
║  📄 Context          │  └────────────────────────────│   ├─ CacheConfig.swift ║
║  🔨 Tasks            │                               │   ├─ CacheModule+DI.sw ║
║  🧩 Blueprints      ●│                               │   ├─ CacheServiceTests.║
║  ──────────────────  │                               │   └─ CacheModule.md    ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests            │                               │  ────────────────      ║
║  🔒 Security         │                               │                        ║
║  ⚡ Performance      │                               │  Preview:              ║
║  ──────────────────  │                               │  CacheService.swift    ║
║   Knowledge         ▾│                               │                        ║
║  📖 Wiki             │                               │  1  import Foundation  ║
║  📜 Conventions      │                               │  2  import SwiftData   ║
║  📰 Changelog        │                               │  3                     ║
║  ──────────────────  │                               │  4  /// Stores API     ║
║   Insights          ▾│                               │  5  /// responses with ║
║  ♡ Health            │                               │  6  /// TTL expiration ║
║  △ Improve           │                               │  7  @Observable        ║
║  📊 Timeline         │                               │  8  final class        ║
║  ──────────────────  │                               │  9    CacheService:    ║
║   AI                ▾│                               │  10   CacheProtocol    ║
║  🧠 Intelligence     │                               │  ...                   ║
║  💬 Ask CodeLens     │                               │                        ║
║  🐛 Debug            │                               │  [Save to Project]     ║
║  ──────────────────  │                               │  [Open as Task →]      ║
║  ⚙ Settings          │                               │  [⟳ Regenerate]        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                ⊕ New Blueprint              2 blueprints   ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 15.4 What Makes Blueprints Special

| Feature | Detail |
|---|---|
| **Convention-aware** | Generated code matches your naming style, patterns, and DI approach |
| **Architecture-aware** | Knows your module structure, doesn't create conflicting names |
| **Complete, not partial** | Protocol + Implementation + Tests + Docs + DI wiring |
| **Editable** | Click any file to edit before saving to project |
| **Chainable** | "Open as Task →" sends to Build Pipeline for integration |
| **History** | Past blueprints are saved for reference and re-generation |

### 15.5 Blueprint Actions

| Action | What It Does |
|---|---|
| **Save to Project** | Writes all files to the correct module directory |
| **Open as Task →** | Creates a Task with the blueprint as the starting point |
| **Regenerate** | Re-runs generation with same prompt (useful after editing options) |
| **Delete** | Removes from history |


---
