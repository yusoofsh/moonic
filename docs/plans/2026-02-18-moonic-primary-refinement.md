# Moonic Primary Theme Refinement Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Refine the Moonic Primary theme with conservative improvements: normalize colors, fix contrast issues, add missing modern UI tokens.

**Architecture:** Direct edits to the JSON theme file. No build step or code generation—just precise modifications to color values and token additions.

**Tech Stack:** VS Code theme JSON, manual testing in VS Code

---

## Task 1: Normalize Color Case

**Files:**
- Modify: `themes/moonic-primary.json`

**Step 1: Find uppercase color values**

Search for uppercase hex values in the file.

**Step 2: Replace uppercase with lowercase**

Change these values:
- Line 14: `"#fff"` → `"#ffffff"`
- Line 24: `"#3d59a1AA"` → `"#3d59a1aa"`
- Line 149: `"#3d59a1DD"` → `"#3d59a1dd"`
- Line 168: `"#3d59a144"` → `"#3d59a144"` (already lowercase)
- Line 248: `"#515c7e40"` → `"#515c7e40"` (already lowercase)
- Line 541: `"#C0CAF5"` → `"#c0caf5"`
- Line 648: `"#C0CAF5"` → `"#c0caf5"`
- Line 661: `"#C0CAF5"` → `"#c0caf5"`
- Line 667: `"#C0CAF5"` → `"#c0caf5"`
- Line 674: `"#C0CAF5"` → `"#c0caf5"`
- Line 715: `"#C0CAF5"` → `"#c0caf5"`
- Line 755: `"#f7768e"` → `"#f7768e"` (already lowercase)

Actually search and replace all occurrences.

**Step 3: Verify no uppercase hex remains**

Run: `grep -n "#[A-F0-9]\{3,8\}" themes/moonic-primary.json | grep -v "[a-f]"`
Expected: No output (no uppercase hex found)

**Step 4: Commit**

```bash
git add themes/moonic-primary.json
git commit -m "style(theme): normalize all hex colors to lowercase"
```

---

## Task 2: Fix Low Contrast UI Elements

**Files:**
- Modify: `themes/moonic-primary.json:120,143,87`

**Step 1: Update editorLineNumber.foreground**

```json
"editorLineNumber.foreground": "#5e6888"
```

**Step 2: Update editorWhitespace.foreground**

```json
"editorWhitespace.foreground": "#5e6888"
```

**Step 3: Update editorCodeLens.foreground**

```json
"editorCodeLens.foreground": "#697090"
```

**Step 4: Test in VS Code**

Open VS Code with theme, check:
1. Line numbers are more visible
2. Whitespace characters (View → Render Whitespace) are visible
3. CodeLens hints (reference counts) are readable

**Step 5: Commit**

```bash
git add themes/moonic-primary.json
git commit -m "fix(theme): improve contrast for line numbers, whitespace, and codelens"
```

---

## Task 3: Add Missing Modern UI Tokens

**Files:**
- Modify: `themes/moonic-primary.json`

**Step 1: Add editorInlineSuggest tokens**

Insert after line ~327 (after existing inlineChat tokens):

```json
"editorInlineSuggest.background": "#1c1d29",
"editorInlineSuggest.border": "#3d59a1",
"editorInlineSuggest.foreground": "#a9b1d6",
"editorInlineSuggest.highlightForeground": "#bb9af7",
```

**Step 2: Add editorInlineEdit tokens**

Insert after inlineSuggest tokens:

```json
"editorInlineEdit.background": "#0E131B",
"editorInlineEdit.border": "#3d59a1",
"editorInlineEdit.originalBackground": "#db4b4b22",
"editorInlineEdit.modifiedBackground": "#41a6b515",
"editorInlineEdit.originalBorder": "#db4b4b",
"editorInlineEdit.modifiedBorder": "#41a6b5",
```

**Step 3: Add inlineProgress token**

```json
"inlineProgress.background": "#3d59a1",
```

**Step 4: Add chat.agent tokens**

```json
"chat.agent.background": "#3d59a1",
"chat.agent.foreground": "#ffffff",
```

**Step 5: Add multiDiffEditor tokens**

```json
"multiDiffEditor.headerBackground": "#0E131B",
"multiDiffEditor.background": "#0E131B",
"multiDiffEditor.border": "#3d59a140",
```

