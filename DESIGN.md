---
name: Lush Nutrition
colors:
  surface: '#fff8f8'
  surface-dim: '#ecd4db'
  surface-bright: '#fff8f8'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#fff0f3'
  surface-container: '#ffe8ef'
  surface-container-high: '#fbe2e9'
  surface-container-highest: '#f5dce4'
  on-surface: '#25181d'
  on-surface-variant: '#594046'
  inverse-surface: '#3c2c32'
  inverse-on-surface: '#ffecf1'
  outline: '#8d7076'
  outline-variant: '#e1bec5'
  surface-tint: '#b90a5a'
  primary: '#b90a5a'
  on-primary: '#ffffff'
  primary-container: '#ff4d8d'
  on-primary-container: '#5b0028'
  inverse-primary: '#ffb1c4'
  secondary: '#9f402f'
  on-secondary: '#ffffff'
  secondary-container: '#ff8a73'
  on-secondary-container: '#752214'
  tertiary: '#bb0253'
  on-tertiary: '#ffffff'
  tertiary-container: '#ff4f85'
  on-tertiary-container: '#5b0024'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#ffd9e0'
  primary-fixed-dim: '#ffb1c4'
  on-primary-fixed: '#3f001a'
  on-primary-fixed-variant: '#8f0043'
  secondary-fixed: '#ffdad3'
  secondary-fixed-dim: '#ffb4a5'
  on-secondary-fixed: '#3f0400'
  on-secondary-fixed-variant: '#7f2a1a'
  tertiary-fixed: '#ffd9df'
  tertiary-fixed-dim: '#ffb1c1'
  on-tertiary-fixed: '#3f0017'
  on-tertiary-fixed-variant: '#90003e'
  background: '#fff8f8'
  on-background: '#25181d'
  surface-variant: '#f5dce4'
typography:
  display-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 48px
    fontWeight: '800'
    lineHeight: 56px
    letterSpacing: -0.03em
  display-lg-mobile:
    fontFamily: Plus Jakarta Sans
    fontSize: 36px
    fontWeight: '800'
    lineHeight: 44px
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
    letterSpacing: -0.02em
  headline-lg-mobile:
    fontFamily: Plus Jakarta Sans
    fontSize: 26px
    fontWeight: '700'
    lineHeight: 34px
    letterSpacing: -0.015em
  headline-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 22px
    fontWeight: '700'
    lineHeight: 30px
    letterSpacing: -0.01em
  headline-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 26px
  body-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  body-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 18px
  label-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 20px
    letterSpacing: 0.01em
  label-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 12px
    fontWeight: '600'
    lineHeight: 16px
    letterSpacing: 0.02em
  label-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 11px
    fontWeight: '700'
    lineHeight: 14px
    letterSpacing: 0.04em
  metric-val:
    fontFamily: Plus Jakarta Sans
    fontSize: 28px
    fontWeight: '800'
    lineHeight: 32px
    letterSpacing: -0.02em
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 1rem
  gutter-desktop: 1.5rem
  margin: 1rem
  margin-tablet: 2rem
  margin-desktop: 3rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 1rem
  space-lg: 1.5rem
  space-xl: 2rem
---

## Brand & Style

The design system embodies a fresh, welcoming, and vitality-focused daily nutrition companion. Built for health-conscious individuals, fitness enthusiasts, and mindful eaters, the interface avoids clinical or restrictive aesthetic tropes in favor of an uplifting, nourishing digital environment. The tone balances playful clarity with scientific precision, transforming daily macro tracking from a chore into an intuitive micro-ritual.

### Aesthetic Direction
A modern hybrid of **Organic Minimalism** and **Tactile Soft Glass**. Surfaces are warm, clean, and card-centric, relying on delicate warm blush undertones, generous breathing room, and soft tactile responses. Macro visualizations leverage juicy, high-clarity pastels rather than harsh primary primaries, fostering calm and motivation.

## Colors

The color palette centers on radiant rose-tinted tones paired with functional pastel markers for daily macronutrient tracking.

### Semantic & Macro Palette
- **Primary (`#FF4D8D` - Vibrant Strawberry):** Core brand actions, progress fill highlights, main interactive buttons, and high-priority milestones.
- **Secondary (`#FF8A73` - Peach Coral / Carbs):** Dedicated to carbohydrate tracking, fiber counts, energy bars, and warm supportive tags.
- **Tertiary (`#E02E6C` - Rose Cherry / Protein):** Dedicated to protein tracking, muscle-target indicators, and essential milestones.
- **Fats Indicator (`#F4A8B9` - Soft Warm Blush):** Dedicated to healthy fats, lipid breakdowns, and soft gauge tracks.
- **Neutral Core (`#544349` - Deep Fig / Slate Cocoa):** High-contrast body typography, subtle boundary lines, and icons. Avoids harsh pure blacks (`#000000`).

### Surface Hierarchy
- **Canvas Base:** `#FFF5F7` (Morning Mist Blush) creates a soft, luminous foundation.
- **Surface Level 1 (Cards):** `#FFFFFF` pure white, offering crisp card isolation against the blush backdrop.
- **Surface Level 2 (Nested / Inputs):** `#FDF2F4` for active input fields, nested breakdown bars, and chip containers.
- **Border / Divider:** `rgba(255, 77, 141, 0.12)` providing hairline structure without visual weight.

## Typography

