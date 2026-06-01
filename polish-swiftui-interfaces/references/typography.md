# Typography

Typography details that make SwiftUI interfaces feel better.

## Contents

- [Semantic Text Styles](#semantic-text-styles)
- [Dynamic Type](#dynamic-type)
- [Monospaced & Numeric Text](#monospaced--numeric-text)
- [Line Limits & Wrapping](#line-limits--wrapping)

## Semantic Text Styles

Use the system's semantic text styles instead of hardcoded point sizes. They scale with the user's Dynamic Type setting, stay consistent with platform chrome, and adapt across iPhone/iPad.

```swift
// Good — semantic styles
Text("Account").font(.headline)
Text("Manage your subscription").font(.subheadline).foregroundStyle(.secondary)

// Bad — fixed size ignores Dynamic Type and platform conventions
Text("Account").font(.system(size: 17, weight: .semibold))
```

If you need a custom font, still tie it to a text style so it scales:

```swift
Text("Headline").font(.custom("Inter", size: 17, relativeTo: .headline))
```

Use `.foregroundStyle(.secondary)` / `.tertiary` for hierarchy rather than custom grays — they adapt to light/dark and accessibility contrast settings.

## Dynamic Type

Text styles scale automatically. The common failure is the *layout* around the text: fixed heights, fixed spacing, and cramped containers that clip at large sizes.

```swift
// Good — spacing scales with the text
struct Row: View {
    @ScaledMetric(relativeTo: .body) private var spacing: CGFloat = 12
    var body: some View {
        HStack(spacing: spacing) {
            Image(systemName: "bell")
            Text("Notifications")
        }
        .padding(.vertical, spacing / 2)
    }
}
```

- Avoid `.frame(height:)` on containers wrapping text — let them grow.
- Test at the largest accessibility sizes (`.environment(\.dynamicTypeSize, .accessibility5)` in previews).
- Use `.dynamicTypeSize(...partial range)` to *cap* growth only where a layout genuinely can't accommodate it (e.g. a tab bar label), not as a default.

```swift
#Preview {
    ContentView()
        .environment(\.dynamicTypeSize, .accessibility3)
}
```

## Monospaced & Numeric Text

When numbers update (counters, timers, prices, table columns), proportional digits cause the text width to jitter. Make digits equal width.

```swift
// Good — stable width as the value changes
Text(elapsed, format: .number)
    .monospacedDigit()

// Also good — applied via font
Text("\(score)").font(.title.monospacedDigit())
```

For animated value changes, combine with `.contentTransition(.numericText())` so digits roll instead of cross-fading:

```swift
Text(count, format: .number)
    .contentTransition(.numericText())
    .monospacedDigit()
    .onTapGesture {
        withAnimation(.snappy) { count += 1 }
    }
```

For a counting/odometer feel where the number trends a direction, pass the value:
`.contentTransition(.numericText(value: Double(count)))`.

### When to use

| Use monospaced digits | Don't |
| --- | --- |
| Counters, timers, stopwatches | Static one-off numbers |
| Prices that update live | Decorative large display numbers |
| Table/grid number columns | Version strings (v2.1.0) |
| Animated number transitions | Phone numbers, zip codes |

## Line Limits & Wrapping

SwiftUI has no `text-wrap: balance`. Control reflow explicitly so labels don't jump as content changes.

```swift
// Reserve space for up to 2 lines so the row height is stable
Text(subtitle)
    .lineLimit(2, reservesSpace: true)
    .multilineTextAlignment(.leading)
    .truncationMode(.tail)
```

- `.lineLimit(2, reservesSpace: true)` keeps a constant height whether the text is 1 or 2 lines — prevents layout jumps in lists.
- `.fixedSize(horizontal: false, vertical: true)` lets text grow vertically when a parent would otherwise clip it to one line.
- Prefer `.truncationMode(.tail)` for labels; use `.middle` for paths/filenames where the start and end both matter.
- For headings that must not break awkwardly, allow wrapping with `.multilineTextAlignment(.center)` rather than forcing a single line that truncates.
