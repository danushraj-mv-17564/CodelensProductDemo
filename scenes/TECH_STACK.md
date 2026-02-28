# CodeLens Demo — Technical Architecture

> Apple-grade presentation system. One file. Zero risk. Full presenter control.

---

## Architecture Decision: Single File

**All scenes live in ONE `presentation.html` file.**

Why:
- No page loads between scenes — seamless transitions
- No broken links or file-not-found during demo
- Open one file in Chrome/Safari → press F11 (full screen) → present
- All fonts, styles, animations, assets baked in
- Works offline — no internet required during presentation

```
scenes/
├── TECH_STACK.md              ← This file
├── 01_the_evolution/
│   └── script.md              ← Presenter script (reference only)
├── 02_[next_scene]/
│   └── script.md
└── presentation.html          ← THE SINGLE DELIVERABLE
```

---

## Presenter Controls

| Action | Control | Visual Feedback |
|--------|---------|-----------------|
| **Next slide** | `→` Arrow key / Click right side / Space bar / Presenter clicker "next" | Smooth transition |
| **Previous slide** | `←` Arrow key / Click left side / Presenter clicker "back" | Reverse transition |
| **First slide** | `Home` key | Jump to start |
| **Last slide** | `End` key | Jump to end |
| **Slide overview** | `Escape` or `O` key | Grid view of all slides (like Keynote light table) |
| **Go to slide #** | Type number + `Enter` | Direct jump |
| **Blackout screen** | `B` key | Fade to black (for Q&A moments) |
| **Presenter notes** | `N` key | Toggle notes overlay (only you see this on your screen) |
| **Progress** | Always visible | Thin progress bar at very bottom (2px, fades after 3s) |

### Clicker Support
Standard Bluetooth/USB presentation clickers send:
- Next = `→` or `PageDown`
- Back = `←` or `PageUp`

All are mapped. **Plug in any clicker and it works.**

---

## Visual Design System

### Window Frame
Every scene is wrapped in a **macOS Sequoia window** — rendered in CSS:

```
┌─────────────────────────────────────────────────────┐
│ 🔴 🟡 🟢       Scene Title                          │  ← 52px title bar
├─────────────────────────────────────────────────────┤
│                                                     │
│                  Scene Content                      │  ← Full content area
│                                                     │
└─────────────────────────────────────────────────────┘
```

- **Corner radius:** 12px
- **Shadow:** `0 25px 80px rgba(0,0,0,0.6)` + `0 0 0 1px rgba(255,255,255,0.06)`
- **Title bar:** #2C2C2E, 52px height
- **Traffic lights:** Pixel-perfect 12px circles with correct colors
- **Background (desk):** #0D0D0F (dark) — makes the window pop

### Typography

| Use | Font | Weight | Size |
|-----|------|--------|------|
| Headlines | Inter | 700 | 48px / 36px / 28px |
| Body text | Inter | 400/500 | 18px / 16px |
| Code | JetBrains Mono | 400/500 | 14px / 13px |
| Labels | Inter | 600 | 11px uppercase |
| Slide numbers | JetBrains Mono | 400 | 11px |

**Font loading strategy:**
- Embed Inter (400, 500, 600, 700) and JetBrains Mono (400, 500) as base64 `@font-face` blocks directly in the HTML
- **Zero external requests** — works offline, loads instantly, no FOUT (Flash of Unstyled Text)
- Fallback stack: `-apple-system, BlinkMacSystemFont, 'SF Pro', 'Segoe UI', sans-serif`

### Color Palette (Dark Theme — primary)

```css
/* Surfaces */
--bg-desk:      #0D0D0F;     /* Behind the window */
--bg-window:    #1A1A1C;     /* Window background */
--bg-elevated:  #2C2C2E;     /* Cards, title bar */
--bg-hover:     #3A3A3C;     /* Hover states */

/* Text */
--text-primary:    #FFFFFF;
--text-secondary:  rgba(235, 235, 245, 0.6);
--text-tertiary:   rgba(235, 235, 245, 0.4);
--text-quaternary: rgba(235, 235, 245, 0.18);

/* Accents */
--purple:  #BF5AF2;
--blue:    #0A84FF;
--green:   #30D158;
--orange:  #FF9F0A;
--red:     #FF453A;
--teal:    #64D2FF;
--yellow:  #FFD60A;
--pink:    #FF375F;
--gold:    #AC8E68;
--indigo:  #5E5CE6;
```

