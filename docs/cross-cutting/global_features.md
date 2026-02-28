# Global Features

> **CodeLens UI/UX Design Specification — Cross-Cutting**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

### 28.1 Project Switcher (Title Bar Dropdown)

Clicking "📁 No Project ▾" in the title bar opens:

```
┌──────────────────────────────────┐
│  Recent Projects                 │
│                                  │
│  📱 Trident Companion       ✓   │  ← checkmark = current
│  🖥 Dashboard Pro                │
│  ⌚ WatchKit Extension           │
│                                  │
│  ──────────────────              │
│  Browse for project...           │
│  ──────────────────              │
│  Clear Recent Projects           │
└──────────────────────────────────┘
```

### 28.2 Keyboard Shortcuts (Complete Map)

| Shortcut | Action |
|---|---|
| ⌘1 – ⌘9, ⌘0 | Switch sidebar section (numbered top-to-bottom) |
| ⌘, | Open Settings window |
| ⌘K | Spotlight search overlay |
| ⌘F | In-page search/filter |
| ⌘O | Browse for project |
| ⌘N | New task / conversation / blueprint (context-dependent) |
| ⌘R | Refresh / re-analyze |
| ⌘⇧I | Toggle inspector (right column) |
| ⌘⇧S | Toggle sidebar |
| ⌘⏎ | Send message / Start build / Generate (context-dependent) |
| ⌘W | Close current project |
| ⌘⇧C | Copy context to clipboard (Context page) |
| ⌘⇧X | Run security scan |
| ⌘⇧B | New blueprint |
| ⌘⇧D | Open Debug Assistant |
| ⌘⇧L | Generate changelog |
| ⌘⇧T | Run tests |

### 28.3 Drag & Drop

| Target | Accepts | Action |
|---|---|---|
| Welcome screen | .xcodeproj, .xcworkspace, folders | Opens project |
| Projects list | Same as above | Adds project |
| Ask CodeLens input | .swift files, code snippets | Attaches as context |
| Tasks input | Text, file references | Pre-fills build request |

---
