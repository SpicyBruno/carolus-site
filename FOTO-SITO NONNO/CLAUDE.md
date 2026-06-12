# CLAUDE.md — Design System & Prototyping Rules

> **Purpose**: Canonical ruleset for consistent, scalable, and accessible design.
> Intended for use inside Figma (via plugin or reference), Claude Code, and any design-to-dev handoff workflow.
> Last updated: 2026-04-20

---

## 1. Design Tokens

Design tokens are the single source of truth. Every visual decision references a token, never a raw value.

### 1.1 Color Palette

```
# Primitives (raw scale — never reference directly in components)
color.gray.0:    #FFFFFF
color.gray.50:   #F9FAFB
color.gray.100:  #F3F4F6
color.gray.200:  #E5E7EB
color.gray.300:  #D1D5DB
color.gray.400:  #9CA3AF
color.gray.500:  #6B7280
color.gray.600:  #4B5563
color.gray.700:  #374151
color.gray.800:  #1F2937
color.gray.900:  #111827
color.gray.950:  #030712

color.brand.50:  #EEF2FF
color.brand.100: #E0E7FF
color.brand.200: #C7D2FE
color.brand.300: #A5B4FC
color.brand.400: #818CF8
color.brand.500: #6366F1
color.brand.600: #4F46E5
color.brand.700: #4338CA
color.brand.800: #3730A3
color.brand.900: #312E81

color.success:   #16A34A
color.warning:   #EAB308
color.error:     #DC2626
color.info:      #2563EB
```

```
# Semantic tokens (reference THESE in components)
color.bg.primary:       color.gray.0
color.bg.secondary:     color.gray.50
color.bg.tertiary:      color.gray.100
color.bg.inverse:       color.gray.900
color.bg.brand:         color.brand.500
color.bg.brand-subtle:  color.brand.50

color.text.primary:     color.gray.900
color.text.secondary:   color.gray.600
color.text.tertiary:    color.gray.400
color.text.inverse:     color.gray.0
color.text.brand:       color.brand.600
color.text.link:        color.brand.600
color.text.link-hover:  color.brand.700

color.border.default:   color.gray.200
color.border.strong:    color.gray.300
color.border.focus:     color.brand.500
color.border.error:     color.error

color.icon.default:     color.gray.500
color.icon.active:      color.brand.600
color.icon.disabled:    color.gray.300
```

### 1.2 Typography Scale

```
# Font families
font.family.display:    "Instrument Serif", Georgia, serif
font.family.heading:    "Satoshi", "DM Sans", sans-serif
font.family.body:       "Satoshi", "DM Sans", sans-serif
font.family.mono:       "JetBrains Mono", "Fira Code", monospace

# Size scale (rem, base = 16px)
font.size.xs:     0.75rem    /* 12px */
font.size.sm:     0.875rem   /* 14px */
font.size.base:   1rem       /* 16px */
font.size.md:     1.125rem   /* 18px */
font.size.lg:     1.25rem    /* 20px */
font.size.xl:     1.5rem     /* 24px */
font.size.2xl:    1.875rem   /* 30px */
font.size.3xl:    2.25rem    /* 36px */
font.size.4xl:    3rem       /* 48px */
font.size.5xl:    3.75rem    /* 60px */

# Line heights
font.leading.tight:    1.2
font.leading.snug:     1.35
font.leading.normal:   1.5
font.leading.relaxed:  1.65

# Font weights
font.weight.regular:   400
font.weight.medium:    500
font.weight.semibold:  600
font.weight.bold:      700
```

```
# Composite text styles (use THESE on frames and text layers)
text.display-xl:     font.family.display / font.size.5xl / font.weight.bold / font.leading.tight
text.display-lg:     font.family.display / font.size.4xl / font.weight.bold / font.leading.tight
text.heading-1:      font.family.heading / font.size.3xl / font.weight.bold / font.leading.tight
text.heading-2:      font.family.heading / font.size.2xl / font.weight.semibold / font.leading.snug
text.heading-3:      font.family.heading / font.size.xl / font.weight.semibold / font.leading.snug
text.heading-4:      font.family.heading / font.size.lg / font.weight.semibold / font.leading.snug
text.body-lg:        font.family.body / font.size.md / font.weight.regular / font.leading.relaxed
text.body-base:      font.family.body / font.size.base / font.weight.regular / font.leading.normal
text.body-sm:        font.family.body / font.size.sm / font.weight.regular / font.leading.normal
text.caption:        font.family.body / font.size.xs / font.weight.medium / font.leading.normal
text.label:          font.family.body / font.size.sm / font.weight.medium / font.leading.tight
text.overline:       font.family.body / font.size.xs / font.weight.semibold / font.leading.tight / uppercase / tracking 0.08em
text.code:           font.family.mono / font.size.sm / font.weight.regular / font.leading.normal
```

