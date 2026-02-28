# Security Scanner

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Quality · **Phase 2**  
> **Accent Color:** `#FF453A` (red) · **SF Symbol:** `lock.shield.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#FF453A` (red)  
**SF Symbol:** `lock.shield.fill`  
**Purpose:** Find secrets in code, scan dependencies for CVEs, check App Transport Security, audit keychain usage. The page that makes project leads trust CodeLens.

> **Sidebar group:** Quality

### 17.1 Empty State

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │         ┌──────────┐          │     ┌──────────┐       ║
║  ──────────────────  │                               │    🔒    │              ║
║   Explore           ▾│                               │  (circle)│             ║
║  📁 Projects         │         └──────────┘          │     └──────────┘       ║
║  🏛 Architecture     │                               │                        ║
║  📦 Dependencies     │    Security Scanner           │   No Issue Selected    ║
║  🔍 Search           │                               │                        ║
║  ──────────────────  │  Scan your project to find    │   Select an issue to   ║
║   Create            ▾│  vulnerabilities, hardcoded se│   see details and      ║
║  📄 Context          │  and security misconfiguration│   remediation steps.   ║
║  🔨 Tasks            │                               │                        ║
║  🧩 Blueprints       │      [🔒 Run Security Scan]    │                        ║
║  ──────────────────  │                               │                        ║
║   Quality           ▾│                               │                        ║
║  ✅ Tests            │                               │                        ║
║  🔒 Security        ●│                               │                        ║
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

### 17.2 Populated State — Scan Results

```
╔══════════════════════╤═══════════════════════════════╤════════════════════════╗
║                      │                               │                        ║
║  🏠 Home             │  Last scan: 2 minutes ago  [⟳ │   ISSUE DETAIL         ║
║  ──────────────────  │                               │                        ║
║   Explore           ▾│  SECURITY SCORE               │   🔴 Hardcoded API Key  ║
║  📁 Projects         │                               │                        ║
║  🏛 Architecture     │  ┌────────────────────────────│   Config.swift:42      ║
║  📦 Dependencies     │                               │                        ║
║  🔍 Search           │                               │    72 / 100  ● Fair    ║
║  ──────────────────  │                               │    ████████████████░░░░║
║   Create            ▾│                               │                        ║
║  📄 Context          │                               │    🔴 2 Critical        ║
║  🔨 Tasks            │                               │    🟠 3 Warning         ║
║  🧩 Blueprints       │                               │    🟢 18 Passed         ║
║  ──────────────────  │                               │                        ║
║   Quality           ▾│  └────────────────────────────│   API keys in source   ║
║  ✅ Tests            │                               │   code can be          ║
║  🔒 Security        ●│  ────────────────────         │   extracted from the   ║
║  ⚡ Performance      │                               │   compiled binary or   ║
║  ──────────────────  │  🔴 CRITICAL (2)               │   git history.         ║
║   Knowledge         ▾│                               │                        ║
║  📖 Wiki             │  ┌────────────────────────────│   RECOMMENDED FIX      ║
║  📜 Conventions      │                               │ 🔴 Hardcoded API Key    ║
║  📰 Changelog        │                               │    Config.swift:42     ║
║  ──────────────────  │                               │    "sk-proj-a8f..." exp║
║   Insights          ▾│  └────────────────────────────│   variable. CodeLens   ║
║  ♡ Health            │  ┌────────────────────────────│   can generate the     ║
║  △ Improve           │                               │ 🔴 HTTP Allowed (No TLS)║
║  📊 Timeline         │                               │    Info.plist:ATS      ║
║  ──────────────────  │                               │    NSAllowsArbitraryLoa║
║   AI                ▾│  └────────────────────────────│   [🔧 Auto-Fix]         ║
║  🧠 Intelligence     │                               │   [Open File →]        ║
║  💬 Ask CodeLens     │  🟠 WARNING (3)                │   [Create Task →]      ║
║  🐛 Debug            │                               │                        ║
║  ──────────────────  │  ┌────────────────────────────│                        ║
║  ⚙ Settings          │                               │ 🟠 Alamofire CVE-2024-31║
║                      │                               │    HTTP header injectio║
║                      │  └────────────────────────────│                        ║
║                      │  ┌────────────────────────────│                        ║
║                      │                               │ 🟠 Weak password validat║
║                      │                               │    AuthService.swift:89║
║                      │  └────────────────────────────│                        ║
║                      │  ┌────────────────────────────│                        ║
║                      │                               │ 🟠 No cert pinning detec║
║                      │                               │    NetworkModule       ║
║                      │  └────────────────────────────│                        ║
║                      │                               │                        ║
║                      │  🟢 PASSED (18)               [│                        ║
║                      │                               │                        ║
╠══════════════════════╧═══════════════════════════════╧════════════════════════╣
║  Trident Companion                                     2 critical · 3 warning ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 17.3 Security Score Card

Ring chart + score number at the top:

- **0-40:** Red. "Critical — immediate action needed"
- **41-70:** Orange. "Fair — some issues to address"
- **71-90:** Yellow-green. "Good — minor improvements possible"
- **91-100:** Green. "Excellent — no known vulnerabilities"

### 17.4 Scan Categories

| Category | What It Checks |
|---|---|
| **Secrets** | API keys, tokens, passwords, private keys in source |
| **Dependencies** | CVEs from NVD/GitHub Advisory Database |
| **Transport** | ATS configuration, certificate pinning, HTTP usage |
| **Authentication** | Weak validation, insecure storage, missing biometrics |
| **Data** | Unencrypted CoreData, plaintext UserDefaults for sensitive data |
| **Permissions** | Unused entitlements, over-broad Info.plist permissions |

### 17.5 Issue Actions

| Button | What It Does |
|---|---|
| **Auto-Fix** | Generates code fix (e.g., moves API key to Keychain) via Developer Agent |
| **Open File →** | Opens in Xcode at the exact line |
| **Create Task →** | Creates a Build Pipeline task for the fix |
| **Suppress** | Mark as false positive (with reason) — won't appear again |

---
