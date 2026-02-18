# Moonic Primary Theme — Conservative Refinement Design

**Date:** 2026-02-18  
**Scope:** Moonic Primary (dark) theme improvements  
**Approach:** Conservative refinement preserving existing aesthetic

---

## Goals

1. Fix critical contrast issues affecting readability
2. Add missing UI tokens for modern VS Code features
3. Normalize color formatting inconsistencies
4. Preserve the existing visual identity

## Success Criteria

- All text meets WCAG AA contrast (4.5:1 for normal, 3:1 for large)
- No missing semantic highlighting for common languages
- All color values use consistent casing (lowercase hex)
- Modern features (Copilot inline suggestions, inline edits) have appropriate theming

---

## Issues Identified

### Issue A: Color Case Inconsistency
Mixed `#fff` vs `#ffffff`, `#AA` vs `#aa`. All colors should be lowercase for consistency.

### Issue B: Low Contrast UI Elements
| Element | Current | Contrast | Status | Proposed | New Contrast |
|---------|---------|----------|--------|----------|--------------|
| `editorWhitespace.foreground` | `#4e5575` | 2.8:1 | Fails WCAG | `#5e6888` | 3.2:1 |
| `editorLineNumber.foreground` | `#4e5575` | 2.8:1 | Fails WCAG | `#5e6888` | 3.2:1 |
| `editorCodeLens.foreground` | `#5e6888` | 3.2:1 | Fails WCAG AA | `#697090` | 3.8:1 |

### Issue C: Missing Modern UI Tokens
Critical gaps for VS Code 1.109+:

- `editorInlineSuggest.*` — inline completions (Copilot)
- `editorInlineEdit.*` — Next Edit Suggestions
- `inlineProgress.*` — AI processing indicators
- `chat.agent.*` — AI agent colors
- `multiDiffEditor.*` — multi-file diff view
- `scmGraph.*` — additional graph colors

### Issue D: Semantic Highlighting Gaps
Missing support for:

- `*.defaultLibrary` — built-in APIs
- `*.readonly` — immutable variables
- `*.typeParameter` — generics
- `*.selfKeyword` — Rust, Python self/this

---

## Color Palette (Preserved)

Core palette unchanged:

| Color | Hex | Usage |
|-------|-----|-------|
| Background | `#0E131B` | Editor, UI chrome |
| Primary accent | `#3d59a1` | Buttons, active states |
| Secondary accent | `#9a7ecc` | Active line numbers |
| Success | `#41a6b5` | Passing tests, info |
| Warning | `#c49a5a` | Warnings, modified |
| Error | `#db4b4b` | Errors, deleted |
| Text primary | `#a9b1d6` | Main foreground |
| Text secondary | `#8b90ab` | Secondary text |

New colors derived from existing palette only — no new hues introduced.

---

## Implementation Plan

### Phase 1: Cleanup (5 min)
- Normalize all hex colors to lowercase
- Sort UI tokens alphabetically for maintainability

### Phase 2: Contrast Fixes (10 min)
- Update 3-5 low-contrast color values
- Test in VS Code with sample files

### Phase 3: Add Missing Tokens (20 min)
- Add ~20 modern UI tokens using existing palette
- Map semantic tokens to appropriate existing colors

### Phase 4: Validation (10 min)
- Verify theme loads without errors
- Quick visual check of key UI elements

**Total estimated time:** ~45 minutes

---

## Out of Scope (YAGNI)

- Light/Secondary theme updates (separate effort)
- Custom color generation scripts
- Automated contrast checking CI
- New color palette experimentation
- Token scoping refinements (too subjective)

---

## Rollback Plan

Theme is version-controlled; any issue can be reverted instantly via git.

---

## Approval

Design approved by: @yusoofsh  
Date: 2026-02-18