### 1.3 Spacing Scale

```
space.0:     0px
space.1:     4px
space.2:     8px
space.3:     12px
space.4:     16px
space.5:     20px
space.6:     24px
space.8:     32px
space.10:    40px
space.12:    48px
space.16:    64px
space.20:    80px
space.24:    96px
space.32:    128px
```

### 1.4 Border Radius

```
radius.none:   0px
radius.sm:     4px
radius.md:     8px
radius.lg:     12px
radius.xl:     16px
radius.2xl:    24px
radius.full:   9999px
```

### 1.5 Shadows

```
shadow.xs:     0 1px 2px rgba(0,0,0,0.05)
shadow.sm:     0 1px 3px rgba(0,0,0,0.1), 0 1px 2px rgba(0,0,0,0.06)
shadow.md:     0 4px 6px rgba(0,0,0,0.1), 0 2px 4px rgba(0,0,0,0.06)
shadow.lg:     0 10px 15px rgba(0,0,0,0.1), 0 4px 6px rgba(0,0,0,0.05)
shadow.xl:     0 20px 25px rgba(0,0,0,0.1), 0 10px 10px rgba(0,0,0,0.04)
shadow.inner:  inset 0 2px 4px rgba(0,0,0,0.06)
shadow.focus:  0 0 0 3px color.brand.200
```

### 1.6 Breakpoints

```
breakpoint.sm:    640px
breakpoint.md:    768px
breakpoint.lg:    1024px
breakpoint.xl:    1280px
breakpoint.2xl:   1440px
```

### 1.7 Z-Index Scale

```
z.base:       0
z.dropdown:   10
z.sticky:     20
z.overlay:    30
z.modal:      40
z.popover:    50
z.toast:      60
z.tooltip:    70
```

---

## 2. Layout Grid Rules

### 2.1 Column Grid

```
Mobile  (< 640px):    4 columns  / 16px gutter / 16px margin
Tablet  (640–1023px): 8 columns  / 24px gutter / 32px margin
Desktop (1024–1439px): 12 columns / 24px gutter / 64px margin
Wide    (>= 1440px):  12 columns / 32px gutter / auto margin / max-width 1280px
```

### 2.2 Spacing Rules

- Use only tokens from the spacing scale. No magic numbers.
- Vertical rhythm between sections: `space.16` minimum, `space.24` recommended.
- Vertical rhythm between related elements: `space.4` to `space.8`.
- Padding inside cards and containers: `space.6` (mobile) / `space.8` (desktop).
- Icon-to-label gap: `space.2`.
- Stack gap for form fields: `space.5`.

### 2.3 Content Width Constraints

```
content.max-width.prose:      680px    /* long-form text */
content.max-width.content:    960px    /* general content */
content.max-width.wide:       1280px   /* full-width sections */
```

---

## 3. Component Architecture

### 3.1 Naming Convention

Use a three-tier naming system in Figma:

```
Category / Component / Variant

Examples:
  Inputs / Button / Primary-Default
  Inputs / Button / Primary-Hover
  Inputs / Button / Primary-Disabled
  Inputs / TextField / Default
  Inputs / TextField / Error
  Feedback / Toast / Success
  Feedback / Toast / Error
  Navigation / Navbar / Desktop
  Navigation / Navbar / Mobile
  Data / Table / Row-Default
  Data / Table / Row-Selected
```

### 3.2 Component States

Every interactive component MUST include these states:

```
State.default
State.hover
State.active       (pressed)
State.focus        (keyboard focus — visible ring)
State.disabled
State.loading      (where applicable)
State.error        (where applicable)
State.success      (where applicable)
```

### 3.3 Component Properties in Figma

Use Figma component properties, not hidden layers:

```
Variant properties:    size, variant, state
Boolean properties:    showIcon, showBadge, showDescription
Text properties:       label, description, placeholder
Instance swap:         leadingIcon, trailingIcon, avatar
```

### 3.4 Base Component Inventory

Every design system MUST contain at minimum:

