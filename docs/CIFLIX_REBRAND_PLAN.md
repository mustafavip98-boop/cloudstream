# CifliX — Modern Rebrand & Implementation Plan

## Product direction
CifliX is an independently branded Android media-center fork built on the upstream CloudStream codebase. Preserve the extension/provider architecture and playback capabilities while replacing the user-facing visual identity and navigation with an original modern design.

## Non-negotiable constraints
- Preserve required GPL-3.0 notices, license text, attribution, and source-availability obligations.
- Do not reuse CloudStream logos, name, screenshots, or proprietary-looking assets as CifliX branding.
- Do not bundle, advertise, or configure unauthorized copyrighted media sources. Users are responsible for choosing lawful providers and content.
- Keep upstream functionality intact until each replacement screen has feature parity and regression coverage.
- Do not claim a feature works until it builds and is tested on a device/emulator.

## Visual identity
- Product name: CifliX
- Direction: modern, premium, minimal, cinematic; distinct from CloudStream's existing layout.
- Palette: near-black / graphite surfaces, cool violet accent, restrained cyan highlights, high-contrast text.
- Shape language: rounded cards, compact metadata chips, consistent spacing, clear hierarchy.
- Typography: readable Arabic-first UI with RTL correctness and English fallback.
- Motion: subtle transitions only; respect reduced-motion and TV/low-end device constraints.

## Navigation and screens
1. Home — featured content area, Continue Watching, recently added, curated categories.
2. Discover — searchable catalog and filters.
3. Library — bookmarks, watch progress, downloads where supported.
4. Sources — installed extensions/providers, repository management, diagnostics.
5. Details — poster/backdrop, synopsis, metadata, seasons/episodes, provider actions.
6. Player — retain the existing playback engine and controls; apply CifliX styling where safe.
7. Settings — language, appearance, playback, downloads, privacy, source management, about/licenses.

## Engineering approach
- First map the existing modules, navigation graph, Compose/Views boundaries, theme system, player entry points, and extension APIs.
- Reuse upstream domain/data/playback layers; avoid rewriting stable provider and playback logic.
- Introduce a CifliX design system (colors, typography, shapes, spacing, reusable components).
- Replace screens incrementally behind stable routes; keep an escape path to upstream screens during migration.
- Keep Android TV layouts and accessibility in scope.
- Verify applicationId, app label, launcher icon, splash screen, deep links, and release signing separately.

## Delivery phases
### Phase 0 — Baseline
- Record upstream commit and fork divergence.
- Inspect Gradle modules, package/application IDs, navigation, themes, and player integration.
- Produce a clean baseline build before UI changes.

### Phase 1 — Identity foundation
- Add CifliX theme tokens and reusable components.
- Change app-facing name, icon, splash, and about screen.
- Keep license/third-party notices visible and accurate.

### Phase 2 — Main experience
- Implement Home, Discover, Library, and bottom navigation.
- Add RTL, loading, empty, error, and offline states.

### Phase 3 — Content and playback
- Redesign details and episode selection.
- Apply player skin while preserving Media3/CloudStream playback behavior.
- Verify subtitles, audio tracks, quality selection, resume, and downloads.

### Phase 4 — Sources and release
- Redesign repository/source management and settings.
- Run unit tests, lint, debug/release builds, and phone/TV smoke tests.
- Publish source and build artifacts in compliance with GPL-3.0.

## Acceptance criteria
- No CloudStream branding in normal CifliX user flows; required legal attribution remains in the licenses/about area.
- Existing extension discovery and playback continue to work.
- Arabic RTL and English LTR layouts render correctly.
- Home, details, library, sources, settings, and player have consistent CifliX styling.
- Debug APK installs and launches; core flows pass smoke tests.
- No unsupported claim of completion without a successful build and test report.

## Current status

### Completed in the first implementation pass
- Created the `ciflix/modern-redesign` working branch from the user's existing fork.
- Added CifliX project documentation and a separate implementation plan.
- Changed the Android application ID to `com.ciflix.app`.
- Replaced the adaptive launcher mark and added a legacy vector launcher icon.
- Added CifliX deep-link schemes while retaining the legacy CloudStream schemes for compatibility.
- Updated the app label, selected user-facing copy, dark palette, and violet/cyan accent colors.
- Added a CifliX wordmark to the phone home header and refined hero height, poster radius, card spacing, and bottom-navigation labels.
- Redirected the in-app update checker to the user's own repository so it no longer points at upstream CloudStream releases.
- Added a branch-specific GitHub Actions workflow to build a stable debug APK and upload it as a temporary artifact.

### Verification status
- Changed Android XML files passed a structural tag-balance check.
- The branch is ahead of `master` and has no unmerged local working tree because edits were committed directly.
- A Gradle build and device/emulator smoke test have **not yet been confirmed**. Do not treat this branch as a tested APK until the CI artifact is available and core flows are checked.

### Next implementation targets
- Replace more of the current home screen structure and card hierarchy.
- Redesign details, library, source management, and settings screens.
- Validate extension loading, playback, subtitles, downloads, Android TV, and Arabic RTL.
- Build, install, and smoke-test the debug APK before preparing a release.
