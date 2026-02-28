# Architecture

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Explore · **Phase 1 — Shipped**  
> **Accent Color:** `#FF9F0A` (orange) · **SF Symbol:** `building.2.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#FF9F0A` (orange)  
**Purpose:** Interactive dependency graph. Visualize your project's structure.

### 5.1 Empty State

```
╔══════════════════════╤══════════════════════════╤════════════════════════════╗
║                      │                          │                            ║
║  🏠 Home             │                          │       ┌──────────┐         ║
║  ──────────────────  │                          │       │    🏛    │          ║
║   Explore           ▾│●       ┌──────────┐      │       │  (circle)│         ║
║  📁 Projects         │                          │    🏛    │             │    ║
║  🏛 Architecture    ●│                          │  (circle)│             │   ║
║  📦 Dependencies     │        └──────────┘      │      Select a Module       ║
║  🔍 Search           │                          │                            ║
║  ──────────────────  │    No Architecture Data  │   Click a module in the    ║
║   Create            ▾│                          │     architecture map.      ║
║  📄 Context          │  Scan a project to genera│                            ║
║  🔨 Tasks            │  the dependency graph.   │                            ║
║  🧩 Blueprints       │                          │                            ║
║  ──────────────────  │                          │                            ║
║   Quality           ▾│                          │                            ║
║  ✅ Tests            │                          │                            ║
║  🔒 Security         │                          │                            ║
║  ⚡ Performance      │                          │                            ║
║  ──────────────────  │                          │                            ║
║   Knowledge         ▾│                          │                            ║
║  📖 Wiki             │                          │                            ║
║  📜 Conventions      │                          │                            ║
║  📰 Changelog        │                          │                            ║
║  ──────────────────  │                          │                            ║
║   Insights          ▾│                          │                            ║
║  ♡ Health            │                          │                            ║
║  △ Improve           │                          │                            ║
║  📊 Timeline         │                          │                            ║
║  ──────────────────  │                          │                            ║
║   AI                ▾│                          │                            ║
║  🧠 Intelligence     │                          │                            ║
║  💬 Ask CodeLens     │                          │                            ║
║  🐛 Debug            │                          │                            ║
║  ──────────────────  │                          │                            ║
║  ⚙ Settings          │                          │                            ║
║                      │                          │                            ║
╠═══════════════╧═════════╤═══════════════════════╧════════════════════════════╣
║  No project selected     │  🔍 100% 🔍   [Tree ●│Layered]   Filter  All ⇅      ║
╚══════════════════════════╧══════════════════════════════════════════════════╝
```

### 5.2 Populated State — The Graph View

```
╔══════════════════════╤══════════════════════════╤════════════════════════════╗
║                      │                          │                            ║
║  🏠 Home             │           ┌──────────┐   │   NetworkModule            ║
║  ──────────────────  │                          │  MainApp │          │      ║
║   Explore           ▾│●          └────┬─────┘   │   ────────────────         ║
║  📁 Projects         │        ┌──────┼──────┐   │                            ║
║  🏛 Architecture    ●│                          │      │      │          │   ║
║  📦 Dependencies     │   ┌────┴──┐ ┌─┴────┐ ┌┴──│   89 functions             ║
║  🔍 Search           │                          │ Auth  │ │ UI   │ │Network ●║
║  ──────────────────  │                          │Service│ │Comps │ │Module  │║
║   Create            ▾│   └───┬───┘ └──────┘ └───│   ────────────────         ║
║  📄 Context          │                          │                  │      │  ║
║  🔨 Tasks            │       └────────┬─────────│   Coverage                 ║
║  🧩 Blueprints       │           ┌────┴─────┐   │   ███████░░░░░░░ 45%       ║
║  ──────────────────  │                          │  Data    │          │   ⚠ B║
║   Quality           ▾│                          │  Layer   │          │      ║
║  ✅ Tests            │           └──────────┘   │   ────────────────         ║
║  🔒 Security         │                          │                            ║
║  ⚡ Performance      │                          │   Depends on               ║
║  ──────────────────  │                          │   · Foundation             ║
║   Knowledge         ▾│                          │   · AuthService            ║
║  📖 Wiki             │                          │                            ║
║  📜 Conventions      │                          │   Used by                  ║
║  📰 Changelog        │                          │   · MainApp                ║
║  ──────────────────  │                          │   · DataLayer              ║
║   Insights          ▾│                          │                            ║
║  ♡ Health            │                          │   ────────────────         ║
║  △ Improve           │                          │                            ║
║  📊 Timeline         │                          │   [View Docs →]            ║
║  ──────────────────  │                          │   [View Source →]          ║
║   AI                ▾│                          │   [Generate Tests →]       ║
║  🧠 Intelligence     │                          │                            ║
║  💬 Ask CodeLens     │                          │                            ║
║  🐛 Debug            │                          │                            ║
║  ──────────────────  │                          │                            ║
║  ⚙ Settings          │                          │                            ║
║                      │                          │                            ║
╠═══════════════╧═════════╤═══════════════════════╧════════════════════════════╣
║  Trident Companion       │  🔍 100% 🔍   [Tree ●│Layered]   Filter  All ⇅      ║
╚══════════════════════════╧══════════════════════════════════════════════════╝
```

