# Zen Tabber

Unified tab styling for Zen Browser. Combines container halo borders, background tints, unloaded tab dimming, and an optional thick left color strip into one mod with three intensity levels.

## Features

- **Unloaded Tab Dimming** — grayscales and fades tabs that haven't loaded yet
- **Container Halo** — wraps container tabs in a colored border matching their container color; hides the default context line strip
- **Background Tint** — fills container tabs with a subtle wash of their container color; non-container selected tabs get a neutral gray tint
- **Colored Left Strip** — replaces the halo's thin left border with a 32px thick color bar on selected container tabs
- **Intensity** — three presets (Low / Medium / High) that scale all opacity and color-mix values together

## Installation

1. Copy `chrome.css`, `preferences.json`, and `theme.json` into your Zen Browser chrome folder.
2. Open Zen Browser's mod manager and enable **Zen Tabber**.
3. Restart Zen Browser.

The chrome folder is usually at `~/.zen/<profile>/chrome/` on Linux/macOS or `%APPDATA%\Zen\Profiles\<profile>\chrome\` on Windows.

## Toggles

| Toggle | Property | Default | What it does |
|---|---|---|---|
| Unloaded Tab Dimming | `mod.zen-tabber.unloaded-dimming` | On | Applies `grayscale(1)` and 50% opacity to tabs with `[pending="true"]` |
| Container Halo | `mod.zen-tabber.container-halo` | On | Adds a 2.5px colored border around container tabs; hides the default context line |
| Background Tint | `mod.zen-tabber.background-tint` | On | Fills container tabs with a translucent wash of their container color |
| Colored Left Strip | `mod.zen-tabber.colored-strip` | Off | Replaces the halo's left border with a 32px thick color bar on selected container tabs |
| Intensity | `mod.zen-tabber.intensity` | Medium | Scales all opacity and color-mix percentages; options: `low`, `medium`, `high` |

## Intensity Presets

| Property | Low | Medium | High |
|---|---|---|---|
| Halo selected | 60% | 90% | 100% |
| Halo unselected | 25% | 45% | 65% |
| Tint selected | 5% | 10% | 20% |
| Tint unselected | 3% | 5% | 10% |
| Neutral tint | 4% | 8% | 12% |
| Strip opacity | 10% | 20% | 35% |
| Opacity selected | 0.9 | 1.0 | 1.0 |
| Opacity unselected | 0.7 | 0.8 | 0.9 |

Medium is the default. Low is subtle enough to barely notice. High is vivid and works well with dark themes.

## Known Limitations

- CSS mods can't be unit-tested. Visual verification requires a running Zen Browser instance.
- The intensity dropdown relies on `-moz-pref()` media queries. If Zen Browser changes this API, intensity presets will stop working.
- All rules use `!important`. This mod will conflict with any other tab-styling mod that also uses `!important` on the same properties.
- Unloaded tab dimming applies `filter: grayscale(1)` to the whole tab element. This desaturates favicons and container halo colors at the same time.

## Compatibility

- Requires Zen Browser with container tab support enabled.
- Designed for vertical tab layout. The thick left strip is most visible in sidebar mode.
- Halo and tint work in horizontal tab bar mode, but the 32px left strip will look out of place there.