---

## Animation Engine

### Philosophy
Apple's motion design rules:
1. **Everything has purpose** — no animation for decoration
2. **Fast in, slow out** — elements arrive quickly, settle gently
3. **Stagger, don't blast** — sequential reveals, not all at once
4. **Spatial consistency** — things come from logical directions
5. **Subtle > dramatic** — the best animation is almost invisible

### Easing Curves

```css
/* Apple-style easing — custom cubic beziers */
--ease-out:     cubic-bezier(0.25, 1, 0.5, 1);       /* Primary: decelerate */
--ease-in-out:  cubic-bezier(0.65, 0, 0.35, 1);       /* Symmetrical */
--ease-spring:  cubic-bezier(0.34, 1.56, 0.64, 1);    /* Slight overshoot */
--ease-smooth:  cubic-bezier(0.4, 0, 0, 1);           /* Ultra-smooth settle */
```

### Default Transitions

| Element Type | Animation | Duration | Easing |
|-------------|-----------|----------|--------|
| Slide enter | Fade + translate Y (20px → 0) | 600ms | ease-out |
| Slide exit | Fade out | 300ms | ease-in |
| Text lines | Staggered fade-up (each +80ms) | 500ms | ease-out |
| Code blocks | Slide-in from bottom + fade | 400ms | ease-out |
| Mockup windows | Scale (0.95 → 1) + fade | 500ms | ease-spring |
| Chart bars | Height grow from 0 | 800ms staggered | ease-out |
| SVG paths | stroke-dashoffset draw | 1200ms | ease-in-out |
| Number counters | Count up from 0 | 1500ms | linear (ease on display) |
| Highlights | Background pulse (2 cycles) | 600ms each | ease-in-out |

### Implementation: CSS-first, JS-assist

```
CSS handles:           JS handles:
├── @keyframes         ├── Slide navigation
├── transitions        ├── Staggered delays (computed)
├── transform          ├── Typewriter text effects
├── opacity            ├── Scroll-triggered animations
├── clip-path          ├── Counter animations
└── filter             └── Conditional reveals
```

**No animation libraries.** All CSS transforms use `will-change` and `transform: translateZ(0)` for GPU acceleration.

---

## Slide System Architecture

### HTML Structure

```html
<body>
  <!-- Progress bar -->
  <div class="progress-bar"><div class="progress-fill"></div></div>

  <!-- Slide container -->
  <div class="slides-container">

    <!-- Each slide -->
    <section class="slide" data-scene="1" data-slide="1" data-title="The Year">
      <div class="mac-window">
        <div class="window-titlebar">
          <div class="traffic-lights">...</div>
          <span class="window-title">The Evolution</span>
        </div>
        <div class="window-content">
          <!-- Slide content here -->
        </div>
      </div>
    </section>

    <section class="slide" data-scene="1" data-slide="2" data-title="The Mess">
      ...
    </section>

  </div>

  <!-- Presenter notes (hidden by default) -->
  <div class="presenter-notes" id="presenterNotes"></div>

  <!-- Slide overview modal -->
  <div class="slide-overview" id="slideOverview"></div>
</body>
```

### Slide Lifecycle

```
[Hidden]  →  [Enter Animation]  →  [Active / Interactive]  →  [Exit Animation]  →  [Hidden]
             ↑                                                                      │
             └──────────────────── (user presses ←) ────────────────────────────────┘
```

Each slide has:
- `data-enter`: animation to play on enter (default: "fadeUp")
- `data-exit`: animation to play on exit (default: "fadeOut")
- `data-auto`: auto-advance timer in ms (optional, for timed reveals within a slide)
- `data-notes`: presenter notes text

### Sub-steps Within a Slide

Some slides have multiple reveals (text appears line by line). These use **fragments**:

```html
<div class="fragment" data-order="1">First this appears...</div>
<div class="fragment" data-order="2">Then this...</div>
<div class="fragment" data-order="3">Then this.</div>
```

