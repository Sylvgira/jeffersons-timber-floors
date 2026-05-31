---
version: "alpha"
name: "Client Site Template"
description: "A neutral small-business website design system for fast, brand-specific Astro build-outs."
colors:
  primary: "#1d4ed8"
  on-primary: "#ffffff"
  secondary: "#f5f5f5"
  accent: "#111111"
  neutral: "#ffffff"
  surface: "#f7f7f7"
  text: "#111111"
  text-muted: "#5f6368"
  border: "#dedede"
typography:
  h1:
    fontFamily: "Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif"
    fontSize: "5.25rem"
    fontWeight: 700
    lineHeight: 1.02
    letterSpacing: "0em"
  h2:
    fontFamily: "Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif"
    fontSize: "2.25rem"
    fontWeight: 700
    lineHeight: 1.12
    letterSpacing: "0em"
  body:
    fontFamily: "Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif"
    fontSize: "1rem"
    fontWeight: 400
    lineHeight: 1.65
    letterSpacing: "0em"
  eyebrow:
    fontFamily: "Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif"
    fontSize: "0.78rem"
    fontWeight: 700
    lineHeight: 1.2
    letterSpacing: "0.08em"
rounded:
  xs: "2px"
  sm: "4px"
  md: "8px"
  pill: "999px"
spacing:
  xs: "0.25rem"
  sm: "0.5rem"
  md: "1rem"
  lg: "1.5rem"
  xl: "2rem"
  section: "clamp(4rem, 9vw, 7rem)"
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.sm}"
    padding: "0.75rem 1.1rem"
  button-secondary:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.text}"
    rounded: "{rounded.sm}"
    padding: "0.75rem 1.1rem"
  link:
    textColor: "{colors.accent}"
  muted-text:
    textColor: "{colors.text-muted}"
  divider:
    backgroundColor: "{colors.border}"
  section-surface:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.text}"
  card:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.text}"
    rounded: "{rounded.md}"
---

## Overview

The template starts as a neutral wireframe. It should adapt to many small-business brands without carrying a strong default style.

Quiet structure, clear type, restrained borders, and simple spacing define the baseline. The first brand pass should come from variables and real content, not decorative effects.

Keep brand changes concentrated in `src/styles/tokens.css`, `src/styles/theme.css`, and `src/content/settings/site.json`.

## Colors

The default palette is intentionally plain and should be replaced with the client brand during build-out.

- **Primary (#1d4ed8):** Default action color. Replace with the client's main CTA or brand color.
- **On Primary (#ffffff):** Text on primary actions. Preserve WCAG AA contrast against the final primary color.
- **Accent (#111111):** Strong neutral accent for brand marks, headings, or restrained emphasis.
- **Surface (#f7f7f7):** Quiet section background for separating content bands without heavy decoration.
- **Text (#111111):** Main readable foreground color.
- **Text Muted (#5f6368):** Paragraphs, captions, metadata, and secondary labels.
- **Border (#dedede):** Rules and quiet component outlines.

Update colors in this order: `--brand-primary`, `--brand-primary-contrast`, `--brand-name-color`, `--brand-secondary`, then `--brand-accent`. Component-specific color overrides should come only after semantic aliases are insufficient.

## Typography

The system uses Inter by default through `--font-sans`, with system fallbacks. Typography should stay readable, direct, and businesslike unless the client brief clearly calls for a more editorial, luxury, playful, or technical voice.

Use one `h1` per page. Home pages may use the larger hero scale; inner pages should use `PageIntro` and tighter hierarchy. Keep letter spacing at `0` for normal headings and body text. Reserve uppercase tracking for small eyebrow labels only.

Change `--font-body` and `--font-display` only when the client's brand direction is clear. Avoid adding web font dependencies unless they materially improve the finished site.

## Layout

Use `Section` for vertical rhythm and background variants. Use `.container` and `.container--narrow` for readable line lengths. Keep pages small and direct: small-business visitors usually need clarity, proof, and contact paths more than complex storytelling.

For a new client, change in this order:

1. `src/content/settings/site.json`: name, description, URL, contact details, CTA.
2. Brand color primitives in `src/styles/tokens.css`.
3. Font variables if the brand has a clear type direction.
4. Section rhythm and radii only if the client needs a sharper, softer, denser, or more editorial style.
5. Component-specific CSS only after the global tokens are insufficient.

Visit `/blocks/` during local preview to compare available component variants before creating new components.

## Elevation & Depth

The default system favors borders, spacing, and surface changes over heavy shadows.

Use `--shadow-subtle` only for small lifts where a component needs separation. Avoid gradient-heavy backgrounds, decorative blobs, nested card layouts, and default stock-like visual effects. Real client photography should replace placeholders when available.

## Shapes

Radii are restrained: `2px`, `4px`, and `8px` cover most UI needs. Buttons default to `4px`. Cards and repeated content items may use `8px`. Pill radius is reserved for compact tags or controls where the shape is expected.

Adapt shape cautiously:

- Professional service: reduce radii and keep the neutral palette.
- Trade or local service: preserve simple radii and strengthen CTA clarity.
- Hospitality or lifestyle: use warmer neutrals and more generous image sections.
- Health or care: use softer palette choices while preserving accessible contrast.

## Components

Compose pages from existing components before creating new ones. Prefer collection-driven components for services, posts, testimonials, and FAQs.

Use `Hero` only on the home page unless the client needs a campaign-style landing page. Use `PageIntro` for inner pages. Public pages should not contain placeholder explanations before launch.

Current variant surface:

- `Hero`: `simple`, `split-media`, `centered`, `service-led`; media can be `left` or `right` where applicable.
- `ServiceGrid`: `grid`, `list`, `featured-first`.
- `Testimonials`: `grid`, `stacked`.
- `GalleryBlock`: `grid`, `feature-left`, `feature-right`.
- `CTABand`: `band`, `split`, `inline`.

Client-editable homepage variant controls live in `src/content/pages/home.json` and Decap's Pages collection. Keep client-editable variant controls limited to safe layout choices. Do not expose raw spacing, color, typography, or arbitrary component controls to clients.

## Do's and Don'ts

Do keep copy specific to the client, use useful alt text, preserve visible focus states, and keep semantic landmarks intact.

Do use real proof points, real service details, real testimonials, and clear contact paths.

Do add new content fields to `public/admin/config.yml` whenever a schema changes, and document new collections in `README.md`.

Don't add UI libraries unless explicitly requested.

Don't add client-side JavaScript for static presentation sections.

Don't create new components until a repeated pattern appears or a page becomes hard to scan.

Don't let the template's neutral defaults become the final brand direction when a client brief provides stronger guidance.