### 5.3 Graph Rendering

The graph lives in the middle column. It's the visual heart of CodeLens.

**Node Design:**
```
┌───────────┐
│  Network  │     Background: module accent color @ 20%
│  Module   │     Border: module accent color @ 60%
└───────────┘     Text: white, SF Pro Semibold 12pt
                  Corner radius: 8pt
                  Size: proportional to LOC (min 80pt, max 160pt width)
```

**Node Colors by Health:**
- `#30D158` green border — healthy (>70% coverage)
- `#FF9F0A` orange border — fair (50-70%)
- `#FF453A` red border — needs attention (<50%)

**Edge Design:**
- 1pt lines, #8E8E93 @ 40%
- Arrow at the "depends on" end → direction = dependency flow
- Hover on edge: brightens to 80%, shows label "depends on"

**Graph Controls (Bottom Bar):**
```
🔍 100% 🔍   │   [Tree ●│Layered]   │   Filter  All ⇅
  zoom           layout toggle           filter dropdown
```

| Control | Behavior |
|---|---|
| 🔍 −/+ | Zoom out/in (10% increments) |
| 100% | Current zoom, click → reset to fit |
| Tree / Layered | Toggle between hierarchical tree and force-directed layout |
| Tree | Active = purple fill capsule |
| Layered | Active = purple fill capsule |
| Filter | Dropdown: All, by health status, by module |

**Graph Interactions:**

| Gesture | Action |
|---|---|
| Click node | Select → right panel shows module inspector |
| Double-click node | Drill into module → shows types within module |
| Scroll/pinch | Zoom |
| Click + drag canvas | Pan |
| Click + drag node | Reposition node |
| Right-click node | "View Docs", "Generate Tests", "View Source", "Focus Connections" |
| Hover node | Tooltip: "NetworkModule — 12 types, 45% coverage". Connected edges highlight. |

### 5.4 Drill-Down: Module → Types

When the user double-clicks a module, the graph zooms into it showing types:

```
╔══════════════════════╤══════════════════════════╤════════════════════════════╗
║                      │                          │                            ║
║  🏠 Home             │  ← NetworkModule         │   APIClient                ║
║  ──────────────────  │                          │                            ║
║   Explore           ▾│●  ┌─ protocol ──┐        │   class · NetworkModule    ║
║  📁 Projects         │                          │ Fetchable   │              ║
║  🏛 Architecture    ●│   └──────┬──────┘        │   Properties (5)           ║
║  📦 Dependencies     │                          │ conforms              │   ·║
║  🔍 Search           │   ┌──────┴──────┐   ┌────│   · baseURL: URL           ║
║  ──────────────────  │                          │  APIClient ●│───│APIRoute│ ║
║   Create            ▾│                          │  (class)    │   │(enum)  │ ║
║  📄 Context          │   └──────┬──────┘   └────│                            ║
║  🔨 Tasks            │                          │ uses                  │   F║
║  🧩 Blueprints       │   ┌──────┴──────┐        │   · fetch<T>(_:) async     ║
║  ──────────────────  │                          │NetworkError │              ║
║   Quality           ▾│                          │(enum)       │              ║
║  ✅ Tests            │   └─────────────┘        │                            ║
║  🔒 Security         │                          │   Tests: 3 / 8 functions   ║
║  ⚡ Performance      │                          │   Coverage: 38%            ║
║  ──────────────────  │                          │                            ║
║   Knowledge         ▾│                          │                            ║
║  📖 Wiki             │                          │                            ║
║  📜 Conventions      │                          │                            ║
║  📰 Changelog        │                          │                            ║
║  ──────────────────  │                          │                            ║
║   Insights          ▾│                          │                            ║
║  ♡ Health            │                          │                            ║
║  △ Improve           │                          │                            ║
║  📊 Timeline         │                          │                            ║
║  ──────────────────  │                          │                            ║
║   AI                ▾│                          │                            ║
║  🧠 Intelligence     │                          │                            ║
║  💬 Ask CodeLens     │                          │                            ║
║  🐛 Debug            │                          │                            ║
║  ──────────────────  │                          │                            ║
║  ⚙ Settings          │                          │                            ║
║                      │                          │                            ║
╠═══════════════╧═════════╤═══════════════════════╧════════════════════════════╣
║  NetworkModule           │  🔍 100% 🔍   [Tree ●│Layered]   Filter  All ⇅      ║
╚══════════════════════════╧══════════════════════════════════════════════════╝
```

The "← NetworkModule" is a back button in the top-left of the middle column. Click → returns to module-level view.

**Type Node Colors:**
- Class: `#0A84FF` blue
- Struct: `#30D158` green
- Protocol: `#BF5AF2` purple
- Enum: `#FF9F0A` orange

---
