# SwiftUI Shape Patterns

Common patterns for programmatic logo construction.

## Basic Shapes

```swift
// Rounded square (app icon base)
RoundedRectangle(cornerRadius: size * 0.2, style: .continuous)

// Circle with stroke
Circle()
    .strokeBorder(lineWidth: size * 0.05)

// Capsule for pill shapes
Capsule()
```

## Custom Path Patterns

### Triangle
```swift
Path { path in
    path.move(to: CGPoint(x: size / 2, y: 0))
    path.addLine(to: CGPoint(x: size, y: size))
    path.addLine(to: CGPoint(x: 0, y: size))
    path.closeSubpath()
}
```

### Hexagon
```swift
Path { path in
    let center = CGPoint(x: size / 2, y: size / 2)
    let radius = size / 2
    for i in 0..<6 {
        let angle = Angle(degrees: Double(i) * 60 - 90)
        let point = CGPoint(
            x: center.x + radius * cos(angle.radians),
            y: center.y + radius * sin(angle.radians)
        )
        if i == 0 { path.move(to: point) }
        else { path.addLine(to: point) }
    }
    path.closeSubpath()
}
```

### Rounded Star
```swift
func starPath(points: Int, innerRadius: CGFloat, outerRadius: CGFloat, center: CGPoint) -> Path {
    Path { path in
        let angleStep = .pi / Double(points)
        for i in 0..<(points * 2) {
            let radius = i.isMultiple(of: 2) ? outerRadius : innerRadius
            let angle = Double(i) * angleStep - .pi / 2
            let point = CGPoint(
                x: center.x + radius * cos(angle),
                y: center.y + radius * sin(angle)
            )
            if i == 0 { path.move(to: point) }
            else { path.addLine(to: point) }
        }
        path.closeSubpath()
    }
}
```

## Gradient Patterns

```swift
// Diagonal gradient
LinearGradient(
    colors: [.blue, .purple],
    startPoint: .topLeading,
    endPoint: .bottomTrailing
)

// Radial glow
RadialGradient(
    colors: [.white.opacity(0.3), .clear],
    center: .center,
    startRadius: 0,
    endRadius: size / 2
)

// Angular sweep
AngularGradient(
    colors: [.red, .orange, .yellow, .green, .blue, .purple, .red],
    center: .center
)
```

## Composition Techniques

### Layered ZStack
```swift
ZStack {
    // Background shape
    RoundedRectangle(cornerRadius: size * 0.2, style: .continuous)
        .fill(gradient)

    // Inner detail
    Circle()
        .fill(.white.opacity(0.15))
        .frame(width: size * 0.6)

    // Foreground symbol
    Image(systemName: "star.fill")
        .font(.system(size: size * 0.35))
        .foregroundStyle(.white)
}
.frame(width: size, height: size)
```

### Masked Shapes
```swift
Circle()
    .fill(gradient)
    .mask {
        Text("A")
            .font(.system(size: size * 0.7, weight: .black, design: .rounded))
    }
```

### Rotated Elements
```swift
ForEach(0..<8, id: \.self) { i in
    RoundedRectangle(cornerRadius: 2)
        .frame(width: size * 0.08, height: size * 0.3)
        .offset(y: -size * 0.25)
        .rotationEffect(.degrees(Double(i) * 45))
}
```
