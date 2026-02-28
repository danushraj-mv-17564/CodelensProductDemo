# Performance Profiler

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Quality · **Phase 2**  
> **Accent Color:** `#FF9F0A` (orange) · **SF Symbol:** `gauge.with.dots.needle.33percent`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#FF9F0A` (orange)  
**SF Symbol:** `gauge.with.dots.needle.33percent`  
**Purpose:** Track build times, binary size, compile-time bottlenecks, and launch-time estimates. Every Xcode developer hates slow builds — this page is their hero.

> **Sidebar group:** Quality

### 18.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │         ┌──────────┐          │     ┌──────────┐       ║
║  ──────────────────  │                               │    ⚡    │              ║
║   Explore           ▾│                               │  (circle)│             ║
║  📁 Projects         │         └──────────┘          │     └──────────┘       ║
║  🏛 Architecture     │                               │                        ║
║  📦 Dependencies     │    Performance Profiler       │  No File Selected      ║
║  🔍 Search           │                               │                        ║
║  ──────────────────  │  Build your project to see com│  Select a file from    ║
║   Create            ▾│  times, binary size, and      │  the slowest-files     ║
║  📄 Context          │  optimization suggestions.    │  list to see why       ║
║  🔨 Tasks            │                               │  it's slow.            ║
║  🧩 Blueprints       │  Waiting for first build…     │                        ║
║  ──────────────────  │                               │                        ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests            │                               │                        ║
║  🔒 Security         │                               │                        ║
║  ⚡ Performance     ●│                               │                        ║
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

> **Auto-populates:** No CTA needed — Performance Profiler activates automatically after the first Xcode build is detected. The empty state shows a subtle pulsing animation on the ⚡ icon.

### 18.2 Populated State — Metrics Dashboard + File-Level Analysis

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  BUILD TIME TREND             │   AppDelegate.swift    ║
║  ──────────────────  │  ┌────────────────────────────│                        ║
║   Explore           ▾│                               │ 45s ┤              ╱╲  ║
║  📁 Projects         │                               │     │         ╱╲╱╱   ╲ ║
║  🏛 Architecture     │                               │ 30s ┤  ╱╲╱╲╱╱          ║
║  📦 Dependencies     │                               │     │╱╲╱               ║
║  🔍 Search           │                               │ 15s ┤                  ║
║  ──────────────────  │                               │     └───Mon──Tue──Wed──║
║   Create            ▾│  └────────────────────────────│                        ║
║  📄 Context          │                               │   • 12 type-checked    ║
║  🔨 Tasks            │  Current: 38s                 │ Avg: 32s │ Best: 18s │ ║
║  🧩 Blueprints       │                               │   • 3 complex closures ║
║  ──────────────────  │  ────────────────────         │   • Heavy string       ║
║   Quality           ▾│                               │     interpolation      ║
║  ✅ Tests            │  BINARY SIZE                  │                        ║
║  🔒 Security         │                               │   SUGGESTIONS          ║
║  ⚡ Performance     ●│  48.2 MB  (↗ +2.1 MB this week│                        ║
║  ──────────────────  │                               │   ● Split into 2 files ║
║   Knowledge         ▾│  UIComponents    ████████░░ 12│   ● Extract generic    ║
║  📖 Wiki             │  Assets          ██████░░░░  9│     type aliases       ║
║  📜 Conventions      │  NetworkModule   █████░░░░░  7│   ● Simplify closures  ║
║  📰 Changelog        │  AuthService     ███░░░░░░░  4│     on lines 45, 89    ║
║  ──────────────────  │  Other           ███████░░░ 14│                        ║
║   Insights          ▾│                               │   [Auto-Fix →]         ║
║  ♡ Health            │  ────────────────────         │   [Create Task →]      ║
║  △ Improve           │                               │                        ║
║  📊 Timeline         │  SLOWEST FILES (Compile Time) │   ────────────────     ║
║  ──────────────────  │                               │                        ║
║   AI                ▾│  AppDelegate.swift       4.2s │   LAUNCH TIME          ║
║  🧠 Intelligence     │  ContentView.swift       3.1s │   ESTIMATE             ║
║  💬 Ask CodeLens     │  SearchViewModel.swift   2.8s │                        ║
║  🐛 Debug            │  NetworkManager.swift    1.9s │   Cold: ~1.8s          ║
║  ──────────────────  │  TaskListView.swift      1.2s │   Warm: ~0.4s          ║
║  ⚙ Settings          │                               │                        ║
║                      │  Total compile: 38.2s (12 modu│   Target: <2.0s (✓)    ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                     38s build · 48.2 MB    ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 18.3 Build Time Chart

- **Swift Charts** line chart with area fill
- X-axis: time (last 7 days default, expandable to 30/90)
- Y-axis: build time in seconds
- Hover: crosshair with exact time + date
- Color: orange when above average, green when below

### 18.4 Binary Size Breakdown

Horizontal bar chart by module:
- Each bar colored by module accent
- Total size + weekly delta at top
- Click bar → right column shows size breakdown (code/assets/resources)

### 18.5 Slowest Files Table

| Column | Content |
|---|---|
| File name | `Body` font, clickable |
| Compile time | `Headline`, right-aligned |
| Warning | ⚠ if in top 5% slowest |

**Click a file → right column shows:**
- Exact compile time
- **WHY it's slow** — CodeLens analyzes Swift AST for: complex generics, long type-inference chains, heavy string interpolation, massive closures
- **Suggestions** — actionable fixes with estimated time savings
- **Auto-Fix →** — sends to Developer Agent to optimize

### 18.6 Launch Time Estimator

Bottom-right card showing estimated cold/warm launch times:
- Calculated from binary size + import count + initialization analysis
- Green if under target, orange if close, red if over
- Target configurable in Settings

---
