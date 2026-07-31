# Screen QR Scanner

Screen QR Scanner is a lightweight desktop utility that detects QR codes displayed on your screen. It is designed for QR codes shown in websites, documents, presentations, videos, and desktop applications that would otherwise require a phone to scan.

The macOS client runs in the menu bar. Start a scan by clicking its icon or pressing a global hotkey. Recognition happens locally using native Apple frameworks, and screenshots are never uploaded.

## Platform Status

| Platform | Status | Implementation |
| --- | --- | --- |
| macOS | Available | Swift, SwiftUI, ScreenCaptureKit, Vision |
| Windows | Planned | Native Windows desktop client |

## Features

- Scan all connected displays with one click
- Start scans from the menu bar or a configurable global hotkey
- Detect multiple QR codes and select the result to use
- Choose what happens after a scan:
  - Open detected URLs automatically
  - Copy the result without opening it
  - Ask before opening or copying
- Copy QR code content to the clipboard
- Open links in the default browser
- Keep a local history of the 200 most recent results
- Check, request, and manage Screen Recording permission
- Launch automatically at login
- Run quietly as a menu bar utility
- Open a regular foreground window for history and settings
- Use Simplified Chinese or English (US)
- Recognize QR codes offline
- Keep screenshots and scan history on the device

## Repository Layout

```text
.
├── README.md
├── macOS/
└── Windows/
```

Each platform uses its native user interface and screen capture frameworks.

## macOS Requirements

- macOS 14.6 or later
- Xcode with a current macOS SDK
- Screen Recording permission

## Build the macOS Client

1. Open the Xcode project in the `macOS` directory.
2. Select the app target.
3. Open `Signing & Capabilities`.
4. Select your Apple Development Team and enable automatic signing.
5. Build the app.
6. Copy the built app to `/Applications`.
7. Launch the app from the Applications folder.

Keep the same bundle identifier and signing identity between builds. Changing either may cause macOS to treat the build as a different application and request Screen Recording permission again.

## Screen Recording Permission

On first launch, the app requests Screen Recording access and opens:

`System Settings > Privacy & Security > Screen & System Audio Recording`

Enable Screen QR Scanner in the list, then quit and relaunch the installed copy from `/Applications`.

If the app does not appear automatically, use the `+` button on the permission page and select it manually from `/Applications`.

For reliable permission persistence, build the app with a valid Apple Development identity. Unsigned builds, invalid signatures, and changing bundle identifiers may cause macOS to forget previously granted access.

## Usage

- Left-click the menu bar QR code icon to scan immediately.
- Right-click the icon to open the app menu.
- Open the main window to view scan history and settings.
- Use `Control + Option + Command + Q` as the default global hotkey.
- Click the hotkey recorder, hold at least one modifier, and press a regular key to assign a new shortcut.
- Press `Esc` to cancel hotkey recording.

When one QR code is detected, the selected scan action is performed immediately. When several QR codes are detected, the app displays a scrollable result list before continuing.

## Scan Actions

The behavior after recognition can be changed under `Settings > Scanning`.

| Mode | Behavior |
| --- | --- |
| Open Automatically | Copies the result and opens recognized URLs in the default browser |
| Copy Only | Copies the result without opening a browser |
| Ask Every Time | Displays the result and asks whether to open or copy it |

`Open Automatically` is the default to preserve the original app behavior.

## Main Window

- **Scan History**: View recent results, copy content, and reopen previously opened links
- **Language**: Switch between Simplified Chinese and English (US)
- **Scanning**: Choose the action performed after recognition
- **Permissions**: Check access, request permission, or open System Settings
- **Hotkey**: Record a new global shortcut or restore the default
- **Startup**: Enable or disable launch at login

The app appears in the Dock and becomes the active foreground application while the main window is open. Closing the window returns it to menu bar mode.

## Language

On first launch, Simplified Chinese is selected only when the system's preferred language is Simplified Chinese. All other system languages default to English (US).

The selected language is saved and takes priority on future launches. The application name displayed by macOS also follows the system language:

- Simplified Chinese: `屏幕扫码`
- Other languages: `Screen QR Scanner`

## Privacy

Screen capture and QR code recognition run entirely on the Mac. The app does not upload screenshots, QR code contents, or scan history. When the user chooses to open a detected URL, it is passed directly to the system default browser.

## Roadmap

- Region selection for focused scanning
- Image and clipboard scanning
- Scan history search and export
- Signed and notarized macOS releases
- Native Windows client
- Automated release builds

## Contributing

Bug reports and focused pull requests are welcome. When reporting a screen capture or recognition problem, include:

- macOS version
- Mac model and processor
- Number and resolution of connected displays
- Steps needed to reproduce the issue

Do not attach screenshots containing private or sensitive information.
