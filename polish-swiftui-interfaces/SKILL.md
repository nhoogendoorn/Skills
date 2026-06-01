---
name: polish-swiftui-interfaces
description: Design engineering principles for making SwiftUI interfaces feel polished on Apple platforms. Use when building or reviewing SwiftUI views, implementing animations, transitions, springs, micro-interactions, haptics, SF Symbol effects, press states, enter/exit animations, or any visual detail work in Swift. Triggers on UI polish, "make it feel better", "feels off", "make this view nicer", stagger/spring animations, corner radius, optical alignment, monospaced/numeric text, Dynamic Type, Reduce Motion, scale on press, sensoryFeedback, separators, shadows, materials, and iOS 26 Liquid Glass. SwiftUI only (iOS/iPadOS-focused).
---

# Details that make SwiftUI interfaces feel better

Great interfaces rarely come from a single thing. They're a collection of small details that compound into a polished experience. Apply these principles when building or reviewing SwiftUI code. Every example here is native SwiftUI — for web/CSS work, use the sibling skill `make-interfaces-feel-better` instead.

## Quick Reference

| Category | When to Use |
| --- | --- |
| [Typography](references/typography.md) | Dynamic Type, text styles, monospaced/numeric text, line limits & wrapping |
| [Surfaces](references/surfaces.md) | Corner radius (concentric/continuous), optical alignment, shadows, materials, separators, hit areas |
| [Animations](references/animations.md) | Interruptible animations, springs, enter/exit transitions, SF Symbol effects, scale on press |
| [Feedback & Accessibility](references/feedback-and-accessibility.md) | Haptics (`sensoryFeedback`), Reduce Motion, Reduce Transparency, Dynamic Type behavior |
| [Performance](references/performance.md) | Scoping animations to values, `drawingGroup`/`compositingGroup`/`geometryGroup` |
| [Liquid Glass](references/liquid-glass.md) | iOS 26 `glassEffect`, `GlassEffectContainer`, `.buttonStyle(.glass)` |

## Core Principles

### 1. Concentric & Continuous Corner Radius

Outer radius = inner radius + padding, and always use `style: .continuous`. `RoundedRectangle(cornerRadius:style:.continuous)` matches Apple's rounded-corner "squircle"; the default `.circular` style looks subtly wrong next to system chrome. The bare `.cornerRadius(_:)` modifier is deprecated and circular — avoid it. On iOS 26, the `.concentric` corner style (`.clipShape(.rect(cornerRadius:style:.concentric))`) derives a child's radius from its container automatically.

### 2. Optical Over Geometric Alignment

When geometric centering looks off, align optically. Buttons with icons, play triangles, and asymmetric SF Symbols need manual padding adjustment. Prefer `Label` and `.imageScale` so the symbol sits on the text baseline.

### 3. Depth via Shadows & Materials, Not Hard Borders

Use a soft, low-opacity `.shadow` or a system material (`.ultraThinMaterial`, `.regularMaterial`) for elevation. Materials adapt to light/dark and the content behind them; hard 1pt strokes don't. Reserve thin strokes for layout separators, not depth.

### 4. Interruptible Animations

`.animation(_, value:)` and `withAnimation` retarget mid-flight — they're interruptible by default. Springs (`.spring`, `.smooth`, `.snappy`, `.bouncy`) handle interruption gracefully. Reserve `PhaseAnimator`/`KeyframeAnimator` for one-shot staged sequences.

### 5. Split and Stagger Enter Animations

Don't animate one big container. Break content into semantic chunks and stagger each with a per-index `.delay` (~0.05–0.1s), combining `opacity` + `offset` + `blur`. `PhaseAnimator` or indexed transitions work well.

### 6. Subtle Exit Animations

Use `.transition(.asymmetric(insertion:removal:))` with a small `offset` (e.g. `y: -8`) on removal, not a full slide-off. Exits should be softer and quicker than enters.

### 7. Contextual Icon Animations

