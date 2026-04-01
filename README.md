# svg-icon-forge

> Describe an icon in words. Get a pixel-perfect SVG in any style.

A [Claude Code](https://claude.ai/code) skill that generates precise SVG icons from natural language descriptions, supporting 5 visual styles and batch generation for consistent icon sets.

## Features

- **5 Icon Styles**

  | Style | Description |
  |-------|-------------|
  | `outline` | 24px line icons, stroke-width 2 (like Lucide) |
  | `filled` | Solid fill style |
  | `duotone` | Two-tone (primary + semi-transparent secondary) |
  | `hand-drawn` | Irregular paths for a sketchy look |
  | `pixel` | Pixel art aligned to grid |

- **15 Built-in Icon Templates** — Navigation, Actions, Status, Media categories
- **SVG Optimizer** — Strips metadata, simplifies paths, ensures standards
- **Quality Standards** — viewBox 0 0 24 24, currentColor, <1KB, pixel-aligned
- **Component Wrappers** — React and Vue component code generation

## Installation

```bash
claude skill add daizhouchen/svg-icon-forge
```

## How It Works

1. Claude interprets your icon description and selects the appropriate style
2. Generates SVG using templates or custom paths
3. `scripts/optimize_svg.py` optimizes and validates the output
4. Delivers SVG file(s) with optional React/Vue component wrappers

## Manual Usage

```bash
# Optimize an SVG file
python3 scripts/optimize_svg.py input.svg -o output.svg

# Validate without modifying
python3 scripts/optimize_svg.py input.svg --validate

# Run the test suite (75 icon/style combinations)
python3 scripts/test_skill.py
```

## Icon Categories

| Category | Icons |
|----------|-------|
| Navigation | arrow_right, menu, close, search |
| Actions | edit, delete, save, share |
| Status | check, warning, error, info |
| Media | play, pause, volume |

## Trigger Phrases

- "图标" / "icon" / "SVG图标"
- "UI图标" / "生成图标集"

## Project Structure

```
svg-icon-forge/
├── SKILL.md                     # Skill definition and quality standards
├── scripts/
│   ├── optimize_svg.py          # SVG optimizer and validator
│   └── test_skill.py            # Test suite (75 combinations)
├── assets/
│   └── icon_templates.py        # 15 parameterized icon templates x 5 styles
├── references/
│   └── examples.md              # 10 icon gallery in all 5 styles
├── test_output/                 # Pre-generated sample SVGs
└── README.md
```

## Quality Guarantees

- All icons use `viewBox="0 0 24 24"`
- Colors use `currentColor` for theme adaptation
- File size < 1KB per icon
- All paths use relative coordinates where possible
- Integer coordinates for pixel alignment
- `<title>` element for accessibility

## Requirements

- Python 3.8+ (no external packages)

## Test Results

- 75/75 icon/style combinations pass all checks
- All SVGs valid XML
- All under 1KB (262-340 bytes optimized)

## License

MIT
