# Timeline / Activity Feed

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Insights · **Phase 3**  
> **Accent Color:** `#64D2FF` (teal) · **SF Symbol:** `clock.arrow.circlepath`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#64D2FF` (teal)  
**SF Symbol:** `clock.arrow.circlepath`  
**Purpose:** A real-time chronological feed of everything happening in your project. Commits, builds, tests, scans, AI actions — all in one living stream. This makes CodeLens feel alive.

> **Sidebar group:** Insights

### 23.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │         ┌──────────┐          │     ┌──────────┐       ║
║  ──────────────────  │                               │    📊    │              ║
║   Explore           ▾│                               │  (circle)│             ║
║  📁 Projects         │         └──────────┘          │     └──────────┘       ║
║  🏛 Architecture     │                               │                        ║
║  📦 Dependencies     │    No Activity Yet            │  No Event Selected     ║
║  🔍 Search           │                               │                        ║
║  ──────────────────  │  Events will appear as you use│  Select an event to    ║
║   Create            ▾│  CodeLens — commits, builds, s│  see full details      ║
║  📄 Context          │  and AI actions, all in one li│  and navigation links. ║
║  🔨 Tasks            │  stream.                      │                        ║
║  🧩 Blueprints       │                               │                        ║
║  ──────────────────  │  Waiting for first event…     │                        ║
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
║  📊 Timeline        ●│                               │                        ║
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

> **Auto-populates:** No CTA needed — the Timeline fills automatically as CodeLens detects commits, builds, scans, and AI actions. A subtle particle animation flows upward while waiting.

### 23.2 Populated State — Chronological Feed + Event Detail

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  🔍 Filter events...   [All ▾] │   EVENT DETAIL         ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│  TODAY                        │   ✓ Build Complete     ║
║  📁 Projects         │                               │                        ║
║  🏛 Architecture     │  14:32 ─── ─── ─── ─── ─── ───│   Offline Search       ║
║  📦 Dependencies     │  ✓  Build complete: Offline se│   Support              ║
║  🔍 Search           │     8m · 5/5 tests · $2.40    │                        ║
║  ──────────────────  │     Tasks → Build Pipeline    │   Duration: 8m 14s     ║
║   Create            ▾│                               │   Cost: $2.40          ║
║  📄 Context          │  14:24 ─── ─── ─── ─── ─── ───│   Tests: 5/5 passed    ║
║  🔨 Tasks            │  ●  Build started: Offline sea│   Retries: 1           ║
║  🧩 Blueprints       │     Tasks → Pipeline          │                        ║
║  ──────────────────  │                               │   ────────────────     ║
║   Quality           ▾│  13:50 ─── ─── ─── ─── ─── ───│                        ║
║  ✅ Tests            │  🔒  Security scan complete    │   FILES CHANGED        ║
║  🔒 Security         │     Score: 72/100 · 2 critical│                        ║
║  ⚡ Performance      │                               │   + OfflineSearch      ║
║  ──────────────────  │  13:45 ─── ─── ─── ─── ─── ───│     Service.swift      ║
║   Knowledge         ▾│  📊  Convention check passed   │   + SearchIndex.swift  ║
║  📖 Wiki             │     14 rules · 91% adherence  │   ~ TaskListView.swift ║
║  📜 Conventions      │                               │   ~ TaskListVM.swift   ║
║  📰 Changelog        │  11:15 ─── ─── ─── ─── ─── ───│                        ║
║  ──────────────────  │  ⚠  Commit: Fix nil date crash│   ────────────────     ║
║   Insights          ▾│     +8 −3 · DataLayer         │                        ║
║  ♡ Health            │                               │   PIPELINE             ║
║  △ Improve           │  09:45 ─── ─── ─── ─── ─── ───│                        ║
║  📊 Timeline        ●│  ↻  Commit: Extract retry logi│   [Plan✓]─[Des✓]─      ║
║  ──────────────────  │     +42 −18 · NetworkModule   │   [Code✓]─[Test✓]─     ║
║   AI                ▾│                               │   [Ship✓]              ║
║  🧠 Intelligence     │  YESTERDAY                    │                        ║
║  💬 Ask CodeLens     │                               │   [View in Tasks →]    ║
║  🐛 Debug            │  ...                          │   [View Diff →]        ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │                               │                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                          42 events today   ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 23.3 Event Types & Icons

| Event | Icon | Color |
|---|---|---|
| Commit (feature) | ✓ | `#30D158` green |
| Commit (bug fix) | ⚠ | `#FF9F0A` orange |
| Commit (refactor) | ↻ | `#0A84FF` blue |
| Build started | ● | `#0A84FF` blue |
| Build complete | ✓ | `#30D158` green |
| Build failed | ✕ | `#FF453A` red |
| Test run passed | ✅ | `#30D158` green |
| Test run failed | ❌ | `#FF453A` red |
| Security scan | 🔒 | `#FF453A` red |
| Convention check | 📊 | `#AC8E68` gold |
| Blueprint generated | 🧩 | `#FFD60A` yellow |
| Changelog generated | 📰 | `#30D158` green |
| Analysis complete | 🏛 | `#FF9F0A` orange |
| Ask CodeLens query | 💬 | `#64D2FF` teal |

### 23.4 Filter Bar

```
[All ▾]  [Builds ▾]  [Commits ▾]  [Scans ▾]  [AI ▾]
```

- Dropdown filters narrow the feed
- Multiple can be active (additive)
- "All" resets to full feed

### 23.5 Right Column — Event Detail

Clicking an event shows:
- Full event description
- Duration/cost (for builds)
- Files changed (for commits/builds)
- Pipeline visualization (for builds)
- Navigation links: "View in Tasks →", "View in Health →", etc.
- For commits: diff preview (syntax highlighted)

### 23.6 Real-Time Updates

- New events slide in from the top with animation
- Auto-scroll to latest (unless user has scrolled up)
- Timestamp updates every minute ("14:32" → "2m ago" → "14:32")
- Build events update in-place (started → in progress → complete)


---
