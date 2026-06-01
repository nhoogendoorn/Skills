# Animations

Interruptible animations, springs, enter/exit transitions, SF Symbol effects, and scale on press in SwiftUI.

## Contents

- [Interruptible Animations & Springs](#interruptible-animations--springs)
- [Enter Animations: Split and Stagger](#enter-animations-split-and-stagger)
- [Exit Animations](#exit-animations)
- [SF Symbol Animations](#sf-symbol-animations)
- [Scale on Press](#scale-on-press)
- [Skip Animation on Appear](#skip-animation-on-appear)

## Interruptible Animations & Springs

Users change intent mid-interaction. SwiftUI's value-driven animations are interruptible: when the bound value changes again mid-flight, the animation retargets smoothly toward the new state. Springs are the best default for interactive changes because they carry velocity through the retarget.

```swift
// Good — interruptible, retargets if toggled again mid-animation
struct Drawer: View {
    @State private var isOpen = false
    var body: some View {
        panel
            .offset(x: isOpen ? 0 : -320)
            .animation(.spring(duration: 0.35, bounce: 0.15), value: isOpen)
    }
}
```

Prefer the named springs introduced in iOS 17 — they're tuned to feel right:

| Spring | Feel | Use for |
| --- | --- | --- |
| `.smooth` | No bounce, gentle | Most state changes, content reveals |
| `.snappy` | Slight bounce, quick | Buttons, toggles, selection |
| `.bouncy` | Noticeable bounce | Playful, attention-drawing moments |

Reserve `PhaseAnimator` and `KeyframeAnimator` for one-shot staged sequences (a success checkmark, a loading pulse) — they run on a fixed timeline and don't retarget like value-driven animations.

## Enter Animations: Split and Stagger

Don't animate one big container. Break content into semantic chunks and stagger each with a small per-index delay, combining `opacity`, `offset`, and `blur`.

```swift
struct PageHeader: View {
    @State private var appeared = false
    private let items = ["Welcome", "A short description.", "Get started"]

    var body: some View {
        VStack(alignment: .leading, spacing: 12) {
            ForEach(Array(items.enumerated()), id: \.offset) { index, text in
                Text(text)
                    .opacity(appeared ? 1 : 0)
                    .blur(radius: appeared ? 0 : 4)
                    .offset(y: appeared ? 0 : 12)
                    .animation(.smooth(duration: 0.4).delay(Double(index) * 0.08),
                               value: appeared)
            }
        }
        .onAppear { appeared = true }
    }
}
```

For lists of views that come and go, `PhaseAnimator` or a transition with an index-based delay gives the same staggered feel. Keep the stagger small (~0.05–0.1s) — large delays feel sluggish.

## Exit Animations

Exits should be softer, quicker, and less attention-grabbing than enters — the user's focus is moving on. Use an `.asymmetric` transition so removal differs from insertion, and keep removal movement small.

```swift
// Good — gentle insert, subtle quick removal
if showBanner {
    BannerView()
        .transition(.asymmetric(
            insertion: .opacity.combined(with: .offset(y: 12)),
            removal: .opacity.combined(with: .offset(y: -8))   // small, not full height
        ))
}
```

Drive it with an animation on the controlling value:

```swift
withAnimation(.smooth(duration: 0.2)) { showBanner = false }
```

- Keep some directional movement so the element reads as *leaving*, not vanishing.
- Removal should be quicker than insertion (e.g. 0.2s vs 0.35s).
- Don't remove the transition entirely — an abrupt disappear loses spatial context.
- Use a full slide-off (`.move(edge:)`) only when spatial context matters, e.g. a card returning to a list or a drawer closing.

## SF Symbol Animations

When a symbol changes state, animate the symbol itself rather than swapping it instantly.

```swift
// Built-in symbol effects (iOS 17+)
Image(systemName: "bell.fill")
    .symbolEffect(.bounce, value: notificationCount)   // bounce when count changes

Image(systemName: isRecording ? "mic.fill" : "mic")
    .symbolEffect(.pulse, isActive: isRecording)        // continuous pulse while active

// Cross-fade/replace when swapping between two symbols
Image(systemName: isPlaying ? "pause.fill" : "play.fill")
    .contentTransition(.symbolEffect(.replace))
```

- Use `.bounce` for one-shot feedback (new message, sent), `.pulse` for ongoing activity, `.variableColor` for progress/levels.
- `.contentTransition(.symbolEffect(.replace))` is the clean way to swap play/pause, like/unlike, etc.
- Apply these inside (or alongside) `withAnimation` when the trigger is a value change you also animate elsewhere.

### When to animate symbols

| Animate | Don't animate |
| --- | --- |
| State changes (play→pause, like→liked) | Static navigation icons |
| Action feedback (sent, saved) | Purely decorative symbols |
| Ongoing activity (recording, syncing) | Always-visible chrome icons |

## Scale on Press

Give buttons tactile feedback with a custom `ButtonStyle` that scales while pressed. Always use `0.96`; never below `0.95` — it feels exaggerated. The press scale is interruptible by nature: releasing mid-press springs back.

```swift
struct PressableButtonStyle: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        PressableLabel(configuration: configuration)
    }

    // Read @Environment inside a View, not in the ButtonStyle struct itself —
    // a ButtonStyle isn't a View, so environment values aren't injected into it.
    private struct PressableLabel: View {
        let configuration: ButtonStyleConfiguration
        @Environment(\.accessibilityReduceMotion) private var reduceMotion

        var body: some View {
            configuration.label
                .scaleEffect(configuration.isPressed && !reduceMotion ? 0.96 : 1)
                .animation(.snappy(duration: 0.15), value: configuration.isPressed)
        }
    }
}

// Usage
Button("Save", action: save)
    .buttonStyle(PressableButtonStyle())
```

Not every button needs this. Skip it for destructive confirmations and dense toolbars where the motion distracts, and always branch on `accessibilityReduceMotion` (shown above) so it degrades to no scale.

## Skip Animation on Appear

Value-driven `.animation(_, value:)` does **not** run on first render — it only fires when the value later changes. That's usually exactly what you want: default-state elements shouldn't animate in on screen load.

The case to watch is `withAnimation` triggered from `.onAppear`/`.task`, which *will* animate on first appearance. Gate it behind a flag only when you genuinely want an entrance:

```swift
// Intentional entrance — fine
.onAppear { withAnimation(.smooth) { appeared = true } }

// Unintentional — a toggle's default state animating in on load
// Fix: don't wrap the initial state in withAnimation; let .animation(value:) handle later changes.
```

Verify on a fresh navigation push / app launch that nothing animates that shouldn't.
