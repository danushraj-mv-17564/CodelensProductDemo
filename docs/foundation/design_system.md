# Design System

> **CodeLens UI/UX Design Specification — Foundation**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

### 2.1 Color Palette (Dark Theme – Primary)

```
┌─ SURFACES ───────────────────────────────────────────────────┐
│                                                              │
│  Window BG         #1A1A1C                  ████████████     │
│  Sidebar BG        #252527                  ████████████     │
│  Middle column BG  #1E1E20                  ████████████     │
│  Right column BG   #1A1A1C                  ████████████     │
│  Card / Input BG   #2C2C2E                  ████████████     │
│  Hover BG          #3A3A3C                  ████████████     │
│  Divider           #3A3A3C @ 50%            ████████████     │
│                                                              │
├─ SIDEBAR SELECTED ───────────────────────────────────────────┤
│                                                              │
│  Active pill BG    #6B3FA0 @ 60%  (magenta-purple)           │
│  Active text       #FFFFFF                                   │
│                                                              │
├─ SECTION ACCENT COLORS ─────────────────────────────────────┤
│                                                              │
│  Projects          #30D158  (green)         ████████████     │
│  Wiki              #BF5AF2  (purple)        ████████████     │
│  Architecture      #FF9F0A  (orange)        ████████████     │
│  Context           #30D158  (green)         ████████████     │
│  Search            #FF375F  (pink)          ████████████     │
│  Intelligence      #BF5AF2  (purple)        ████████████     │
│  Ask CodeLens      #64D2FF  (teal)          ████████████     │
│  Settings          #8E8E93  (gray)          ████████████     │
│                                                              │
├─ CTA BUTTONS ────────────────────────────────────────────────┤
│                                                              │
│  Primary CTA       #BF5AF2  (purple, capsule)                │
│  CTA text          #FFFFFF                                   │
│  Secondary CTA     #3A3A3C  (outline)                        │
│                                                              │
├─ SEMANTIC ───────────────────────────────────────────────────┤
│                                                              │
│  Success           #30D158  (green)         ████████████     │
│  Warning           #FF9F0A  (orange)        ████████████     │
│  Error             #FF453A  (red)           ████████████     │
│  Info              #64D2FF  (teal)          ████████████     │
│                                                              │
├─ TEXT ───────────────────────────────────────────────────────┤
│                                                              │
│  Primary           #FFFFFF                                   │
│  Secondary         #EBEBF5 @ 60%                             │
│  Tertiary          #EBEBF5 @ 40%                             │
│  Quaternary        #EBEBF5 @ 20%                             │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### 2.2 Typography

```
┌─ TYPOGRAPHY ─────────────────────────────────────────────────┐
│                                                              │
│  Page Title        SF Pro Semibold   17pt    Title bar       │
│  Section Header    SF Pro Semibold   15pt    "Coding Intel…" │
│  Card Title        SF Pro Semibold   15pt    "No Projects"   │
│  Body              SF Pro Regular    13pt    Descriptions     │
│  Subtext           SF Pro Regular    12pt    Hints, meta      │
│  Caption           SF Pro Regular    11pt    Status bar       │
│  Small             SF Pro Regular    10pt    Badges           │
│                                                              │
│  Code              SF Mono Regular   12pt    Code blocks      │
│  Code Small        SF Mono Regular   11pt    Inline refs      │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### 2.3 Empty State Pattern

Every page follows the same empty state formula:

```
           ┌─────────┐
           │         │
           │  (icon  │    ← 64pt, section accent color, 
           │  in a   │       inside a lighter circle (color @ 15%)
           │  circle)│
           │         │
           └─────────┘
          
           Title Text         ← SF Pro Semibold 15pt, white
           
        Description text       ← SF Pro Regular 13pt, 50% opacity
        Second line if needed

        ┌─────────────────┐
        │  ⊕  Action CTA  │   ← Purple capsule button with icon
        └─────────────────┘
```

This pattern is consistent across ALL pages. The icon changes, the color matches the section, the CTA is always purple.

### 2.4 Three-Column Right Panel Empty Pattern

When no item is selected in the middle column, the right panel shows:

```
           ┌─────────┐
           │  (icon  │    ← Same icon as middle panel, but
           │  circle)│       slightly larger circle, dimmer
           └─────────┘
          
           Title Text         ← "No Project Selected"
           
        Descriptive prompt     ← "Select a project to see its details."
```

### 2.5 CTA Button Styles

```
┌─ PRIMARY ────────────────────────────────────────────────────┐
│                                                              │
│  Shape        Capsule (full rounded)                         │
│  Background   #BF5AF2 (purple)                               │
│  Text         White, SF Pro Semibold 13pt                    │
│  Icon         SF Symbol, white, leading                      │
│  Padding      12pt vertical, 20pt horizontal                 │
│  Hover        Brightness +10%                                │
│  Press        Scale 0.97                                     │
│                                                              │
│  Examples:    [⊕ Add Project]  [⊕ Generate Docs]            │
│               [✦ Generate]     [▶ Send]                      │
│                                                              │
├─ SECONDARY ──────────────────────────────────────────────────┤
│                                                              │
│  Shape        Rounded rect (8pt radius)                      │
│  Background   #3A3A3C                                        │
│  Text         White, SF Pro Regular 13pt                     │
│  Hover        Brightness +5%                                 │
│                                                              │
├─ SEGMENTED CONTROL ──────────────────────────────────────────┤
│                                                              │
│  Active       Purple fill capsule                            │
│  Inactive     Transparent, white text                        │
│  Used in:     Architecture (Tree | Layered)                  │
│               Search (All Kinds | Functions | Types | Prop)  │
│               Context (CLAUDE.md | .cursor/rules | Copilot) │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### 2.6 Search Input Pattern

Used across multiple pages — Projects, Wiki, Search, Architecture:

```
┌──────────────────────────────────────────────────────────┐
│  🔍  Search [section]...                                  │
└──────────────────────────────────────────────────────────┘

Background:  #2C2C2E  (card bg)
Border:      none (borderless)
Icon:        SF Symbol magnifyingglass, 40% opacity
Placeholder: 40% opacity text
Focus:       subtle bottom border line in section color
Corner:      8pt radius
```

---
