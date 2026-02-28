# Conventions

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Knowledge · **Phase 2**  
> **Accent Color:** `#AC8E68` (gold) · **SF Symbol:** `text.book.closed.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#AC8E68` (gold/tan)  
**SF Symbol:** `text.book.closed.fill`  
**Purpose:** CodeLens learns your coding style — naming conventions, architecture patterns, formatting rules — and shows where the codebase deviates. The "your AI learned your style" moment.

> **Sidebar group:** Knowledge

### 19.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │         ┌──────────┐          │     ┌──────────┐       ║
║  ──────────────────  │                               │    📜    │              ║
║   Explore           ▾│                               │  (circle)│             ║
║  📁 Projects         │         └──────────┘          │     └──────────┘       ║
║  🏛 Architecture     │                               │                        ║
║  📦 Dependencies     │    Conventions                │  No Violation Selected ║
║  🔍 Search           │                               │                        ║
║  ──────────────────  │  CodeLens will analyze your co│  Select a violation    ║
║   Create            ▾│  and learn your coding style —│  to see details,       ║
║  📄 Context          │  naming, architecture, formatt│  examples, and         ║
║  🔨 Tasks            │                               │  suggested fixes.      ║
║  🧩 Blueprints       │  Learning from your code…     │                        ║
║  ──────────────────  │                               │                        ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests            │                               │                        ║
║  🔒 Security         │                               │                        ║
║  ⚡ Performance      │                               │                        ║
║  ──────────────────  │                               │                        ║
║   Knowledge         ▾│                               │                        ║
║  📖 Wiki             │                               │                        ║
║  📜 Conventions     ●│                               │                        ║
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

> **Auto-detects:** No CTA needed — Conventions analysis begins automatically when a project is indexed. The empty state shows a progress indicator ("Analyzing 247 files…") that updates in real time.

### 19.2 Populated State — Detected Rules + Violations

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  DETECTED CONVENTIONS         │   VIOLATION DETAIL     ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│  CodeLens analyzed 247 files a│   Function too long    ║
║  📁 Projects         │  learned 14 conventions from y│                        ║
║  🏛 Architecture     │  codebase.                    │   AuthService.swift:89 ║
║  📦 Dependencies     │                               │   `refreshToken()` is  ║
║  🔍 Search           │  Adherence: 91%  █████████████│   67 lines. Your       ║
║  ──────────────────  │                               │   convention is <50.   ║
║   Create            ▾│  ────────────────────         │                        ║
║  📄 Context          │                               │   ────────────────     ║
║  🔨 Tasks            │  📐 NAMING (5 rules · 96%)     │                        ║
║  🧩 Blueprints       │                               │   SIMILAR FUNCTIONS    ║
║  ──────────────────  │  ✓ Types: UpperCamelCase      │   (that follow the     ║
║   Quality           ▾│  ✓ Functions: lowerCamelCase  │    convention):        ║
║  ✅ Tests            │  ✓ Booleans: is/has/should pre│                        ║
║  🔒 Security         │  ✓ Protocols: -Protocol suffix│   ✓ authenticate()     ║
║  ⚡ Performance      │  ⚠ Constants: 2 use UPPER_SNAK│     42 lines           ║
║  ──────────────────  │    (your convention: lowerCame│   ✓ validateToken()    ║
║   Knowledge         ▾│                               │     38 lines           ║
║  📖 Wiki             │  🏛 ARCHITECTURE (4 rules · 89%│                        ║
║  📜 Conventions     ●│                               │   ────────────────     ║
║  📰 Changelog        │  ✓ Pattern: MVVM              │                        ║
║  ──────────────────  │  ✓ DI: Protocol-based injectio│   SUGGESTED FIX        ║
║   Insights          ▾│  ⚠ 3 ViewModels access Reposit│                        ║
║  ♡ Health            │    directly (convention: via S│   Extract retry logic  ║
║  △ Improve           │  ✓ Views: no business logic   │   (lines 45-67) into   ║
║  📊 Timeline         │                               │   separate function    ║
║  ──────────────────  │  📏 STRUCTURE (3 rules · 91%)  │   `performRetry()`.    ║
║   AI                ▾│                               │                        ║
║  🧠 Intelligence     │  ✓ Max function length: <50 li│   [Auto-Fix →]         ║
║  💬 Ask CodeLens     │  ⚠ 2 functions exceed limit   │   [Suppress Rule]      ║
║  🐛 Debug            │  ✓ Max file length: <300 lines│                        ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │  🧪 TESTING (2 rules · 88%)    │                        ║
║                      │                               │                        ║
║                      │  ✓ Test naming: test_behavior_│                        ║
║                      │  ⚠ 4 test files missing setUp(│                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion              14 conventions · 91%          7 violations    ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 19.3 How Conventions Are Detected

CodeLens doesn't use a static ruleset. It **learns** from the codebase:

| What It Learns | How It Learns |
|---|---|
| Naming conventions | Statistical analysis of all identifiers |
| Architecture pattern | Import graph + class relationships |
| DI style | Constructor injection patterns, protocol conformance |
| Function length | Histogram of all function bodies, picks P90 as threshold |
| File organization | Extension patterns, MARK usage, import ordering |
| Test conventions | Test function naming, setup/teardown patterns |
| Error handling | Result vs throws vs optional patterns |

### 19.4 Convention Categories

| Category | Icon | Rules Detected |
|---|---|---|
| Naming | 📐 | Type/function/variable naming patterns |
| Architecture | 🏛 | MVVM/MVC/VIPER, layer separation, DI |
| Structure | 📏 | Function length, file length, complexity |
| Testing | 🧪 | Naming, setup patterns, assertion styles |
| Formatting | 🎨 | Import ordering, MARK sections, spacing |

### 19.5 Right Column — Violation Detail

When a violation is selected:

- **File + line** — clickable, opens in Xcode
- **What the convention is** — plain language
- **This code vs convention** — side by side comparison
- **Similar code that follows the convention** — proof it's a real pattern
- **Suggested fix** — with explanation
- **[Auto-Fix →]** — one-click remediation
- **[Suppress Rule]** — if it's a valid exception (logged in history)

### 19.6 Convention Editing

Users can override detected conventions:

- Click any rule → "Edit Rule" button
- Set custom thresholds (e.g., max function length: 60 instead of 50)
- Disable specific rules
- Export as `.codelens-conventions.json` for team sharing

---
