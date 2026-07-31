# Screen QR Code Scanner

A lightweight desktop utility that detects QR codes displayed on your screen.

Screen QR Code Scanner is built for situations where a website, document, presentation, or desktop app shows a QR code that is inconvenient to scan with a phone. Trigger a scan from the menu bar or with a global hotkey, and the app recognizes the code locally, copies its content, and opens URLs when appropriate.

## Platform Status

| Platform | Status | Implementation |
| --- | --- | --- |
| macOS | Available | Swift, SwiftUI, ScreenCaptureKit, Vision |
| Windows | Planned | Native Windows desktop app |

## Features

- One-click screen scanning
- Configurable global hotkey
- Multi-display support
- Automatic URL opening
- Automatic clipboard copy
- Local scan history
- Launch at login
- Simplified Chinese and English (US)
- Offline QR code recognition
- No screenshot uploads

## Repository Layout

```text
.
├── README.md
├── macOS/
└── Windows/
```

The macOS and Windows clients live in separate directories so each platform can use its native frameworks.

## macOS

The macOS client is currently available. It runs in the menu bar, opens a regular foreground window when needed, and switches back to menu bar mode after the main window is closed.

To build it:

1. Open the Xcode project in the `macOS` directory.
2. Select your Apple Development Team under `Signing & Capabilities`.
3. Build the project and copy the resulting app to `/Applications`.
4. Grant Screen Recording access in System Settings.

See the macOS directory for detailed build, permission, and usage instructions.

## Privacy

Screen capture and QR code recognition run locally. The app does not upload screenshots or scan results. Detected URLs are passed to the system default browser.

## Roadmap

- Continue improving the macOS client
- Add signed and notarized macOS releases
- Build the native Windows client
- Add automated release builds

## Contributing

Bug reports and focused pull requests are welcome. Include the operating system version and display configuration when reporting capture or recognition problems. Do not attach screenshots containing private information.
