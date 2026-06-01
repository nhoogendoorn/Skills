# Liquid Glass (iOS 26)

Liquid Glass is the iOS 26 material for floating, interactive chrome. Used well it adds depth and focus; overused it turns content into mush. Everything here requires iOS 26 — gate with `if #available(iOS 26, *)` and provide a material/opaque fallback for earlier OS versions.

## Contents

- [When to Use Glass](#when-to-use-glass)
- [Applying glassEffect](#applying-glasseffect)
- [Grouping with GlassEffectContainer](#grouping-with-glasseffectcontainer)
- [Glass Buttons](#glass-buttons)
- [Do's and Don'ts](#dos-and-donts)

## When to Use Glass

Glass belongs on elements that **float above content**: toolbars, floating action buttons, overlay controls, custom tab/segment bars, HUD-style panels. It does **not** belong on large content backgrounds, list rows, or full-screen surfaces — glass over glass and glass over big content areas looks muddy and hurts legibility.

Before adding it manually, check whether a standard component already gives you glass for free — toolbars, sheets, and tab bars adopt the system look automatically on iOS 26. Reach for `.glassEffect()` only for *custom* floating controls.

## Applying glassEffect

```swift
if #available(iOS 26, *) {
    HStack(spacing: 16) {
        Button { } label: { Image(systemName: "backward.fill") }
        Button { } label: { Image(systemName: "play.fill") }
        Button { } label: { Image(systemName: "forward.fill") }
    }
    .padding()
    .glassEffect(in: .rect(cornerRadius: 24, style: .continuous))
}
```

- The signature is `glassEffect(_ style: GlassEffectStyle = .regular, in shape: some Shape = .rect)`. Pass an explicit shape with `in:` (`.rect(cornerRadius:)`, `.capsule`, `.circle`) to match surrounding corners.
- Apply `.glassEffect` **after** layout and visual modifiers (padding, frame, background) — it samples the laid-out content.
- Use `.glassEffect(.regular.interactive())` for controls that should react to touch with the lensing/highlight behavior.
- Keep content on glass high-contrast — glass is translucent, so thin/low-contrast labels disappear.

## Grouping with GlassEffectContainer

When several glass elements sit near each other, wrap them in a `GlassEffectContainer` so they blend and morph as one system rather than rendering as separate overlapping panes. Use `glassEffectID` (with a `@Namespace`) to animate elements merging/splitting.

```swift
@Namespace private var glassNamespace

if #available(iOS 26, *) {
    GlassEffectContainer(spacing: 16) {
        ForEach(actions) { action in
            Button(action: action.run) { Image(systemName: action.symbol) }
                .glassEffect()
                .glassEffectID(action.id, in: glassNamespace)
        }
    }
}
```

## Glass Buttons

For individual buttons, the built-in style is simpler than applying the effect by hand:

```swift
if #available(iOS 26, *) {
    Button("Continue", action: next)
        .buttonStyle(.glass)            // or .glassProminent for the primary action
}
```

Use `.glassProminent` for the single primary action; `.glass` for secondary floating actions.

## Do's and Don'ts

| Do | Don't |
| --- | --- |
| Use glass on floating controls and overlays | Put glass on large content backgrounds or list rows |
| Group nearby glass in a `GlassEffectContainer` | Stack independent glass layers over each other |
| Keep labels/icons high-contrast | Place thin, low-contrast text on glass |
| Match the glass shape to nearby corners (`.continuous`) | Mix circular and continuous corners |
| Let standard toolbars/tab bars adopt glass automatically | Re-skin every surface with `.glassEffect()` |
| Gate with `if #available(iOS 26, *)` + fallback | Assume glass exists on older OS versions |

**Accessibility:** Liquid Glass respects Reduce Transparency automatically, falling back to a more opaque surface — but verify custom labels stay legible in that state. See [feedback-and-accessibility.md](feedback-and-accessibility.md).