Animate SF Symbols with `.symbolEffect(.bounce)`, `.symbolEffect(.pulse)`, variable color, or `.contentTransition(.symbolEffect(.replace))` when swapping symbols — never toggle visibility abruptly.

### 8. System Fonts & Text Styles

Use semantic text styles (`.font(.headline)`, `.body`, `.caption`) over hardcoded point sizes. They scale with Dynamic Type and stay consistent with platform conventions. (Font smoothing is a web concern — the system handles rendering on Apple platforms.)

### 9. Numeric Text

Use `.monospacedDigit()` for any dynamically updating numbers (counters, timers, prices) to prevent width jitter, and `.contentTransition(.numericText())` inside `withAnimation` for rolling digit transitions.

### 10. Text Wrapping & Truncation

Set explicit `.lineLimit(_:)` (or `.lineLimit(_, reservesSpace:)` to avoid layout jumps), `.multilineTextAlignment`, and `.truncationMode`. Avoid letting labels reflow unpredictably as content changes.

### 11. Hairline Separators & Image Outlines

Use `Color(.separator)` for hairlines and a thin `.overlay(RoundedRectangle(...).strokeBorder(Color(.separator), lineWidth: 1))` on images/thumbnails for a crisp edge — never a tinted near-black/near-white that reads as dirt.

### 12. Scale on Press

Give buttons tactile feedback with a custom `ButtonStyle` that scales to `0.96` while `configuration.isPressed`, animated with a quick spring. Never go below `0.95` — it feels exaggerated. Honor Reduce Motion.

### 13. Skip Animation on Appear

`.animation(_, value:)` does not fire on first render, which is usually what you want. When using `withAnimation` in `.onAppear` or `.task`, gate it behind a state flag so default-state elements don't animate in unintentionally.

### 14. Animate Specific Values, Not Everything

Scope animations to the value that changed: `.animation(.snappy, value: isExpanded)`. Avoid the deprecated value-less `.animation(_)` modifier — it implicitly animates every change to the view, the SwiftUI equivalent of `transition: all`.

### 15. Use Rasterization Hints Sparingly

`.drawingGroup()`, `.compositingGroup()`, and `.geometryGroup()` can fix real stutter or compositing glitches, but each adds cost and can break blending/accessibility. Add only when you observe a problem — never preemptively.

### 16. Minimum Hit Area

Interactive elements need at least 44×44pt (Apple HIG). Expand small controls with `.frame(minWidth: 44, minHeight: 44)` and `.contentShape(Rectangle())` so the whole frame is tappable. Never let two hit areas overlap.

### 17. Haptics via `sensoryFeedback`

Pair meaningful state changes with `.sensoryFeedback(_, trigger:)` (iOS 17+) — `.impact` for presses, `.success`/`.warning`/`.error` for outcomes, `.selection` for pickers. Don't over-fire; haptics lose meaning when constant.

### 18. Honor Reduce Motion

Read `@Environment(\.accessibilityReduceMotion)` and provide a cross-fade or instant change instead of large movement/scale when it's on. Polish must degrade gracefully.

### 19. Support Dynamic Type

Drive spacing from `@ScaledMetric` and avoid fixed-height containers around text. Verify layouts at the largest accessibility sizes.

### 20. Liquid Glass on Floating Controls Only (iOS 26)

Apply `.glassEffect()` to floating/overlay controls (toolbars, action buttons), not to large content backgrounds. Group adjacent glass elements in a `GlassEffectContainer`, and respect Reduce Transparency. Gate with `if #available(iOS 26, *)`.

## Common Mistakes

