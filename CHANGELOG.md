# Changelog

All notable updates, improvements, and fixes to Moonic.

## [0.8.3] - 2026-11-18

### Changed
- Removed the blue outline VS Code draws around the focused editor area (`focusBorder` is now transparent in all three themes). Individual inputs and buttons keep their own focus colors

## [0.8.2] - 2026-11-16

### Changed
- Moonic Light: imports and exports (`import`, `export`, `from`, `default`) are now magenta, control flow (`await`, `return`, `break`) is violet like other keywords, and imported names use the plain variable color. Previously these shared one teal with types, classes and support functions, so they were hard to tell apart
- Moonic Light bracket pair colors follow the new syntax palette (blue, violet, teal, amber, green, red) instead of olive and dark green

## [0.8.1] - 2026-11-16

### Changed
- Moonic Light syntax colors are brighter and more distinct. The 0.8.0 palette darkened every Primary hue to 7-10:1 contrast, which turned yellow into olive-brown and made keys, tags and numbers look muddy. Syntax colors now target 5-7:1 (all above 4.5:1 on white): amber tags and JSON keys, rose numbers, vivid blue properties and functions, violet keywords, teal types, green strings. Comments are lighter so they recede. Workbench colors are unchanged

## [0.8.0] - 2026-11-16

### Changed
- Moonic Light now mirrors Moonic Primary one-to-one: identical 755-key workbench color set in identical order, the same 112 TextMate rules (4 were missing) and the same 26 semantic token mappings, with each color chosen by role (surface, text, muted, accent, status) instead of copied hex
- Light chrome (sidebar, activity bar, status bar, title bar, tabs, panel) is now flat on the editor surface like Primary; Primary gains the same accent hairline Light uses between regions
- Keyboard focus is visible again in both themes (`focusBorder` and list focus outline use the accent); this reverses the outline-free choice from 0.7.0 for accessibility. Set `focusBorder` and `list.focusOutline` to transparent in `workbench.colorCustomizations` to restore the old look
- Added ~220 color keys from the current VS Code theme-color reference (diff and merge editors, status bar item states, command center, settings editor, keybinding labels, sticky scroll, quick input, debug toolbar icons, markdown alerts, terminal find and cursor, chat, welcome page)
- Fixed Primary `errorForeground` (was gray); normalized hex casing and 3-digit values in Light

### Fixed
- Light current-line highlight rendered as a heavy grey bar; it is now a soft tint
- Light is easier to read: UI text, descriptions, line numbers, whitespace, punctuation and comments are darker (UI text 8:1, muted text 6:1 on white; syntax colors stay at 5.9:1 or higher)
- Contrast raised toward WCAG AA in Primary: input, checkbox and dropdown borders (3:1), inactive panel title, comment docs, markdown separators and quotes, deleted-file decorations, SCM graph lines, git gutter bars, error badge text, command center labels
- Popups (suggest list, widgets) keep a visible border in both themes; drag-and-drop backgrounds are translucent again; find-match text is readable on its highlight in both themes
- Scrollbar slider hover and active states are now distinguishable
- Fixed `support.orther.namespace.use.php` typo in Light

### Notes
- Moonic Secondary now has the same 756 color keys as the others (plus its own extras), the 4 missing syntax rules, the semantic map and the same focus, border and contrast fixes as the others, using its own palette; its existing values are kept
- `semanticHighlighting` stays `false` in both themes (the 0.7.0 notes said otherwise). The semantic token map ships in both and applies when `editor.semanticHighlighting.enabled` is `true`
- `images/preview.jpeg` is regenerated from VS Code for the web, showing Light, Primary and Secondary

## [0.7.1] - 2026-08-05

### Changed
- Removed active tab borders entirely; active state is now indicated by background fill only
- Made find match highlight foreground translucent

## [0.7.0] - 2026-08-05

### Added
- Restored semantic highlighting (`semanticHighlighting: true`) with 26 token mappings aligned to the theme palette
- Restored ~109 modern VS Code workbench color keys accidentally dropped in the 0.6.3 release (checkbox/radio, button secondary, multi-cursor, problems/symbol icons, sticky scroll, toolbar, and more)

### Fixed
- Semantic token colors now match the tuned TextMate palette (removed clashing purple types/enums, washed-out readonly constants, purple decorators/macros)
- Active tab now has a clear background indicator and visible top border; inactive tabs are dimmed for contrast
- Activity bar active state is now clearly visible (distinct background, brighter icon and border)
- Activity bar icons, inactive panel title, and error badge contrast improved toward WCAG AA
- Made chart grid lines and editor column ruler visible (were identical to background)
- Fixed typo in PHP namespace TextMate scope (`support.orther.namespace.use.php`)
- Normalized redundant alpha values for a more consistent translucency hierarchy

### Changed
- Focus outlines and widget/toolbar/tab-hover borders removed for a cleaner, outline-free look (selection still shown via background)

## [0.6.5] - 2026-03-05

### Changed
- Added scmGraph history item remote ref color
- Updated readonly variable color
- Reverted scmGraph color changes from 0.6.4

## [0.6.4] - 2026-02-23

### Changed
- Updated scmGraph colors for improved visibility

## [0.6.3] - 2026-02-18

### Fixed
- Improved contrast for line numbers, whitespace characters, and CodeLens to meet WCAG AA standards
- Warning color contrast improved to meet WCAG AA (3.8:1 → 4.6:1)
- const/readonly variables no longer appear red (error-like)
- Types now use consistent blue-cyan from existing palette instead of clashing purple

### Added
- Support for modern VS Code features: inline suggestions, inline edits, Copilot chat agents, multiDiffEditor
- Semantic highlighting with tokens mapped to existing palette (class, interface, function, variable, etc.)
- Additional scmGraph colors for better source control visualization
- Semantic token colors for defaultLibrary, readonly variables, type parameters, and self/this keywords

### Changed
- Normalized all color values to lowercase for consistency
- Consolidated palette: merged 5 pairs of near-duplicate colors (#7dcfff→#89ddff, #0da0ba→#0db9d7, #25aac2→#41a6b5, #cc7580→#c0768e, #697090→#7a80a0)
- Reduced unique color count by ~10% through consolidation
- Improved overall color harmony by eliminating subtle variations

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
