# Surfaces

Corner radius, optical alignment, depth, separators, and hit areas in SwiftUI.

## Contents

- [Concentric & Continuous Corner Radius](#concentric--continuous-corner-radius)
- [Optical Alignment](#optical-alignment)
- [Depth: Shadows & Materials](#depth-shadows--materials)
- [Hairline Separators & Image Outlines](#hairline-separators--image-outlines)
- [Minimum Hit Area](#minimum-hit-area)

## Concentric & Continuous Corner Radius

Two rules: corners should be **continuous** (Apple's squircle), and nested radii should be **concentric**.

```
outerRadius = innerRadius + padding
```

```swift
// Good — continuous + concentric (outer 24 = inner 16 + padding 8)
VStack { /* inner content */ }
    .padding(8)
    .background(
        RoundedRectangle(cornerRadius: 16, style: .continuous)
            .fill(Color(.secondarySystemBackground))
    )
    .background(
        RoundedRectangle(cornerRadius: 24, style: .continuous)
            .fill(Color(.systemBackground))
    )

// Bad — deprecated, circular corners, same radius on both layers
VStack { }.padding(8).cornerRadius(16)   // ⚠️ .cornerRadius is deprecated and .circular
```

- Always pass `style: .continuous`. The default `.circular` reads subtly wrong next to system chrome.
- Use `.clipShape(.rect(cornerRadius:style:.continuous))` instead of the deprecated `.cornerRadius(_:)`.
- If padding exceeds ~24pt, treat the layers as separate surfaces and choose radii independently — strict concentric math stops mattering when surfaces are far apart.

### iOS 26: concentric corner style

On iOS 26, the `.concentric` corner style derives a child's radius from its container automatically, so you don't recompute it by hand — the child's corners stay concentric with the surface it sits in:

```swift
if #available(iOS 26, *) {
    Button("Confirm") { confirm() }
        .clipShape(.rect(cornerRadius: 12, style: .concentric))
}
```

## Optical Alignment

When geometric centering looks off, align optically.

### Buttons with text + icon

Prefer `Label` so the symbol sits on the text baseline at a matched scale. When you build it manually, give the icon side slightly less trailing padding so the row feels balanced:

```swift
// Label handles spacing/baseline for you
Button(action: continueAction) {
    Label("Continue", systemImage: "arrow.right")
        .labelStyle(.titleAndIcon)
}

// Manual layout — trailing padding a touch smaller than leading
HStack(spacing: 6) {
    Text("Continue")
    Image(systemName: "arrow.right").imageScale(.small)
}
.padding(.leading, 16)
.padding(.trailing, 14)   // icon side ≈ text side − 2
```

### Play triangles & asymmetric symbols

A play triangle's geometric center isn't its visual center — nudge it right. SF Symbols are pre-corrected, so prefer the symbol; only nudge custom shapes.

```swift
Image(systemName: "play.fill")            // already optically centered
Path { /* custom triangle */ }
    .offset(x: 1)                          // shift right to balance the apex
```

## Depth: Shadows & Materials

For cards, sheets, popovers, and floating controls, create elevation with a **soft shadow** or a **system material** — not a hard stroke. Materials adapt to the content behind them and to light/dark; a fixed stroke color doesn't.

```swift
// Good — soft, low-opacity shadow for lift
RoundedRectangle(cornerRadius: 16, style: .continuous)
    .fill(.background)
    .shadow(color: .black.opacity(0.12), radius: 8, y: 4)

// Good — material for overlays/floating chrome
HStack { /* toolbar contents */ }
    .padding()
    .background(.regularMaterial, in: .rect(cornerRadius: 16, style: .continuous))
```

Keep shadows subtle: small radius, low opacity, slight positive `y`. Stacked huge shadows read as fake.

### Shadows/materials vs. strokes

| Use shadow / material | Use a thin stroke |
| --- | --- |
| Cards & containers with depth | Dividers between list rows |
| Sheets, popovers, dropdowns | Table/grid cell boundaries |
| Floating buttons & toolbars | Input field outlines (focus/accessibility) |
| Elements over photos/varied backgrounds | Hairline separators in dense UI |

`List` and `Form` already provide system separators — don't hand-draw them.

## Hairline Separators & Image Outlines

Use the semantic `Color(.separator)` for hairlines so they match system dividers and adapt to light/dark. For images and thumbnails, add a thin inset stroke so the edge stays crisp on any background:

```swift
// Crisp edge on a thumbnail — neutral separator, never a tinted gray
image
    .resizable()
    .aspectRatio(contentMode: .fill)
    .frame(width: 56, height: 56)
    .clipShape(RoundedRectangle(cornerRadius: 12, style: .continuous))
    .overlay(
        RoundedRectangle(cornerRadius: 12, style: .continuous)
            .strokeBorder(Color(.separator), lineWidth: 1)   // strokeBorder insets — no size change
    )
```

- Use `.strokeBorder` (insets the line) rather than `.stroke` so the outline doesn't expand the frame.
- Use `Color(.separator)` — never a tinted near-black/near-white, which picks up the surface color and reads as dirt on the edge.

## Minimum Hit Area

Interactive elements need at least 44×44pt (Apple HIG). When the visible control is smaller, expand the tappable region — don't make users aim.

```swift
// Small icon button with a full 44pt target
Button(action: toggle) {
    Image(systemName: "xmark")
        .imageScale(.small)
        .frame(width: 44, height: 44)        // hit area, not just glyph
        .contentShape(Rectangle())            // whole frame is tappable, incl. transparent areas
}
.buttonStyle(.plain)
```

- `.contentShape(Rectangle())` makes transparent padding tappable — without it, only the opaque glyph responds.
- In dense layouts, keep targets from overlapping: two interactive elements should never share hit area. Expand as far as possible without colliding.
- For list rows, `.contentShape(Rectangle())` on the row makes the entire row tappable, not just the text.