Pressing → advances fragments first, then moves to next slide when all fragments are revealed.

---

## Mockup Components Library

Pre-built CSS components we'll reuse across scenes:

### 1. VS Code Mockup
```
┌─ VS Code ──────────────────────────────────────┐
│ 📁 Explorer │  editor.swift          │ Copilot │
│ ├── src/    │  1 │ func test() {     │ Chat    │
│ │   ├── ..  │  2 │   // code here    │ > msg1  │
│ └── tests/  │  3 │ }                 │ > msg2  │
└─────────────────────────────────────────────────┘
```

### 2. Terminal Mockup
```
┌─ Terminal ─────────────────────────────┐
│ $ swift test                           │
│ ✓ testAuthenticate passed (0.02s)      │
│ ✓ testRefreshToken passed (0.01s)      │
│ All tests passed.                      │
└────────────────────────────────────────┘
```

### 3. Chat Conversation Mockup
- User messages (right-aligned, dark bg)
- AI messages (left-aligned, card bg)
- Typing indicator (3 dots animation)
- Highlighted/pulsing messages for emphasis

### 4. File Explorer Mockup
- macOS Finder-style sidebar
- File icons with correct colors
- Selected file highlight

### 5. Animated Diagram Components
- Flowcharts (SVG with animated connections)
- Leaking bucket (SVG + CSS animation)
- Progress trackers (step indicators)
- Counter animations (numbers counting up)

---

## Performance Guarantees

| Metric | Target | How |
|--------|--------|-----|
| First paint | < 100ms | No external resources, inline everything |
| Animation FPS | 60fps constant | CSS transforms only, GPU layers |
| Slide transition | < 16ms JS | `requestAnimationFrame`, minimal DOM changes |
| Total file size | < 500KB | Inline fonts + SVG, no images |
| Memory | < 50MB | No video, no canvas (unless needed), DOM recycling |
| Input latency | < 50ms | Direct event listeners, no framework overhead |

### Offline Resilience
- ✅ No CDN fonts (embedded as base64)
- ✅ No external images (all SVG inline)
- ✅ No API calls
- ✅ No build step
- ✅ Works in airplane mode

---

## Browser Target

**Primary:** Safari on macOS (your MacBook for presenting)
**Secondary:** Chrome on macOS (backup)

Both support:
- CSS `backdrop-filter` (for blur effects)
- `cubic-bezier` custom easing
- CSS `@property` for animated custom properties
- `IntersectionObserver`
- `navigator.clipboard`
- Fullscreen API

### Fullscreen Presentation Mode
```
Open file → Press F11 (or ⌘⇧F in Safari) → Present
```
The page is designed for **1440×900** or **1920×1080** viewport (standard MacBook Pro / external display). Responsive to both.

---

## Development Workflow

1. **Write script** → `scenes/XX_name/script.md`
2. **Build scene** → Add slides to `scenes/presentation.html`
3. **Test scene** → Open in browser, arrow-key through
4. **Iterate** → Refine timing, animations, content
5. **Next scene** → Repeat
6. **Final assembly** → All scenes are already in one file — just verify flow

### Scene Independence During Development
While building, each scene's slides are tagged with `data-scene="N"`. During development, you can:
- Jump to any scene: press scene number
- Test one scene in isolation: URL param `?scene=1`
- See scene boundaries in slide overview

---

## Risk Mitigation

| Risk | Mitigation |
|------|-----------|
| Font doesn't load | Base64 embedded + system font fallback |
| Animation jank | CSS-only transforms, `will-change` hints, tested on target hardware |
| Wrong slide during demo | Escape → overview grid → click correct slide |
| Clicker doesn't work | Keyboard arrows always work as backup |
| Screen resolution mismatch | Viewport-relative sizing (`vh`, `vw`), tested at 1440×900 and 1920×1080 |
| Browser crash | File is static HTML — refresh and jump back to slide (`localStorage` remembers position) |
| Projector color shift | High-contrast design, no subtle color distinctions for meaning |

---

## Summary

```
ONE FILE. ZERO DEPENDENCIES. FULL CONTROL.

Open → Fullscreen → Present → Arrow keys to advance.

That's it.
```
