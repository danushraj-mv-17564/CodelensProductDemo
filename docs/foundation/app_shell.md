# App Shell & Navigation

> **CodeLens UI/UX Design Specification — Foundation**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

### 1.1 Window Structure

CodeLens uses a three-column `NavigationSplitView`. The rightmost column can be toggled via the inspector button (top-right).

```
╔══════════════════════════════════════════════════════════════════════════════╗
║ ● ● ●   ☐     📁 No Project ▾     Projects       ⟳      🔍    ☐☐        ║
╠═══════════════╤═══════════════════════════════╤══════════════════════════════╣
║               │                               │                              ║
║   SIDEBAR     │        MIDDLE COLUMN          │       RIGHT COLUMN           ║
║               │                               │                              ║
║  (navigate)   │    (list / content / form)    │   (detail / inspector /      ║
║               │                               │    preview)                   ║
║               │                               │                              ║
╠═══════════════╧═══════════════════════════════╧══════════════════════════════╣
║  No project selected         + Add Project                     0 projects    ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 1.2 Title Bar

```
● ● ●   ☐     📁 No Project ▾     Projects       ⟳      🔍    ☐☐
 ╰─┘    ╰┘     ╰──────┬──────╯     ╰──┬──╯      ╰┘      ╰┘    ╰┘
traffic sidebar  project            current     refresh  search  inspector
lights  toggle   switcher           page name            (⌘F)   toggle
```

| Element | Behavior |
|---|---|
| Sidebar toggle (☐) | Hides/shows sidebar. Standard macOS. |
| Project switcher (📁 No Project ▾) | Dropdown showing recently opened projects. Click → select. |
| Page name | Static label — matches selected sidebar item |
| Refresh (⟳) | Re-scans/re-analyzes current project. Rotates while working. |
| Search (🔍) | Global search shortcut — same as clicking Search in sidebar |
| Inspector toggle (☐☐) | Shows/hides the right column |

### 1.3 Sidebar — The Complete Navigation

The sidebar uses two groups with a separator and per-item accent colors:

```
┌─────────────────┐
│  Workspace       │  ← Section header (Caption, 50% opacity)
│                  │
│  📁 Projects     │  green         ⌘1
│  📖 Wiki         │  purple        ⌘2
│  🏛 Architecture │  orange        ⌘3
│  📄 Context      │  green         ⌘4
│  🔍 Search       │  pink          ⌘5
│                  │
│  AI              │  ← Section header
│                  │
│  🧠 Intelligence │  purple        ⌘6
│  💬 Ask CodeLens │  teal          ⌘7
│                  │
│  ⚙ Settings      │  white/gray    ⌘,
│                  │
└─────────────────┘
```

**Sidebar Item States:**

| State | Appearance |
|---|---|
| Default | Icon + label at normal opacity, icon uses its section color |
| Hover | Row background lightens slightly (#2A2A2C) |
| Selected | Full-width purple/magenta pill highlight (#6B3FA0 @ 60%), white text |
| Keyboard focus | Thin outline ring (accessibility) |

**Icon-Color Mapping (exact from screenshots):**

| Item | Icon | Color | SF Symbol |
|---|---|---|---|
| Projects | 📁 | `#30D158` green | `folder.fill` |
| Wiki | 📖 | `#BF5AF2` purple | `building.columns.fill` |
| Architecture | 🏛 | `#FF9F0A` orange | `building.2.fill` |
| Context | 📄 | `#30D158` green | `doc.text.fill` |
| Search | 🔍 | `#FF375F` pink | `magnifyingglass` |
| Intelligence | 🧠 | `#BF5AF2` purple | `brain.head.profile` |
| Ask CodeLens | 💬 | `#64D2FF` teal | `bubble.left.and.text.bubble.right.fill` |
| Settings | ⚙ | `#8E8E93` gray | `gearshape.fill` |

### 1.4 Bottom Bar

A thin status bar at the bottom. Adapts per page:

```
╠══════════════════════════════════════════════════════════════════════════════╣
║  No project selected                + Add Project               0 projects  ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

| Element | Position | Behavior |
|---|---|---|
| Project status | Left | "No project selected" or project name |
| Quick action | Center | Page-specific shortcut ("+ Add Project", "+ Generate Docs", etc.) |
| Count | Right | "0 projects", "12 docs", "1,247 symbols" etc. |

---
