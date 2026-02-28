# Tests / UI Test Lab

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Quality · **Phase 2**  
> **Accent Color:** `#30D158` (green) · **SF Symbol:** `checkmark.shield.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#30D158` (green)  
**SF Symbol:** `checkmark.shield.fill`  
**Purpose:** Generate, run, and manage XCUITests for SwiftUI views. A test laboratory — select a view, generate tests, run them, see results.

> **Sidebar group:** Quality

### 16.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  🔍 Filter views...            │     ┌──────────┐       ║
║  ──────────────────  │                               │     │    ✅    │        ║
║   Explore           ▾│                               │     │  (circle)│       ║
║  📁 Projects         │         ┌──────────┐          │     └──────────┘       ║
║  🏛 Architecture     │                               │    ✅    │              ║
║  📦 Dependencies     │                               │  (circle)│             ║
║  🔍 Search           │         └──────────┘          │                        ║
║  ──────────────────  │                               │   Select a SwiftUI     ║
║   Create            ▾│    No SwiftUI Views Found     │   view to generate     ║
║  📄 Context          │                               │   and run tests.       ║
║  🔨 Tasks            │   Make sure the project has   │                        ║
║  🧩 Blueprints       │   .swift files with SwiftUI vi│                        ║
║  ──────────────────  │                               │                        ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests           ●│                               │                        ║
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
║  📊 Timeline         │                               │                        ║
║  ──────────────────  │                               │                        ║
║   AI                ▾│                               │                        ║
║  🧠 Intelligence     │                               │                        ║
║  💬 Ask CodeLens     │                               │                        ║
║  🐛 Debug            │                               │                        ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │                               │                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                              0 views       ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 16.2 Populated State — View Tree + Test Generator

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  🔍 Filter views...            │  GENERATE TESTS        ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│  ▼ ContentView                │  Selected:             ║
║  📁 Projects         │     ▼ NavigationStack         │  TaskListView          ║
║  🏛 Architecture     │       ● TaskListView          │                        ║
║  📦 Dependencies     │         TaskDetailView        │  ────────────────      ║
║  🔍 Search           │         TaskEditView          │                        ║
║  ──────────────────  │     ▼ TabView                 │  What to test:         ║
║   Create            ▾│       HomeTab                 │                        ║
║  📄 Context          │       SearchTab               │  [✓] Elements exist    ║
║  🔨 Tasks            │       ProfileTab              │  [✓] Navigation works  ║
║  🧩 Blueprints       │                               │  [✓] Search & results  ║
║  ──────────────────  │  ────────────────────         │  [ ] State changes     ║
║   Quality           ▾│                               │  [ ] Edge cases        ║
║  ✅ Tests           ●│  Accessibility IDs            │                        ║
║  🔒 Security         │                               │  Notes (optional):     ║
║  ⚡ Performance      │  ● 6 / 10 elements have IDs   │  ┌────────────────┐    ║
║  ──────────────────  │                               │  │                │    ║
║   Knowledge         ▾│  Missing:                     │  └────────────────┘    ║
║  📖 Wiki             │  · searchBar                  │                        ║
║  📜 Conventions      │  · filterButton               │    [⊕ Generate Tests]  ║
║  📰 Changelog        │  · emptyStateLabel            │                        ║
║  ──────────────────  │  · sortButton                 │  ────────────────      ║
║   Insights          ▾│                               │                        ║
║  ♡ Health            │  [Add Missing IDs]            │  Previous tests:       ║
║  △ Improve           │                               │  ✓ TaskListViewUI      ║
║  📊 Timeline         │                               │    5 tests · 2h ago    ║
║  ──────────────────  │                               │                        ║
║   AI                ▾│                               │  [Run Again]  [Edit]   ║
║  🧠 Intelligence     │                               │                        ║
║  💬 Ask CodeLens     │                               │                        ║
║  🐛 Debug            │                               │                        ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │                               │                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                             12 views       ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 16.3 Middle Column — View Tree

Outline view of the SwiftUI view hierarchy with disclosure triangles:

| Element | Details |
|---|---|
| View name | Regular weight, SF Pro 13pt |
| Selected | Purple pill highlight |
| Full a11y coverage | Green dot ● |
| Partial a11y coverage | Orange dot ● |
| No accessibility IDs | Red dot ● |
| Filter | Real-time tree filter at top |

**Below tree — Accessibility ID Report:**

- Shows "6/10 elements have IDs"
- Lists missing elements by name
- **[Add Missing IDs]** — triggers Developer Agent to add `.accessibilityIdentifier()` modifiers to source. One-click fix.

### 16.4 Test Type Checkboxes

Simple, not overwhelming:

| Option | What it generates |
|---|---|
| Elements exist | Basic smoke — launch, navigate, assert elements present |
| Navigation works | Tap buttons/links, verify destination views load |
| Search & results | Type text, verify results update, verify empty state |
| State changes | Toggle switches, selections, verify UI updates |
| Edge cases | Memory pressure, network loss, rotation, large text |

### 16.5 Generated Test Preview (Right Column After Generate)

```
Generated: TaskListViewUITests.swift
5 tests · Estimated runtime: ~45s

────────────────────────────────────

  1  import XCTest
  2
  3  final class TaskListViewUITests:
  4      XCTestCase {
  5
  6      let app = XCUIApplication()
  7
  8      override func setUpWithError()
  9          throws {
 10          continueAfterFailure = false
 11          app.launch()
 12      }
 13
 14      func test_elementsExist() {
 15          let list = app
 16              .collectionViews[
 17              "TaskList.collection"]
 18          XCTAssert(list
 19              .waitForExistence(
 20                  timeout: 5))
 21      }
 22      ...

────────────────────────────────────

[▶ Run Tests]  [Save to Project]  [🔄 Regenerate]
```

- Syntax highlighted Swift (SF Mono 12pt)
- Line numbers in gutter
- Actions at bottom

### 16.6 Test Runner — Live Execution View

When "Run Tests" is pressed, the right column transforms:

```
Running Tests
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Simulator: iPhone 16 Pro — iOS 18.0

┌────────────────────────────────┐
│                                │
│   ┌──────────────────────┐    │
│   │                      │    │   Live simulator
│   │  📱 Simulator        │    │   feed showing
│   │  Preview             │    │   tests running
│   │                      │    │
│   │  (Real-time screen   │    │
│   │   capture from       │    │
│   │   simulator)         │    │
│   │                      │    │
│   └──────────────────────┘    │
│                                │
└────────────────────────────────┘

✓ test_elementsExist        0.8s
✓ test_navigation           1.2s
● test_search        Running...
○ test_emptyState           —
○ test_filter               —

Progress: 2/5  ·  2.0s elapsed
                          [Stop]
```

- **Live simulator preview** — screenshot stream from the simulator while tests run. Visually compelling, builds trust.
- Results appear one by one with check/cross animation
- Active test has pulsing ● indicator
- On completion: summary card with pass/fail count

---
