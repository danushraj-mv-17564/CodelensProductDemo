# Sidebar Evolution Roadmap

> **CodeLens UI/UX Design Specification — Cross-Cutting**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

The sidebar grows across four phases. Each phase adds a new group. The 6-group structure (Explore → Create → Quality → Knowledge → Insights → AI) emerges organically — developers never face a wall of 21 items on day one.

### Phase 1 — Current (Shipped MVP) — 8 Items

```
┌─────────────────┐
│                  │
│  Explore         │
│                  │
│  📁 Projects     │
│  📖 Wiki         │
│  🏛 Architecture │
│  📄 Context      │
│  🔍 Search       │
│                  │
│  AI              │
│                  │
│  🧠 Intelligence │
│  💬 Ask CodeLens │
│                  │
│  ⚙ Settings      │
│                  │
└─────────────────┘
```

Two groups. Focused on understanding your codebase and talking to AI about it.

### Phase 2 — Create & Quality — 16 Items

```
┌─────────────────┐
│                  │
│  Explore         │
│                  │
│  🏠 Home         │  ← NEW
│  📁 Projects     │
│  🏛 Architecture │
│  📦 Dependencies │  ← NEW
│  🔍 Search       │
│                  │
│  Create          │  ← NEW GROUP
│                  │
│  📄 Context      │  ← moved here
│  🔨 Tasks        │  ← NEW
│  🧩 Blueprints   │  ← NEW
│                  │
│  Quality         │  ← NEW GROUP
│                  │
│  ✅ Tests        │  ← NEW
│  🔒 Security     │  ← NEW
│  ⚡ Performance  │  ← NEW
│                  │
│  AI              │
│                  │
│  🧠 Intelligence │
│  💬 Ask CodeLens │
│                  │
│  ⚙ Settings      │
│                  │
└─────────────────┘
```

Three new groups appear. Context moves to Create (it creates output files). Wiki stays undocked until Knowledge group launches.

### Phase 3 — Knowledge & Insights — 21 Items (Full Vision)

```
┌─────────────────┐
│                  │
│  Explore         │  🔵 "Understand your codebase"
│                  │
│  🏠 Home         │  blue     house.fill
│  📁 Projects     │  green    folder.fill
│  🏛 Architecture │  orange   building.2.fill
│  📦 Dependencies │  indigo   shippingbox.fill
│  🔍 Search       │  pink     magnifyingglass
│                  │
│  Create          │  🟠 "Build new things"
│                  │
│  📄 Context      │  green    doc.text.fill
│  🔨 Tasks        │  orange   hammer.fill
│  🧩 Blueprints   │  yellow   puzzlepiece.extension.fill
│                  │
│  Quality         │  🔴 "Make sure it's right"
│                  │
│  ✅ Tests        │  green    checkmark.shield.fill
│  🔒 Security     │  red      lock.shield.fill
│  ⚡ Performance  │  orange   gauge.with.dots.needle.33percent
│                  │
│  Knowledge       │  🟤 "Learn & document"
│                  │
│  📖 Wiki         │  purple   building.columns.fill
│  📜 Conventions  │  gold     text.book.closed.fill
│  📰 Changelog    │  green    doc.text.magnifyingglass
│                  │
│  Insights        │  🟣 "Track & improve"
│                  │
│  ♡ Health        │  pink     heart.text.square.fill
│  △ Improve       │  purple   chart.line.uptrend.xyaxis
│  📊 Timeline     │  teal     clock.arrow.circlepath
│                  │
│  AI              │  🔵 "The brain"
│                  │
│  🧠 Intelligence │  purple   brain.head.profile
│  💬 Ask CodeLens │  teal     bubble.left.and.text.bubble.right.fill
│  🐛 Debug        │  red      ant.fill
│                  │
│  ⚙ Settings      │  gray     gearshape.fill
│                  │
└─────────────────┘
```

21 items across 6 groups. The sidebar reads as a sentence: *"Explore my code. Create something new. Validate quality. Build knowledge. Gain insights. Talk to AI."*

**Complete Icon-Color Mapping (Full Vision):**

| # | Item | Group | Color | Hex | SF Symbol |
|---|---|---|---|---|---|
| 1 | Home | Explore | Blue | `#0A84FF` | `house.fill` |
| 2 | Projects | Explore | Green | `#30D158` | `folder.fill` |
| 3 | Architecture | Explore | Orange | `#FF9F0A` | `building.2.fill` |
| 4 | Dependencies | Explore | Indigo | `#5E5CE6` | `shippingbox.fill` |
| 5 | Search | Explore | Pink | `#FF375F` | `magnifyingglass` |
| 6 | Context | Create | Green | `#30D158` | `doc.text.fill` |
| 7 | Tasks | Create | Orange | `#FF9F0A` | `hammer.fill` |
| 8 | Blueprints | Create | Yellow | `#FFD60A` | `puzzlepiece.extension.fill` |
| 9 | Tests | Quality | Green | `#30D158` | `checkmark.shield.fill` |
| 10 | Security | Quality | Red | `#FF453A` | `lock.shield.fill` |
| 11 | Performance | Quality | Orange | `#FF9F0A` | `gauge.with.dots.needle.33percent` |
| 12 | Wiki | Knowledge | Purple | `#BF5AF2` | `building.columns.fill` |
| 13 | Conventions | Knowledge | Gold | `#AC8E68` | `text.book.closed.fill` |
| 14 | Changelog | Knowledge | Green | `#30D158` | `doc.text.magnifyingglass` |
| 15 | Health | Insights | Pink | `#FF375F` | `heart.text.square.fill` |
| 16 | Improve | Insights | Purple | `#BF5AF2` | `chart.line.uptrend.xyaxis` |
| 17 | Timeline | Insights | Teal | `#64D2FF` | `clock.arrow.circlepath` |
| 18 | Intelligence | AI | Purple | `#BF5AF2` | `brain.head.profile` |
| 19 | Ask CodeLens | AI | Teal | `#64D2FF` | `bubble.left.and.text.bubble.right.fill` |
| 20 | Debug | AI | Red | `#FF453A` | `ant.fill` |
| 21 | Settings | — | Gray | `#8E8E93` | `gearshape.fill` |

---
