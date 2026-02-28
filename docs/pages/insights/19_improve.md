# Improve / AI Insights

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Insights · **Phase 3**  
> **Accent Color:** `#BF5AF2` (purple) · **SF Symbol:** `chart.line.uptrend.xyaxis`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#BF5AF2` (purple)  
**SF Symbol:** `chart.line.uptrend.xyaxis`  
**Purpose:** AI-powered recommendations. What to fix, what to improve, what's exemplary. Actionable coaching, not a data dump.

> **Sidebar group:** Insights

### 22.1 Layout — Middle Column Recommendations + Right Column Visualizations

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  TOP RECOMMENDATION           │   MODULE RISK MAP      ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│  ┌────────────────────────────│   ┌─────────────────┐  ║
║  📁 Projects         │                               │                        ║
║  🏛 Architecture     │                               │  ⚠ NetworkModule is    ║
║  📦 Dependencies     │                               │    becoming fragile    ║
║  🔍 Search           │                               │                        ║
║  ──────────────────  │                               │  Coverage dropped 7% th║
║   Create            ▾│                               │  month (now 45%). 3 of ║
║  📄 Context          │                               │  last 5 bug fixes were ║
║  🔨 Tasks            │                               │  28 tests would bring i║
║  🧩 Blueprints       │                               │  your 70% target.      ║
║  ──────────────────  │                               │                        ║
║   Quality           ▾│                               │  [Generate 28 Tests ▶] ║
║  ✅ Tests            │                               │  [Show me the problems ║
║  🔒 Security         │                               │                        ║
║  ⚡ Performance      │  └────────────────────────────│                        ║
║  ──────────────────  │                               │   ────────────────     ║
║   Knowledge         ▾│  ────────────────────         │                        ║
║  📖 Wiki             │                               │   TRENDS               ║
║  📜 Conventions      │  TRENDS (Quick Glance)        │                        ║
║  📰 Changelog        │                               │   Build Success        ║
║  ──────────────────  │  Build Success    ████████████│   ████████████ 94%     ║
║   Insights          ▾│  Agent Efficiency ████████░░ $│   ↗ improving          ║
║  ♡ Health            │  Conventions      █████████░░░│                        ║
║  △ Improve          ●│  Self-Correction  ██░░░░░░░░ 1│   Agent Efficiency     ║
║  📊 Timeline         │  (lower = better)             │   $2.10 / feature      ║
║  ──────────────────  │                               │   ↘ getting cheaper    ║
║   AI                ▾│  ────────────────────         │                        ║
║  🧠 Intelligence     │                               │   Conventions          ║
║  💬 Ask CodeLens     │  MORE RECOMMENDATIONS         │   █████████░░░ 91%     ║
║  🐛 Debug            │                               │   → stable             ║
║  ──────────────────  │  ● AuthService has 2 functions│                        ║
║  ⚙ Settings          │    >50 LOC (convention: <50)  │   Self-Correction      ║
║                      │    [Auto-refactor →]          │   18% of builds        ║
║                      │                               │   ↘ fewer retries      ║
║                      │  ● 3 views missing accessibili│                        ║
║                      │    identifiers                │                        ║
║                      │    [Add IDs →]                │                        ║
║                      │                               │                        ║
║                      │  ✓ UIComponents is exemplary  │                        ║
║                      │    91% coverage, 0 bugs this m│                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                        3 recommendations   ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 22.2 Top Recommendation — The Hero Card

Always shows the **single most impactful thing** the developer should do:

- Written in plain language, not metrics jargon
- Orange left border strip (warning) or green (all healthy)
- Two action buttons: one automatic fix, one to investigate
- If everything is healthy → green card: "Your project is in great shape. Keep it up."

### 22.3 Module Risk Map — Bubble Chart (Right Column)

A **2D scatter plot** (Swift Charts):

- **X-axis:** Change frequency (how often the module is modified)
- **Y-axis:** Risk level (fragility score)
- **Bubble size:** Lines of code
- **Color:** Health (green/orange/red, matching Architecture node colors)
- **Top-right corner = danger zone** — modules that change often AND have high risk
- Click bubble → shows detail popover for that module
- Hover → tooltip with name + key stats

### 22.4 Trends — 4-Stat Grid

Four compact trend indicators:

| Metric | Good direction | Format |
|---|---|---|
| Build Success | ↗ Higher is better | Percentage + bar |
| Agent Efficiency | ↘ Lower is better | Dollar amount per feature |
| Convention Adherence | ↗ Higher is better | Percentage + bar |
| Self-Correction Rate | ↘ Lower is better | Percentage (fewer retries) |

Each: progress bar + value + trend arrow. Single glance = "are things improving?"

### 22.5 More Recommendations

Actionable items, each with a one-click fix:

- Sorted by impact (highest first)
- ● orange = suggestion with auto-fix button
- ⚠ red = critical issue
- ✓ green = positive affirmation mixed in to balance the tone
- Each recommendation card: `#2C2C2E`, 8pt radius

---
