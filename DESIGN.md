# Renault Design System Tokens (extracted from https://getdesign.md/renault/design-md)

## Color Palette
- **Sunlight Yellow (Primary)**: `#ffed00`
- **Sunlight Yellow Pressed**: `#e6d200`
- **On‑Primary (Label)**: `#000000`
- **Surface Dark**: `#111111`
- **Surface Canvas**: `#ffffff`
- **Surface Soft**: `#f7f7f7`
- **Hairline**: `#f2f2f2`
- **Ink (Headings & Structural Text)**: `#000000`
- **Body Text**: `#222222`
- **Charcoal (Captions & Metadata)**: `#333333`
- **Mute (Secondary Text)**: `#666666`
- **Ash (Placeholder)**: `#8a8a8a`
- **Error**: `#be6464`
- **Warning**: `#f0ad4e`
- **Success**: `#8dc572`
- **Info**: `#337ab7`

## Typography
- **Display‑XL**: 56px, weight 700, line‑height 0.95 (NouvelR)
- **Display‑LG**: 40px, weight 700, line‑height 0.95 (NouvelR)
- **Title**: 24px, weight 700, line‑height 0.95 (NouvelR)
- **Subtitle**: 18px, weight 600, line‑height 1.0 (NouvelR)
- **Body**: 18px, weight 400, line‑height 1.5 (Inter Tight substitute)
- **Body‑LG**: 16px, weight 400, line‑height 1.5 (Inter Tight)
- **Body‑SM**: 14px, weight 400, line‑height 1.57 (Inter Tight)
- **Caption**: 12px, weight 400, line‑height 1.4 (Inter Tight)
- **Overline**: 10px, weight 700, line‑height 1.45 (Inter Tight)

## Button Variants
- **Primary**: Sunlight Yellow pill button (`border-radius: 2px`)
- **Primary Pressed**: Darker yellow (`#e6d200`)
- **Secondary**: Outline button (transparent background, yellow border)
- **Secondary Dark**: Black outline button
- **Pill**: Fully rounded (`border-radius: 9999px`) for sub‑nav and badges

## Forms & Inputs
- **Height**: 44px
- **Corner Radius**: 0 (borderless top/sides, single hairline bottom)
- **Focus Indicator**: 1px hairline at bottom only

## Card & Container
- **Standard Card**: Full‑bleed product photography, no rounded corners, no overlay text
- **Configurator**: Right‑hand option list with circular colour swatches (`border-radius: full`) and sticky summary footer

## Spacing Scale
- **Base Unit**: 4px
- **Section Rhythm**: 80px (drives full‑bleed band‑to‑band rhythm)
- **Breakpoints**: 4px (xxs), 8px (xs), 12px (sm), 16px (md), 20px (lg), 24px (xl), 32px (xxl), 40px (section)

## Border Radius Scale
- **Standard**: 0 (square corners)
- **Small**: 2px
- **Pill**: 9999px (fully rounded)
- **Circle**: 50% (for avatar‑style swatches)

## Elevation & Depth
- **Level 0**: Flat (no shadow)
- **Level 1**: Outline (structural border)
- **Level 2**: Colour Block (solid fill with contrast)
- **Level 3**: Dark Inversion (dark overlay for hero sections)

## Responsive Behavior
| Breakpoint | Min‑Width | Layout |
|------------|-----------|--------|
| **Desktop XL** | ≥1440px | 4‑up vehicle grid, 2‑up promo tile grid |
| **Desktop** | 1280–1439px | Container shrinks; side padding 24px |
| **Tablet Large** | 1024–1279px | 3‑up vehicle grid, 55/45 split configurator |
| **Tablet** | 768–1023px | 2‑up promo tiles, sub‑nav becomes scroll‑rail |
| **Mobile Large** | 426–767px | 2‑up vehicle grid, nav collapses to hamburger |
| **Mobile** | ≤425px | All grids 1‑up, display‑XL clamped to 40px |

## Additional Tokens
- **Success**: `#8dc572` (used for positive states)
- **Error**: `#be6464` (used for negative states)
- **Warning**: `#f0ad4e`
- **Info**: `#337ab7`

*All values are taken from the public Renault design specification at https://getdesign.md/renault/design-md and are intended for inspirational use in AI‑generated UI scaffolding.*