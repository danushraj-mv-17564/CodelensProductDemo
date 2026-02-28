# Tasks / Build Pipeline

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Create · **Phase 2**  
> **Accent Color:** `#FF9F0A` (orange) · **SF Symbol:** `hammer.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#FF9F0A` (orange)  
**SF Symbol:** `hammer.fill`  
**Purpose:** Describe what you want to build. AI agents plan, write, test, and ship it. This is the soul of CodeLens.

> **Sidebar group:** Create

### 14.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  🔍 Search tasks...            │     ┌──────────┐       ║
║  ──────────────────  │                               │     │    🔨    │        ║
║   Explore           ▾│                               │     │  (circle)│       ║
║  📁 Projects         │                               │     └──────────┘       ║
║  🏛 Architecture     │         ┌──────────┐          │                        ║
║  📦 Dependencies     │                               │    🔨    │              ║
║  🔍 Search           │                               │  (circle)│             ║
║  ──────────────────  │         └──────────┘          │   Select a task to     ║
║   Create            ▾│                               │   see its pipeline     ║
║  📄 Context          │       No Tasks Yet            │   and progress.        ║
║  🔨 Tasks           ●│                               │                        ║
║  🧩 Blueprints       │  Describe what you want to bui│                        ║
║  ──────────────────  │  CodeLens will plan, write, te│                        ║
║   Quality           ▾│  and ship it for you.         │                        ║
║  ✅ Tests            │                               │                        ║
║  🔒 Security         │      [⊕ New Task]             │                        ║
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
║  Trident Companion              ⊕ New Task                       0 tasks      ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 14.2 New Task Input

Clicking "⊕ New Task" opens a sheet or inline expanding input at the top of the middle column:

```
┌──────────────────────────────────────────────────────────┐
│                                                          │
│  What do you want to build?                              │
│                                                          │
│  ┌──────────────────────────────────────────────────┐   │
│  │ Add dark mode support with automatic             │   │
│  │ switching based on system preferences.           │   │
│  │                                                  │   │
│  └──────────────────────────────────────────────────┘   │
│                                                          │
│  ┌────────────────────┐                                  │
│  │ Model: Claude Opus 4│  ← Uses Code & Design model    │
│  └────────────────────┘                                  │
│                                                          │
│                                          [▶ Start Build] │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

- Multi-line text area, auto-expands up to 6 lines
- Placeholder: "What do you want to build?" at 40% opacity
- "▶ Start Build" — orange capsule button, appears when text is entered
- ⌘Enter also triggers the build
- Model indicator shows which AI model will be used (from Intelligence settings)

### 14.3 Populated State — Task List

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  🔍 Search tasks...            │                        ║
║  ──────────────────  │                               │   Dark mode support    ║
║   Explore           ▾│  ┌────────────────────────────│                        ║
║  📁 Projects         │                               │  ● Dark mode support   ║
║  🏛 Architecture     │                               │    Step 3/5 · 4m elapse║
║  📦 Dependencies     │  └────────────────────────────│   [Plan✓]─[Des✓]─      ║
║  🔍 Search           │  ┌────────────────────────────│   [Code●]─[Test○]─     ║
║  ──────────────────  │                               │  ✓ Offline search suppo║
║   Create            ▾│                               │    12m · $2.40 · 5/5 te║
║  📄 Context          │  └────────────────────────────│   Step 3 of 5          ║
║  🔨 Tasks           ●│  ┌────────────────────────────│   4m 12s · $1.80       ║
║  🧩 Blueprints       │                               │  ✕ Push notification ha║
║  ──────────────────  │                               │    22m · $5.20 · Build ║
║   Quality           ▾│  └────────────────────────────│                        ║
║  ✅ Tests            │                               │   (See 14.5 for full   ║
║  🔒 Security         │                               │    pipeline detail)    ║
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
║  Trident Companion              ⊕ New Task                       3 tasks      ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 14.4 Task List Item

```
┌──────────────────────────────────────┐
│  ● Dark mode support                 │  ← status icon: ● blue (running), ✓ green (done), ✕ red (failed)
│    Step 3/5 · 4m elapsed            │  ← progress info, Caption, 50% opacity
└──────────────────────────────────────┘
```

| State | Icon | Color |
|---|---|---|
| Running | ● (pulsing) | `#0A84FF` blue |
| Completed | ✓ | `#30D158` green |
| Failed | ✕ | `#FF453A` red |
| Paused | ⏸ | `#FF9F0A` orange |
| Review needed | 🔒 | `#BF5AF2` purple |

### 14.5 Right Column — The 5-Step Pipeline (Active Task)

This is the heart of the Build experience. The 5-step pipeline renders in the right column when a task is selected:

```
Dark mode support
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Plan ✓]───[Design ✓]───[Code ●]───[Test ○]───[Ship ○]

Step 3 of 5  ·  4m 12s elapsed  ·  $1.80 so far

────────────────────────────────────────

┌─ PLAN ──────────────────────────── ✓ Done ───┐
│                                               │
│  Requirements                                 │
│  ✓ Support automatic dark/light switching     │
│  ✓ Persist user preference                    │
│  ✓ Theme all screens consistently             │
│  ✓ Respect system appearance setting          │
│                                               │
│  Edge cases: 3 identified                     │
│                                      [Expand] │
└───────────────────────────────────────────────┘

┌─ DESIGN ────────────────────────── ✓ Done ───┐
│                                               │
│  Modules: UIComponents, MainApp, Settings     │
│  Approach: ThemeManager + asset catalog        │
│  Risk: Low — isolated UI layer changes        │
│                                      [Expand] │
└───────────────────────────────────────────────┘

┌─ CODE ────────────────────── ● Writing... ───┐
│                                               │
│  Writing ThemeManager.swift...                │
│                                               │
│  Files:                                       │
│  + ThemeManager.swift          42 lines       │
│  + ColorAssets.xcassets        (new)          │
│  ~ ContentView.swift           +18 −4        │
│  ~ AppDelegate.swift           +6 −2         │
│                                               │
│  ██████████████████░░░░░░░  72%               │
│                                               │
└───────────────────────────────────────────────┘

   ○ TEST — Waiting for Code

   ○ SHIP — Waiting for Test

────────────────────────────────────────

                            [Pause]  [Cancel]
```

