# DEBUG Preview Setup

Pattern for adding a live logo preview to the app behind a `#if DEBUG` flag. Works on both macOS and iOS.

## Preview Sheet (Cross-Platform)

```swift
#if DEBUG
struct LogoPreviewSheet: View {
    @Environment(\.dismiss) private var dismiss
    private let previewSizes: [CGFloat] = [16, 32, 64, 128, 256, 512]

    var body: some View {
        NavigationStack {
            ScrollView {
                LazyVGrid(columns: [GridItem(.adaptive(minimum: 120))], spacing: 16) {
                    ForEach(previewSizes, id: \.self) { size in
                        VStack(spacing: 4) {
                            LogoView(size: min(size, 120))
                                .frame(width: 120, height: 120)
                            Text("\(Int(size))pt")
                                .font(.caption2)
                                .foregroundStyle(.secondary)
                        }
                    }
                }
                .padding()
            }
            .navigationTitle("Logo Preview")
            #if os(macOS)
            .frame(width: 400, height: 500)
            #endif
            .toolbar {
                ToolbarItem(placement: .confirmationAction) {
                    Button("Done") { dismiss() }
                }
            }
        }
    }
}
#endif
```

## Integration Patterns

### Toolbar Button (Recommended)

Works on both macOS and iOS. The placement adapts per platform:

```swift
#if DEBUG
@State private var showingLogoPreview = false
#endif

// In body:
.toolbar {
    #if DEBUG
    ToolbarItem(placement: .automatic) {
        Button {
            showingLogoPreview = true
        } label: {
            Label("Logo Preview", systemImage: "paintbrush")
        }
    }
    #endif
}
#if DEBUG
.sheet(isPresented: $showingLogoPreview) {
    LogoPreviewSheet()
}
#endif
```

> **Placement note:** `.automatic` works on both platforms. For more control, use `.primaryAction` on macOS or `.navigationBarTrailing` on iOS via `#if os()`:
>
> ```swift
> #if os(macOS)
> ToolbarItem(placement: .automatic) { ... }
> #else
> ToolbarItem(placement: .navigationBarTrailing) { ... }
> #endif
> ```

### Settings / Debug Menu

Good for apps with an existing settings screen:

```swift
// Inside a Settings or Debug view
#if DEBUG
Section("Developer Tools") {
    Button("Preview Logo") { showingLogoPreview = true }
}
#endif
```

### Menu Command (macOS only)

```swift
#if DEBUG && os(macOS)
CommandGroup(after: .help) {
    Button("Preview Logo") {
        NotificationCenter.default.post(name: .showLogoPreview, object: nil)
    }
    .keyboardShortcut("L", modifiers: [.command, .shift])
}
#endif
```

### Context Menu / Long-Press (iOS)

```swift
#if DEBUG
.contextMenu {
    Button {
        showingLogoPreview = true
    } label: {
        Label("Preview Logo", systemImage: "paintbrush")
    }
}
#endif
```

## Key Considerations

- Always wrap in `#if DEBUG` — never ship preview UI to production
- `#if DEBUG` works identically on macOS and iOS
- The existing codebase already uses `#if DEBUG` for "Reset All Data" — follow the same pattern
- Keep the preview sheet self-contained (no dependencies on app state)
- Show multiple sizes to verify the logo scales well
- Include a dark/light mode toggle if the logo uses system colors
