# Scene 1: The Evolution

> **Duration:** ~3 minutes  
> **Emotional Arc:** Recognition → Frustration → Progress → Anticipation  
> **Presenter:** Danush  
> **Display:** macOS laptop (full screen, Safari/Chrome)

---

## Overview

This scene sets the stage by showing the audience where we started and how far we've come — from manual "vibe coding" with LLMs to structured agentic workflows. It ends with a bridge question that leads into the CodeLens reveal.

---

## ACT 1 — The Vibe Coding Era (~90 seconds)

### Slide 1.1 — The Year
**Visual:** Dark screen. Single word fades in: **"2024"**

**Script:**
> "Let's go back to where this started."

---

### Slide 1.2 — The Mess
**Visual:** Animated VS Code + Copilot Chat mockup — a long conversation thread, 40+ messages deep, scrolling slowly

**Script:**
> "This was us. Vibe coding."
>
> *(pause)*
>
> "You open Copilot. You say — *'Write unit tests for this file.'* It asks *'which file?'* You paste the file. It writes something. It's wrong. You correct it. It fixes one thing, breaks another."
>
> *(pause)*
>
> "By message twenty... the LLM has forgotten what you said in message three."

---

### Slide 1.3 — The Repetition
**Visual:** Chat messages scrolling with highlighted repeated instructions — pulsing red highlights on:
- "Remember, use Swift Testing framework"
- "I said no XCTest"  
- "Follow the guidelines I gave you earlier"

**Script:**
> "So you start repeating yourself. *'Use Swift Testing, not XCTest.'* *'Follow the AAA pattern.'* *'Don't force unwrap.'*"
>
> "Over and over. Every session. Every file."
>
> *(pause)*
>
> "By the end of the day, you're not coding anymore. You're **spoon-feeding** the AI. One instruction at a time."

---

### Slide 1.4 — The Leaking Bucket
**Visual:** Clean animated graphic — a developer icon pushing instructions one-by-one into a box labeled "LLM". Below the box, a bucket with context visibly dripping out the bottom. Counter shows "Context retained: 34%... 21%... 12%..."

**Script:**
> "The context was leaking. And every time it leaked, we paid for it — in time, in frustration, in quality."
>
> "That was the Vibe Coding era."

---

## ACT 2 — The Agentic Era (~90 seconds)

### Slide 2.1 — The Shift
**Visual:** Fade transition. **"2025–2026"** appears. Screen shows a clean project structure with organized files: instruction templates, rules files, context documents displayed in a macOS Finder-style or VS Code explorer.

**Script:**
> "Then something changed."
>
> "We stopped talking to the AI message by message. We started giving it **structure**."

---

### Slide 2.2 — The Rules
**Visual:** Show the actual instruction file — `copilot_unit_test_generation_instructions.md` — scrolling through rules with key lines highlighted in purple:
- "Always use Swift Testing framework"
- "AAA pattern with comment headers"
- "Every #expect must have a descriptive failure message"
- "No force unwraps"

**Script:**
> "We wrote rules. Proper rules. *'Always use Swift Testing framework.'* *'AAA pattern with comment headers.'* *'Every assertion needs a failure message.'* *'No force unwraps. Ever.'*"
>
> "We didn't ask the AI to remember. We made it **impossible to forget**."

---

### Slide 2.3 — The Workflow
**Visual:** Show the prompt template — 6 mode cards appearing one by one with icons: Write → Review → Verify Tags → Build & Run → Coverage → Fix

**Script:**
> "Then we built templates. Not just for tests — for the entire workflow. Write. Review. Build. Run. Fix. All structured. All repeatable."
>
> *(pause)*
>
> "And it worked."

---

### Slide 2.4 — The Proof
**Visual:** Show the Resource Booking Backend — a macOS window with terminal output: green checkmarks, passing tests, "Build Succeeded", test coverage numbers

**Script:**
> "You saw the demo. The Resource Booking Backend. The agent gathers context on its own. It reads the codebase structure. It follows the rules. It writes tests, builds them, runs them — and if something fails, it fixes it automatically. Up to five iterations. No hand-holding."
>
> *(pause)*
>
> "We went from spoon-feeding... to **delegation**."

---

### Slide 2.5 — Current Progress
**Visual:** Progress tracker showing three items:
- ✅ Unit Tests (Resource Booking Backend) — Complete
- 🔨 UI Tests — In Progress  
- ○ Backend Logic — Next
- ○ Wiring — Planned

**Script:**
> "And right now, today, we're using this same approach to build outward. UI. Backend. Wiring. Each piece follows the same pattern — structured context, intelligent agents, automated validation."

---

## THE BRIDGE (~15 seconds)

### Slide 3.1 — The Question
**Visual:** Everything fades to dark. Long pause (2 seconds). Then a single line fades in, centered:

***"But what if we could take this further?"***

**Script:**
> *(Let the slide speak for 2 beats)*
>
> "What if the platform itself... understood your code?"

---

### Slide 3.2 — The Tease
**Visual:** Fade to black. The CodeLens logo begins to glow softly — purple (#BF5AF2) ambient light.

**Script:**
> "That's what we built."

**[→ Transition to Scene 2]**

---

## PRESENTER NOTES

| Moment | Tip |
|--------|-----|
| Act 1 opening | Make eye contact. Everyone has felt this pain — they'll nod. |
| Chat scrolling | Let the visual do the work. Don't rush the silence. |
| "Spoon-feeding" | This is the punch word. Deliver it with slight frustration. |
| Act 2 pivot | Tone shifts from frustration to pride. Stand taller. |
| Resource Booking reference | This is your proof — the team saw the demo video. Call back to it directly. |
| Bridge question | This is your micro "one more thing." Pause before AND after. |
| "That's what we built" | Say it quietly. Confidence, not volume. |

---

## VISUAL ASSETS NEEDED

1. Animated VS Code chat mockup (scrolling conversation)
2. Highlighted instruction messages (with red pulse)
3. Leaking bucket animation (context dripping out)
4. Instruction file viewer (styled like VS Code)
5. 6-mode workflow cards (Write → Fix)
6. Terminal output mockup (passing tests)
7. Progress tracker (4 milestones)
8. CodeLens logo with glow animation

---

## INTERACTION MODEL

- **Navigation:** Arrow keys (→ next slide, ← previous)
- **Auto-advance:** None — presenter controls pace
- **Animations:** Trigger on slide enter, CSS-only
- **Escape:** Shows slide overview/progress

