# window_pain

A one-call Flutter helper that opens your desktop app maximized and focused. It wraps [`window_manager`](https://pub.dev/packages/window_manager) so you don't have to repeat the same window setup in every macOS, Windows and Linux app.

[pub.dev/packages/window_pain](https://pub.dev/packages/window_pain)

## Features

- `WindowPain.maximizeWindow()` initializes `window_manager`, then shows, focuses and maximizes the window once it's ready.
- Starts from a centered 1200×800 window with a normal title bar and a taskbar entry.
- Does nothing on mobile and web, so you can call it from shared startup code.

## Installation

```yaml
dependencies:
  window_pain: ^0.0.2
```

## Usage

Call it before `runApp`:

```dart
import 'package:flutter/material.dart';
import 'package:window_pain/window_pain.dart';

Future<void> main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await WindowPain.maximizeWindow();
  runApp(const MyApp());
}
```

## How it works

Everything lives in `lib/window_pain.dart`. It checks `UniversalPlatform` for Linux, Windows or macOS, builds a `WindowOptions` (1200×800, centered, transparent background, `TitleBarStyle.normal`) and uses `windowManager.waitUntilReadyToShow` to show, focus and maximize.

## Development

```sh
flutter pub get
flutter test
```

Requires Dart `^3.9.0`. Dependencies: `window_manager ^0.5.1`, `universal_platform ^1.1.0`.

## License

The `LICENSE` file currently contains placeholder text, so no license has been chosen yet.
