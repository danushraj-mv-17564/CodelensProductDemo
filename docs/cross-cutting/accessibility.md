# Accessibility

> **CodeLens UI/UX Design Specification — Cross-Cutting**  
> **Navigation:** [← Back to Overview](../00_MAIN_OVERVIEW.md)

---

### 31.1 Requirements

| Requirement | Implementation |
|---|---|
| VoiceOver | Every interactive element has an accessibility label |
| Keyboard nav | Full Tab key navigation through all controls |
| Keyboard shortcuts | ⌘1-7+ for pages, ⌘K for search, ⌘N for new task/build |
| Dynamic Type | All text respects system font size preference |
| Reduce Motion | Crossfades replace all spring/slide/graph animations |
| High Contrast | Borders become more visible, colors increase saturation |
| Color-blind safe | All status uses shape + color (✓ ● ▲ ✕), never color alone |
| Min tap target | All buttons at least 44 × 44pt |
| Focus indicators | Visible focus ring on all interactive elements |

### 31.2 VoiceOver Labels (Examples)

| Element | Label |
|---|---|
| Health score ring | "Project health score: 78 out of 100. Good." |
| Coverage bar | "NetworkModule test coverage: 45 percent. Needs attention." |
| Build pipeline step | "Step 3 of 5: Writing code. 68 percent complete." |
| Graph node | "NetworkModule. 12 types. 2,450 lines. Coverage 45 percent." |
| Task list item | "Dark mode support. Running. Step 3 of 5. 4 minutes elapsed." |
| Sidebar item | "Projects. Tab 1 of 7. Selected." |
| Empty state CTA | "Add Project button. Opens file picker." |
| Search result | "AuthService. Class. AuthModule. 89 percent relevance." |
| Chat message | "CodeLens says: The retry logic in Trident Companion is handled by RetryPolicy." |

---
