# Projects

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Explore · **Phase 1 — Shipped**  
> **Accent Color:** `#30D158` (green) · **SF Symbol:** `folder.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#30D158` (green)  
**Purpose:** Manage project folders. This is the home base — the first thing a user sees.

### 3.1 Empty State (No Projects)

```
╔══════════════════════╤════════════════════════╤══════════════════════════════╗
║                      │                        │                              ║
║  🏠 Home             │  🔍 Search projects...  │                              ║
║  ──────────────────  │                        │                              ║
║   Explore           ▾│                        │                              ║
║  📁 Projects        ●│                        │         ┌──────────┐         ║
║  🏛 Architecture     │                        │         │    📁    │          ║
║  📦 Dependencies     │        ┌──────────┐    │         │  (circle)│         ║
║  🔍 Search           │                        │    📁    │           │        ║
║  ──────────────────  │                        │  (circle)│           │       ║
║   Create            ▾│        └──────────┘    │      No Project Selected     ║
║  📄 Context          │                        │                              ║
║  🔨 Tasks            │       No Projects      │   Select a project to see    ║
║  🧩 Blueprints       │                        │        its details.          ║
║  ──────────────────  │   Add a project folder │                              ║
║   Quality           ▾│       get started.     │                              ║
║  ✅ Tests            │                        │                              ║
║  🔒 Security         │    [⊕ Add Project]     │                              ║
║  ⚡ Performance      │                        │                              ║
║  ──────────────────  │                        │                              ║
║   Knowledge         ▾│                        │                              ║
║  📖 Wiki             │                        │                              ║
║  📜 Conventions      │                        │                              ║
║  📰 Changelog        │                        │                              ║
║  ──────────────────  │                        │                              ║
║   Insights          ▾│                        │                              ║
║  ♡ Health            │                        │                              ║
║  △ Improve           │                        │                              ║
║  📊 Timeline         │                        │                              ║
║  ──────────────────  │                        │                              ║
║   AI                ▾│                        │                              ║
║  🧠 Intelligence     │                        │                              ║
║  💬 Ask CodeLens     │                        │                              ║
║  🐛 Debug            │                        │                              ║
║  ──────────────────  │                        │                              ║
║  ⚙ Settings          │                        │                              ║
║                      │                        │                              ║
╠══════════════════════╧════════════════════════╧══════════════════════════════╣
║  No project selected              + Add Project                  0 projects  ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 3.2 Populated State (With Projects)

```
╔══════════════════════╤════════════════════════╤══════════════════════════════╗
║                      │                        │                              ║
║  🏠 Home             │  🔍 Search projects...  │   Trident Companion          ║
║  ──────────────────  │                        │                              ║
║   Explore           ▾│  ┌─────────────────────│   ────────────────────       ║
║  📁 Projects        ●│                        │ 📱                     │   │  ║
║  🏛 Architecture     │                        │ Trident Companion    ● │←  │ ║
║  📦 Dependencies     │                        │ ~/Dev/Trident          │   │ ║
║  🔍 Search           │                        │ 12 modules · Score 78  │   │ ║
║  ──────────────────  │  └─────────────────────│   Types       247            ║
║   Create            ▾│  ┌─────────────────────│   Functions   1,089          ║
║  📄 Context          │                        │ 🖥                     │   │  ║
║  🔨 Tasks            │                        │ Dashboard Pro          │   │ ║
║  🧩 Blueprints       │                        │ ~/Dev/Dashboard        │   │ ║
║  ──────────────────  │                        │ 4 modules · Score 91   │   │ ║
║   Quality           ▾│  └─────────────────────│   Health Score               ║
║  ✅ Tests            │  ┌─────────────────────│                              ║
║  🔒 Security         │                        │ ⌚                     │   │  ║
║  ⚡ Performance      │                        │ WatchKit Extension     │   │ ║
║  ──────────────────  │                        │ ~/Dev/WatchKit         │   │ ║
║   Knowledge         ▾│                        │ 2 modules · Score 65   │   │ ║
║  📖 Wiki             │  └─────────────────────│   ────────────────────       ║
║  📜 Conventions      │                        │                              ║
║  📰 Changelog        │                        │   Test Coverage              ║
║  ──────────────────  │                        │                              ║
║   Insights          ▾│                        │     72%                      ║
║  ♡ Health            │                        │     ██████████████░░░░░░     ║
║  △ Improve           │                        │     Fair                     ║
║  📊 Timeline         │                        │                              ║
║  ──────────────────  │                        │   ────────────────────       ║
║   AI                ▾│                        │                              ║
║  🧠 Intelligence     │                        │   Last Analyzed              ║
║  💬 Ask CodeLens     │                        │   Today at 2:32 PM           ║
║  🐛 Debug            │                        │                              ║
║  ──────────────────  │                        │   Last Commit                ║
║  ⚙ Settings          │                        │   "Add offline search"       ║
║                      │                        │   14m ago                    ║
║                      │                        │                              ║
║                      │                        │   ────────────────────       ║
║                      │                        │                              ║
║                      │                        │   [Re-analyze]  [Open in     ║
║                      │                        │                  Finder]     ║
║                      │                        │                              ║
╠══════════════════════╧════════════════════════╧══════════════════════════════╣
║  Trident Companion                + Add Project                  3 projects  ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 3.3 Project List Item

Each project in the middle column list:

```
┌────────────────────────────────────────┐
│ 📱                                     │
│ Trident Companion                    ● │  ← green dot = healthy
│ ~/Dev/Trident                          │  ← path, tertiary text
│ 12 modules · Score 78                  │  ← stats, secondary text
└────────────────────────────────────────┘
```

| Element | Details |
|---|---|
| Platform icon | 📱 iOS, 🖥 macOS, ⌚ watchOS, 📺 tvOS, 📦 SPM |
| Name | `Section Header` weight |
| Path | `Caption`, 40% opacity, truncated with ~ |
| Stats | `Caption`, 60% opacity |
| Health dot | Right-aligned: green (>70), orange (50-70), red (<50) |
| Selected | Purple highlight pill background |
| Hover | #3A3A3C background |
| Right-click | "Re-analyze", "Remove", "Open in Finder", "Open in Xcode" |

### 3.4 Project Detail Panel (Right Column)

When a project is selected, the right panel shows:

**A. Header**
- Project name (Title 2)
- Horizontal divider

**B. Metadata Grid**
```
Platform    iOS
Language    Swift
Modules     12
Types       247
Functions   1,089
Lines       42,500
```
Each row: label (`Subtext`, 50% opacity, left) + value (`Body`, right-aligned).

**C. Health Score Card**
```
78 / 100
████████████████░░░░  
Good                    ← colored text (green/orange/red)
```
Large number top, progress bar, qualitative label below. Click → navigates to Architecture or future Health page.

**D. Test Coverage Card**
Same layout as health score.

**E. Recent Activity**
```
Last Analyzed       Today at 2:32 PM
Last Commit         "Add offline search"  14m ago
```

**F. Actions**
```
[Re-analyze]    [Open in Finder]
```
Secondary button style. "Re-analyze" triggers PKG re-ingestion with progress.

---