```
INPUTS
  Button          sizes: sm, md, lg | variants: primary, secondary, ghost, destructive
  IconButton      sizes: sm, md, lg
  TextField       variants: default, error | with optional label, helper, icon
  TextArea        same variants as TextField
  Select          native + custom dropdown
  Checkbox        + indeterminate state
  Radio           
  Toggle          
  Slider          

FEEDBACK
  Toast           variants: success, error, warning, info
  Alert           same variants as Toast, inline
  Badge           variants: neutral, brand, success, warning, error
  ProgressBar     
  Skeleton        

NAVIGATION
  Navbar          desktop + mobile (hamburger)
  Sidebar         collapsible
  Tabs            variants: underline, pill
  Breadcrumb      
  Pagination      
  Link            inline + standalone

DATA DISPLAY
  Card            
  Table           with sortable headers + row selection
  Avatar          sizes: xs, sm, md, lg, xl | with fallback initials
  Tag / Chip      removable variant
  Tooltip         
  Stat / KPI      

OVERLAY
  Modal           sizes: sm, md, lg, fullscreen
  Drawer          left, right
  Dropdown Menu   
  Popover         
  Command Palette 

LAYOUT
  Container       
  Section         
  Divider         horizontal, vertical
  Spacer          uses spacing tokens
```

---

## 4. Prototyping Rules

### 4.1 Interaction Patterns

```
NAVIGATION FLOWS
  - Every screen must have a clear back path. No dead ends.
  - Use overlays for modals and drawers, not separate pages.
  - Tab bars / sidebars must reflect active state on every screen.

TRANSITION DEFAULTS
  Smart Animate:         300ms ease-out (page-to-page)
  Overlay open:          250ms ease-out + background dim 50%
  Overlay close:         200ms ease-in
  Hover state:           Instant (no delay)
  Tooltip:               200ms delay before open, 150ms fade

SCROLL BEHAVIOR
  - Long pages: use sticky headers and floating CTAs.
  - Prototype with realistic content length, not lorem ipsum.
  - Mark fixed elements with "Fix position when scrolling" in Figma.
```

### 4.2 Prototype Structure

```
FRAME NAMING
  Use numbered prefixes for flow order:
    01 — Onboarding / Splash
    02 — Login
    03 — Dashboard
    04 — Detail View
    05 — Settings
    06 — Empty States
    07 — Error States

PAGE ORGANIZATION IN FIGMA
  Page: "🎨 Design System"      → all tokens, styles, base components
  Page: "📐 Wireframes"         → low-fidelity structure
  Page: "🖥 Desktop"            → high-fidelity desktop screens
  Page: "📱 Mobile"             → high-fidelity mobile screens
  Page: "▶️ Prototype Flows"    → connected flows with interactions
  Page: "🧪 Playground"         → experimentation and explorations
  Page: "📦 Archive"            → deprecated or old versions
```

### 4.3 Flow Documentation

Every prototype flow must include a cover frame:

```
Flow Cover Frame Contents:
  - Flow name              (e.g. "User Onboarding — Email Signup")
  - Flow description       (1–2 sentence goal)
  - Entry point            (which screen starts the flow)
  - Happy path steps       (numbered)
  - Edge cases covered     (list)
  - Owner                  (designer name)
  - Last updated           (date)
```

---

## 5. Accessibility Rules

### 5.1 Color Contrast

```
Text contrast (WCAG AA):
  Normal text (< 18px):         minimum 4.5:1 ratio
  Large text  (>= 18px bold):   minimum 3:1 ratio
  UI elements and icons:        minimum 3:1 ratio

NEVER rely on color alone to communicate state.
Always pair color with: icon, label, pattern, or border.
```

### 5.2 Touch Targets

```
Minimum touch target:     44 × 44px (iOS + WCAG)
Minimum spacing between
adjacent touch targets:   8px
```

### 5.3 Focus Indicators

```
Every interactive element must show a visible focus ring.
Default focus style:   2px solid color.border.focus + 2px offset
Never use outline: none without a replacement.
```

### 5.4 Content Accessibility

```
- Heading hierarchy must be sequential: h1 → h2 → h3 (never skip levels).
- Every image must have a defined alt-text role: informative, decorative, or functional.
- Form fields must have visible labels. Placeholder text is NOT a label.
- Error messages must identify the field and describe the correction needed.
- Minimum body font size: 16px (1rem). Never below 14px for any UI text.
```

---

## 6. Design QA Checklist

Run this checklist before handoff or review:

