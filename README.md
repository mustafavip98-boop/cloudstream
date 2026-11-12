# CifliX

**CifliX is a modern Android media-center project built as a branded derivative of the open-source CloudStream codebase.** It keeps the extension-based provider architecture and playback foundation while introducing a separate CifliX identity and a redesigned user experience.

> This repository does not bundle media catalogs or video sources. Users should add only providers and content they are legally permitted to access.

## Project direction

- Product identity: CifliX
- Platform: Android phones and Android TV
- Language and build: Kotlin, Gradle
- Existing playback foundation: AndroidX Media3
- Provider architecture: compatible with supported CloudStream extensions
- UI direction: modern dark surfaces, violet and cyan accents, refreshed poster cards, and CifliX navigation

## Current development branch

The active redesign work is in:

`ciflix/modern-redesign`

See [the implementation plan](docs/CIFLIX_REBRAND_PLAN.md).

## Build locally

Requirements:
- JDK 17
- Android SDK for the compile SDK configured in `gradle/libs.versions.toml`

Build a debug APK:

```bash
chmod +x ./gradlew
./gradlew assembleStableDebug
```

The APK is generated under:

`app/build/outputs/apk/stable/debug/`

A GitHub Actions workflow builds this branch and uploads a temporary debug APK artifact after successful completion.

## Licensing and attribution

CifliX is a derivative of [CloudStream](https://github.com/recloudstream/cloudstream). The upstream project is distributed under **GNU General Public License v3.0**. This repository retains the upstream license and notices. Changes and redistributed builds must continue to comply with GPL-3.0, including providing the corresponding source code and preserving required copyright and license notices.

CifliX is an independent project and is not an official CloudStream release or endorsed by the upstream maintainers.

## Responsible use

CifliX is a media-center application, not a distributor of copyrighted media. Do not add or distribute extensions that provide unauthorized access to copyrighted works. Respect the laws and terms that apply in your location.
