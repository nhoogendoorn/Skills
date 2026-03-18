# Export Guide

Render SwiftUI logos to images for asset catalogs using `ImageRenderer`. Works on both macOS and iOS.

## Cross-Platform ImageRenderer Usage

`ImageRenderer` returns `.nsImage` on macOS and `.uiImage` on iOS. Use `#if os()` to handle platform differences:

```swift
import SwiftUI

@MainActor
func renderLogoToPNGData(size: CGFloat) -> Data? {
    let renderer = ImageRenderer(content: LogoView(size: size))
    renderer.scale = 1.0 // Already at target resolution

    #if os(macOS)
    guard let image = renderer.nsImage,
          let tiffData = image.tiffRepresentation,
          let bitmap = NSBitmapImageRep(data: tiffData),
          let pngData = bitmap.representation(using: .png, properties: [:]) else {
        return nil
    }
    return pngData
    #else
    guard let image = renderer.uiImage,
          let pngData = image.pngData() else {
        return nil
    }
    return pngData
    #endif
}
```

## macOS Export — NSSavePanel

```swift
#if os(macOS)
import AppKit

@MainActor
func exportLogoMacOS(size: CGFloat = 1024) {
    guard let pngData = renderLogoToPNGData(size: size) else { return }

    let panel = NSSavePanel()
    panel.allowedContentTypes = [.png]
    panel.nameFieldStringValue = "AppIcon.png"

    guard panel.runModal() == .OK, let url = panel.url else { return }
    try? pngData.write(to: url)
}
#endif
```

## iOS Export — Save to Photos

```swift
#if os(iOS)
import UIKit

@MainActor
func exportLogoiOS(size: CGFloat = 1024) {
    let renderer = ImageRenderer(content: LogoView(size: size))
    renderer.scale = 1.0

    guard let image = renderer.uiImage else { return }
    UIImageWriteToSavedPhotosAlbum(image, nil, nil, nil)
}
#endif
```

> **Note:** Saving to Photos requires the `NSPhotoLibraryAddUsageDescription` key in Info.plist.

## iOS Export — ShareLink Alternative

For a no-permissions-needed approach, render to a `UIImage` and share it. `Image` does not conform to `Transferable`, so use the rendered `UIImage` directly:

```swift
#if os(iOS)
struct LogoShareButton: View {
    let size: CGFloat = 1024

    @State private var renderedImage: UIImage?

    var body: some View {
        if let renderedImage {
            ShareLink(
                item: Image(uiImage: renderedImage),
                preview: SharePreview("App Logo", image: Image(uiImage: renderedImage))
            )
        }
    }

    // Call from .task or .onAppear
    @MainActor
    func renderLogo() {
        let renderer = ImageRenderer(content: LogoView(size: size))
        renderer.scale = 1.0
        renderedImage = renderer.uiImage
    }
}
#endif
```

## Multi-Size Export

Generate all required sizes for an app icon. Uses the cross-platform `renderLogoToPNGData` helper:

```swift
@MainActor
func exportAllSizes(to directory: URL) throws {
    let sizes: [(name: String, size: CGFloat)] = [
        ("icon_16x16", 16),
        ("icon_16x16@2x", 32),
        ("icon_32x32", 32),
        ("icon_32x32@2x", 64),
        ("icon_128x128", 128),
        ("icon_128x128@2x", 256),
        ("icon_256x256", 256),
        ("icon_256x256@2x", 512),
        ("icon_512x512", 512),
        ("icon_512x512@2x", 1024),
    ]

    for (name, size) in sizes {
        guard let pngData = renderLogoToPNGData(size: size) else { continue }
        let fileURL = directory.appendingPathComponent("\(name).png")
        try pngData.write(to: fileURL)
    }
}
```

## Asset Catalog Integration

### Single Image (Recommended)

Modern Xcode (13+) supports a single 1024×1024 image that auto-generates all sizes. This works for both macOS and iOS targets:

```swift
@MainActor
func exportSingleIcon(to url: URL) throws {
    guard let pngData = renderLogoToPNGData(size: 1024) else { return }
    try pngData.write(to: url)
}
```

### Manual Setup
1. Export all sizes using `exportAllSizes(to:)`
2. Open Assets.xcassets in Xcode
3. Add a new "App Icon" image set (or use the default AppIcon)
4. Drag each exported PNG into the corresponding slot

## Icon Composer

Apple provides [Icon Composer](https://developer.apple.com/icon-composer/) — a standalone tool for assembling multi-layer app icons. It supports the automatic icon rendering system introduced in macOS Sequoia, iOS 18, and visionOS 2, which composites separate layers (front, middle, back) with dynamic effects like lighting, shadows, and parallax.

### When to use Icon Composer
- When targeting platforms that support dynamic icon rendering (macOS 26+, iOS 26+, visionOS 2+)
- When you want separate foreground/background layers for parallax or depth effects
- To preview how the icon looks across all platforms and sizes before committing to the asset catalog

### Workflow with SwiftUI logos
1. Export separate layers as individual PNGs (e.g., background gradient at 1024×1024, foreground symbol at 1024×1024)
2. Open Icon Composer and import each layer into the appropriate slot (front, middle, back)
3. Preview the composited result across platforms
4. Save the `.icon` file and add it to your Xcode project
