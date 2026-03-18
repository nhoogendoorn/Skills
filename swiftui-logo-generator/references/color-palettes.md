# Curated Color Palettes

Palettes organized by semantic meaning. Each includes a primary, secondary, and accent.

## Professional / Corporate
```swift
// Slate Blue
Color(red: 0.25, green: 0.35, blue: 0.55)  // Primary
Color(red: 0.15, green: 0.22, blue: 0.35)  // Dark
Color(red: 0.45, green: 0.65, blue: 0.85)  // Accent

// Charcoal + Gold
Color(red: 0.18, green: 0.18, blue: 0.20)  // Primary
Color(red: 0.85, green: 0.72, blue: 0.35)  // Accent
Color(red: 0.40, green: 0.40, blue: 0.42)  // Secondary
```

## Creative / Playful
```swift
// Sunset
Color(red: 1.0, green: 0.45, blue: 0.35)   // Primary (coral)
Color(red: 1.0, green: 0.72, blue: 0.28)   // Secondary (amber)
Color(red: 0.85, green: 0.25, blue: 0.45)  // Accent (magenta)

// Ocean
Color(red: 0.10, green: 0.60, blue: 0.85)  // Primary (sky)
Color(red: 0.05, green: 0.35, blue: 0.65)  // Dark (deep)
Color(red: 0.30, green: 0.85, blue: 0.75)  // Accent (teal)
```

## Nature / Organic
```swift
// Forest
Color(red: 0.18, green: 0.50, blue: 0.35)  // Primary (green)
Color(red: 0.12, green: 0.32, blue: 0.22)  // Dark
Color(red: 0.55, green: 0.78, blue: 0.45)  // Light

// Earth
Color(red: 0.60, green: 0.42, blue: 0.28)  // Primary (brown)
Color(red: 0.85, green: 0.72, blue: 0.55)  // Secondary (sand)
Color(red: 0.40, green: 0.28, blue: 0.18)  // Dark
```

## Tech / Modern
```swift
// Neon
Color(red: 0.25, green: 0.95, blue: 0.85)  // Primary (cyan)
Color(red: 0.65, green: 0.35, blue: 1.0)   // Secondary (violet)
Color(red: 0.08, green: 0.08, blue: 0.12)  // Background (near-black)

// Minimal
Color(red: 0.12, green: 0.12, blue: 0.14)  // Primary (dark)
Color(red: 0.95, green: 0.95, blue: 0.97)  // Light
Color(red: 0.40, green: 0.45, blue: 1.0)   // Accent (indigo)
```

## Warm / Friendly
```swift
// Peach
Color(red: 1.0, green: 0.60, blue: 0.48)   // Primary
Color(red: 1.0, green: 0.78, blue: 0.65)   // Light
Color(red: 0.85, green: 0.40, blue: 0.35)  // Deep

// Lavender
Color(red: 0.72, green: 0.58, blue: 0.88)  // Primary
Color(red: 0.88, green: 0.78, blue: 1.0)   // Light
Color(red: 0.48, green: 0.35, blue: 0.68)  // Deep
```

## Using with Gradients

```swift
// Two-tone diagonal
LinearGradient(colors: [primary, accent], startPoint: .topLeading, endPoint: .bottomTrailing)

// Subtle depth (same hue, vary lightness)
LinearGradient(colors: [primary, dark], startPoint: .top, endPoint: .bottom)

// Vibrant radial
RadialGradient(colors: [accent, primary], center: .center, startRadius: 0, endRadius: size / 2)
```