**Step 6: Add missing scmGraph colors**

Ensure these exist (they may already be there):

```json
"scmGraph.foreground6": "#bb7a61",
"scmGraph.foreground7": "#9a7ecc",
"scmGraph.foreground8": "#41a6b5",
```

**Step 7: Verify JSON is valid**

Run: `python3 -m json.tool themes/moonic-primary.json > /dev/null && echo "Valid JSON"`
Expected: "Valid JSON"

**Step 8: Commit**

```bash
git add themes/moonic-primary.json
git commit -m "feat(theme): add modern UI tokens for inline suggestions, edits, and chat agents"
```

---

## Task 4: Add Missing Semantic Token Colors

**Files:**
- Modify: `themes/moonic-primary.json` (tokenColors array)

**Step 1: Add semantic token colors to end of tokenColors array**

Add these entries before the closing `]`:

```json
{
  "name": "Default Library",
  "scope": ["support.variable.defaultLibrary", "support.function.defaultLibrary", "support.class.defaultLibrary"],
  "settings": {
    "foreground": "#0db9d7"
  }
},
{
  "name": "Readonly Variables",
  "scope": ["variable.other.constant", "variable.other.readonly"],
  "settings": {
    "foreground": "#c0768e"
  }
},
{
  "name": "Type Parameters",
  "scope": ["entity.name.type.parameter", "meta.type.parameters entity.name.type"],
  "settings": {
    "foreground": "#9a7ecc"
  }
},
{
  "name": "Self/This Keyword",
  "scope": ["variable.language.this", "variable.language.self", "variable.language.special"],
  "settings": {
    "foreground": "#f7768e",
    "fontStyle": "italic"
  }
}
```

**Step 2: Verify JSON validity**

Run: `python3 -m json.tool themes/moonic-primary.json > /dev/null && echo "Valid JSON"`
Expected: "Valid JSON"

**Step 3: Test semantic highlighting**

Open a TypeScript or Python file and verify:
- Built-in methods (console.log, Array.from) have distinct color
- const/readonly variables are colored differently
- Generic type parameters are distinct
- this/self keywords are italicized

**Step 4: Commit**

```bash
git add themes/moonic-primary.json
git commit -m "feat(theme): add semantic highlighting for defaultLibrary, readonly, typeParameters, selfKeyword"
```

---

## Task 5: Final Verification

**Step 1: Full JSON validation**

Run: `python3 -m json.tool themes/moonic-primary.json > /dev/null && echo "Valid JSON" || echo "Invalid JSON"`
Expected: "Valid JSON"

**Step 2: Compare file size**

Run: `wc -l themes/moonic-primary.json`
Expected: ~1500 lines (original was ~1440, +60 for new tokens)

**Step 3: Visual smoke test in VS Code**

1. Reload VS Code window
2. Select Moonic Primary theme
3. Open a file with various syntax elements
4. Trigger Copilot inline suggestion (Ctrl+Enter) to test new tokens
5. Check that no errors appear in VS Code DevTools (Help → Toggle Developer Tools)

**Step 4: Update CHANGELOG**

Add entry to CHANGELOG.md under "Unreleased":

```markdown
## [Unreleased]

### Fixed
- Improved contrast for line numbers, whitespace characters, and CodeLens

### Added
- Support for modern VS Code features: inline suggestions, inline edits, Copilot chat agents
- Semantic highlighting for defaultLibrary, readonly variables, type parameters, and self/this keywords

### Changed
- Normalized all color values to lowercase for consistency
```

**Step 5: Commit CHANGELOG**

```bash
git add CHANGELOG.md
git commit -m "docs: update changelog with theme improvements"
```

---

## Summary of Changes

| Area | Changes |
|------|---------|
| **Consistency** | All 1400+ hex colors normalized to lowercase |
| **Accessibility** | 3 contrast improvements (line numbers, whitespace, codelens) |
| **Modern Features** | 15+ new UI tokens for VS Code 1.109+ features |
| **Semantics** | 4 new semantic highlighting categories |

**Files Modified:**
- `themes/moonic-primary.json`
- `CHANGELOG.md`

**Estimated Total Time:** 45 minutes