| Mistake | Fix |
| --- | --- |
| Same corner radius on parent and child | `outerRadius = innerRadius + padding`, both `.continuous` |
| `.cornerRadius(12)` (deprecated, circular) | `.clipShape(.rect(cornerRadius: 12, style: .continuous))` |
| Icons look off-center in a button | Optical padding, `Label`, or fix `imageScale`/baseline |
| Hard 1pt stroke used for elevation | Soft `.shadow` or a system material |
| Numbers cause width jitter | `.monospacedDigit()` (+ `.contentTransition(.numericText())`) |
| Value-less `.animation(_)` on a view | Scope it: `.animation(.snappy, value: state)` |
| Animation plays on first appear | `.animation(value:)`, or gate `withAnimation` behind a flag |
| Tiny tap targets on small controls | `.frame(minWidth: 44, minHeight: 44)` + `.contentShape` |
| Hardcoded font sizes | Semantic text styles (`.headline`, `.body`) |
| Animations ignore Reduce Motion | Branch on `accessibilityReduceMotion` |
| `.glassEffect()` on large backgrounds | Reserve glass for floating controls |

## Review Output Format

Always present changes as a markdown table with **Before** and **After** columns. Include every change you made — not just a subset. Never list findings as separate "Before:" / "After:" lines outside of a table. Group changes by principle with a heading above each table, and keep each row focused on a single diff so the reader can scan quickly. If a principle was reviewed but nothing changed, omit that table entirely.

### Example

#### Concentric & continuous corner radius
| Before | After |
| --- | --- |
| `.cornerRadius(16)` on card + `.cornerRadius(16)` on inner button (`.padding(8)`) | Card `RoundedRectangle(cornerRadius: 24, style: .continuous)`, inner `16` |
| `RoundedRectangle(cornerRadius: 12)` (circular) | `RoundedRectangle(cornerRadius: 12, style: .continuous)` |

#### Numeric text
| Before | After |
| --- | --- |
| `Text(count, format: .number)` on live counter | Added `.monospacedDigit()` + `.contentTransition(.numericText())` |

#### Scale on press
| Before | After |
| --- | --- |
| Plain `Button { } label: { }` | Applied `.buttonStyle(PressableButtonStyle())` (scales to `0.96`) |
| `scaleEffect(0.9)` on press | Raised to `0.96` — below `0.95` feels exaggerated |

Cite the specific file and modifier that changed when it isn't obvious from the snippet.

## Review Checklist

- [ ] Nested rounded shapes use concentric radii and `.continuous` style
- [ ] No deprecated `.cornerRadius(_:)`
- [ ] Icons are optically centered, not just geometrically
- [ ] Elevation uses shadows/materials, not hard strokes
- [ ] Enter animations are split and staggered
- [ ] Exit animations are subtle (asymmetric, small offset)
- [ ] SF Symbol changes use `symbolEffect` / `contentTransition`
- [ ] Dynamic numbers use `.monospacedDigit()`
- [ ] Text uses semantic styles and explicit line limits
- [ ] Animations are scoped to a value (no value-less `.animation`)
- [ ] Animations don't fire unintentionally on appear
- [ ] Buttons use scale-on-press where appropriate
- [ ] Meaningful actions have `sensoryFeedback`
- [ ] Animations honor Reduce Motion
- [ ] Layout supports Dynamic Type (`@ScaledMetric`, no fixed text heights)
- [ ] Interactive elements have at least 44×44pt hit area
- [ ] Liquid Glass (iOS 26) used only on floating controls, gated with `#available`

## Reference Files

- [typography.md](references/typography.md) — Dynamic Type, text styles, monospaced/numeric text, line limits & wrapping
- [surfaces.md](references/surfaces.md) — Corner radius, optical alignment, shadows & materials, separators, hit areas
- [animations.md](references/animations.md) — Interruptible animations, springs, enter/exit transitions, SF Symbol effects, scale on press
- [feedback-and-accessibility.md](references/feedback-and-accessibility.md) — Haptics, Reduce Motion, Reduce Transparency, Dynamic Type
- [performance.md](references/performance.md) — Scoping animations, rasterization hints
- [liquid-glass.md](references/liquid-glass.md) — iOS 26 Liquid Glass effects
