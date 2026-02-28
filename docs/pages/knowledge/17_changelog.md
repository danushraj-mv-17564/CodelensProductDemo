# Changelog Generator

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Knowledge · **Phase 2**  
> **Accent Color:** `#30D158` (green) · **SF Symbol:** `doc.text.magnifyingglass`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#30D158` (green)  
**SF Symbol:** `doc.text.magnifyingglass`  
**Purpose:** Select a date range. CodeLens reads every commit, build, and test result, and generates beautiful release notes. Saves hours every release cycle.

> **Sidebar group:** Knowledge

### 20.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │         ┌──────────┐          │     ┌──────────┐       ║
║  ──────────────────  │                               │    📰    │              ║
║   Explore           ▾│                               │  (circle)│             ║
║  📁 Projects         │         └──────────┘          │     └──────────┘       ║
║  🏛 Architecture     │                               │                        ║
║  📦 Dependencies     │    Changelog Generator        │  No Changelog Yet      ║
║  🔍 Search           │                               │                        ║
║  ──────────────────  │  Select a date range to genera│  Generate a changelog  ║
║   Create            ▾│  beautiful release notes from │  to preview it here.   ║
║  📄 Context          │  commits, builds, and test res│                        ║
║  🔨 Tasks            │                               │                        ║
║  🧩 Blueprints       │      [✦ Generate Changelog]   │                        ║
║  ──────────────────  │                               │                        ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests            │                               │                        ║
║  🔒 Security         │                               │                        ║
║  ⚡ Performance      │                               │                        ║
║  ──────────────────  │                               │                        ║
║   Knowledge         ▾│                               │                        ║
║  📖 Wiki             │                               │                        ║
║  📜 Conventions      │                               │                        ║
║  📰 Changelog       ●│                               │                        ║
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

### 20.2 Populated State — Date Range + Generated Output

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  CHANGELOG GENERATOR          │   PREVIEW              ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│  From: [Feb 1, 2026 ▾]        │   # Release Notes      ║
║  📁 Projects         │  To:   [Feb 27, 2026 ▾]       │   ## v2.3.0            ║
║  🏛 Architecture     │                               │   February 27, 2026    ║
║  📦 Dependencies     │  Version:  [v2.3.0         ]  │                        ║
║  🔍 Search           │                               │   ### ✨ New Features   ║
║  ──────────────────  │  Format: [Markdown ▾]         │                        ║
║   Create            ▾│                               │   - **Offline search** ║
║  📄 Context          │  Include:                     │     Full-text search   ║
║  🔨 Tasks            │  ☑ Features     ☑ Bug fixes   │     works without      ║
║  🧩 Blueprints       │  ☑ Improvements ☑ Breaking cha│     network (#142)     ║
║  ──────────────────  │  ☐ Internal     ☐ Dependencies│                        ║
║   Quality           ▾│                               │   - **Dark mode** —    ║
║  ✅ Tests            │  Tone: [Professional ▾]       │     Automatic theme    ║
║  🔒 Security         │                               │     switching (#138)   ║
║  ⚡ Performance      │               [✦ Generate Chan│                        ║
║  ──────────────────  │                               │   ### 🐛 Bug Fixes      ║
║   Knowledge         ▾│  ────────────────────         │                        ║
║  📖 Wiki             │                               │   - Fixed nil crash in ║
║  📜 Conventions      │  PREVIOUS CHANGELOGS          │     date formatting    ║
║  📰 Changelog       ●│                               │     (#145)             ║
║  ──────────────────  │  ┌────────────────────────────│   - Fixed retry loop   ║
║   Insights          ▾│                               │ v2.2.0  Feb 1   12 chan║
║  ♡ Health            │  └────────────────────────────│     (#143)             ║
║  △ Improve           │  ┌────────────────────────────│                        ║
║  📊 Timeline         │                               │ v2.1.0  Jan 15  8 chang║
║  ──────────────────  │  └────────────────────────────│                        ║
║   AI                ▾│                               │   - 14 commits         ║
║  🧠 Intelligence     │                               │   - 3 contributors     ║
║  💬 Ask CodeLens     │                               │   - 486 lines added    ║
║  🐛 Debug            │                               │   - 12 files changed   ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │                               │   [📋 Copy]  [💾 Save]   ║
║                      │                               │   [Export .md]         ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                     14 commits selected    ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 20.3 How It Works

1. **Date range selection** → CodeLens gathers all commits in range
2. **AI classification** → Each commit is classified (feature/fix/improvement/breaking/internal)
3. **Grouping** → Changes grouped by category with human-readable descriptions
4. **Enhancement** → AI rewrites commit messages into user-facing language
5. **Stats** → Commit count, contributor count, lines changed, files touched
6. **PR/Issue linking** → If git remotes configured, auto-links to GitHub issues

### 20.4 Tone Options

| Tone | Style |
|---|---|
| Professional | "Added offline search support for improved reliability" |
| Casual | "You can now search offline! 🎉" |
| Technical | "Implemented FTS5-based local search index (SQLite)" |
| Marketing | "Introducing lightning-fast offline search — stay productive anywhere" |

### 20.5 Export Formats

| Format | Description |
|---|---|
| Markdown | Standard `.md` file |
| HTML | Styled HTML for web publishing |
| Plain text | For pasting into emails |
| JSON | Structured data for CI/CD pipelines |
| GitHub Release | Formatted for GitHub Releases API |


---
