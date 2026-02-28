# Spotlight Search (⌘K)

> **CodeLens UI/UX Design Specification — Cross-Cutting**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

A floating search overlay — the fastest way to navigate CodeLens. Inspired by macOS Spotlight.

### 26.1 Layout

```
╔══════════════════════════════════════════════════════════════╗
║                                                              ║
║      ┌──────────────────────────────────────────────┐       ║
║      │  🔍  Search CodeLens...                ⌘K    │       ║
║      ├──────────────────────────────────────────────┤       ║
║      │                                              │       ║
║      │  TYPES                                       │       ║
║      │  ● AuthService          class · AuthModule   │ ← sel ║
║      │  ○ AuthToken            struct · AuthModule  │       ║
║      │                                              │       ║
║      │  FUNCTIONS                                   │       ║
║      │  ○ authenticate()       AuthService          │       ║
║      │  ○ refreshToken()       AuthService          │       ║
║      │                                              │       ║
║      │  MODULES                                     │       ║
║      │  ○ AuthModule           8 types · 88% cov   │       ║
║      │                                              │       ║
║      │  PAGES                                       │       ║
║      │  ○ Architecture                              │       ║
║      │  ○ Ask CodeLens                              │       ║
║      │                                              │       ║
║      │  ACTIONS                                     │       ║
║      │  ○ Generate tests for AuthModule             │       ║
║      │  ○ Start a new build                         │       ║
║      │                                              │       ║
║      │  ↑↓ Navigate   ⏎ Open   ⌘⏎ Source   Esc     │       ║
║      └──────────────────────────────────────────────┘       ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

### 26.2 Behavior

- **Dark frosted glass overlay** covering the window (vibrancy material)
- **Instant results** as you type — no delay, searches PKG locally
- **Categories:** Types, Functions, Modules, Views, Tests, Pages, Actions
- **Actions** are special — they trigger functionality ("Start a build", "Generate tests", "Run tests", "Open settings")
- **Keyboard navigation:** ↑↓ = move, Enter = select, ⌘Enter = open in Xcode source, Esc = close
- Results: `Body` font, subtext `Caption` 50% opacity
- Category headers: `Caption` all-caps, 40% opacity
- Selected row: purple highlight pill
- Empty input: shows recent searches
- No results: "No results for 'query'" + "Ask CodeLens about this?" link

---
