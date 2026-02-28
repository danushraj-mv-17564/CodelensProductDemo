# Health

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Insights · **Phase 3**  
> **Accent Color:** `#FF375F` (pink) · **SF Symbol:** `heart.text.square.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#FF375F` (pink)  
**SF Symbol:** `heart.text.square.fill`  
**Purpose:** Track project health over time. Coverage trends, module health, commit impact. Answers: "Is my project getting better or worse?"

> **Sidebar group:** Insights

### 21.1 Layout — Scrollable Middle Column + Detail Right Column

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  COVERAGE OVER TIME           │   NetworkModule        ║
║  ──────────────────  │  ┌────────────────────────────│                        ║
║   Explore           ▾│                               │ 80% ┤                  ║
║  📁 Projects         │                               │     │         ╱╲╱╲╱╱╱╱ ║
║  🏛 Architecture     │                               │ 70% ┤  ╱╲╱╲╱╱          ║
║  📦 Dependencies     │                               │     │╱╲╱               ║
║  🔍 Search           │                               │ 60% ┤                  ║
║  ──────────────────  │                               │     └──Jan──Feb──Mar──A║
║   Create            ▾│  └────────────────────────────│   Coverage             ║
║  📄 Context          │                               │   █████░░░░░░ 45%      ║
║  🔨 Tasks            │  Current: 72%                 │  Trend: ↗ +3%      │   ║
║  🧩 Blueprints       │                               │  Goal: 80% (dashed line║
║  ──────────────────  │                               │   Fragility            ║
║   Quality           ▾│  ────────────────────         │   ██████░░░░ 0.72      ║
║  ✅ Tests            │                               │                        ║
║  🔒 Security         │  MODULE HEALTH                │   ────────────────     ║
║  ⚡ Performance      │                               │                        ║
║  ──────────────────  │  UIComponents  █████████████░ │   Recent Commits       ║
║   Knowledge         ▾│  AuthService   ████████████░░ │                        ║
║  📖 Wiki             │  MainApp       █████████░░░░░ │   14:32 ✓ Add offline  ║
║  📜 Conventions      │  DataLayer     ███████░░░░░░░ │     search (+124 −32)  ║
║  📰 Changelog        │  NetworkModule █████░░░░░░░░░ │   11:15 ⚠ Fix nil      ║
║  ──────────────────  │                               │     date crash (+8 −3) ║
║   Insights          ▾│  ✓ Healthy  ● Fair  ▲ Needs at│   09:45 ↻ Extract      ║
║  ♡ Health           ●│  ↗ Improving → Stable ↘ Declin│     retry logic        ║
║  △ Improve           │                               │                        ║
║  📊 Timeline         │  ────────────────────         │   ────────────────     ║
║  ──────────────────  │                               │                        ║
║   AI                ▾│  RECENT CHANGES               │   [View in             ║
║  🧠 Intelligence     │                               │    Architecture →]     ║
║  💬 Ask CodeLens     │  Today                        │   [Generate Tests →]   ║
║  🐛 Debug            │                               │                        ║
║  ──────────────────  │  ┌────────────────────────────│                        ║
║  ⚙ Settings          │                               │ ✓ Add offline search   ║
║                      │                               │   Feature · DataLayer, ║
║                      │                               │   +124 −32 · Coverage: ║
║                      │  └────────────────────────────│                        ║
║                      │                               │                        ║
║                      │  ┌────────────────────────────│                        ║
║                      │                               │ ⚠ Fix nil date crash   ║
║                      │                               │   Bug fix · DataLayer  ║
║                      │                               │   +8 −3 · Coverage: +0.║
║                      │  └────────────────────────────│                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                           5 modules        ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 21.2 Coverage Chart

- **Swift Charts** line chart with area fill (gradient fade to transparent)
- X-axis: time (auto-scales: days if <2 weeks, weeks if <3 months, months otherwise)
- Y-axis: coverage percentage
- Goal line (80%) = dashed horizontal, labeled
- Hover on chart: crosshair shows exact value + date
- Below chart: "Current: 72% │ Trend: ↗ +3% │ Goal: 80%"

### 21.3 Module Health List

Each row:

```
UIComponents    █████████████░░  91%  ✓  ↗
```

- Module name: `Body`
- Progress bar: 200pt wide, colored (green >70%, orange 50-70%, red <50%)
- Percentage: `Headline`
- Health icon: ✓ (green circle check), ● (orange dot), ▲ (red triangle)
- Trend arrow: ↗ (improving), → (stable), ↘ (declining)
- Click row → selects module, right column shows its detail
- Sorted by coverage ascending (worst first = most actionable)

### 21.4 Recent Changes

Commit cards grouped by day:

```
┌──────────────────────────────────────────┐
│ ✓  Add offline search support     14:32  │
│    Feature · DataLayer, SearchModule     │
│    +124 −32 · Coverage impact: +2.1%    │
└──────────────────────────────────────────┘
```

- Left icon: ✓ green (feature), ⚠ orange (bug fix), ↻ blue (refactor)
- Commit message: `Headline`
- Classification + modules: `Subheadline` 50% opacity
- Stats: `Caption` 40% opacity. Green if +coverage, red if −coverage.
- Click → expands inline showing full diff summary and PKG changes
- Cards: `#2C2C2E`, 8pt radius, 8pt vertical spacing

### 21.5 Right Column — Module Detail (When Row Selected)

Shows module stats, recent commits impacting it, and action links:
- Type/function/LOC counts
- Coverage bar + fragility score
- Commit list filtered to this module
- "View in Architecture →", "Generate Tests →"

---
