# Changelog

All notable updates, improvements, and fixes to Moonic.

## [Unreleased]

### Fixed
- Improved contrast for line numbers, whitespace characters, and CodeLens to meet WCAG AA standards

### Added
- Support for modern VS Code features: inline suggestions, inline edits, Copilot chat agents, multiDiffEditor
- Semantic highlighting for defaultLibrary, readonly variables, type parameters, and self/this keywords
- Additional scmGraph colors for better source control visualization

### Changed
- Normalized all color values to lowercase for consistency

## [0.6.2] - 2026-02-17

### Changed

- Normalize `Moonic Primary` colors so UI accents are derived from the theme's primary/main palette (harmonized charts, editor highlights, terminal ANSI, debug tokens, and testing icons)
- Set `scmGraph.historyItemRefColor` to the theme error red (`#db4b4b`) for improved visibility and semantic consistency

### Fixed

- Replace legacy accent values in `moonic-primary.json` with primary-derived equivalents for consistent contrast and accessibility

## [0.6.1] - 2026-02-17

### Fixed

- Refine SCM graph colors for improved visibility and consistency
- Adjust color values in Primary and Light themes for improved clarity and accessibility
- Minor theme consistency and visual tweaks

## [0.6.0] - 2026-02-17

### Added

- Chat and testing theme colors to Primary, Secondary, and Light themes

### Fixed

- Comment block documentation foreground color
- Function red color
- Variable color adjustments
- VSCode engine compatibility updated to ^1.109.0

### Changed

- Code cleanup and maintenance improvements

## [0.5.14] - 2026-02-17

### Fixed

- Improved contrast for documentation comment punctuation (accessibility enhancement)

## [0.5.13] - 2024-06-13

### Fixed

- Revert to whitish variable color

## [0.5.12] - 2024-06-10

### Fixed

- Update dependencies
- Color adjustments

## [0.5.11] - 2024-06-07

### Fixed

- Update manifest

## [0.5.10] - 2024-06-07

### Fixed

- Miscellaneous color adjustments

## [0.5.9] - 2024-06-07

### Fixed

- Miscellaneous color adjustments

## [0.5.8] - 2024-06-07

### Fixed

- Miscellaneous color adjustments

## [0.5.7] - 2024-06-07

### Fixed

- Renamed I and II to Primary and Secondary

## [0.5.6] - 2024-06-07

### Fixed

- Class color adjustment
- Removed semantic highlighting

## [0.5.5] - 2024-05-24

### Fixed

- Hover color adjustment

## [0.5.4] - 2023-12-20

### Fixed

- Vibrant object key color
- Use circle icon

## [0.5.3] - 2023-12-18

### Fixed

- Fix wrong reference on release-please-action

## [0.5.2] - 2023-12-18

### Added

- GitHub Actions workflows for release

## [0.5.1] - 2023-12-18

### Fixed

- Brighter terminal foreground color

## [0.5.0] - 2023-12-17

### Added

- Initial release
