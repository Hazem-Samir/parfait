# Parfait × Natsumi — Merged Theme

## Installation

1. Put this `chrome/` folder in your Firefox profile directory.
2. In `about:config`, set `toolkit.legacyUserProfileCustomizations.stylesheets` = `true`
3. **Required**: Set `natsumi.urlbar.disabled` = `true` in `about:config`
   (this lets Parfait own the urlbar — without it, both themes fight over it)
4. Restart Firefox.

---

## How it works

**Parfait** loads first and owns layout: tabs, toolbar, urlbar, sidebar, popups.

**Natsumi** loads second and contributes: color system, glimpse, backdrop blur,
compact mode, icons, workspaces, notifications, theming engine, and all its JS scripts.

Where both themes touch the same element, the last one loaded wins. Most rules
don't actually conflict because they use different CSS custom properties.
The one real conflict — the urlbar — is resolved by the `natsumi.urlbar.disabled` pref.

---

## Required about:config pref

| Pref | Value | Why |
|---|---|---|
| `natsumi.urlbar.disabled` | `true` | **Required.** Prevents Natsumi's urlbar from fighting Parfait's. |

---

## Optional about:config prefs

### Natsumi features
| Pref | Value | Effect |
|---|---|---|
| `natsumi.theme.compact-mode` | `true` | Compact toolbar |
| `natsumi.theme.single-toolbar` | `true` | Merge tab bar + toolbar (needs `sidebar.verticalTabs`) |
| `natsumi.theme.disable-translucency` | `true` | Disable window transparency |
| `natsumi.findbar.disabled` | `true` | Use default findbar style |
| `natsumi.pip.disabled` | `true` | Use default PiP style |
| `natsumi.theme.accent-color` | e.g. `sky-blue` | Preset accent (overrides natsumi-config.css) |

Preset accent values: `sky-blue`, `turquoise`, `yellow`, `peach-orange`, `warmer-pink`, `beige`, `light-red`, `muted-pink`, `pink`, `lavender-purple`, `system`

### Parfait features
| Pref | Value | Effect |
|---|---|---|
| `parfait.toolbar.unified-sidebar` | `true` | Urlbar inside sidebar |
| `parfait.bg.accent-color` | `true` | Accent-tinted browser background |
| `parfait.blur.enabled` | `true` | Acrylic blur on background |
| `parfait.window.borderless` | `true` | No border around browser pane |
| `parfait.bg.gradient` | `true` | Gradient background (needs accent-color) |

---

## Customization

### Change accent color
Open `natsumi-config.css` and edit `--natsumi-accent-color`.
One value updates both themes.

### Parfait-specific overrides
Add to `parfait/custom.css`.

---

## File structure

```
chrome/
├── userChrome.css          ← entry point
├── userContent.css         ← page styles
├── natsumi-config.css      ← shared config (accent color, etc.)
├── README-MERGED.md        ← this file
├── parfait/                ← Parfait theme files (unmodified)
└── natsumi/
    ├── natsumi-merged.css  ← Natsumi entry point (replaces natsumi.css)
    └── ...                 ← Natsumi files (unmodified)
```
