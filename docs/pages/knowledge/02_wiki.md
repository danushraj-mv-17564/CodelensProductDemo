# Wiki

> **CodeLens UI/UX Design Specification**  
> **Sidebar Group:** Knowledge · **Phase 1 — Shipped**  
> **Accent Color:** `#BF5AF2` (purple) · **SF Symbol:** `building.columns.fill`  
> **Navigation:** [← Back to Overview](../../00_MAIN_OVERVIEW.md)

---

**Accent color:** `#BF5AF2` (purple)  
**Purpose:** Auto-generated documentation from the codebase. Read, search, browse your project's knowledge.

### 4.1 Empty State

```
╔══════════════════════╤════════════════════════╤══════════════════════════════╗
║                      │  🔍 Search docs...      │                              ║
║  🏠 Home             │                        │         ┌──────────┐         ║
║  ──────────────────  │                        │         │    📖    │          ║
║   Explore           ▾│        ┌──────────┐    │         │  (circle)│         ║
║  📁 Projects         │                        │    📖    │           │        ║
║  🏛 Architecture     │                        │  (circle)│           │       ║
║  📦 Dependencies     │        └──────────┘    │       No Page Selected       ║
║  🔍 Search           │                        │                              ║
║  ──────────────────  │    No Documentation    │    Select a documentation    ║
║   Create            ▾│                        │       page to read.          ║
║  📄 Context          │  Scan a project and gen│                              ║
║  🔨 Tasks            │  docs to see them here.│                              ║
║  🧩 Blueprints       │                        │                              ║
║  ──────────────────  │    [⊕ Generate Docs]   │                              ║
║   Quality           ▾│                        │                              ║
║  ✅ Tests            │                        │                              ║
║  🔒 Security         │                        │                              ║
║  ⚡ Performance      │                        │                              ║
║  ──────────────────  │                        │                              ║
║   Knowledge         ▾│                        │                              ║
║  📖 Wiki            ●│                        │                              ║
║  📜 Conventions      │                        │                              ║
║  📰 Changelog        │                        │                              ║
║  ──────────────────  │                        │                              ║
║   Insights          ▾│                        │                              ║
║  ♡ Health            │                        │                              ║
║  △ Improve           │                        │                              ║
║  📊 Timeline         │                        │                              ║
║  ──────────────────  │                        │                              ║
║   AI                ▾│                        │                              ║
║  🧠 Intelligence     │                        │                              ║
║  💬 Ask CodeLens     │                        │                              ║
║  🐛 Debug            │                        │                              ║
║  ──────────────────  │                        │                              ║
║  ⚙ Settings          │                        │                              ║
║                      │                        │                              ║
╠══════════════════════╧════════════════════════╧══════════════════════════════╣
║  No project selected                                              0 docs     ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 4.2 Populated State

```
╔══════════════════════╤════════════════════════╤══════════════════════════════╗
║                      │  🔍 Search docs...      │                              ║
║  🏠 Home             │                        │   NetworkModule              ║
║  ──────────────────  │  ▼ Architecture Overvie│                              ║
║   Explore           ▾│    System Architecture │   ────────────────────       ║
║  📁 Projects         │    Module Dependency Ma│                              ║
║  🏛 Architecture     │    Design Patterns Used│   ## Overview                ║
║  📦 Dependencies     │                        │                              ║
║  🔍 Search           │  ▼ Modules             │   `NetworkModule` handles    ║
║  ──────────────────  │    NetworkModule       │←  all HTTP communication     ║
║   Create            ▾│    DataLayer           │   in the application. It     ║
║  📄 Context          │    AuthService         │   wraps URLSession and       ║
║  🔨 Tasks            │    UIComponents        │   provides a typed API       ║
║  🧩 Blueprints       │    MainApp             │   layer for all endpoints.   ║
║  ──────────────────  │                        │                              ║
║   Quality           ▾│  ▼ Key Patterns        │   ### Key Types              ║
║  ✅ Tests            │    Repository Pattern  │                              ║
║  🔒 Security         │    Coordinator Pattern │   - `APIClient` — Main       ║
║  ⚡ Performance      │    DI Container        │     entry point              ║
║  ──────────────────  │                        │   - `APIRouter` — Defines    ║
║   Knowledge         ▾│  ▼ API Reference       │     endpoints                ║
║  📖 Wiki            ●│    APIClient           │   - `NetworkError` — Typed   ║
║  📜 Conventions      │    APIRouter           │     error handling           ║
║  📰 Changelog        │    NetworkError        │                              ║
║  ──────────────────  │    RequestBuilder      │   ### Dependencies           ║
║   Insights          ▾│                        │                              ║
║  ♡ Health            │                        │   Depended on by:            ║
║  △ Improve           │                        │   `DataLayer`, `AuthService` ║
║  📊 Timeline         │                        │                              ║
║  ──────────────────  │                        │   Depends on:                ║
║   AI                ▾│                        │   `Foundation`               ║
║  🧠 Intelligence     │                        │                              ║
║  💬 Ask CodeLens     │                        │   ### Coverage: 45%          ║
║  🐛 Debug            │                        │                              ║
║  ──────────────────  │                        │   ⚠ Below target (70%).      ║
║  ⚙ Settings          │                        │   28 untested functions.     ║
║                      │                        │                              ║
║                      │                        │   ────────────────────       ║
║                      │                        │                              ║
║                      │                        │   Last updated: 2h ago       ║
║                      │                        │   [🔄 Regenerate]  [Copy]     ║
║                      │                        │                              ║
╠══════════════════════╧════════════════════════╧══════════════════════════════╣
║  Trident Companion               🔄 Regenerate All                  24 docs   ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 4.3 Middle Column — Documentation Tree

An outline view with disclosure triangles, organized by category:

```
▼ Architecture Overview        ← Group (bold, no icon)
   System Architecture         ← Doc page
   Module Dependency Map
   Design Patterns Used

▼ Modules
   NetworkModule             ● ← Dot = has warnings
   DataLayer
   AuthService
   UIComponents
   MainApp

▼ Key Patterns
   Repository Pattern
   Coordinator Pattern
   DI Container

▼ API Reference
   APIClient
   APIRouter
   NetworkError
   RequestBuilder
```

| Element | Details |
|---|---|
| Groups | Disclosure triangle, bold label, collapsible |
| Doc pages | Regular weight, click to load in right panel |
| Warning dot (●) | Orange dot on modules with coverage < target |
| Search | Filters the tree in real-time |

### 4.4 Right Column — Documentation Viewer

Renders Markdown with:
- Proper heading hierarchy (##, ###)
- Inline code blocks with SF Mono
- Syntax-highlighted code fences
- Warning callouts (⚠) with orange left border
- Dependency lists with bullet points
- **Footer:** "Last updated" timestamp + "Regenerate" (re-runs AI doc gen for this page) + "Copy" (copies markdown to clipboard)

---
