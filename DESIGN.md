---
name: varavel-design-guidelines
description: Design, build, or improve a Varavel product. Use for websites, dashboards, apps, customer reports, proposals, briefs, benchmarks, comparisons, narrative data pages, pricing, and anything that need Varavel look and feel, Geist typography, data presentation, and dark/light themes
---

# Varavel Design Guidelines

This document serves as the single source of truth for the visual, typographic, and architectural rules that define the Varavel brand.

This guide is entirely platform-agnostic. Whether you are designing a web interface, a mobile application, a physical product, or a marketing deck, these principles dictate how to integrate new designs harmoniously with the Varavel identity.

_Note: All technical values mentioned here (colors, spacing, breakpoints, typography) are easily translatable to configuration files in tools like Tailwind CSS, Figma, or any native styling system._

## 1. Brand Philosophy & Identity

Varavel's design language is built upon **clarity, structure, and technical precision**. We design systems, and our visual identity reflects that.

- **Minimalism:** We aggressively remove unnecessary visual elements. The focus is always on content, functionality, and clean layouts.
- **Mathematical Precision:** All elements align to strict grid systems and geometric formulas to maintain visual harmony. Design decisions are calculated, not guessed.
- **Utility over Decoration:** Every visual choice—color, spacing, borders—must serve a structural or semantic purpose. If it doesn't aid navigation or comprehension, it should be removed.

## 2. Color Strategy

Varavel relies on a **high-contrast, monochromatic base**. We do not use warm/cool tint shifts in our structural palette. The core identity must remain neutral, allowing content to breathe and semantic states to guide attention without visual conflict.

### The Monochromatic Core

- **Primary Brand Colors:** Solid Black (`#000000`) and Solid White (`#FFFFFF`). Core logos and brand typography must always be rendered in one of these two extremes.
- **Text & Content:**
  - **Primary (`content`):** Maximum contrast against the background.
    - _Light Mode:_ Near Black (`#0a0a0a` / `neutral-950`)
    - _Dark Mode:_ Near White (`#fafafa` / `neutral-50`)
  - **Secondary/Muted (`content-muted`):** Medium gray for metadata, descriptions, and helper text.
    - _Light Mode:_ Medium-Dark Gray (`#737373` / `neutral-500`)
    - _Dark Mode:_ Medium-Light Gray (`#a1a1a1` / `neutral-400`)

### Structural Base Layers (The Canvas)

Regardless of the platform (light mode or dark mode), interfaces are built on a 4-tier elevation system:

1. **Canvas (`base-100`):** The absolute background of the application/design.
   - _Light Mode:_ Solid White (`#ffffff` / `white`)
   - _Dark Mode:_ Solid Black (`#000000` / `black`)
2. **Surface (`base-200`):** Primary structural containers (Sidebars, Cards, Panels). Slight contrast from the canvas.
   - _Light Mode:_ Light Gray (`#f5f5f5` / `neutral-100`)
   - _Dark Mode:_ Very Dark Gray (`#171717` / `neutral-900`)
3. **Interactive (`base-300`):** Smaller UI elements, input fields, and hover states.
   - _Light Mode:_ Lighter Gray (`#e5e5e5` / `neutral-200`)
   - _Dark Mode:_ Dark Gray (`#262626` / `neutral-800`)
4. **Structural/Borders (`base-400`):** The border color. Used strictly to define component limits and separate containers.
   - _Light Mode:_ Gray (`#d4d4d4` / `neutral-300`)
   - _Dark Mode:_ Medium-Dark Gray (`#404040` / `neutral-700`)

### Semantic Colors

Color is used sparingly and only to convey state. They should pop vibrantly against the monochromatic canvas.

