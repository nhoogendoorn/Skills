# Performance

Scoping animations and using rasterization hints without hurting smoothness.

## Contents

- [Animate Specific Values, Not Everything](#animate-specific-values-not-everything)
- [Avoid Animating Layout-Driving Values](#avoid-animating-layout-driving-values)
- [Rasterization Hints: drawingGroup / compositingGroup / geometryGroup](#rasterization-hints-drawinggroup--compositinggroup--geometrygroup)

## Animate Specific Values, Not Everything

Scope every animation to the value that changed. The value-driven form only animates that property; the deprecated value-less form animates *every* change to the view — the SwiftUI equivalent of CSS `transition: all`.

```swift
// Good — only this value animates, on change
.animation(.snappy, value: isExpanded)

// Bad — value-less modifier animates every state change implicitly (deprecated)
.animation(.snappy)
```

For changes you trigger imperatively, scope with `withAnimation` so unrelated state updates in the same tick don't animate:

```swift
withAnimation(.smooth) { isExpanded.toggle() }   // only this change animates
selection = newValue                              // outside — no animation
```

Use `.transaction { $0.animation = nil }` to explicitly opt a subtree out of an inherited animation.

## Avoid Animating Layout-Driving Values

Animating properties that force SwiftUI to re-run layout every frame (changing `frame`, list insertions, or anything that resizes siblings) is far more expensive than animating `opacity`, `scale`, `offset`, or `rotation`, which can be applied as cheap transforms.

- Prefer `.scaleEffect`, `.offset`, `.opacity`, `.rotationEffect` for continuous/interactive motion.
- Reserve animating actual `frame`/layout for discrete state changes, not per-frame drags.
- `.geometryGroup()` (iOS 17+) isolates a subtree's geometry so parent layout changes don't cause its children to animate in lockstep — useful when nested animations visibly fight each other.

## Rasterization Hints: drawingGroup / compositingGroup / geometryGroup

These can fix real stutter or compositing glitches, but each has a cost and can change rendering. Add only when you observe a problem — never preemptively.

| Modifier | What it does | Reach for it when |
| --- | --- | --- |
| `.drawingGroup()` | Flattens the subtree into a single Metal-rendered layer | A complex view (many shapes/gradients/blurs) stutters while animating |
| `.compositingGroup()` | Composites the subtree before applying opacity/blend/shadow | Opacity or a shadow is applied to overlapping children and looks wrong (double-blended edges) |
| `.geometryGroup()` | Isolates geometry so parent changes don't propagate per-child | Nested animated views visibly fight or lag during a parent transition |

```swift
// Only after profiling shows this subtree is the bottleneck
ComplexChartView()
    .drawingGroup()
```

### Cautions

- `.drawingGroup()` rasterizes the subtree: text can lose crispness, and it can break certain blend modes, accessibility, and hit-testing. Don't wrap whole screens in it.
- A separate compositing layer costs memory. Don't add these to every animated view.
- Profile with Instruments (or the SwiftUI Animation Hitches / Time Profiler) to confirm the win before keeping the hint.
