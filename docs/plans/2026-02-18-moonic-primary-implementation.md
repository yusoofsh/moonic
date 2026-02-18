# Moonic Primary Theme Update - Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Update moonic-primary.json with VSCode 1.109 API color keys and re-introduce semantic highlighting.

**Architecture:** Add 60+ missing color keys organized by priority tiers, add semanticTokenColors section with 20+ token mappings using existing Moonic palette, ensure backward compatibility.

**Tech Stack:** VSCode Theme JSON, Moonic color palette

---

## Prerequisites

- Current working directory: `/Users/yusoofsh/Developer/Community/moonic`
- Source file: `themes/moonic-primary.json`
- VSCode version target: 1.109.0+
- Design document: `docs/plans/2026-02-18-moonic-primary-vscode-1.109-update.md`

---

## Task 1: Add Tier 1 - Critical UI Color Keys (25 keys)

**Files:**
- Modify: `themes/moonic-primary.json:5-389` (colors section)

**Step 1: Add Activity Error/Warning Badge Colors**

Insert after line ~14 (after activityBarBadge.foreground):

```json
    "activityErrorBadge.background": "#db4b4b",
    "activityErrorBadge.foreground": "#ffffff",
    "activityWarningBadge.background": "#d4aa6a",
    "activityWarningBadge.foreground": "#0e131b",
```

**Step 2: Add Enhanced List/Tree Colors**

Insert after list.warningForeground (around line 192):

```json
    "list.activeSelectionIconForeground": "#a9b1d6",
    "list.inactiveSelectionIconForeground": "#a9b1d6",
    "list.focusHighlightForeground": "#668ac4",
    "list.focusOutline": "#3d59a1",
    "list.focusAndSelectionOutline": "#3d59a1",
    "list.inactiveFocusBackground": "#1c1d29",
    "list.inactiveFocusOutline": "#3d59a140",
    "list.filterMatchBackground": "#3d59a166",
    "list.filterMatchBorder": "#3d59a1",
    "list.dropBetweenBackground": "#3d59a1",
```

**Step 3: Add List Filter Widget Shadow**

Insert after listFilterWidget.outline:

```json
    "listFilterWidget.shadow": "#00000033",
```

**Step 4: Add Inlay Hint Colors**

Insert after editorLightBulbAutoFix.foreground (around line 118):

```json
    "editorLightBulbAi.foreground": "#bb9af7",
    "editorInlayHint.background": "#1c1d29",
    "editorInlayHint.foreground": "#8b90ab",
    "editorInlayHint.typeForeground": "#0db9d7",
    "editorInlayHint.typeBackground": "#1c1d29",
    "editorInlayHint.parameterForeground": "#f7768e",
    "editorInlayHint.parameterBackground": "#1c1d29",
```

**Step 5: Add Enhanced Tab Colors**

Insert after tab.unfocusedInactiveForeground (around line 283):

```json
    "tab.unfocusedActiveBackground": "#0e131b",
    "tab.selectedBorderTop": "#3d59a1",
    "tab.selectedBackground": "#0e131b",
    "tab.selectedForeground": "#a9b1d6",
    "tab.dragAndDropBorder": "#3d59a1",
    "tab.unfocusedInactiveBackground": "#0e131b",
    "tab.hoverBackground": "#1c1d29",
    "tab.unfocusedHoverBackground": "#1c1d29",
    "tab.hoverForeground": "#a9b1d6",
    "tab.unfocusedHoverForeground": "#a9b1d6",
    "tab.hoverBorder": "#3d59a140",
    "tab.unfocusedHoverBorder": "#3d59a140",
    "tab.unfocusedActiveModifiedBorder": "#3d59a1",
    "tab.unfocusedInactiveModifiedBorder": "#3d59a140",
```

**Step 6: Add Minimap Colors**

Insert after minimapGutter.modifiedBackground (around line 211):

