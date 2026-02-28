# Home Dashboard

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Explore · **Phase 2**  
> **Accent Color:** `#0A84FF` (blue) · **SF Symbol:** `house.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#0A84FF` (blue)  
**SF Symbol:** `house.fill`  
**Purpose:** The morning dashboard. A developer opens CodeLens, glances at Home, and knows: Is my project healthy? What happened? What should I do next?

> **Sidebar group:** Explore

### 12.1 Layout — Three-Column

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home            ●│  Good morning.                │   WHAT'S NEW           ║
║  ──────────────────  │  Trident Companion            │ 12 modules      │      ║
║   Explore           ▾│  Score 78/100                 │   Today                ║
║  📁 Projects         │                               │                        ║
║  🏛 Architecture     │  ┌──────────┐  ┌──────────┐   │   14:32                ║
║  📦 Dependencies     │                               │    78    │  │   72%    ║
║  🔍 Search           │                               │  Score   │  │Coverage  ║
║  ──────────────────  │                               │    ◉     │  │   ◉      ║
║   Create            ▾│                               │   Good   │  │  Fair    ║
║  📄 Context          │  └──────────┘  └──────────┘   │   ⚠ Bug fix: nil       ║
║  🔨 Tasks            │  ┌──────────┐  ┌──────────┐   │     date crash         ║
║  🧩 Blueprints       │                               │   247    │  │    12    ║
║  ──────────────────  │                               │  Types   │  │ Modules  ║
║   Quality           ▾│  └──────────┘  └──────────┘   │   ↻ Network retry      ║
║  ✅ Tests            │                               │     refactored         ║
║  🔒 Security         │  ────────────────────────     │                        ║
║  ⚡ Performance      │                               │   Yesterday            ║
║  ──────────────────  │  YOUR PROJECT MAP             │   ...                  ║
║   Knowledge         ▾│                               │                        ║
║  📖 Wiki             │  ┌────────────────────────────│   ────────────────     ║
║  📜 Conventions      │                               │   ┌──────┐       ┌─────║
║  📰 Changelog        │                               │   │ Net  │───────│ Data║
║  ──────────────────  │                               │   └──┬───┘       └──┬──║
║   Insights          ▾│                               │      │              │  ║
║  ♡ Health            │                               │   ┌──┴───┐       ┌──┴──║
║  △ Improve           │                               │   │ Auth │       │  UI ║
║  📊 Timeline         │                               │   └──────┘       └─────║
║  ──────────────────  │                               │                        ║
║   AI                ▾│                               │     Click to explore → ║
║  🧠 Intelligence     │  └────────────────────────────│                        ║
║  💬 Ask CodeLens     │                               │                        ║
║  🐛 Debug            │                               │                        ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │                               │                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion          ⌘K Search                        ✦ 0 tasks        ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 12.2 Home Components

#### A. Greeting + Context Bar

```
Good morning.
Trident Companion │ 12 modules │ Score 78/100
```

- Greeting changes by time: "Good morning" / "Good afternoon" / "Good evening"
- `SF Pro Semibold 17pt` for greeting, `Body` at 50% opacity for project context
- Score is colored: 0-40 red, 41-70 orange, 71-100 green

#### B. Stat Cards (2×2 Grid)

Four cards in a 2×2 grid. Each follows the Design System card pattern (`#2C2C2E`, 12pt radius):

```
┌────────────────────┐
│                    │
│    78              │   ← Large number: SF Pro Semibold 26pt, colored
│    Score           │   ← Label: Caption, 50% opacity
│     ◉              │   ← Ring chart indicator
│    Good            │   ← Qualitative label, colored
│                    │
└────────────────────┘
```

| Card | Number | Indicator | Click navigates to |
|---|---|---|---|
| Health Score | 78 | Ring 78/100, green | Health page |
| Coverage | 72% | Ring 72/100, orange | Tests page |
| Types | 247 | — | Search page |
| Modules | 12 | — | Architecture page |

#### C. Project Map (Mini Graph)

A small, non-interactive preview of the module dependency graph:

- Shows only top-level modules (not types/functions)
- Nodes sized by LOC, colored by health
- Labels appear on hover
- Click → navigates to Architecture page with full interactive graph
- Same Canvas rendering as the Architecture page but simplified

#### D. What's New (Right Column — Activity Timeline)

Chronological feed of meaningful events:

```
14:32
✓ Offline search added (+124 lines)
```

- ✓ green (feature), ⚠ orange (bug fix), ↻ blue (refactor), ● purple (build)
- Grouped by day ("Today", "Yesterday", "Feb 24")
- Scrollable, each entry clickable → navigates to relevant page

#### E. Needs Attention (Right Column, Below Timeline)

Notification-style list of actionable items. Maximum 3 visible, expandable.

- ⚠ orange = needs action
- ✓ green = positive confirmation
- 🔴 red = critical
- Each clickable → navigates to relevant page
- Disappears when empty (timeline fills the space)

---
