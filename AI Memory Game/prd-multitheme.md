# Memory Game - Multi-Color Theme Picker Feature PRD

## 1. Executive Summary

**Feature Name:** Multi-Color Theme Picker
**Product:** Memory Game Web Application
**Platform:** Browser-based (Desktop & Mobile)
**Target Users:** All existing users; users who want to personalize the game's look
**Primary Goal:** Replace the single light/dark toggle with a picker that lets users choose from multiple color themes, with their selection persisted across sessions.

**Supersedes:** `prd-darktheme.md` — the previous binary light/dark toggle is rolled into this richer picker. Light and Dark remain available as two of the bundled themes.

---

## 2. Product Overview

### Description
The Multi-Color Theme Picker upgrades the theme system from a binary toggle to a curated menu of named color themes. Each theme is a complete palette covering background, cards, text, controls, and modals. Users open a small popover from the controls panel, pick a theme by its swatch + label, and the game applies it instantly with a smooth transition. The chosen theme is saved to `localStorage` and reapplied on subsequent visits.

### Key Value Propositions
- **Personalization** — More than light/dark; users pick a palette that matches their taste.
- **Coherent palettes** — Each theme is hand-tuned for contrast and readability across every UI element.
- **One-click switching** — Picker opens, a single click applies, popover closes.
- **Persistence** — Choice is remembered per device.
- **Backwards compatible** — Existing users with `'light'` or `'dark'` saved values keep their preference; no migration needed.

---

## 3. Goals & Objectives

### Short-term Goals
1. Ship a working theme picker with 5 bundled themes (Light, Dark, Ocean, Forest, Sunset).
2. Maintain WCAG AA contrast in every theme.
3. Preserve all existing gameplay, accessibility, and persistence behavior.

### Long-term Goals
1. Allow user-defined custom palettes.
2. Auto-detect and offer a "Match system" theme via `prefers-color-scheme`.
3. Add seasonal / limited-time themes.

---

## 4. User Stories

**U1 — Personalization-first user**
*As a* player who likes to make tools their own, *I want to* pick from several color themes, *so that* the game feels mine.

**U2 — Existing dark-mode user**
*As a* user who already uses dark mode, *I want to* keep using dark mode after the upgrade, *so that* I'm not disrupted.

**U3 — Mood-driven user**
*As a* player whose preference shifts with time of day or mood, *I want to* swap themes in one click, *so that* the switch is frictionless.

**U4 — Accessibility-first user**
*As a* user who relies on high contrast and keyboard navigation, *I want to* the picker to be fully keyboard- and screen-reader-accessible, *so that* I can use it like any other control.

---

## 5. Features & Requirements

### 5.1 Theme Picker UI

- [ ] A circular button in the controls panel (replaces the previous sun/moon toggle), labeled with a palette icon (🎨).
- [ ] Clicking the button opens a popover menu listing all available themes.
- [ ] Each menu item shows a colored swatch + the theme's display name.
- [ ] The currently active theme is marked with a checkmark and bold label.
- [ ] Clicking a theme applies it immediately and closes the menu.
- [ ] The menu closes when the user clicks outside it or presses `Escape`.
- [ ] Button has `aria-haspopup="true"` and `aria-expanded` reflecting menu state.
- [ ] Menu uses `role="menu"`; items use `role="menuitemradio"` with `aria-checked`.
- [ ] Fully keyboard-accessible: Tab to focus, Enter/Space to open, click/Enter on items, Esc to close.

### 5.2 Bundled Themes

Five themes ship in v1. Each defines a complete palette via CSS custom properties.

| Theme  | Background | Primary  | Card Back | Text     | Notes                        |
|--------|------------|----------|-----------|----------|------------------------------|
| Light  | `#f5f5f5`  | `#2196f3`| `#1976d2` | `#333333`| Default; existing look       |
| Dark   | `#121212`  | `#64b5f6`| `#333333` | `#ffffff`| Existing dark mode           |
| Ocean  | `#e0f7fa`  | `#006064`| `#00838f` | `#004d40`| Cool teal/cyan palette       |
| Forest | `#e8f5e9`  | `#2e7d32`| `#1b5e20` | `#1b3a1f`| Calm green palette           |
| Sunset | `#fff3e0`  | `#e65100`| `#bf360c` | `#3e2723`| Warm orange/brown palette    |

### 5.3 Theme Application Scope

The active theme must drive every themable element:
- [ ] Page background and body text
- [ ] Controls panel (background, shadow, stat values)
- [ ] Grid-size selector buttons (default, hover, active states)
- [ ] Card front and card back faces
- [ ] Card focus outline
- [ ] Win modal overlay and content
- [ ] Best Scores section background and text
- [ ] Theme picker button and menu (so the picker itself respects the active palette)

### 5.4 Persistence

