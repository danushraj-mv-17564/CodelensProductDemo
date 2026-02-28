# CodeLens — Complete UI/UX Design Specification

> **Version:** 3.2 — Split documentation  
> **Date:** February 27, 2026  
> **Framework:** SwiftUI · NavigationSplitView · Swift Charts  
> **Theme:** Dark-first · Per-section accent colors  
> **Window:** Three-column — Sidebar · List/Content · Detail/Inspector

---

## Design Philosophy

1. **Three-column spatial model.** Sidebar = navigate. Middle = browse/act. Right = inspect/preview. Always.
2. **Color-coded navigation.** Each section owns a color. This builds muscle memory — green means projects, orange means architecture, pink means search.
3. **Progressive disclosure.** Empty states invite action. Populated states reveal depth. Power features hide until needed.
4. **Dark-first elegance.** The dark theme is the brand. Deep blacks (#1A1A1C), vibrant accent colors, soft shadows. Light mode exists but dark is home.
5. **AI is a collaborator, not a feature.** AI lives in dedicated sections and surfaces contextually everywhere else — never intrusive, always available.
6. **Six groups tell a story.** The sidebar reads: *Explore → Create → Quality → Knowledge → Insights → AI.* Every page belongs to exactly one group. This is intuitive on day one and powerful on day 100.

---

## App Architecture

| Layer | Detail |
|---|---|
| **Platform** | macOS 14 Sonoma+, Apple Silicon M1+ |
| **Framework** | SwiftUI, NavigationSplitView three-column |
| **AI** | Hybrid — Cloud (Anthropic Claude, OpenAI) + Local (MLX) |
| **Distribution** | Developer ID signed, Notarized, direct download |

---

## Sidebar — 6 Groups, 21 Pages

```
┌─────────────────┐
│                  │
│  🏠 Home         │  ← Standalone at top
│                  │
│  Explore ─────── │  "Understand your codebase"
│                  │
│  📁 Projects     │
│  🏛 Architecture │
│  📦 Dependencies │  NEW
│  🔍 Search       │
│                  │
│  Create ──────── │  "Build new things"
│                  │
│  📄 Context      │
│  🔨 Tasks        │  NEW
│  🧩 Blueprints   │  NEW
│                  │
│  Quality ─────── │  "Make sure it's right"
│                  │
│  ✅ Tests        │  NEW
│  🔒 Security     │  NEW
│  ⚡ Performance  │  NEW
│                  │
│  Knowledge ───── │  "Learn & document"
│                  │
│  📖 Wiki         │
│  📜 Conventions  │  NEW
│  📰 Changelog    │  NEW
│                  │
│  Insights ────── │  "Track & improve"
│                  │
│  ♡ Health        │  NEW
│  △ Improve       │  NEW
│  📊 Timeline     │  NEW
│                  │
│  AI ──────────── │  "The brain"
│                  │
│  🧠 Intelligence │
│  💬 Ask CodeLens │
│  🐛 Debug        │  NEW
│                  │
│  ⚙ Settings      │
│                  │
└─────────────────┘
```

---

## Complete Icon-Color Map

| # | Page | Group | Color | Hex | SF Symbol |
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

## Documentation Index

### Foundation
| Document | Description |
|---|---|
| [App Shell & Navigation](foundation/app_shell.md) | Window structure, title bar, sidebar, bottom bar |
| [Design System](foundation/design_system.md) | Colors, typography, empty state pattern, CTA buttons, inputs |
| [Onboarding & First Launch](foundation/onboarding.md) | Welcome flow, project import, analysis animation |

### Explore — "Understand your codebase"
| Document | Page | Phase | Accent |
|---|---|---|---|
| [Home Dashboard](pages/explore/09_home_dashboard.md) | Home | Phase 2 | 🔵 Blue |
| [Projects](pages/explore/01_projects.md) | Projects | Shipped | 🟢 Green |
| [Architecture](pages/explore/03_architecture.md) | Architecture | Shipped | 🟠 Orange |
| [Dependencies](pages/explore/10_dependencies.md) | Dependencies | Phase 2 | 🟣 Indigo |
| [Search](pages/explore/05_search.md) | Search | Shipped | 🔴 Pink |

### Create — "Build new things"
| Document | Page | Phase | Accent |
|---|---|---|---|
| [Context](pages/create/04_context.md) | Context | Shipped | 🟢 Green |
| [Tasks / Build Pipeline](pages/create/11_tasks.md) | Tasks | Phase 2 | 🟠 Orange |
| [Blueprints / Module Generator](pages/create/12_blueprints.md) | Blueprints | Phase 2 | 🟡 Yellow |

### Quality — "Make sure it's right"
| Document | Page | Phase | Accent |
|---|---|---|---|
| [Tests / UI Test Lab](pages/quality/13_tests.md) | Tests | Phase 2 | 🟢 Green |
| [Security Scanner](pages/quality/14_security.md) | Security | Phase 2 | 🔴 Red |
| [Performance Profiler](pages/quality/15_performance.md) | Performance | Phase 2 | 🟠 Orange |

### Knowledge — "Learn & document"
| Document | Page | Phase | Accent |
|---|---|---|---|
| [Wiki](pages/knowledge/02_wiki.md) | Wiki | Shipped | 🟣 Purple |
| [Conventions](pages/knowledge/16_conventions.md) | Conventions | Phase 2 | 🟤 Gold |
| [Changelog Generator](pages/knowledge/17_changelog.md) | Changelog | Phase 2 | 🟢 Green |

### Insights — "Track & improve"
| Document | Page | Phase | Accent |
|---|---|---|---|
| [Health](pages/insights/18_health.md) | Health | Phase 3 | 🔴 Pink |
| [Improve / AI Insights](pages/insights/19_improve.md) | Improve | Phase 3 | 🟣 Purple |
| [Timeline / Activity Feed](pages/insights/20_timeline.md) | Timeline | Phase 3 | 🔵 Teal |

### AI — "The brain"
| Document | Page | Phase | Accent |
|---|---|---|---|
| [Intelligence](pages/ai/06_intelligence.md) | Intelligence | Shipped | 🟣 Purple |
| [Ask CodeLens](pages/ai/07_ask_codelens.md) | Ask CodeLens | Shipped | 🔵 Teal |
| [Debug Assistant](pages/ai/21_debug.md) | Debug | Phase 3 | 🔴 Red |

### Settings
| Document | Page | Phase | Accent |
|---|---|---|---|
| [Settings](pages/settings/08_settings.md) | Settings | Shipped | ⚪ Gray |

### Cross-Cutting
| Document | Description |
|---|---|
| [Sidebar Evolution Roadmap](cross-cutting/sidebar_evolution.md) | 3-phase growth: 8 → 16 → 21 items |
| [Spotlight Search (⌘K)](cross-cutting/spotlight_search.md) | Global command palette |
| [Notification System](cross-cutting/notifications.md) | Toast + feed design |
| [Global Features](cross-cutting/global_features.md) | Keyboard shortcuts, drag & drop, themes |
| [Empty States & Error States](cross-cutting/empty_states.md) | Complete catalog for all 21 pages |
| [Animations & Transitions](cross-cutting/animations.md) | Motion design language |
| [Accessibility](cross-cutting/accessibility.md) | VoiceOver, keyboard nav, color contrast |
| [Full User Journey](cross-cutting/user_journey.md) | Day 1 → Day 365 walkthrough |

---

## Release Phases

### Phase 1 — Shipped MVP (8 sidebar items)
Projects · Wiki · Architecture · Context · Search · Intelligence · Ask CodeLens · Settings

### Phase 2 — Create & Quality (16 sidebar items)
+Home · +Dependencies · +Tasks · +Blueprints · +Tests · +Security · +Performance · +Conventions · +Changelog

### Phase 3 — Full Vision (21 sidebar items)
+Health · +Improve · +Timeline · +Debug

---

> *21 pages across 6 sidebar groups. Each page has its own document with wireframes,*  
> *empty states, populated states, component specs, and interaction details.*  
> *The sidebar reads: Explore → Create → Quality → Knowledge → Insights → AI.*

---

*CodeLens — The Autonomous Software Development Intelligence Platform*  
*UI/UX Design Specification v3.2 — February 27, 2026*  
*Designed for developers. Built as a Mac app. Inspired by Apple.*