```json
    "minimap.findMatchHighlight": "#3d59a166",
    "minimap.selectionHighlight": "#9a7ecc66",
    "minimap.errorHighlight": "#db4b4b",
    "minimap.warningHighlight": "#d4aa6a",
    "minimap.background": "#0e131b",
    "minimap.selectionOccurrenceHighlight": "#9a7ecc44",
    "minimap.foregroundOpacity": "#000000c0",
    "minimap.infoHighlight": "#0db9d7",
    "minimap.chatEditHighlight": "#41a6b5",
    "minimapSlider.background": "#868bc434",
    "minimapSlider.hoverBackground": "#868bc444",
    "minimapSlider.activeBackground": "#868bc454",
    "editorMinimap.inlineChatInserted": "#41a6b5",
```

**Step 7: Verify Tier 1 additions**

Run: `cat themes/moonic-primary.json | jq '.colors | keys[]' | grep -E "(activityError|activityWarning|editorInlayHint|list.focus|list.filterMatch|tab.selected|tab.hover|minimap)" | wc -l`

Expected: 25 keys found

**Step 8: Commit**

```bash
git add themes/moonic-primary.json
git commit -m "feat(theme): add Tier 1 critical UI color keys for VSCode 1.109

- Activity error/warning badges (4 keys)
- Enhanced list/tree interactions (11 keys)
- Editor inlay hints (7 keys)
- Improved tab styling (8 keys)
- Minimap enhancements (13 keys)"
```

---

## Task 2: Add Tier 2 - Modern Editor Features (35 keys)

**Files:**
- Modify: `themes/moonic-primary.json:5-389` (colors section)

**Step 1: Add Multi-Cursor Colors**

Insert after editorCursor.foreground (around line 89):

```json
    "editorMultiCursor.primary.foreground": "#9a7ecc",
    "editorMultiCursor.primary.background": "#9a7ecc40",
    "editorMultiCursor.secondary.foreground": "#7aa2f7",
    "editorMultiCursor.secondary.background": "#7aa2f740",
```

**Step 2: Add Editor Selection Enhancements**

Insert after editor.selectionBackground (around line 67):

```json
    "editor.selectionForeground": "#a9b1d6",
    "editor.selectionHighlightBorder": "#515c7e66",
```

**Step 3: Add Word Highlight Borders**

Insert after editor.wordHighlightStrongBackground (around line 71):

```json
    "editor.wordHighlightBorder": "#515c7e66",
    "editor.wordHighlightStrongBorder": "#515c7e77",
    "editor.wordHighlightTextBackground": "#515c7e33",
    "editor.wordHighlightTextBorder": "#515c7e55",
```

**Step 4: Add Symbol Highlight Colors**

Insert after editor.rangeHighlightBackground (around line 66):

```json
    "editor.symbolHighlightBackground": "#3d59a140",
    "editor.symbolHighlightBorder": "#3d59a1",
```

**Step 5: Add Hover and Range Highlight Borders**

Insert after editor.rangeHighlightBackground:

```json
    "editor.hoverHighlightBackground": "#3d59a120",
    "editor.rangeHighlightBorder": "#515c7e33",
```

**Step 6: Add Line Highlight and Placeholder**

Insert after editor.lineHighlightBackground (around line 65):

```json
    "editor.inactiveLineHighlightBackground": "#00000050",
    "editor.lineHighlightBorder": "#00000000",
    "editor.placeholder.foreground": "#7a80a0",
    "editor.compositionBorder": "#3d59a1",
```

**Step 7: Add Unicode Highlight Colors**

Insert after editorHint.foreground (around line 101):

```json
    "editorUnicodeHighlight.border": "#d4aa6a",
    "editorUnicodeHighlight.background": "#d4aa6a20",
```

**Step 8: Add Find Match Foregrounds**

Insert after editor.findMatchHighlightBackground (around line 59):

```json
    "editor.findMatchForeground": "#a9b1d6",
    "editor.findMatchHighlightForeground": "#a9b1d6",
```

**Step 9: Add Fold Placeholder**

Insert after editor.foldBackground (around line 62):

```json
    "editor.foldPlaceholderForeground": "#8b90ab",
```

**Step 10: Add Bracket Match Foreground**

Insert after editorBracketMatch.border (around line 80):