- **Information / Action (`info`):** Blue (`#2b7fff` / `blue-500`). Used for links, active states, and primary actions.
- **Error / Destructive (`error`):** Red (`#fb2c36` / `red-500`). Used for critical alerts, deletion, and server errors.
- **Success (`success`):** Emerald Green (`#00bc7d` / `emerald-500`). Used for healthy statuses and completion.
- **Warning (`warning`):** Orange/Amber (`#ff6900` / `orange-500`). Used for degradation and warnings.

## 3. Typography

Varavel utilizes the **Geist** typeface family by Vercel. It is specifically optimized for modern interfaces and development tools.

### 1. Interface and Text (Geist Sans)

Used for all standard communication: headings, paragraphs, buttons, and navigation.

- **Fallbacks:** `ui-sans-serif`, `system-ui`, `-apple-system`, `"Segoe UI"`, `sans-serif`
- **Permitted Weights:**
  - `Regular (400)`: Body text and long-form reading.
  - `Medium (500)`: Interactive elements (buttons, form labels, tabs).
  - `SemiBold (600)`: Structural hierarchy (H1, H2, H3). No weights bolder than SemiBold should be used.

### 2. Data and Code (Geist Mono)

Used strictly for structured, technical information: code blocks, tokens, IDs, metrics, and data tables.

- **Fallbacks:** `ui-monospace`, `"SFMono-Regular"`, `Menlo`, `Monaco`, `Consolas`, `"Liberation Mono"`, `monospace`
- **Purpose:** Its tabular width ensures that numbers and data points align perfectly in vertical columns without visual shifting.

## 4. Geometry, Spacing & Architecture

### The Grid

All designs must align to a standard **4px grid** (or equivalent 4pt baseline). Consistent spacing is the foundation of a minimalist layout. (e.g., margins/padding should be 4px, 8px, 12px, 16px, 24px, etc.)

### Strict Border Radius Scale

We enforce a rigid 3-tier geometric scale to maintain structural cohesion across any platform:

- **Large (`16px` / `1rem`):** Structural Elements (Cards, Modals, Panels). _This value is mathematically derived from the logo's micro-bevel._
- **Medium (`8px` / `0.5rem`):** Interactive Components (Buttons, Inputs, Dropdowns).
- **Small (`4px` / `0.25rem`):** Nested Elements (Badges, Tags, Tooltips).
- **Full / None:** Reserved exclusively for full-bleed images or perfect circles (Avatars, Pills).

### The Mathematics of Nesting (Concentricity)

When placing a rounded element inside another rounded container, optical harmony must be maintained. You must use the following formula; **never guess the padding**:

`Inner Radius = Outer Radius - Padding`

_Example:_ To nest an interactive element inside a structural card with perfect concentricity:

- Outer Radius (`16px`) - Padding (`8px`) = Inner Element Radius (`8px`).

### Borders and Elevation

- **Borders over Shadows:** We prefer subtle, 1px structural borders (using `base-400` color) to separate elements globally rather than heavy drop shadows. This maintains a sharp, technical aesthetic.
- **Scrollbars:** Use thin scrollbars colored with the structural border color (`base-400`), remaining transparent until interacted with.
- **Shadows:** If depth is absolutely required (e.g., a floating modal over a canvas), use a clean, low-opacity, blurred shadow. Avoid colored or harsh shadows.

## 5. Responsive Design & Breakpoints

We employ a pragmatic **"Single Breakpoint"** architecture. We bypass complex multi-tier responsive scales in favor of a single, highly intentional threshold.

- **The Threshold (`desk`): 1024px (`64rem`)**
- **Mobile/Constrained Base (< 1024px):** Everything below 1024px is treated as a mobile or portrait-tablet environment. Layouts must stack vertically, and data density is optimized for touch interfaces. Sidebars become drawers.
- **Desktop (>= 1024px):** The exact threshold where horizontal space is unlocked. Sidebars become fixed, data tables expand to full columns, and complex horizontal layouts are permitted.

## 6. Global UX Behaviors

Whether building for Web, Desktop, or Mobile, the following interaction patterns must be present:

