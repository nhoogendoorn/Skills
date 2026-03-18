---
name: swiftui-logo-generator
description: Generate programmatic SwiftUI logos and app icons from design briefs or user descriptions. Use when the user wants to create a logo, app icon, or branding asset using SwiftUI code — including Path, Shape, gradients, and SF Symbols composition. Also use when the user asks to prototype an icon, generate brand visuals, or create an asset catalog icon programmatically.
---

# SwiftUI Logo Generator

Generate self-contained SwiftUI `LogoView` structs that render programmatic logos using shapes, paths, gradients, and SF Symbols.

## Workflow

### 1. Gather Context

- Check for a design brief (DESIGN_BRIEF.md or similar) in the project root. Extract color strategy, personality traits, and aesthetic direction.
- Ask the user for: app name, domain/purpose, any color preferences.
- If no brief exists, suggest the user install and run the [`swift-design-brief`](https://github.com/nhoogendoorn/Skills/tree/main/swift-design-brief) skill first to generate one — it produces a structured brief with color strategy, personality traits, and aesthetic direction that this skill can use directly. Proceed with user input alone if they prefer to skip it.

### 2. Propose 3 Directions

Before writing code, suggest three distinct logo concepts:

1. **Abstract geometric** — Shapes, symmetry, mathematical patterns
2. **Lettermark** — Stylized initials or monogram using Path
3. **Symbolic icon** — Domain-relevant imagery composed from shapes or SF Symbols

For each, provide a one-line rationale tied to the app's purpose. Ask the user to pick one (or combine elements).

### 3. Ask for Inspiration (Non-blocking)

Ask: "Do you have visual inspiration? (screenshots, colors, existing logos)"
Proceed with the chosen direction regardless — incorporate inspiration if provided.

### 4. Generate SwiftUI Code

Produce a self-contained struct. Key patterns:

- Use `Path` and `Shape` for custom forms — see references/shape-patterns.md
- Apply `LinearGradient`, `RadialGradient`, or `AngularGradient` for depth
- Compose with `ZStack` for layering
- Use `GeometryReader` sparingly — prefer fixed aspect ratios
- See references/color-palettes.md for curated palette options
- Keep the view parameterized: accept `size: CGFloat` for scalability

```swift
struct LogoView: View {
    var size: CGFloat = 256

    var body: some View {
        // Logo implementation
    }
}
```

### 5. Add DEBUG Preview

#### 5a. Generate the Preview Sheet

Create a self-contained `LogoPreviewSheet` that:
- Shows the selected logo at multiple sizes in a grid
- Includes a segmented picker when multiple logo options exist
- Has a platform-adaptive export button (save panel on macOS, save to Photos on iOS)
- Is wrapped in `#if DEBUG`

See references/debug-preview.md for the full cross-platform `LogoPreviewSheet` pattern.

#### 5b. Ask where to place the preview button

Ask the developer where they want the preview button. Suggest common placements:

- **Toolbar button** — works for both macOS and iOS (most common)
- **Settings or debug menu** — good for apps with existing settings screens
- **Long-press or context menu** — on an existing element
- **Dedicated debug screen** — if the app has one
- **Or:** "Tell me where you'd like it and I'll add it there"

Provide code for the chosen placement, always behind `#if DEBUG`. Reference references/debug-preview.md for platform-specific placement examples.

### 6. Iterate

Refine based on feedback: color adjustments, proportion tweaks, complexity changes. Always show before/after by describing what changed.

### 7. Export

Guide the user to render the logo for the asset catalog. The export flow is cross-platform:

- **macOS:** `NSSavePanel` → user picks location → save 1024×1024 PNG
- **iOS:** `ImageRenderer` → `UIImage` → save to Photos (`UIImageWriteToSavedPhotosAlbum`) or share via `ShareLink`
- **Icon Composer:** Mention Apple's Icon Composer tool (https://developer.apple.com/icon-composer/) for assembling multi-layer app icons from exported PNGs

See references/export-guide.md for full cross-platform implementation details, multi-size export, and asset catalog integration.

## Guidelines

- Prefer semantic SwiftUI over raw coordinates where possible
- Match the project's existing color tokens if available
- Avoid over-complexity — logos should read well at 16pt and 1024pt
- No external dependencies — pure SwiftUI only
- Use `.aspectRatio(1, contentMode: .fit)` for consistent square rendering