```json
    "editorBracketMatch.foreground": "#89ddff",
```

**Step 11: Add Inactive Bracket Pair Guide Colors**

Insert after editorBracketPairGuide.activeBackground6 (around line 86):

```json
    "editorBracketPairGuide.background1": "#3d59a130",
    "editorBracketPairGuide.background2": "#68b3de30",
    "editorBracketPairGuide.background3": "#9a7ecc30",
    "editorBracketPairGuide.background4": "#41a6b530",
    "editorBracketPairGuide.background5": "#80a85630",
    "editorBracketPairGuide.background6": "#d4aa6a30",
```

**Step 12: Add Editor Gutter Colors**

Insert after editorGutter.modifiedBackground (around line 100):

```json
    "editorGutter.background": "#0e131b",
    "editorGutter.modifiedSecondaryBackground": "#394b7080",
    "editorGutter.addedSecondaryBackground": "#16484680",
    "editorGutter.deletedSecondaryBackground": "#823c4180",
```

**Step 13: Add Error/Warning/Info Backgrounds and Borders**

Insert after editorError.foreground (around line 90):

```json
    "editorError.border": "#db4b4b40",
    "editorError.background": "#db4b4b20",
    "editorWarning.border": "#d4aa6a40",
    "editorWarning.background": "#d4aa6a20",
    "editorInfo.border": "#0db9d740",
    "editorInfo.background": "#0db9d720",
```

**Step 14: Add Problems Icon Colors**

Insert after peekViewTitleLabel.foreground (around line 241):

```json
    "problemsErrorIcon.foreground": "#db4b4b",
    "problemsWarningIcon.foreground": "#d4aa6a",
    "problemsInfoIcon.foreground": "#0db9d7",
```

**Step 15: Add Overview Ruler Enhancements**

Insert after editorOverviewRuler.wordHighlightStrongForeground (around line 135):

```json
    "editorOverviewRuler.background": "#0e131b",
    "editorOverviewRuler.wordHighlightTextForeground": "#515c7e44",
    "editorOverviewRuler.inlineChatInserted": "#41a6b5",
    "editorOverviewRuler.inlineChatRemoved": "#c0768e",
    "editorOverviewRuler.commentDraftForeground": "#d4aa6a",
```

**Step 16: Add Unused Code Colors**

Insert after problemsInfoIcon.foreground:

```json
    "editorUnnecessaryCode.border": "#7a80a040",
    "editorUnnecessaryCode.opacity": "#00000080",
```

**Step 17: Add Scrollbar Background**

Insert after scrollbar.shadow (around line 246):

```json
    "scrollbar.background": "#0e131b",
```

**Step 18: Verify Tier 2 additions**

Run: `cat themes/moonic-primary.json | jq '.colors | keys[]' | wc -l`

Expected: 383 + 25 (Tier 1) + 35 (Tier 2) = ~443 keys

**Step 19: Commit**

```bash
git add themes/moonic-primary.json
git commit -m "feat(theme): add Tier 2 modern editor feature colors

- Multi-cursor support (4 keys)
- Selection and word highlight borders (7 keys)
- Symbol highlight and range borders (4 keys)
- Line highlight improvements (4 keys)
- Unicode highlight (2 keys)
- Find match foregrounds (2 keys)
- Bracket enhancements (7 keys)
- Gutter improvements (4 keys)
- Error/warning/info backgrounds and borders (6 keys)
- Problems icons (3 keys)
- Overview ruler additions (5 keys)
- Unused code styling (2 keys)
- Scrollbar background"
```

---

## Task 3: Add Semantic Highlighting Section

**Files:**
- Modify: `themes/moonic-primary.json` (add new section after tokenColors)

**Step 1: Add semanticHighlighting flag**

After line 4 (`"type": "dark"`), add:

```json
  "semanticHighlighting": true,
```

**Step 2: Add semanticTokenColors section**

After the `tokenColors` array (after line 1473, before the closing `}`), add:

```json
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
```

**Step 3: Validate JSON structure**

Run: `cat themes/moonic-primary.json | jq empty`

Expected: No output (valid JSON)