**The 5 steps:**

| Step | Label | Internal Agents | User Sees |
|---|---|---|---|
| 1 | **Plan** | PM Agent | Requirements list, edge cases |
| 2 | **Design** | Architect Agent | Affected modules, approach, risk level |
| 3 | **Code** | Developer Agent | File list with diffs, live progress |
| 4 | **Test** | Test Agent + QA Agent | Test results (pass/fail), self-correction |
| 5 | **Ship** | Reviewer Agent + Execution Engine | Review comments, build output, ready branch |

**Why 5, not 7?** Because the user doesn't care about internal agent roles. They care about the journey: Plan → Design → Code → Test → Ship.

#### Step Card States

**Pending:**
```
○ TEST — Waiting for Code
```
Single line, gray, minimal.

**Active:**
```
┌─ CODE ────────────────────── ● Writing... ───┐
│  (Live streaming content — text as agent works)│
│  ██████████████████░░░░░░░  68%               │
└───────────────────────────────────────────────┘
```
Expanded, orange border glow, progress bar inside.

**Completed:**
```
┌─ PLAN ──────────────────────────── ✓ Done ───┐
│  (Summary, collapsed to key points)           │
│                                      [Expand] │
└───────────────────────────────────────────────┘
```
Green checkmark, collapsed. "Expand" reveals full output.

### 14.6 Human Review Gates

When a step requires human approval (configurable in Settings), the card pauses:

```
┌─ DESIGN ───────────────── 🔒 Review needed ──┐
│                                               │
│  Modules: DataLayer, SearchModule, TaskViews  │
│                                               │
│  Approach                                     │
│  Create OfflineSearchService using SQLite     │
│  FTS5. Wire into TaskListViewModel via        │
│  existing DI pattern.                         │
│                                               │
│  Risk: Low — isolated, no breaking deps       │
│                                               │
│  ┌─────────┐  ┌──────────────┐  ┌──────────┐│
│  │ Approve │  │ Edit & Retry │  │  Reject  ││
│  │    ▶    │  │      ✏️       │  │    ✕     ││
│  └─────────┘  └──────────────┘  └──────────┘│
│                                               │
└───────────────────────────────────────────────┘
```

Three actions:
- **Approve** (green) — continue to next step
- **Edit & Retry** — opens output in editable text area, regenerates
- **Reject** (red) — stops the entire build

### 14.7 Code Step — Diff Viewer (Expanded)

When Code step completes and user clicks "Expand":

```
Files Changed: 4  │  +187 −12

[Side by Side]  [Unified]
────────────────────────────────

OfflineSearchService.swift  (NEW)

  1   + import Foundation
  2   + import SwiftData
  3   +
  4   + /// Offline full-text search over tasks
  5   + @Observable
  6   + final class OfflineSearchService {
  7   +     private let index: SearchIndex
  ...

────────────────────────────────
SearchIndex.swift  (NEW)
TaskListView.swift  (MODIFIED)
TaskListViewModel.swift  (MODIFIED)
```

- Syntax highlighting (Xcode-style, dark mode)
- New lines: green background tint (+)
- Removed lines: red background tint (−)
- `SF Mono` at 12pt
- Click filename → scrolls to that file's diff

### 14.8 Test Step — Results View

```
┌─ TEST ─────────────────── ✓ 5/5 passed ─────┐
│                                               │
│  ✓ test_search_byTitle         0.3s          │
│  ✓ test_search_emptyQuery      0.1s          │
│  ✓ test_search_specialChars    0.2s          │
│  ✓ test_search_debounced       0.4s          │
│  ✓ test_search_offline         0.2s          │
│                                               │
│  Total: 1.2s                                  │
│  Self-correction: 1 retry (fixed assertion)   │
│                                      [Details]│
└───────────────────────────────────────────────┘
```

If tests fail and self-correct:

```
│  ✕ test_search_specialChars    0.2s          │
│    Expected: 1, Got: 0                        │
│    → Retrying... (attempt 2/3)                │
│  ✓ test_search_specialChars    0.3s  (retry) │
```

### 14.9 Ship Step — Final Result

```
┌─ SHIP ──────────────── ✓ Ready to merge ──── ┐
│                                               │
│  Branch: feature/offline-search               │
│  Build:  ✓ Succeeded                          │
│  Tests:  ✓ 5/5 passing                        │
│  Review: ✓ No issues found                    │
│                                               │
│  Time: 8m 14s  │  Cost: $2.40  │  Retries: 1 │
│                                               │
│  ┌─────────────────┐  ┌──────────────────┐   │
│  │ Open in Xcode   │  │ View in Terminal │   │
│  └─────────────────┘  └──────────────────┘   │
│                                               │
│  Review Summary                               │
│  "Clean implementation. Follows existing      │
│   repository pattern. Good test coverage.     │
│   Suggestion: consider search history cache." │
│                                               │
└───────────────────────────────────────────────┘
```

---
