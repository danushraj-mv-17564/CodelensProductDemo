# Onboarding & First Launch

> **CodeLens UI/UX Design Specification — Foundation**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

The very first thing a new user sees. This must be warm, confident, and fast.

### 11.1 Welcome Screen — First Launch

CodeLens launches to a full-bleed centered welcome experience — no sidebar, no three-column split. Just the brand and a single, clear invitation.

```
╔══════════════════════════════════════════════════════════════════════════╗
║ ● ● ●     CodeLens                                                     ║
╠══════════════════════════════════════════════════════════════════════════╣
║                                                                         ║
║                                                                         ║
║                                                                         ║
║                              ◇                                          ║
║                           CodeLens                                      ║
║                                                                         ║
║                  Understands your code.                                  ║
║                  Builds with you.                                        ║
║                  Gets better over time.                                  ║
║                                                                         ║
║                                                                         ║
║              ┌─────────────────────────────────────┐                    ║
║              │                                     │                    ║
║              │                                     │                    ║
║              │      Open a Swift Project           │                    ║
║              │                                     │                    ║
║              │      Drop an .xcodeproj, workspace, │                    ║
║              │      or folder with Swift files     │                    ║
║              │                                     │                    ║
║              │              📂                      │                    ║
║              │                                     │                    ║
║              │                                     │                    ║
║              └─────────────────────────────────────┘                    ║
║                                                                         ║
║                         — or —                                          ║
║                                                                         ║
║                    [ Browse...  ⌘O ]                                    ║
║                                                                         ║
║                                                                         ║
║                                                                         ║
╚══════════════════════════════════════════════════════════════════════════╝
```

**Design Details:**

- **Logomark** fades in with a gentle 0.6s opacity animation on launch
- **Tagline** uses SF Pro Semibold 17pt, 60% opacity, each line staggered 0.1s
- **Drop zone** — dashed border (1pt, 30% opacity), `#2C2C2E` fill, 12pt corner radius
- Valid hover: border turns solid green (`#30D158`), background gets a subtle green tint, scale to 1.02×
- Invalid drop: border turns red briefly, shake animation (0.3s)
- **Browse button** — secondary style (outline capsule, `#3A3A3C` fill)
- No sidebar visible — the sidebar appears only after a project is loaded

### 11.2 Returning User — Recent Projects on Welcome

After first use, the welcome screen shows recent projects below the drop zone:

```
║              ┌─────────────────────────────────────┐                    ║
║              │      Open a Swift Project            │                    ║
║              │      Drop or browse ...              │                    ║
║              └─────────────────────────────────────┘                    ║
║                                                                         ║
║                        Recent Projects                                  ║
║                                                                         ║
║         ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          ║
║         │ 📱            │  │ 🖥            │  │ ⌚            │          ║
║         │              │  │              │  │              │          ║
║         │ Trident      │  │ Dashboard    │  │ WatchKit     │          ║
║         │ Companion    │  │ Pro          │  │ Extension    │          ║
║         │              │  │              │  │              │          ║
║         │ 247 types    │  │ 89 types     │  │ 34 types     │          ║
║         │ Score: 78    │  │ Score: 91    │  │ Score: 65    │          ║
║         │              │  │              │  │              │          ║
║         │ 2 hours ago  │  │ Yesterday    │  │ 5 days ago   │          ║
║         └──────────────┘  └──────────────┘  └──────────────┘          ║
║                                                                         ║
╚══════════════════════════════════════════════════════════════════════════╝
```

**Recent Project Card:**

- 140 × 170pt, `Card BG` (`#2C2C2E`), 12pt radius, subtle shadow
- Top: Platform icon (📱 iOS, 🖥 macOS, ⌚ watchOS, 📦 SPM) — 28pt, centered
- Middle: Project name (Section Header), type count (Subtext, 50% opacity)
- Bottom: Health score as colored number (green/orange/red), last opened time (Caption, 40% opacity)
- Hover: lift with shadow increase, 1.02× scale
- Click: loads project, transitions to three-column Projects page
- Right-click: "Remove from Recent", "Open in Finder", "Re-analyze"

### 11.3 Analysis Progress — The "Getting to Know You" Experience

When a project is opened for the first time, CodeLens shows a beautiful analysis overlay. This is NOT a loading bar. It's the product demonstrating intelligence.

```
╔══════════════════════════════════════════════════════════════════════════╗
║ ● ● ●     CodeLens — Analyzing Trident Companion                       ║
╠══════════════════════════════════════════════════════════════════════════╣
║                                                                         ║
║                                                                         ║
║                 Understanding Trident Companion                         ║
║                                                                         ║
║                                                                         ║
║     ┌───────────────────────────────────────────────────────────┐       ║
║     │                                                           │       ║
║     │              ◉ ─── ◉ ─── ◉                               │       ║
║     │             ╱│╲         ╱ ╲                               │       ║
║     │            ◉ ◉ ◉     ◉   ◉                               │       ║
║     │              │       │                                    │       ║
║     │              ◉ ─── ◉                                     │       ║
║     │                                                           │       ║
║     │          (Live-building graph animation —                 │       ║
║     │           nodes appear and connect as                     │       ║
║     │           CodeLens discovers the project)                 │       ║
║     │                                                           │       ║
║     └───────────────────────────────────────────────────────────┘       ║
║                                                                         ║
║                                                                         ║
║     Discovering structure...                                            ║
║                                                                         ║
║     ✓  Found 247 Swift files across 12 modules                         ║
║     ✓  Identified MVVM architecture with Combine                       ║
║     ●  Mapping relationships between 1,247 entities...                  ║
║     ○  Analyzing test coverage                                          ║
║     ○  Learning your conventions                                        ║
║                                                                         ║
║                                                                         ║
║     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━░░░░░░░░░░   74%                 ║
║                                                                         ║
║     About 20 seconds remaining                                          ║
║                                                                [Cancel] ║
╚══════════════════════════════════════════════════════════════════════════╝
```

**Design Details:**

- **The graph is alive.** As CodeLens discovers modules and types, nodes appear with a pop animation and edges draw in with a path animation. The user watches their project's structure materialize in real time. This transforms "loading" into "revelation."
- Nodes are color-coded by type (same palette as Architecture page)
- Discovery log uses checkmark animation (✓ draws in like a todo completion)
- Current step has a pulsing dot (●)
- Future steps are dim (○, 30% opacity)
- Progress bar uses purple accent (`#BF5AF2`), smooth spring animation
- "About 20 seconds remaining" updates every 5 seconds, `Subtext` at 50% opacity
- **On completion:** progress bar turns green, brief celebratory pulse on the graph, then smooth crossfade transition to the Projects page with the three-column layout (0.5s)

---
