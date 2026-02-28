# Search

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Explore · **Phase 1 — Shipped**  
> **Accent Color:** `#FF375F` (pink) · **SF Symbol:** `magnifyingglass`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#FF375F` (pink)  
**Purpose:** Semantic code search. Find code by meaning, not just names.

### 7.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  🔍 Search by meaning...       │     ┌──────────┐       ║
║  ──────────────────  │                               │     │    🔍    │        ║
║   Explore           ▾│  All Kinds  Functions  Types  │     │  (circle)│       ║
║  📁 Projects         │  Module [All Mo... ⇅]  Lang [A│     └──────────┘       ║
║  🏛 Architecture     │                               │                        ║
║  📦 Dependencies     │                               │    Search Results      ║
║  🔍 Search          ●│                               │                        ║
║  ──────────────────  │         ┌──────────┐          │   Search for code to   ║
║   Create            ▾│                               │    🔍    │              ║
║  📄 Context          │                               │  (circle)│             ║
║  🔨 Tasks            │         └──────────┘          │                        ║
║  🧩 Blueprints       │                               │                        ║
║  ──────────────────  │       Semantic Search         │                        ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests            │  Search for code by meaning,  │                        ║
║  🔒 Security         │  not just names.              │                        ║
║  ⚡ Performance      │  Try "authentication logic"   │                        ║
║  ──────────────────  │  or "network error handling". │                        ║
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
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                              0 results     ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 7.2 Populated State — Search Results

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  🔍 authentication logic       │  AuthService           ║
║  ──────────────────  │                               │  class · AuthModule    ║
║   Explore           ▾│  All Kinds  Functions  Types  │                        ║
║  📁 Projects         │  Module [All Mo... ⇅]  Lang [A│  ────────────────      ║
║  🏛 Architecture     │                               │                        ║
║  📦 Dependencies     │  ┌────────────────────────────│  /// Manages user      ║
║  🔍 Search          ●│                               │  🟣 AuthService         ║
║  ──────────────────  │                               │     class · AuthModule ║
║   Create            ▾│  └────────────────────────────│  /// refresh lifecycle ║
║  📄 Context          │  ┌────────────────────────────│                        ║
║  🔨 Tasks            │                               │  🔵 authenticate(email:p║
║  🧩 Blueprints       │                               │     func · AuthService ║
║  ──────────────────  │  └────────────────────────────│      KeychainAccess    ║
║   Quality           ▾│  ┌────────────────────────────│    let tokenStore:     ║
║  ✅ Tests            │                               │  🔵 refreshToken()      ║
║  🔒 Security         │                               │     func · AuthService ║
║  ⚡ Performance      │  └────────────────────────────│    func authenticate(  ║
║  ──────────────────  │  ┌────────────────────────────│      email: String,    ║
║   Knowledge         ▾│                               │  🟢 LoginCredentials    ║
║  📖 Wiki             │                               │     struct · AuthModule║
║  📜 Conventions      │  └────────────────────────────│      -> User {         ║
║  📰 Changelog        │  ┌────────────────────────────│      ...               ║
║  ──────────────────  │                               │  🟣 AuthTokenRefresher  ║
║   Insights          ▾│                               │     protocol · AuthModu║
║  ♡ Health            │  └────────────────────────────│                        ║
║  △ Improve           │                               │  ────────────────      ║
║  📊 Timeline         │                               │                        ║
║  ──────────────────  │                               │  Coverage: 89%         ║
║   AI                ▾│                               │  12 functions          ║
║  🧠 Intelligence     │                               │  340 LOC               ║
║  💬 Ask CodeLens     │                               │                        ║
║  🐛 Debug            │                               │  [View in Architecture]║
║  ──────────────────  │                               │  [Open in Xcode]       ║
║  ⚙ Settings          │                               │                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                              5 results     ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 7.3 Filter Bar

```
[All Kinds●]  [Functions]  [Types]  [Properties]    Module [All Mo...⇅]  Language [All L...⇅]
```

- **Kind filters:** Segmented control (pill style). Active = pink fill. Click toggles.
- **Module dropdown:** Dropdown menu listing all modules. "All Modules" default.
- **Language dropdown:** "All Languages", "Swift", "Objective-C" etc.

### 7.4 Search Result Item

```
┌──────────────────────────────────────┐
│  🟣 AuthService                    ● │  ← type dot color (class=purple)
│     class · AuthModule · 89%        │  ← kind · module · relevance%
└──────────────────────────────────────┘
```

| Element | Details |
|---|---|
| Color dot | Class = purple, Struct = green, Function = blue, Protocol = purple, Enum = orange |
| Name | `Headline` |
| Metadata | `Caption`, 50% opacity: kind · module · match relevance |
| Relevance % | Semantic match confidence |
| Selected | Purple pill highlight |

### 7.5 Symbol Detail (Right Column)

Shows when a search result is selected:

**A. Header**: Symbol name + kind + module  
**B. Documentation**: Doc comment rendered  
**C. Code Preview**: Syntax-highlighted Swift source (first ~30 lines)  
**D. Stats**: Coverage, function count, LOC  
**E. Actions**: "View in Architecture" (jumps to graph), "Open in Xcode" (opens file)

---
