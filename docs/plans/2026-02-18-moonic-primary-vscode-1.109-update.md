# Moonic Primary Theme Update - VSCode 1.109 API

**Date:** 2026-02-18  
**Theme:** moonic-primary.json  
**Target VSCode Version:** 1.109.0+

## Summary

Update moonic-primary.json to support the latest VSCode 1.109 theme API by adding missing color keys and re-introducing semantic highlighting to work alongside TextMate token colors.

## Current State Analysis

- **Existing color keys:** 383
- **Missing keys identified:** 157 (from VSCode 1.109 API)
- **Current structure:** colors + tokenColors (no semantic highlighting)
- **Last semantic commit:** 68dc995 (subsequently removed in d13f8c9)

## Design Decisions

### 1. Missing Color Keys (Priority Tiers)

#### Tier 1 - Critical UI Elements (25 keys)
High-impact additions for modern VSCode features:

| Category | Keys |
|----------|------|
| Activity Badges | `activityErrorBadge.*`, `activityWarningBadge.*` (4 keys) |
| List/Tree | `list.activeSelectionIconForeground`, `list.filterMatch*`, `list.focus*`, `list.dropBetweenBackground` (7 keys) |
| Inlay Hints | `editorInlayHint.*` (6 keys for type/parameter hints) |
| Tab Improvements | `tab.hover*`, `tab.selected*`, `tab.dragAndDropBorder` (8 keys) |

#### Tier 2 - Modern Editor Features (35 keys)
Enhancements for current editing experience:

| Category | Keys |
|----------|------|
| Multi-Cursor | `editorMultiCursor.*` (4 keys) |
| Word Highlight | `editor.wordHighlight*Border`, `editor.wordHighlightText*` (5 keys) |
| Bracket Guides | `editorBracketPairGuide.background*` (6 inactive colors) |
| Selection | `editor.selectionForeground`, `editor.selectionHighlightBorder` (2 keys) |
| Symbol Highlight | `editor.symbolHighlight*` (2 keys) |
| Overview Ruler | `editorOverviewRuler.background`, `wordHighlightTextForeground`, `commentDraftForeground` (3 keys) |
| Error/Warning | `editorError.*`, `editorWarning.*`, `editorInfo.*` backgrounds/borders (9 keys) |
| Problems Icons | `problemsErrorIcon.*`, `problemsWarningIcon.*`, `problemsInfoIcon.*` (3 keys) |

#### Tier 3 - Nice-to-Have Polish (30 keys)
Additional UI consistency:
- Checkbox and radio button colors
- Button secondary styles
- Toolbar hover states
- Extension icon colors
- Search editor colors
- Tree table styling

#### Tier 4 - Low Priority (67 keys)
Remaining less commonly used keys for complete coverage.

### 2. Semantic Highlighting Design

**Goal:** Re-introduce semantic highlighting that complements TextMate tokenColors.

**Structure:**
```json
{
  "semanticHighlighting": true,
  "semanticTokenColors": {
    "class": "#0db9d7",
    "interface": "#0db9d7",
    "enum": "#9a7ecc",
    "enumMember": "#d4aa6a",
    "struct": "#0db9d7",
    "type": "#0db9d7",
    "typeParameter": "#9a7ecc",
    "function": "#7aa2f7",
    "method": "#7aa2f7",
    "variable": "#c0caf5",
    "variable.readonly": "#a9b1d6",
    "variable.defaultLibrary": "#0db9d7",
    "parameter": "#f7768e",
    "property": "#7aa2f7",
    "property.readonly": "#a9b1d6",
    "namespace": "#0db9d7",
    "label": "#c0caf5",
    "event": "#e0af68",
    "macro": "#bb9af7",
    "decorator": "#bb9af7",
    "modifier": "#bb9af7",
    "operator": "#89ddff",
    "comment": "#7a85a8",
    "string": "#85d0b7",
    "number": "#c0768e",
    "regexp": "#b4f9f8",
    "keyword": "#bb9af7",
    "selfKeyword": "#f7768e"
  }
}
```

**Rationale:**
- Uses existing Moonic palette colors (no new colors introduced)
- Semantic tokens provide language-server accurate highlighting
- TextMate provides base coverage, semantic adds precision
- Works for TypeScript, JavaScript, Java, and other supported languages

### 3. Color Derivation Strategy

All new color keys will use existing Moonic palette colors:

**Core Palette:**
- Background: `#0e131b`
- Foreground: `#a9b1d6`
- Muted: `#8b90ab`
- Primary accent: `#3d59a1`
- Secondary accent: `#9a7ecc` (purple)
- Blue: `#7aa2f7`
- Cyan: `#0db9d7`
- Teal: `#41a6b5`
- Green: `#80a856`
- Yellow: `#d4aa6a`
- Red: `#db4b4b`
- Error: `#c0768e`

**Mapping Rules:**
1. Error states → `#db4b4b` or `#c0768e`
2. Warning states → `#d4aa6a`
3. Info states → `#0db9d7`
4. Backgrounds → Alpha variants of `#0e131b` or `#1c1d29`
5. Borders → `#3d59a1` with alpha or `#545c7e33`

## Implementation Phases

### Phase 1: Tier 1 + Tier 2 Color Keys
Add ~60 critical and modern editor color keys.

### Phase 2: Semantic Highlighting
Add `semanticHighlighting: true` and comprehensive `semanticTokenColors`.

### Phase 3: Tier 3 Polish (Optional)
Add remaining 30 nice-to-have keys if needed.

## Success Criteria

- [ ] All Tier 1 and Tier 2 color keys added
- [ ] Semantic highlighting enabled with comprehensive token mapping
- [ ] Colors derived from existing Moonic palette
- [ ] No visual regressions in existing theme
- [ ] Theme validates against VSCode 1.109 schema

## References

- VSCode Theme Color Reference: https://code.visualstudio.com/api/references/theme-color
- Semantic Highlighting Guide: https://code.visualstudio.com/api/language-extensions/semantic-highlight-guide
- Previous semantic commit: 68dc995