- [ ] `localStorage` key: `memoryGameTheme`
- [ ] Valid values: `'light'`, `'dark'`, `'ocean'`, `'forest'`, `'sunset'`
- [ ] Default: `'light'` if no value saved or value is unrecognized.
- [ ] Theme is applied as a `data-theme="<id>"` attribute on `<html>`.
- [ ] If `localStorage` access throws (private mode, etc.), the theme still applies for the current session — persistence failure is non-fatal.

### 5.5 Transitions

- [ ] All themable elements transition `background-color` and `color` over `0.3s ease`.
- [ ] No layout shift or jank when switching themes.
- [ ] Theme switch is visible within 100ms.

### 5.6 Accessibility

- [ ] All bundled themes meet WCAG 2.1 AA contrast (≥ 4.5:1 for normal text).
- [ ] Focus indicators (3px outline using `--primary-color`) remain visible in every theme.
- [ ] Theme picker button is reachable via Tab and operable via Enter/Space.
- [ ] Menu items are reachable via Tab; Esc returns focus to the picker button.
- [ ] Active theme is announced via `aria-checked="true"`.

### 5.7 Backwards Compatibility

- [ ] Users with existing `memoryGameTheme = 'light'` or `'dark'` values retain their theme.
- [ ] Unknown / legacy values fall back to the default (`'light'`) without errors.
- [ ] The `[data-theme="dark"]` selector continues to work; new themes use the same attribute mechanism.

---

## 6. Technical Architecture

### Implementation Approach
- **CSS custom properties** define all themable values inside `:root` and per-theme `[data-theme="<id>"]` selectors.
- **A single `themeManager` object** in JS owns: theme registry, `localStorage` reads/writes, applying `data-theme`, building the menu, and handling open/close/select/keyboard interactions.
- The menu is built dynamically from a `THEMES` array, so adding a new theme is one entry plus one CSS block.

### Data Model

```
themeManager.THEMES = [
  { id: 'light',  label: 'Light',  swatch: '#2196f3' },
  { id: 'dark',   label: 'Dark',   swatch: '#1e1e1e' },
  { id: 'ocean',  label: 'Ocean',  swatch: '#006064' },
  { id: 'forest', label: 'Forest', swatch: '#2e7d32' },
  { id: 'sunset', label: 'Sunset', swatch: '#e65100' }
]
```

### localStorage Schema
```
memoryGameTheme: 'light' | 'dark' | 'ocean' | 'forest' | 'sunset'
```

### Browser Compatibility
- [ ] Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- [ ] Mobile Safari, Chrome Mobile
- [ ] Requires CSS custom properties, `localStorage`, CSS transitions

---

## 7. User Experience Flow

1. **Page load** — `themeManager.init()` runs; reads `memoryGameTheme` from `localStorage` (defaults to `'light'` if missing or invalid); applies `data-theme` to `<html>`; builds the picker menu.
2. **User clicks 🎨 button** — popover menu opens; `aria-expanded="true"`.
3. **User clicks a theme option** — `data-theme` updates, palette transitions over 0.3s, value saved to `localStorage`, menu closes, focus returns to the button.
4. **User presses Esc or clicks outside** — menu closes without changing theme.
5. **Subsequent visits** — saved theme is applied immediately on load.

---

## 8. Success Metrics

- [ ] Theme picker open rate ≥ 25% of new sessions in the first 2 weeks post-release.
- [ ] No drop in 7-day retention vs. pre-release baseline.
- [ ] Zero new accessibility violations in audit (axe / Lighthouse).
- [ ] Theme switch render time < 100ms on mid-range mobile.
- [ ] Net CSS size delta < 3 KB.

---

## 9. Out of Scope (v1)

- User-created / custom hex palettes
- System theme auto-detection (`prefers-color-scheme`)
- Per-device-time scheduling (e.g. dark at night)
- Sharing themes between users
- Animated / gradient theme backgrounds

---

## 10. Definition of Done

- [ ] Picker UI works on desktop and mobile.
- [ ] All 5 themes render correctly across every UI element listed in §5.3.
- [ ] Persistence verified across reloads and browser restarts.
- [ ] Keyboard + screen reader flow validated.
- [ ] WCAG AA contrast verified for all 5 themes.
- [ ] No console errors or warnings.
- [ ] Lighthouse scores unchanged or improved.

---

## 11. Risk Assessment

| Risk | Impact | Mitigation |
|------|--------|-----------|
| Contrast regressions in custom themes | Medium | Audit each palette before ship; AA-test every text/background pair. |
| Picker menu clipped on small screens | Low | Position relative to the picker container; cap `min-width`; verify on 320px viewport. |
| Legacy `memoryGameTheme` values cause errors | Low | Validate against allow-list on read; fall back silently to default. |
| Adding themes later requires CSS + JS edits in two places | Low | Document the two-file pattern; consider extracting a single source of truth in v2. |

---

## 12. Approval & Sign-off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Product Owner | | | |
| Engineering Lead | | | |
| UX/Design | | | |
| QA Lead | | | |

---

**Document Version:** 1.0
**Last Updated:** April 26, 2026
**Status:** APPROVED FOR DEVELOPMENT