```
TOKENS
  [ ] All colors reference semantic tokens, not raw hex
  [ ] All spacing uses the spacing scale
  [ ] All text uses a defined text style
  [ ] All radii use a radius token
  [ ] All shadows use a shadow token

COMPONENTS
  [ ] All interactive elements have every required state
  [ ] All components use Figma auto-layout
  [ ] All components use component properties (not hidden layers)
  [ ] Naming follows Category / Component / Variant convention
  [ ] Icons are consistent size and stroke weight

LAYOUT
  [ ] Grid is applied and content aligns to columns
  [ ] Responsive behavior is defined for at least mobile + desktop
  [ ] Content width constraints are respected
  [ ] Vertical spacing is consistent and uses tokens

PROTOTYPE
  [ ] Every screen is reachable and has a way back
  [ ] Active navigation states match the current screen
  [ ] Transitions use the defined defaults
  [ ] Empty states and error states exist for data-driven screens
  [ ] Loading states exist for async operations

ACCESSIBILITY
  [ ] Contrast ratios pass AA for all text and UI elements
  [ ] Touch targets meet 44px minimum
  [ ] Focus states are visible on all interactive elements
  [ ] Heading hierarchy is sequential
  [ ] Form fields have visible labels

HANDOFF READINESS
  [ ] All layers are named descriptively (no "Frame 237")
  [ ] Auto-layout is used on all containers
  [ ] Exportable assets are marked for export
  [ ] Spacing and sizing are inspectable (no absolute positioning hacks)
  [ ] Design rationale is documented in a cover frame or annotation layer
```

---

## 7. File Hygiene

```
LAYER NAMING
  Never: "Frame 1", "Group 5", "Rectangle 12"
  Always: "card-header", "nav-logo", "hero-cta-button"

  Use lowercase-kebab-case for layers.
  Use PascalCase for component names.

AUTO-LAYOUT
  Use auto-layout on everything.
  If you are using absolute positioning inside a component, reconsider.
  Exception: decorative overlapping elements.

STYLES AND VARIABLES
  Every color, text style, and effect must be registered as a
  Figma variable or style. No detached styles in production frames.

VERSION CONTROL
  Name versions meaningfully: "v2.1 — Added dark mode tokens"
  Not: "final", "final-v2", "final-FINAL"
```

---

## 8. Dark Mode Token Mapping

```
# Override semantic tokens for dark mode
color.bg.primary:       color.gray.950
color.bg.secondary:     color.gray.900
color.bg.tertiary:      color.gray.800
color.bg.inverse:       color.gray.0
color.bg.brand:         color.brand.400

color.text.primary:     color.gray.50
color.text.secondary:   color.gray.400
color.text.tertiary:    color.gray.500
color.text.inverse:     color.gray.900
color.text.brand:       color.brand.300

color.border.default:   color.gray.700
color.border.strong:    color.gray.600
color.border.focus:     color.brand.400

color.icon.default:     color.gray.400
color.icon.active:      color.brand.300
color.icon.disabled:    color.gray.600

shadow.sm:              0 1px 3px rgba(0,0,0,0.4), 0 1px 2px rgba(0,0,0,0.3)
shadow.md:              0 4px 6px rgba(0,0,0,0.4), 0 2px 4px rgba(0,0,0,0.3)
```

Use Figma variable modes to switch between `light` and `dark` collections.
Never hard-code dark mode colors into components.

---

## 9. Motion & Micro-interaction Tokens

```
# Duration
duration.instant:    0ms
duration.fast:       100ms
duration.normal:     200ms
duration.moderate:   300ms
duration.slow:       500ms

# Easing
easing.default:      cubic-bezier(0.4, 0.0, 0.2, 1)
easing.in:           cubic-bezier(0.4, 0.0, 1, 1)
easing.out:          cubic-bezier(0.0, 0.0, 0.2, 1)
easing.spring:       cubic-bezier(0.175, 0.885, 0.32, 1.275)

# Composites
transition.hover:    duration.fast / easing.default
transition.expand:   duration.moderate / easing.out
transition.modal:    duration.moderate / easing.spring
transition.fade:     duration.normal / easing.default
transition.page:     duration.moderate / easing.out
```

---

## 10. Do / Don't Quick Reference

```
DO                                        DON'T
─────────────────────────────────────────  ─────────────────────────────────────────
Use semantic tokens everywhere             Use raw hex codes in components
Use auto-layout on all containers          Use absolute positioning by default
Name every layer descriptively             Leave "Frame 47" in production files
Design all interactive states              Ship components with only default state
Test contrast with a plugin                Eyeball contrast ratios
Use 44px minimum touch targets             Make buttons 32px and call it done
Use component properties                   Hide/show internal layers for variants
Document flows with cover frames           Leave prototypes unexplained
Use Figma variables for theming            Duplicate components for dark mode
Keep spacing consistent with tokens        Mix 13px and 17px spacing values
```

---

*End of design system ruleset.*
*This file should be placed in the Figma project root or linked via the Figma plugin that reads claude.md files.*