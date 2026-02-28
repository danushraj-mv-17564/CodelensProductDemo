# Full User Journey

> **CodeLens UI/UX Design Specification — Cross-Cutting**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

### Day 1 — Getting Started (Explore + AI Groups)

1. **Download** CodeLens from the website. Open.
2. **Welcome screen** appears — centered, no sidebar. The user drags their Xcode project onto the drop zone.
3. **Analysis begins** — the live graph animation shows modules appearing, edges connecting. "Found 247 Swift files. Identified MVVM architecture. Detected 32 dependencies." Takes ~45 seconds.
4. **Projects page** appears with three-column layout. The project is in the list. Right panel shows health score (78/100), coverage (72%), module count (12).
5. **User clicks Architecture** → the dependency graph appears. They click NetworkModule, see 45% coverage in the inspector, discover a fragile module.
6. **User clicks Dependencies** → sees 32 packages. 🔴 **Alamofire has a CVE.** They click "Update to 5.10.0" — fixed in one click. Viewer gasps.
7. **User clicks Search** → types "authentication logic" → finds the exact class, reads the code, sees coverage stats.
8. **User clicks Intelligence** → adds Anthropic API key. Assigns Claude Sonnet to analysis.
9. **User clicks Ask CodeLens** → asks "How does the retry logic work?" → gets a grounded answer with source references.
10. **User drags a crash log onto Debug** → CodeLens traces to `NetworkManager.swift:89`, explains "force-unwrapping a nil value when cache expires", suggests a fix, and finds 3 similar patterns elsewhere. **The demo mic drop.**

### Day 14 — Getting Comfortable (Explore + AI)

- Wiki docs auto-generated and browsable. Context file regenerated for Claude.
- ⌘K Spotlight search replaced most code navigation.
- Ask CodeLens has replaced half their Slack questions to teammates.
- 3 projects loaded. Quick-switch via title bar dropdown.
- Debug Assistant has found and fixed 4 crash-prone patterns.

### Day 30 — Building (Create + Quality Groups)

- **Tasks page** is now in the sidebar. User types "Add offline search for tasks" → hits Start Build.
- The 5-step pipeline runs: Plan (15s) → Design (30s) → Code (2m) → Test (1m) → Ship (30s).
- They review the Design step, approve it. Watch code being written file by file. 5/5 tests pass. They merge.
- **Blueprints** — "I need a caching layer with TTL expiration." CodeLens generates 6 files: CacheService, CacheProtocol, CacheConfig, DI registration, tests, and docs. **All matching their existing MVVM + protocol-based DI style.**
- **Tests page** shows SwiftUI view tree. They select `TaskListView`, generate 5 XCUITests, run them with live simulator preview. All pass. Accessibility ID coverage jumps from 60% to 100%.
- **Security scan** reveals a **hardcoded API key in Config.swift:42** and weak password validation. One-click Auto-Fix moves the key to Keychain. Score: 72 → 89.
- **Performance** shows AppDelegate.swift takes 4.2s to compile (top 5% slowest). CodeLens explains: "12 type-checked generics." Suggests splitting into 2 files. Build time drops from 38s to 26s.

### Day 60 — Knowledge & Insights (Knowledge + Insights Groups)

- **Conventions** page shows CodeLens learned 14 coding conventions: camelCase naming, MVVM architecture, protocol-based DI, <50-line functions. Adherence: 91%. The 7 violations each have one-click fixes.
- **Changelog** — release day. Select Feb 1→Feb 28. CodeLens reads 47 commits, classifies each, generates beautiful release notes in 5 seconds. Export as GitHub Release markdown. Done.
- **Home dashboard** shows: Score 86/100 (up from 78), coverage 81% (up from 72%), 3 modules excellent, 1 needs attention.
- **Health page** shows coverage trending upward over 2 months. NetworkModule was the weak spot — now at 72% after AI-generated tests.
- **Improve page** recommends extracting a helper module and auto-refactoring 2 long functions. They click "Auto-refactor →" and CodeLens creates a Task.
- **Timeline** shows everything CodeLens did today: 3 builds, 2 security scans, 1 convention check, 14 commits analyzed. The project has a heartbeat.

### Day 100 — Mastery

- Build Success: 94%. Agent Efficiency: $2.10/feature (down from $3.80).
- Self-correction rate: 18% (down from 35%).
- Convention adherence: 96% (up from 91%).
- Security score: 94 (up from 72). Zero CVEs. Zero hardcoded secrets.
- Build time: 22s (down from 38s). Binary size: 42MB (down from 48MB).
- 12 blueprints generated. 3 became production modules.
- 47 tasks completed autonomously. 8 needed human review edits.
- Changelog generated for every release. Release notes take 10 seconds.
- Debug Assistant has caught 23 crash-prone patterns before they shipped.

### Day 365 — The Platform

CodeLens now knows:
- Their coding conventions (naming, patterns, DI style, error handling preferences)
- Which modules are fragile, which are rock-solid
- How to write code that matches their project's style
- Which types of features it handles well vs. needs human guidance
- The right model assignments for cost vs. quality tradeoffs
- Their dependency risk profile and update cadence
- Their performance bottlenecks and optimization patterns

The sidebar has 21 items across 6 groups, and they use every single one.

Health score: 78 → 94. Test coverage: 72% → 91%. Security score: 72 → 98. Build time: 38s → 18s. Convention adherence: 91% → 98%.

Cost per feature dropped 55%. The user ships 4× faster.

CodeLens didn't replace them — it made them dangerous.

---

> *This document defines 21 pages across 6 sidebar groups, every component, every state,*  
> *every animation, every interaction in CodeLens. It uses the visual language*  
> *established in the shipped app (dark theme, per-section accent colors, three-column*  
> *NavigationSplitView, purple capsule CTAs) and extends it to the complete product*  
> *vision — from Explore to Create to Quality to Knowledge to Insights to AI.*

---

*CodeLens — The Autonomous Software Development Intelligence Platform*  
*UI/UX Design Specification v3.2 — February 27, 2026*  
*Designed for developers. Built as a Mac app. Inspired by Apple.*
