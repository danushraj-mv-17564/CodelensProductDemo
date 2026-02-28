# Empty States & Error States

> **CodeLens UI/UX Design Specification — Cross-Cutting**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

### 29.1 Empty States — Every Page

All empty states follow the Design System pattern (Section 2.3): centered icon in accent-colored circle, title, subtitle, purple CTA button.

| Page | Icon | Color | Title | Subtitle | CTA |
|---|---|---|---|---|---|
| Home | 🏠 | blue | Welcome to CodeLens | Add a project to see your dashboard. | ⊕ Add Project |
| Projects | 📁 | green | No Projects | Add a project folder to get started. | ⊕ Add Project |
| Architecture | 🏛 | orange | No Architecture Data | Scan a project to generate the graph. | — (auto) |
| Dependencies | 📦 | indigo | No Dependencies Found | Open a project with Package.swift. | — (auto) |
| Search | 🔍 | pink | Semantic Search | Search by meaning, not just names. | — (type to search) |
| Context | 📄 | green | Context Preview | Configure and generate context files. | ✦ Generate |
| Tasks | 🔨 | orange | No Tasks Yet | Describe what you want to build. | ⊕ New Task |
| Blueprints | 🧩 | yellow | Module Blueprints | Describe a module to generate scaffolding. | ⊕ New Blueprint |
| Tests | ✅ | green | No Views Found | Project needs SwiftUI views. | — |
| Security | 🔒 | red | Security Scanner | Scan for vulnerabilities and secrets. | 🔒 Run Scan |
| Performance | ⚡ | orange | Performance Profiler | Build the project to see metrics. | — (auto) |
| Wiki | 📖 | purple | No Documentation | Scan a project and generate docs. | ⊕ Generate Docs |
| Conventions | 📜 | gold | Conventions | CodeLens will learn your style. | — (auto) |
| Changelog | 📰 | green | Changelog Generator | Select a date range to generate notes. | ✦ Generate |
| Health | ♡ | pink | Come Back Tomorrow | Needs a few commits for trends. | — |
| Improve | △ | purple | Not Enough Data | After a few weeks, insights appear. | — |
| Timeline | 📊 | teal | No Activity Yet | Events appear as you use CodeLens. | — |
| Intelligence | 🧠 | purple | Select a Provider | Configure AI providers for analysis. | + Add Provider |
| Ask CodeLens | 💬 | teal | Ask CodeLens | Ask questions about your codebase. | — (type to ask) |
| Debug | 🐛 | red | Debug Assistant | Paste a crash log to analyze. | — (paste to start) |
| Settings | ⚙ | gray | Settings | Open with Cmd+, | — |

**Right column empty states** all follow: icon circle + "No X Selected" + "Select/Click X to see details."

### 29.2 Error States

**Network error (cloud LLM unavailable):**

```
┌──────────────────────────────────────────┐
│                                          │
│  ⚠ Couldn't reach Claude API            │
│                                          │
│  The AI service is temporarily           │
│  unavailable. CodeLens will retry        │
│  automatically in 30 seconds.            │
│                                          │
│  Local features (Architecture, Search,   │
│  Wiki) continue to work offline.         │
│                                          │
│              [Retry Now]                 │
│                                          │
└──────────────────────────────────────────┘
```

Orange left border. `#2C2C2E` background. Informative + reassuring.

**Build failure (max retries exceeded):**

```
┌─ SHIP ──────────────── ⚠ Couldn't complete ─┐
│                                               │
│  CodeLens tried 5 times but couldn't get     │
│  a clean build.                               │
│                                               │
│  Remaining errors:                            │
│  · Type 'SearchIndex' has no member 'reindex'│
│  · Missing return in 'performSearch'          │
│                                               │
│  Branch feature/offline-search has partial    │
│  code. You can finish manually or try a       │
│  simpler approach.                            │
│                                               │
│  ┌──────────────┐  ┌──────────────────┐      │
│  │ Open Branch  │  │ Try Simpler Way  │      │
│  └──────────────┘  └──────────────────┘      │
│                                               │
└───────────────────────────────────────────────┘
```

Red left border. Shows exact errors + two constructive options.

**Analysis failure:**

```
┌──────────────────────────────────────────┐
│                                          │
│  ⚠ Couldn't analyze project              │
│                                          │
│  No Swift files found in the selected    │
│  folder. Make sure you opened a folder   │
│  containing .swift files, an .xcodeproj, │
│  or an .xcworkspace.                     │
│                                          │
│       [Try Again]  [Browse...]           │
│                                          │
└──────────────────────────────────────────┘
```

**API key invalid:**

```
┌──────────────────────────────────────────┐
│                                          │
│  ✕ API key validation failed             │
│                                          │
│  The key you entered couldn't be         │
│  verified. Check that it's correct and   │
│  has the required permissions.            │
│                                          │
│  [Edit Key]  [Get a new key →]           │
│                                          │
└──────────────────────────────────────────┘
```

Red left border. Every error has a constructive next step.

---
