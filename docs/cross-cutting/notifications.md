# Notification System

> **CodeLens UI/UX Design Specification — Cross-Cutting**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

### 27.1 In-App Toasts

Non-blocking notifications that appear at the top-right of the content area:

```
                              ┌──────────────────────────┐
                              │ ✓ Build complete         │
                              │   Offline search — 8m    │
                              │                  [View →]│
                              └──────────────────────────┘
```

- Slides in from right, auto-dismisses after 5s
- Click → navigates to relevant page
- `#2C2C2E` background, 12pt radius, subtle shadow
- Stacks if multiple (max 3 visible, then "+ N more")

### 27.2 macOS System Notifications

For events when CodeLens is in the background:

| Event | Notification Text |
|---|---|
| Build complete | "Build complete: Offline search — ready for review" |
| Build failed | "Build failed: Push notifications — needs attention" |
| Coverage dropped | "Coverage dropped 5% in NetworkModule" |
| Review needed | "Review needed: Architect plan for offline search" |

### 27.3 Sidebar Badges

Sidebar icons show subtle badges for pending items:

```
│  🔨 Tasks   ② │   2 builds need review
│  ✅ Tests   ① │   1 test failure
```

- Small red circle with count, positioned top-right of icon
- Uses `SF Pro Bold 9pt`, white text on `#FF453A` red
- Disappears when addressed

---
