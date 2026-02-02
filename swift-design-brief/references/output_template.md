# Design Brief Output Template — Apple Platforms

Generate the brief using this exact structure. Every section is required. Fill all fields — do not leave placeholders.

```markdown
# Design Brief

## 1. Product Context
- Product type:
- Target platform(s): [iOS / iPadOS / macOS / watchOS / visionOS]
- Primary user:
- Core problem being solved:
- Usage context (environment, frequency, constraints):

## 2. Design Goals
- Primary goal:
- Secondary goals:
- Explicit non-goals:

## 3. Design Principles (Ordered by Priority)
1. [Principle] — [Operational definition]
2. [Principle] — [Operational definition]
3. [Principle] — [Operational definition]

## 4. User Experience Stance
- Target emotional tone:
- Complexity tolerance:
- Guidance vs. discoverability:
- Information density:

## 5. Visual & Interaction Direction
- Overall aesthetic:
- Navigation pattern: [Tab bar / Sidebar / NavigationStack / other]
- Layout philosophy:
- Motion & feedback:
- Accessibility baseline:

## 6. Apple Platform Specifics
- Typography: [System default / custom font with Dynamic Type]
- Color strategy: [Semantic only / semantic + accent / custom palette with dark mode]
- Iconography: [SF Symbols only / SF Symbols + custom]
- Spacing system: [Standard 8pt grid / custom]
- Multi-platform adaptations: [if targeting more than one platform]

## 7. Constraints & Trade-offs
- Technical constraints:
- Platform constraints:
- Explicit trade-offs we accept:

## 8. Decision Heuristics
When making design decisions, prefer:
- [A] over [B] when [condition]
- [A] over [B] when [condition]
- [A] over [B] when [condition]

## 9. Red Flags (What to Avoid)
- [Specific anti-pattern with why]
- [Specific anti-pattern with why]

## 10. Assumptions
- [Stated assumption]
- [Stated assumption]
```

## Section Guidance

**Product Context** — Ground the brief. Be specific about who uses this, on which Apple device(s), where, and how often. Platform choice shapes everything downstream — an iPhone app has different navigation, density, and interaction patterns than a macOS app.

**Design Goals** — Non-goals are as important as goals. They prevent scope creep in future LLM sessions.

**Design Principles** — Order matters. When two principles conflict, the higher-ranked one wins. Each principle must have an operational definition (what it means in practice, not an abstract value). Consider how Apple's Clarity/Deference/Depth principles apply to this specific product — you don't need to repeat them, but your principles should not contradict them.

**User Experience Stance** — "Complexity tolerance" means: does the user expect a power tool or a simple utility? "Guidance vs. discoverability" means: do we hold their hand or let them explore? "Information density" is especially relevant: iPhone apps should be low-density with progressive disclosure; iPad/macOS apps can surface more information simultaneously via sidebars and split views.

**Visual & Interaction Direction** — Ground this in Apple platform conventions. Instead of "minimal sidebar", say "NavigationSplitView with two-column layout on iPad, collapsing to NavigationStack on iPhone." Specify the navigation pattern — this is the single most impactful design choice on Apple platforms. Reference system components (List with `.insetGrouped`, sheet with `.presentationDetents`, etc.) rather than abstract descriptions.

**Apple Platform Specifics** — Only deviate from system defaults with justification. System defaults: San Francisco font, semantic colors, SF Symbols, 8pt grid, standard navigation patterns. If the brief says "system default" for everything, that's a valid and strong choice — it means the product leans fully into native feel. Deviations should be specific: "Custom font: Inter, using `.custom(relativeTo: .body)` for Dynamic Type" not just "custom font."

**Constraints & Trade-offs** — "Explicit trade-offs we accept" is the most important sub-field. Apple-specific examples: "We accept less brand differentiation to stay fully native", "We accept the learning curve of a sidebar-based iPad layout for long-term efficiency", "We trade visual density for one-thumb reachability on iPhone."

**Decision Heuristics** — These are the tiebreakers. When a future LLM faces an ambiguous choice, these rules resolve it. Write 3-5 concrete heuristics. At least one should address platform convention vs. custom design. Examples:
- "Platform convention over custom design when the interaction pattern exists in iOS SDK"
- "Progressive disclosure over visible complexity when the feature is used less than once per session"
- "System components over custom implementations unless the custom version measurably improves task completion"

**Red Flags** — Specific patterns to reject. Apple-platform examples:
- "Don't build custom tab bars — use the system TabView"
- "Don't disable large titles on top-level navigation views"
- "Don't use fixed font sizes — all text must scale with Dynamic Type"
- "Don't use color as the sole indicator of state (VoiceOver and color blindness)"
- "Don't hide navigation with hamburger menus on iOS"

**Assumptions** — Anything inferred rather than stated by the user. Makes it easy to challenge and update the brief later.
