# Context

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Create · **Phase 1 — Shipped**  
> **Accent Color:** `#30D158` (green) · **SF Symbol:** `doc.text.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#30D158` (green)  
**Purpose:** Generate AI context files (CLAUDE.md, .cursor/rules, Copilot) from your codebase, so external AI tools understand your project.

### 6.1 Layout — Form + Preview

This page is unique — it's a form in the middle column and a file preview in the right column.

```
╔══════════════════════╤════════════════════════╤══════════════════════════════╗
║                      │                        │                              ║
║  🏠 Home             │  Output Format         │   CLAUDE.md Preview          ║
║  ──────────────────  │                        │                              ║
║   Explore           ▾│                        │                              ║
║  📁 Projects         │                        │ CLAUDE.md│ │.cursor/  │ │C│  ║
║  🏛 Architecture     │                        │    ✓     │ │ rules    │ │o│  ║
║  📦 Dependencies     │                        │                              ║
║  🔍 Search           │                        │   ## Architecture            ║
║  ──────────────────  │  ────────────────────  │                              ║
║   Create            ▾│                        │   This project follows       ║
║  📄 Context         ●│  Token Budget          │   MVVM with Coordinators.    ║
║  🔨 Tasks            │  ━━━━━━━━━━━━●━━━━━  8,│   12 modules, primary        ║
║  🧩 Blueprints       │                        │   language Swift 5.9.        ║
║  ──────────────────  │  ────────────────────  │                              ║
║   Quality           ▾│                        │   ## Modules                 ║
║  ✅ Tests            │  Options               │                              ║
║  🔒 Security         │                        │   ### NetworkModule          ║
║  ⚡ Performance      │  ✅ Include architecture│   Handles all HTTP...        ║
║  ──────────────────  │     overview           │                              ║
║   Knowledge         ▾│  ✅ Include key patterns│   ### DataLayer              ║
║  📖 Wiki             │  ✅ Include module      │   CoreData persistence...    ║
║  📜 Conventions      │     descriptions       │                              ║
║  📰 Changelog        │  ☐  Include file tree  │   ## Key Patterns            ║
║  ──────────────────  │                        │                              ║
║   Insights          ▾│  ────────────────────  │   - Repository Pattern       ║
║  ♡ Health            │                        │   - Coordinator Pattern      ║
║  △ Improve           │  [✦ Generate]          │   - DI via Container         ║
║  📊 Timeline         │                        │                              ║
║  ──────────────────  │                        │   ────────────────────       ║
║   AI                ▾│                        │                              ║
║  🧠 Intelligence     │                        │   6,847 / 8,000 tokens       ║
║  💬 Ask CodeLens     │                        │                              ║
║  🐛 Debug            │                        │   [Copy to Clipboard]        ║
║  ──────────────────  │                        │   [Save to Project Root]     ║
║  ⚙ Settings          │                        │                              ║
║                      │                        │                              ║
╠══════════════════════╧════════════════════════╧══════════════════════════════╣
║  Trident Companion                                                           ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 6.2 Output Format Selector

Three cards in a horizontal row, card-style radio buttons:

```
┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│     📄       │  │     ✦        │  │     ➡        │
│  CLAUDE.md   │  │ .cursor/rules│  │   Copilot    │
└──────────────┘  └──────────────┘  └──────────────┘
     selected         default           default
  (green border)   (no border)       (no border)
```

Selected card: green border (2pt), icon has subtle glow.  
Unselected: `#2C2C2E` background, no border.

### 6.3 Token Budget Slider

```
Token Budget                                    8,000 tokens
━━━━━━━━━━━━━━━━━━━━●━━━━━━━━━━━━━━━━━━━━━━━━━
```

- Range: 2,000 – 32,000 tokens
- Green filled track to the left of thumb
- Dotted track to the right
- Value label right-aligned
- Moving the slider updates the preview in real-time

### 6.4 Options Checkboxes

Standard macOS checkboxes with green fill when checked:

| Option | Default | Effect |
|---|---|---|
| Include architecture overview | ✅ On | Adds system architecture section |
| Include key patterns | ✅ On | Adds design pattern descriptions |
| Include module descriptions | ✅ On | Adds per-module documentation |
| Include file tree | ☐ Off | Adds full directory tree listing |

### 6.5 Right Column — Live Preview

Shows a real-time rendered preview of the context file that will be generated:
- Rendered Markdown (not raw text)
- Token count at bottom: "6,847 / 8,000 tokens" with progress bar
- **Actions:** "Copy to Clipboard" (copies raw markdown), "Save to Project Root" (writes .claude.md / .cursor/rules to project directory)
- Preview updates live as options/budget change

---
