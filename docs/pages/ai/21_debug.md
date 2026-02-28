# Debug Assistant

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** AI · **Phase 3**  
> **Accent Color:** `#FF453A` (red) · **SF Symbol:** `ant.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#FF453A` (red)  
**SF Symbol:** `ant.fill`  
**Purpose:** Paste a crash log, error message, or stack trace. CodeLens traces it to the exact source line, explains the root cause in plain language, and suggests (or auto-generates) a fix. THE demo moment.

> **Sidebar group:** AI

### 24.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │                               │     ┌──────────┐       ║
║  ──────────────────  │         ┌──────────┐          │     │    🐛    │        ║
║   Explore           ▾│                               │    🐛    │              ║
║  📁 Projects         │                               │  (circle)│             ║
║  🏛 Architecture     │         └──────────┘          │                        ║
║  📦 Dependencies     │                               │   Paste a crash log    ║
║  🔍 Search           │    Debug Assistant            │   or error to see      ║
║  ──────────────────  │                               │   the analysis.        ║
║   Create            ▾│  Paste a crash log, error mess│                        ║
║  📄 Context          │  or stack trace. CodeLens will│                        ║
║  🔨 Tasks            │  it to your source code and ex│                        ║
║  🧩 Blueprints       │  the root cause.              │                        ║
║  ──────────────────  │                               │                        ║
║   Quality           ▾│  ┌────────────────────────────│                        ║
║  ✅ Tests            │                               │                        ║
║  🔒 Security         │                               │  Paste crash log here..║
║  ⚡ Performance      │                               │                        ║
║  ──────────────────  │                               │                        ║
║   Knowledge         ▾│                               │                        ║
║  📖 Wiki             │  └────────────────────────────│                        ║
║  📜 Conventions      │                               │                        ║
║  📰 Changelog        │           [🐛 Analyze]         │                        ║
║  ──────────────────  │                               │                        ║
║   Insights          ▾│                               │                        ║
║  ♡ Health            │                               │                        ║
║  △ Improve           │                               │                        ║
║  📊 Timeline         │                               │                        ║
║  ──────────────────  │                               │                        ║
║   AI                ▾│                               │                        ║
║  🧠 Intelligence     │                               │                        ║
║  💬 Ask CodeLens     │                               │                        ║
║  🐛 Debug           ●│                               │                        ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │                               │                        ║
║                      │                               │                        ║
╚══════════════════════╧═══════════════════════════════╧════════════════════════╝
```

### 24.2 Analysis Results

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  CRASH ANALYSIS               │   SOURCE LOCATION      ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│  ┌────────────────────────────│   NetworkManager.swift ║
║  📁 Projects         │                               │                        ║
║  🏛 Architecture     │                               │  🔴 EXC_BAD_ACCESS      ║
║  📦 Dependencies     │                               │                        ║
║  🔍 Search           │                               │  Thread 1: Fatal signal║
║  ──────────────────  │                               │                        ║
║   Create            ▾│                               │  Crashed at:           ║
║  📄 Context          │                               │  NetworkManager.swift:8║
║  🔨 Tasks            │                               │  → retry(request:)     ║
║  🧩 Blueprints       │                               │                        ║
║  ──────────────────  │  └────────────────────────────│   ```                  ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests            │  ────────────────────         │   ────────────────     ║
║  🔒 Security         │                               │                        ║
║  ⚡ Performance      │  ROOT CAUSE                   │   CALL STACK           ║
║  ──────────────────  │                               │                        ║
║   Knowledge         ▾│  Force-unwrapping a nil value.│   5 NetworkManager     ║
║  📖 Wiki             │  `cache[key]!` at line 89 cras│     .retry()           ║
║  📜 Conventions      │  when the cache entry has expi│   4 APIClient          ║
║  📰 Changelog        │  or was never set. This happen│     .fetch()           ║
║  ──────────────────  │  when the network request is r│   3 TaskService        ║
║   Insights          ▾│  after the cache TTL expires. │     .loadTasks()       ║
║  ♡ Health            │                               │   2 TaskListVM         ║
║  △ Improve           │  ────────────────────         │     .refresh()         ║
║  📊 Timeline         │                               │   1 TaskListView       ║
║  ──────────────────  │  SUGGESTED FIX                │     .onAppear          ║
║   AI                ▾│                               │                        ║
║  🧠 Intelligence     │  Replace force-unwrap with    │   ────────────────     ║
║  💬 Ask CodeLens     │  optional binding:            │                        ║
║  🐛 Debug           ●│                               │   SIMILAR CRASHES      ║
║  ──────────────────  │  ```                          │                        ║
║  ⚙ Settings          │  // Before (crashes)          │   This pattern appears ║
║                      │  return cache[key]!           │   in 3 other places:   ║
║                      │                               │                        ║
║                      │  // After (safe)              │   • CacheService:42    ║
║                      │  guard let cached =           │   • ImageLoader:67     ║
║                      │    cache[key] else {          │   • ConfigMgr:23       ║
║                      │    return fetchFresh(request) │                        ║
║                      │  }                            │   [Fix All 4 →]        ║
║                      │  return cached                │                        ║
║                      │  ```                          │                        ║
║                      │                               │                        ║
║                      │  [🔧 Apply Fix]  [Create Task →│                        ║
║                      │  [Fix All Similar →]          │                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                               Root cause: force-unwrap nil ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 24.3 What Debug Assistant Analyzes

| Input Type | What CodeLens Does |
|---|---|
| **Crash log** | Symbolicate → map to source → explain root cause |
| **Stack trace** | Parse frames → identify your code vs system → explain |
| **Error message** | Match to known patterns → show location → suggest fix |
| **Console output** | Parse warnings/errors → classify → prioritize |
| **Screenshot** | (Future) Analyze UI issue → identify layout problem |

### 24.4 Analysis Features

| Feature | Description |
|---|---|
| **Source mapping** | Links crash to exact file + line in YOUR project |
| **Root cause** | Plain-language explanation ("Force-unwrapping a nil value because...") |
| **Call stack** | Simplified, showing only YOUR code (system frames collapsed) |
| **Suggested fix** | Code patch with before/after |
| **Similar crashes** | Finds the same anti-pattern elsewhere in the codebase |
| **Apply Fix** | One-click fix via Developer Agent |
| **Fix All Similar** | Fix this pattern everywhere it appears |
| **Create Task** | Send to Build Pipeline for a comprehensive fix |

### 24.5 History

Previous debug sessions are saved and accessible:
```
┌──────────────────────────────────────────┐
│ 🔴 EXC_BAD_ACCESS — NetworkManager   2h │
│ 🟠 Type mismatch — DataParser       1d │
│ 🟢 Fixed: nil date crash — DataLayer 3d │
└──────────────────────────────────────────┘
```
- 🔴 = unresolved, 🟠 = in progress, 🟢 = fixed
- Click to re-open the analysis


---
