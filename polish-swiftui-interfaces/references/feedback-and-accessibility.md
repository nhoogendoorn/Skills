# Feedback & Accessibility

Haptics, Reduce Motion, Reduce Transparency, and Dynamic Type — the details that make polish feel *good* and keep it working for everyone.

## Contents

- [Haptics with sensoryFeedback](#haptics-with-sensoryfeedback)
- [Honor Reduce Motion](#honor-reduce-motion)
- [Honor Reduce Transparency](#honor-reduce-transparency)
- [Dynamic Type Behavior](#dynamic-type-behavior)

## Haptics with sensoryFeedback

`.sensoryFeedback(_, trigger:)` (iOS 17+) ties a haptic to a state change declaratively — no `UIFeedbackGenerator` plumbing. The feedback fires when `trigger` changes.

```swift
// Outcome feedback when a save completes
ContentView()
    .sensoryFeedback(.success, trigger: didSave)

// Selection tick as a picker value changes
Picker("Speed", selection: $speed) { /* ... */ }
    .sensoryFeedback(.selection, trigger: speed)

// Impact on a deliberate press/toggle
.sensoryFeedback(.impact(weight: .light), trigger: isOn)
```

Conditional firing (only on a specific transition):

```swift
.sensoryFeedback(trigger: count) { old, new in
    new > old ? .increase : nil      // haptic only when incrementing
}
```

### Choosing the right feedback

| Feedback | Use for |
| --- | --- |
| `.selection` | Moving through pickers, segmented controls, steppers |
| `.impact` (light/medium/heavy) | Deliberate presses, toggles, snapping into place |
| `.success` / `.warning` / `.error` | Operation outcomes |
| `.increase` / `.decrease` | Value going up/down (counters, sliders crossing marks) |

**Don't over-fire.** Haptics lose meaning when constant — reserve them for meaningful, discrete moments. Never fire on every frame of a drag or every keystroke. The system already handles haptics for standard controls; add your own only for custom interactions.

## Honor Reduce Motion

Large movement, scaling, and parallax can cause discomfort for motion-sensitive users. Read the environment value and degrade to a cross-fade or instant change.

```swift
struct Card: View {
    @Environment(\.accessibilityReduceMotion) private var reduceMotion
    @State private var expanded = false

    var body: some View {
        content
            .scaleEffect(expanded ? 1.05 : 1)
            .animation(reduceMotion ? nil : .snappy, value: expanded)
            // When reduceMotion is on: state still changes, just without the animated motion.
    }
}
```

- Replace big `offset`/`scale` transitions with `.opacity` when Reduce Motion is on.
- A reusable transition helper keeps call sites clean:

```swift
extension AnyTransition {
    static func accessible(_ motion: AnyTransition,
                           reduceMotion: Bool) -> AnyTransition {
        reduceMotion ? .opacity : motion
    }
}
```

- The custom `ButtonStyle` press-scale in [animations.md](animations.md) already branches on `reduceMotion` — follow that pattern for any motion you add.

## Honor Reduce Transparency

System materials (`.ultraThinMaterial`, `.regularMaterial`) and Liquid Glass blur the content behind them. With Reduce Transparency on, that blur should fall back to an opaque surface.

```swift
struct GlassPanel: View {
    @Environment(\.accessibilityReduceTransparency) private var reduceTransparency
    var body: some View {
        content
            .background {
                if reduceTransparency {
                    Color(.systemBackground)            // solid fallback
                } else {
                    Rectangle().fill(.regularMaterial)  // translucent
                }
            }
    }
}
```

System components (toolbars, sheets, `.glassEffect`) handle this automatically — only branch manually when you build a custom translucent surface.

## Dynamic Type Behavior

Covered in depth in [typography.md](typography.md); the accessibility essentials:

- Drive spacing/padding from `@ScaledMetric` so layouts breathe at large sizes.
- Avoid fixed-height containers around text — let them grow.
- Test at accessibility sizes in previews:

```swift
#Preview("AX5") {
    ContentView().environment(\.dynamicTypeSize, .accessibility5)
}
```

- Cap growth with `.dynamicTypeSize(...DynamicTypeSize.accessibility1)` only where a layout genuinely can't accommodate more (e.g. a fixed tab bar) — never as a blanket default.
