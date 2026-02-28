# Animations & Transitions

> **CodeLens UI/UX Design Specification — Cross-Cutting**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

### 30.1 Page Transitions

- **Sidebar navigation:** Crossfade (0.2s, `easeInOut`). Content fades out, new content fades in. No sliding.
- **Three-column selection:** Middle → right column content crossfades (0.15s).
- **Drill-down (Architecture module → types):** Push from right (0.3s, `spring(response: 0.3, dampingFraction: 0.85)`).
- **Modal/sheet:** Slide up + fade in (0.3s).
- **Inspector show/hide:** Width expansion with `spring` (0.35s).

### 30.2 Graph Animations

- **Node appear (during ingestion):** Scale 0 → 1 with overshoot spring (response: 0.4, damping: 0.7).
- **Edge draw:** Path stroke from source to target (0.3s, `easeOut`).
- **Layout change (Tree → Layered):** All nodes spring-interpolate to new positions (0.5s).
- **Node selection:** Scale 1.05×, border brightens, connected edges highlight.
- **Drill-down (module → types):** Zoom + crossfade (0.4s).
- **Filter dim:** Non-matching nodes fade to 15% opacity (0.2s).
- **Zoom:** Smooth scale with momentum (respects trackpad velocity).

### 30.3 Build Pipeline Animations

- **Step completion:** Card collapses from full → summary with spring.
- **New step activation:** Card expands from single line → full size.
- **Progress bar:** Smooth width animation; indeterminate shimmer when % unknown.
- **Checkmark (✓):** Draw-in animation (like iOS Reminders check-off).
- **Failure cross (✕):** Shake animation (0.3s, horizontal oscillation).

### 30.4 Data Updates

- **Stat card number change:** Count-up/down animation (slot machine style).
- **Chart data update:** Line morphs smoothly to new values.
- **Activity feed new item:** Slides in from top, pushes others down.

### 30.5 Micro-Interactions

- **Button hover:** Brightness +8%.
- **Button press:** Scale 0.97 (0.1s) then back to 1.0 on release.
- **Sidebar hover:** Row background brightens (#2A2A2C).
- **List selection:** Purple pill background, 0.15s animation.
- **Toggle switch:** Standard macOS spring.
- **Progress bars:** Smooth width transition (0.3s `easeInOut`).
- **Refresh icon (⟳):** Rotates 360° continuously while processing.
- **Chat message appear:** Fade in + slide up 8pt (0.2s).
- **Toast notification:** Slide in from top-right (0.3s spring).
- **Badge count change:** Brief scale pulse (1.0 → 1.2 → 1.0, 0.3s).

### 30.6 First-Launch Analysis Progress

```
Understanding Trident Companion...

✓  Found 247 Swift files
✓  Identified MVVM architecture
●  Mapping 1,247 entities...
○  Analyzing coverage
○  Learning conventions

━━━━━━━━━━━━━━━━━━━━░░░░░░░  74%
About 20 seconds remaining
```

- Checkmark (✓) draws in with path animation
- Active step (●) pulses
- Graph nodes appear behind/beside the progress as they're discovered
- On completion: progress bar turns green, celebratory pulse, crossfade to Projects (0.5s)

---