**Step 4: Count semantic tokens**

Run: `cat themes/moonic-primary.json | jq '.semanticTokenColors | keys | length'`

Expected: 26

**Step 5: Commit**

```bash
git add themes/moonic-primary.json
git commit -m "feat(theme): add semantic highlighting support

- Enable semanticHighlighting: true
- Add 26 semantic token color mappings
- Map to existing Moonic palette colors
- Support for class, interface, enum, type, function,
  variable, parameter, property, namespace, decorator,
  keyword, selfKeyword, and more"
```

---

## Task 4: Add Tier 3 - Nice-to-Have Polish (30 keys)

**Files:**
- Modify: `themes/moonic-primary.json` (colors section)

**Step 1: Add Input Option Enhancements**

Insert after inputOption.activeForeground (around line 169):

```json
    "inputOption.activeBorder": "#3d59a1",
    "inputOption.hoverBackground": "#3d59a122",
```

**Step 2: Add Button Secondary Styles**

Insert after button.hoverBackground (around line 24):

```json
    "button.border": "#3d59a140",
    "button.separator": "#3d59a140",
    "button.secondaryForeground": "#a9b1d6",
    "button.secondaryBackground": "#1c1d29",
    "button.secondaryHoverBackground": "#20222c",
    "button.secondaryBorder": "#3d59a140",
```

**Step 3: Add Checkbox Colors**

Insert after button.secondaryBorder:

```json
    "checkbox.background": "#0e131b",
    "checkbox.foreground": "#a9b1d6",
    "checkbox.border": "#3d59a1",
    "checkbox.disabled.background": "#1c1d29",
    "checkbox.disabled.foreground": "#7a80a0",
    "checkbox.selectBackground": "#1c1d29",
    "checkbox.selectBorder": "#3d59a1",
```

**Step 4: Add Radio Button Colors**

Insert after checkbox.selectBorder:

```json
    "radio.activeForeground": "#a9b1d6",
    "radio.activeBackground": "#3d59a144",
    "radio.activeBorder": "#3d59a1",
    "radio.inactiveForeground": "#8b90ab",
    "radio.inactiveBackground": "#0e131b",
    "radio.inactiveBorder": "#3d59a140",
    "radio.inactiveHoverBackground": "#1c1d29",
```

**Step 5: Add Toolbar Colors**

Insert after radio.inactiveHoverBackground:

```json
    "toolbar.hoverBackground": "#1c1d29",
    "toolbar.hoverOutline": "#3d59a140",
    "toolbar.activeBackground": "#1c1d29",
```

**Step 6: Add Action List Colors**

Insert after toolbar.activeBackground:

```json
    "editorActionList.background": "#0e131b",
    "editorActionList.foreground": "#a9b1d6",
    "editorActionList.focusForeground": "#a9b1d6",
    "editorActionList.focusBackground": "#1c1d29",
```

**Step 7: Add Extension Icon Colors**

Insert after extensionButton.prominentHoverBackground (around line 151):

```json
    "extensionIcon.starForeground": "#d4aa6a",
    "extensionIcon.verifiedForeground": "#41a6b5",
    "extensionIcon.preReleaseForeground": "#9a7ecc",
    "extensionIcon.sponsorForeground": "#c0768e",
```

**Step 8: Add Search Editor Colors**

Insert after notificationsWarningIcon.foreground (around line 220):

```json
    "search.resultsInfoForeground": "#8b90ab",
    "searchEditor.findMatchBackground": "#3d59a166",
    "searchEditor.findMatchBorder": "#3d59a1",
    "searchEditor.textInputBorder": "#3d59a1",
```

**Step 9: Add Side by Side Editor Colors**

Insert after sideBySideEditor.verticalBorder (this is a new key):

Insert after editorPane.background (around line 136):

```json
    "sideBySideEditor.horizontalBorder": "#3d59a140",
    "sideBySideEditor.verticalBorder": "#3d59a140",
```

**Step 10: Add Tree Table Colors**

Insert after tree.indentGuidesStroke (around line 318):