- **Accessibility (Focus Rings):** All focusable elements must receive a high-contrast, monochromatic focus ring. Usability must never be sacrificed for aesthetics. Do not disable native focus indicators unless providing a custom, high-visibility alternative.
- **Text Selection:** Highlighted text should invert cleanly (e.g., Background becomes `content` color, Text becomes `base-100` color), avoiding default system blues unless it is an explicit brand choice on that platform.

## 7. Do's and Don'ts

### Best Practices (Do's)

- **Always provide a light/dark theme switch.** Verify first whether a mechanism already exists before building a new one.
- **Use [Lucide](https://lucide.dev) when icons are needed.** Check whether Lucide is already installed in the project before adding it.
- **Keep everything symmetric.** Ensure the information density is right for human consumption, and that boxes never grow in disproportionate or visually broken ways.
- **Optimize information density for reading.** Adapt it to the type of information presented.

### Things to Avoid (Don'ts)

- **Don't overuse background layers (`base-200`, `base-300`).** Use them only when they genuinely add value to the design. Otherwise, keep the layout minimal and consistent.
- **Don't overuse colored left/top borders on containers (divs, cards, panels — not quotes) to indicate state.** Prefer other indicators such as icons, backgrounds, or badges.
- **Don't overuse semantic colors.** Apply them with intention, always adding value and direction: guide the user visually, but never flood the interface with state colors.

## Summary for Designers & Engineers

When creating anything for Varavel:

1. Keep it monochromatic; let the content be the color.
2. Rely on the 4-tier Base Layer system (`base-100` to `base-400`).
3. Use Geist Sans for UI, Geist Mono for Data.
4. Align everything to a 4px grid.
5. Calculate your nesting (`Inner Radius = Outer Radius - Padding`).
6. Prefer 1px borders over shadows.
7. Design mobile-first, and unlock horizontal layouts only at `1024px`.
8. When in doubt, remove it.

## 8. Local Configuration & Tooling

Before applying these guidelines, verify if the project already has a dedicated style configuration file (e.g., Tailwind CSS, UnoCSS, or similar) with pre-defined tokens. Reusing an existing configuration eliminates duplicated effort and ensures consistency with the project's real output.

A working example integrating this design system into Tailwind CSS is available at `./tailwind.css` (relative to this file). Use it as a reference when setting up a new project or adapting an existing one or as an inspiration when working with other technologies.

## 9. Brand Assets

Use these CDN URLs for Varavel brand assets. They are official, versioned, and ready to embed directly.

**Priority rule:** If a project has its own assets (logo, favicon, etc.), use those first. Fall back to these Varavel assets only when the project does not provide its own.

**Format rule:** Prefer SVG whenever possible. Use PNG or ICO only when a rasterized image is required (legacy platforms, fixed-size slots, email clients).

### Asset Types

- **Logo:** Logo with no background and no padding. Use for headers, footers, and inline branding.
- **Avatar:** Logo with a background and padding, meant for avatars or profile pictures. Note: it is not rounded.
- **Icon:** Logo with a rounded background. Use for app icons and compact marks.
- **Favicon:** Same as the icon but with less padding. Use for browser tabs and web manifests.

### Variants

Each asset ships in color variants:

- **Dark:** For light backgrounds.
- **Light:** For dark backgrounds.
- `logo` ships as `black` and `white`.

### Official URLs

Logo:

- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/logo-black.png
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/logo-black.svg
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/logo-white.png
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/logo-white.svg

Avatar:

- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/avatar-dark.png
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/avatar-dark.svg
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/avatar-light.png
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/avatar-light.svg

Icon:

- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/icon-dark.png
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/icon-dark.svg
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/icon-light.png
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/icon-light.svg

Favicon:

- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/favicon.ico
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/favicon.png
- https://cdn.jsdelivr.net/gh/varavelio/brand@refs/tags/v1.0.3/dist/favicon.svg