**Plus Jakarta Sans** provides a geometric yet friendly structure with open apertures and clean terminals. It supports both high-impact data visualization (e.g., calorie counters, macro gram targets) and comfortable readability for ingredient lists and nutritional advice.

- **Numerics & Macro Metrics:** Display numbers and values (`metric-val`) leverage tabular figures and bold weights (`700` and `800`) to avoid layout jitter during live calculation updates.
- **Scale Continuity:** Mobile breakpoints compress display and headline tiers dynamically to prevent broken word wraps on calorie breakdowns and meal names.

## Layout & Spacing

The system implements a fluid, mobile-first responsive structure optimized for rapid thumb actions that scales into an organized multi-pane dashboard on wide displays.

### Form Factor Adaptations
- **Mobile (< 768px):** Single-column layout. Top summary card houses the active daily calorie progress ring and macro pillars. Vertical stack for food logs, meal groupings, and search fields. Margins are locked to `margin` (16px) with 12px gaps between interactive cards.
- **Tablet (768px - 1024px):** 8-column fluid grid. Daily overview locks into a cohesive top grid banner; food log entries split into two symmetrical columns (e.g., Breakfast/Lunch on left, Dinner/Snacks on right).
- **Desktop (> 1024px):** 12-column fixed-max layout (max content container: 1200px centered). Left 4 columns display the sticky Daily Summary, Target Calculator, and Water Log; right 8 columns display the interactive Food Logging Diary, Macro Analysis, and Recipe Builder.

## Elevation & Depth

Visual depth is achieved through **ambient warm-tinted diffusion** and soft tonal layering rather than cold, dark drop shadows.

- **Level 0 (Canvas):** Flat `#FFF5F7`.
- **Level 1 (Card & Content Blocks):** Pure `#FFFFFF` surface accompanied by a diffused rose glow shadow: `0 8px 24px -4px rgba(255, 77, 141, 0.08), 0 2px 6px -1px rgba(84, 67, 73, 0.03)`. Perimeter finished with an ultra-fine border: `1px solid rgba(255, 77, 141, 0.08)`.
- **Level 2 (Floating Action / Sticky Bottom Bar):** Elevated above content scrolling with `0 12px 32px -4px rgba(224, 46, 108, 0.16)`. Optional backdrop blur: `backdrop-filter: blur(16px); background: rgba(255, 255, 255, 0.88)`.
- **Level 3 (Modal Sheets & Food Search Pickers):** Smooth slide-over sheet elevated with `0 24px 48px -8px rgba(84, 67, 73, 0.14)`.

## Shapes

The geometric architecture is built on friendly, approachable curves (`roundedness: 2`).

- **Cards & Summary Surfaces:** 16px (`1rem`) border radius on mobile, expanding to 20px on desktop cards to project a soft, welcoming demeanor.
- **Buttons, Inputs & Metric Badges:** 12px to 16px pill-adjacent curves (`rounded-lg` / `rounded-xl`), creating comfortable touch points.
- **Macro Progress Tracks & Circular Rings:** Fully rounded caps (`stroke-linecap: round`) and 9999px pill tracks to reinforce organic health and vitality.

## Components

### Buttons
- **Primary Action (Add Food, Save Target):** Solid `#FF4D8D` background with white label text, `font-weight: 700`, 48px height. On hover/active, transitions to `#E02E6C` with slight downward scale (`transform: scale(0.98)`).
- **Secondary (Quick Add / Edit):** `#FDF2F4` background, `#FF4D8D` label text, no border. Focus ring applies a 2px offset in `#FF4D8D`.
- **Icon Button:** 40x40px rounded circle with soft rose background and `#FF4D8D` icon fill.

### Macro Progress Indicators & Rings
- **Total Calorie Radial Meter:** Outer circular gauge with track `#FDF2F4` and fill `#FF4D8D`. Center displays `metric-val` remaining calories and a small label (`label-sm`).
- **Macro Distribution Bars:** Segmented linear bars with 8px height and rounded ends.
  - Carbs: `#FF8A73` (Peach Coral)
  - Protein: `#E02E6C` (Rose Cherry)
  - Fats: `#F4A8B9` (Soft Warm Blush)
  - Each item displays the current gram counter beside target totals (e.g., `120g / 150g`).

### Food & Nutrition Cards
- Built on Level 1 white surfaces with 16px padding.
- Food entry row displays food item title, serving size descriptor in `body-sm`, and macro pills on the right side.
- Swipe or hover reveals quick adjustment steppers (`+`, `-`) and delete triggers.

### Chips & Meal Tags
- 32px height, pill-shaped (`9999px` radius).
- **Unselected:** `#FDF2F4` background with `#544349` text.
- **Selected:** `#FF4D8D` background with `#FFFFFF` bold text and subtle shadow.

### Input Fields & Steppers
- 48px height, rounded-lg (12px).
- Inactive state uses `#FDF2F4` fill with subtle border `1px solid rgba(255, 77, 141, 0.15)`.
- Active focus state transitions background to `#FFFFFF` with `2px solid #FF4D8D` ring and an ambient rose shadow glow.
- Numeric quantity steppers feature circular `+` and `–` touch pads flanking a centered bold value.

### Checkboxes & Segmented Toggles
- Custom rounded-md (6px) checkbox with `#FF4D8D` fill and crisp white checkmark upon selection.
- Macro/Calorie unit segmented switches (e.g., `kcal` vs. `kJ`, `g` vs. `%`) utilize a pill container `#FDF2F4` with a smooth white sliding thumb element.