```json
    "tree.inactiveIndentGuidesStroke": "#3f426040",
    "tree.tableColumnsBorder": "#3d59a140",
    "tree.tableOddRowsBackground": "#0e131b",
```

**Step 11: Add Text Formatting Colors**

Insert after textSeparator.foreground (around line 312):

```json
    "textBlockQuote.border": "#3d59a1",
    "textPreformat.background": "#1c1d29",
    "textPreformat.border": "#3d59a140",
```

**Step 12: Add Contrast Colors (for accessibility)**

Insert after sash.hoverBorder (around line 245):

```json
    "contrastActiveBorder": "#3d59a1",
    "contrastBorder": "#3d59a1",
    "disabledForeground": "#7a80a0",
```

**Step 13: Add Side Bar Sticky Scroll**

Insert after sideBarTitle.foreground (around line 259):

```json
    "sideBarTitle.background": "#0e131b",
    "sideBarTitle.border": "#0e131b",
    "sideBarStickyScroll.background": "#0e131b",
    "sideBarStickyScroll.border": "#3d59a140",
    "sideBarStickyScroll.shadow": "#00000033",
    "sideBarActivityBarTop.border": "#3d59a140",
```

**Step 14: Verify Tier 3 additions**

Run: `cat themes/moonic-primary.json | jq '.colors | keys | length'`

Expected: 383 + 25 + 35 + 30 = ~473 keys

**Step 15: Commit**

```bash
git add themes/moonic-primary.json
git commit -m "feat(theme): add Tier 3 polish colors

- Input option enhancements (2 keys)
- Button secondary styles (6 keys)
- Checkbox colors (7 keys)
- Radio button colors (7 keys)
- Toolbar colors (3 keys)
- Action list colors (4 keys)
- Extension icon colors (4 keys)
- Search editor colors (4 keys)
- Side by side editor borders (2 keys)
- Tree table colors (3 keys)
- Text formatting colors (3 keys)
- Contrast/accessibility colors (3 keys)
- Side bar sticky scroll (6 keys)"
```

---

## Task 5: Final Validation

**Step 1: Validate JSON syntax**

Run: `cat themes/moonic-primary.json | jq empty && echo "Valid JSON"`

Expected: "Valid JSON"

**Step 2: Count total color keys**

Run: `cat themes/moonic-primary.json | jq '.colors | keys | length'`

Expected: ~473 keys (original 383 + 90 new)

**Step 3: Verify semantic section exists**

Run: `cat themes/moonic-primary.json | jq 'has("semanticHighlighting")' && cat themes/moonic-primary.json | jq 'has("semanticTokenColors")'`

Expected:
```
true
true
```

**Step 4: Check for duplicate keys**

Run: `cat themes/moonic-primary.json | jq '.colors | keys' | sort | uniq -d | wc -l`

Expected: 0 (no duplicates)

**Step 5: Test in VSCode (manual)**

Open VSCode, switch to Moonic Primary theme, verify:
- No errors in Developer Tools console
- Semantic highlighting works in TypeScript files
- New UI elements display correctly

**Step 6: Commit final changes**

```bash
git add themes/moonic-primary.json
git commit -m "chore(theme): final validation for VSCode 1.109 update

Total changes:
- Added ~90 new color keys across 3 priority tiers
- Re-introduced semantic highlighting with 26 token mappings
- All colors derived from existing Moonic palette
- Validated JSON structure and theme integrity"
```

---

## Summary

This implementation plan adds comprehensive VSCode 1.109 API support to moonic-primary.json:

1. **Tier 1 (25 keys):** Critical UI elements - activity badges, inlay hints, tab improvements, minimap
2. **Tier 2 (35 keys):** Modern editor features - multi-cursor, word highlights, bracket guides, error backgrounds
3. **Tier 3 (30 keys):** Nice-to-have polish - checkboxes, radio buttons, toolbars, extension icons
4. **Semantic highlighting:** 26 token mappings for language-server accurate coloring

**Total new keys:** ~90 color keys + 26 semantic tokens
**Files modified:** 1 (themes/moonic-primary.json)
**Breaking changes:** None (additive only)
