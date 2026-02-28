# Dependencies

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Explore · **Phase 2**  
> **Accent Color:** `#5E5CE6` (indigo) · **SF Symbol:** `shippingbox.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#5E5CE6` (indigo)  
**SF Symbol:** `shippingbox.fill`  
**Purpose:** Visualize every SPM/CocoaPods/Carthage dependency as a beautiful tree. Surface CVEs, license conflicts, and outdated versions instantly. Viewers will gasp when they see red vulnerability badges.

> **Sidebar group:** Explore  
> **Available from:** Phase 2

### 13.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │                               │     ┌──────────┐       ║
║  ──────────────────  │                               │     │    📦    │        ║
║   Explore           ▾│         ┌──────────┐          │     │  (circle)│       ║
║  📁 Projects         │                               │    📦    │              ║
║  🏛 Architecture     │                               │  (circle)│             ║
║  📦 Dependencies    ●│         └──────────┘          │   No Package Selected  ║
║  🔍 Search           │                               │                        ║
║  ──────────────────  │    No Dependencies Found      │   Select a package     ║
║   Create            ▾│                               │   to see its version,  ║
║  📄 Context          │  Open a project with a Package│   license, and CVE     ║
║  🔨 Tasks            │  Podfile, or Cartfile to see y│   status.              ║
║  🧩 Blueprints       │  dependency tree.             │                        ║
║  ──────────────────  │                               │                        ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests            │                               │                        ║
║  🔒 Security         │                               │                        ║
║  ⚡ Performance      │                               │                        ║
║  ──────────────────  │                               │                        ║
║   Knowledge         ▾│                               │                        ║
║  📖 Wiki             │                               │                        ║
║  📜 Conventions      │                               │                        ║
║  📰 Changelog        │                               │                        ║
║  ──────────────────  │                               │                        ║
║   Insights          ▾│                               │                        ║
║  ♡ Health            │                               │                        ║
║  △ Improve           │                               │                        ║
║  📊 Timeline         │                               │                        ║
║  ──────────────────  │                               │                        ║
║   AI                ▾│                               │                        ║
║  🧠 Intelligence     │                               │                        ║
║  💬 Ask CodeLens     │                               │                        ║
║  🐛 Debug            │                               │                        ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │                               │                        ║
║                      │                               │                        ║
╚══════════════════════╧═══════════════════════════════╧════════════════════════╝
```

### 13.2 Populated State — Dependency Tree + Detail Panel

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  🔍 Filter packages...         │   Alamofire            ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│  32 packages · 3 warnings     │   5.9.1 → 5.10.0 ⬆     ║
║  📁 Projects         │                               │   MIT License  ✓       ║
║  🏛 Architecture     │  ▼ Direct Dependencies (8)    │                        ║
║  📦 Dependencies    ●│                               │   ────────────────     ║
║  🔍 Search           │   ● Alamofire        5.9.1   ⚠│                        ║
║  ──────────────────  │     Moya             15.0.3   │   VULNERABILITIES      ║
║   Create            ▾│     Kingfisher       7.12.0   │                        ║
║  📄 Context          │     SwiftyJSON       5.0.2    │   🔴 CVE-2024-3197      ║
║  🔨 Tasks            │     KeychainAccess   4.2.2    │   HTTP header          ║
║  🧩 Blueprints       │     Lottie           4.4.3    │   injection in         ║
║  ──────────────────  │     SnapKit          5.7.1    │   redirect handling    ║
║   Quality           ▾│     Sentry           8.36.0   │   Severity: High       ║
║  ✅ Tests            │                               │   Fixed in: 5.10.0     ║
║  🔒 Security         │  ▶ Transitive (24)            │                        ║
║  ⚡ Performance      │                               │   [Update to 5.10.0]   ║
║  ──────────────────  │  ────────────────────         │                        ║
║   Knowledge         ▾│                               │   ────────────────     ║
║  📖 Wiki             │  HEALTH OVERVIEW              │                        ║
║  📜 Conventions      │                               │   DEPENDENCY GRAPH     ║
║  📰 Changelog        │  Up to date    ████████████░░ │                        ║
║  ──────────────────  │  Outdated      ██░░░░░░░░░░░░ │   ┌─────────────────┐  ║
║   Insights          ▾│  Vulnerable    █░░░░░░░░░░░░░ │   │  Alamofire      │  ║
║  ♡ Health            │                               │   │   ↓    ↓       │   ║
║  △ Improve           │  LICENSE COMPATIBILITY        │   │  Moya  Sentry  │   ║
║  📊 Timeline         │                               │   │   ↓             │  ║
║  ──────────────────  │  ✓ All MIT/Apache 2.0 — compat│   │  Kingfisher    │   ║
║   AI                ▾│                               │   └─────────────────┘  ║
║  🧠 Intelligence     │                               │                        ║
║  💬 Ask CodeLens     │                               │   [Open in             ║
║  🐛 Debug            │                               │    Architecture →]     ║
║  ──────────────────  │                               │                        ║
║  ⚙ Settings          │                               │                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                          32 packages       ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 13.3 Middle Column — Package List

**Direct dependencies** shown first (disclosure triangle), then **transitive** (collapsed by default):

```
● Alamofire        5.9.1    ⚠ ⬆
```

| Element | Meaning |
|---|---|
| Package name | `Body`, SF Pro |
| Version | `Caption`, 50% opacity |
| ✓ | Green — up to date, no issues |
| ⬆ | Blue — newer version available |
| ⚠ | Orange — has a known CVE |
| 🔴 | Red — critical vulnerability |

**Health Overview** below the list — three horizontal progress bars.

**License Compatibility** — automated check. ✓ = all compatible. ⚠ = GPL in a non-GPL project, etc.

### 13.4 Right Column — Package Detail

When a package is selected:

- **Version badge**: current vs latest, with blue "Update" capsule
- **License**: detected license name + compatibility status
- **Vulnerabilities**: CVE ID, description, severity badge (Low/Medium/High/Critical), fixed version
- **Mini dependency subgraph**: shows what THIS package pulls in (not the full tree)
- **"Update to X.Y.Z"** — purple CTA, triggers a Task that updates the package
- **"Open in Architecture →"** — navigates to Architecture page filtered to this package's types

### 13.5 Bulk Actions

Bottom bar shows contextual actions when issues exist:

```
╠══════════════════════════════════════════════════════════════════════════════╣
║  Trident Companion    [⬆ Update All 5]  [🔒 Fix 2 CVEs]     32 packages   ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

- **"Update All 5"** — creates a Task to update all outdated packages
- **"Fix 2 CVEs"** — creates a Task to update only vulnerable packages to safe versions

---
