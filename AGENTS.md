# Agent Guide

This repository is designed for AI-assisted client build-outs. Preserve the template’s simplicity unless the client brief clearly requires more.

## Default Workflow

1. Read `CLIENT_BRIEF.example.md` and the actual client brief supplied for the build.
2. Update `src/content/settings/site.json`.
3. Replace content in `src/content/services`, `src/content/posts`, `src/content/testimonials`, and `src/content/faqs`.
4. Adjust `src/styles/tokens.css` for brand primitives.
5. Visit `/blocks/` during local preview to compare available component variants.
6. Compose pages from existing components before creating new ones.
7. Run `npm run build` before handing work back.

## Rules

- Keep brand changes concentrated in `src/styles/tokens.css`, `src/styles/theme.css`, and site settings.
- Do not add UI libraries unless explicitly requested.
- Do not add client-side JavaScript for static presentation sections.
- Prefer plain Astro components with clear props.
- Keep copy specific to the client. Remove placeholder explanations from public pages before launch.
- Keep pages small and direct. Small-business visitors usually need clarity, proof, and contact paths.
- Preserve accessibility basics: one `h1`, labelled controls, useful alt text, visible focus states, and semantic landmarks.

## Component Guidance

- Use `Hero` only on the home page unless the client needs a campaign-style landing page.
- Use `PageIntro` for inner pages.
- Use `Section` for layout rhythm and background variants.
- Use collection-driven components for services, posts, testimonials, and FAQs.
- Create new components only when a repeated pattern appears or a page becomes hard to scan.
- Prefer existing variants before building new components: hero variants, service layouts, testimonial layouts, gallery layouts, and CTA layouts are documented on `/blocks/`.
- Keep client-editable variant controls limited to safe layout choices in `src/content/pages/home.json`.

## Decap Guidance

- Any field added to a content schema should also be added to `public/admin/config.yml`.
- Any new collection should be documented in `README.md`.
- Keep filenames slug-friendly and content portable.

## Stock Photography

Source photos without a browser. Workflow:

1. **Search** — find an Unsplash photo page via web_search
   ```
   web_search("unsplash.com timber floor interior living room")
   ```
2. **Extract the photo ID** — photo page URLs contain the ID, e.g. `Kq8uV6tZM20` from `.../wooden-floor-with-herringbone-pattern-Kq8uV6tZM20`
3. **Download direct** — build the download URL and curl it:
   ```
   curl -sL -o public/uploads/filename.jpg \
     "https://images.unsplash.com/photo-{ID}?w=2000&q=85"
   ```
   Add `&fit=crop&h={height}` for specific aspect ratios.
4. **Wire it in** — reference `/uploads/filename.jpg` in the component or page.
5. **Keep it lean** — images over ~500KB are fine for hero backgrounds but resize gallery images to `w=800&h=1100` to keep page weight down.

No browser, no API key, no page rendering. Search → fetch → curl → done.
