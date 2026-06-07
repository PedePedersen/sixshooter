# Six Shooter

A western-style revolver cylinder spinner for picking a winner — or a loser —
among up to six players. One self-contained HTML file, fully offline, styled
like a weathered parchment poster from a frontier saloon.

Spin the cylinder: it rattles around (with sound), zooms in on the chamber
that lands on top, and announces the result. Every player gets exactly one
cartridge in their own colour; the remaining chambers stay empty. Land on a
cartridge and that player wins ("Tuco!" — bang); land on an empty chamber and
nobody does (click).

## Features

- **Players & colours** — up to six players, each with a named cartridge in
  one of 12 dusty western colours (including silver, gold, iron and brass).
- **Teams** — save, load, edit and delete named rosters (stored in
  localStorage; the app remembers your latest state between visits).
- **Elimination mode** — after each spin, choose between two icon buttons:
  spin again with all cartridges, or remove the winner's cartridge and spin
  again. Great for "who's doing the dishes" countdowns.
- **First launch** — comes pre-loaded with Blondie, Tuco and Sentenza, saved
  as the team *"The Good, the Bad & the Ugly"*.
- **Mobile-first** — portrait layout, big touch targets, no hover required,
  parchment background extending edge-to-edge (`viewport-fit=cover` with
  safe-area insets).

## Running it

Open `sixshooter.html` in any modern browser. No server, no build step, no
network access required — fonts, sounds and the background live in `assets/`.

## Building the Android APK

The Android app is a thin offline WebView wrapper around this HTML file
(portrait-only, fullscreen immersive, **no internet permission**). The
wrapper project lives in a separate repository:
[sixshooter-apk](https://github.com/PedePedersen/sixshooter-apk).

Requirements: JDK 17 and an Android SDK with platform 34 + build-tools 34.0.0.

```sh
git clone https://github.com/PedePedersen/sixshooter-apk.git
cd sixshooter-apk
echo "sdk.dir=$HOME/android-sdk" > local.properties   # point at your SDK
JAVA_HOME=/path/to/jdk17 ./gradlew assembleDebug
# → app/build/outputs/apk/debug/app-debug.apk
```

The wrapper embeds `sixshooter.html` + `assets/` as Android assets; after
changing them here, copy them into `app/src/main/assets/` in the wrapper
repo and bump `versionCode` before rebuilding. Two WebView settings are
load-bearing: `setDomStorageEnabled(true)` (localStorage on `file://`) and
`layoutInDisplayCutoutMode = SHORT_EDGES` (lets the parchment paint behind
the camera cutout).

F-Droid/IzzyOnDroid metadata lives in `fastlane/metadata/android/en-US/`.

## Asset credits

Six Shooter is a standalone app, but it borrows its visual and audio DNA
from **Gallows Creek**, a Danish western/horror text adventure by Dusty
Tales. These assets are *not* covered by the MIT license of this repository
and keep their respective origins/licenses:

| Asset | Origin |
|---|---|
| `assets/Rye-Regular.ttf` | Rye (Google Fonts, OFL) — headlines, results & cartridge stamp |
| `assets/BleedingCowboys.ttf` | Bleeding Cowboys font — retained in `assets/` but currently unused |
| `assets/OldNewspaperTypes.ttf` | Old Newspaper Types font — body text |
| `assets/paper.webp` | Gallows Creek parchment background |
| `assets/spin.mp3` | Gallows Creek revolver-spin sound |
| `assets/bang.mp3` | Gunshot sound (added for Six Shooter) |
| `assets/klik.mp3` | Empty-chamber click, derived from freesound.org #387484 by cosmicembers |

The revolver drum rendering and spin/zoom animation are adapted from
Gallows Creek's combat drum UI (same author).

## License

The code is released under the [MIT License](LICENSE) — Copyright (c) 2026
Dusty Tales. See asset credits above for the bundled fonts/sounds/images.
