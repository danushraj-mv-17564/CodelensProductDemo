# Settings

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Settings · **Phase 1 — Shipped**  
> **Accent Color:** `#8E8E93` (gray) · **SF Symbol:** `gearshape.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#8E8E93` (gray)  
**Purpose:** App-wide preferences. Opens in a separate window (standard macOS pattern via ⌘,).

### 10.1 Sidebar Placeholder

The Settings page in the main window is minimal — it directs you to open the preferences window:

```
╔═══════════════╤══════════════════════════════════════════════════════════════╗
║               │                                                              ║
║  📁 Projects  │                                                              ║
║  📖 Wiki      │                                                              ║
║  🏛 Architectu│                                                              ║
║  📄 Context   │                   ⚙                                          ║
║  🔍 Search    │                                                              ║
║               │                Settings                                      ║
║  🧠 Intellige│                                                              ║
║  💬 Ask CodeL │        Open the Settings window with                         ║
║               │        Cmd+, for full configuration                          ║
║  ⚙ Settings ● │        options.                                              ║
║               │                                                              ║
║               │                                                              ║
╠═══════════════╧══════════════════════════════════════════════════════════════╣
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 10.2 Settings Window (⌘,)

Standard macOS Preferences window with toolbar tabs:

```
╔══════════════════════════════════════════════════════════════════╗
║  ● ● ●      CodeLens Settings                                   ║
║                                                                  ║
║  [ General ]  [  AI  ]  [ Analysis ]  [ Privacy ]  [ Updates ]  ║
║                                                                  ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  GENERAL                                                         ║
║                                                                  ║
║  Appearance        [System ▼] / Light / Dark                    ║
║  Accent Color      [Purple ▼]   (matches CTA)                  ║
║  Sidebar Labels    [Icon + Text ▼] / Icon Only                  ║
║                                                                  ║
║  ────────────────────────────────────────                        ║
║                                                                  ║
║  On Launch         [Open Last Project ▼]                        ║
║                    / Show Projects / Do Nothing                  ║
║                                                                  ║
║  Graph Layout      [Tree ▼] / Layered / Force / Radial         ║
║  Code Font Size    [12pt ▼]                                     ║
║                                                                  ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  AI                                                              ║
║                                                                  ║
║  Default Provider  [Anthropic ▼]                                ║
║  Monthly Limit     [$500      ]                                  ║
║  Per-query Limit   [$10       ]                                  ║
║                                                                  ║
║  Extended Thinking [Default Off ▼] / Default On                 ║
║                                                                  ║
║  ────────────────────────────────────────                        ║
║                                                                  ║
║  ANALYSIS                                                        ║
║                                                                  ║
║  Auto-analyze on project open    [●  On]                        ║
║  Watch for file changes          [●  On]                        ║
║  Coverage target                 [70%    ]                      ║
║                                                                  ║
║  ────────────────────────────────────────                        ║
║                                                                  ║
║  PRIVACY                                                         ║
║                                                                  ║
║  What's sent to cloud:                                           ║
║  · Code snippets for analysis (anonymized)                      ║
║  · Architecture summaries                                        ║
║  · Chat messages                                                 ║
║                                                                  ║
║  What never leaves your Mac:                                     ║
║  · Full source code                                              ║
║  · Git history                                                   ║
║  · API keys                                                      ║
║  · PKG database                                                  ║
║                                                                  ║
║  [View API Call Log]                                             ║
║  [Clear All Project Data]                                        ║
║                                                                  ║
║  ────────────────────────────────────────                        ║
║                                                                  ║
║  UPDATES                                                         ║
║                                                                  ║
║  Auto-check for updates         [●  On]                         ║
║  Current version                1.0.0 (Build 42)                ║
║  [Check Now]                                                     ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

---
