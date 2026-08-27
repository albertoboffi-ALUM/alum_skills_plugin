---
name: alum-brand-identity
description: Apply the ALUM visual brand identity (logo, colors, typography, components) to HTML deliverables such as guides, how-tos, user manuals, documentation pages, reports, and one-pagers. Use this skill WHENEVER you build or restyle an HTML page for ALUM or any ALUM product (for example maluS, duit, Sinapsi, alum-server), even if the user never says the word brand. Triggers include guida, guide, manual, how-to, documentation, HTML page, readme page, report, one-pager, or any request to produce an .html file to share or hand to users in an ALUM context. Consult it for the exact ALUM colors (coral, teal, ink — hex in references/brand.md), the Space Grotesk plus Inter plus JetBrains Mono type system, the logo variants and which background each is for, and the ready component template, so output matches ALUM identity instead of generic styling. ALUM-only — do NOT use it for non-ALUM work, and do NOT use another company brand skill or templates for ALUM.
---

# ALUM Brand Identity — HTML guides

Produces HTML documents that carry ALUM's visual identity: a dark coral-accented
hero, a sticky numbered contents sidebar, a fixed palette and type system, and a
set of ready components (cards, callouts, code blocks, tables, pills, a stepper).
The design system is already built and validated — **compose content into it;
don't restyle from scratch.**

> **Logo aggiornato il 14 agosto 2026.** Il marchio precedente (esagono angolare
> con chevron teal) è stato ritirato e i suoi file SVG sono stati rimossi da
> `assets/`. Usare esclusivamente i PNG elencati sotto. Vedi
> `references/brand.md` per le regole complete. Con il cambio di marchio sono
> stati riallineati anche i token coral e teal dell'interfaccia.

## When to use

Any HTML deliverable in an ALUM context (the company or its products — maluS,
duit, Sinapsi, alum-server, etc.): user guides, how-tos, manuals, documentation
pages, reports, one-pagers. If the output is a `.docx`/`.pptx` instead, this
skill's tokens still define the brand, but the layout template here is HTML-only.
Do not apply ALUM branding to non-ALUM work.

## Workflow

1. **Start from the template.** Copy `assets/guide-template.html` to your output
   location. It is a complete, self-contained, single-file page: fonts linked,
   all design tokens and components wired, and the current ALUM logo embedded as
   base64 PNG in three places (hero mark, watermark, footer lockup). It renders
   as-is, with no external asset files.

2. **Fill it in.** Replace every `{{PLACEHOLDER}}` and each `<!-- SECTION -->`
   block with real content. Add or remove sections; keep one `<a href="#id">` in
   the sidebar per section (the active-section script needs matching ids). Delete
   the version chip if the doc isn't versioned.

3. **Compose from the provided components**, not new CSS:
   - `.card` grids for parallel concepts; `.rule` (coral) for the one
     must-not-miss point per section; `.note` (teal) for asides.
   - `<pre>` for code — wrap commands in `.k`, options in `.o`, comments in `.c`.
   - `.flow`/`.step` **stepper** for any ordered sequence, pipeline, or
     lifecycle (the signature ALUM pattern); `.step.accent` / `.accent2` to
     highlight key stages.
   - `.pill.coral/.teal/.gray` for compact tags; `.term` for glossary terms.

4. **Logos — use the right variant for the background** (they're in `assets/`):
   - `alum-mark.png` — the coral+teal knot mark, no wordmark. Transparent
     background, works on light and dark alike (hero topbar, watermark, favicon).
     Already embedded in the template.
   - `alum-stacked.png` — mark above the wordmark, **ink** wordmark →
     **light** backgrounds only.
   - `alum-stacked-light.png` — mark above the wordmark, **paper** wordmark →
     **dark** backgrounds (already embedded in the template footer).
   - `alum-logo-source.png` — the full-resolution original as supplied
     (1254×1254, RGBA). Source of truth; regenerate the other variants from it.

   **There is no horizontal lockup in the current identity.** If a layout needs
   one, ask for it rather than assembling mark + wordmark by hand. Embed the PNG
   as a base64 data URL for a portable single file. **Never place the ink-wordmark
   stacked lockup on a dark background.** Keep clear space ≥ the mark's height;
   don't recolor, stretch, or add effects to the mark.

5. **Deliver** the finished `.html` with `SendUserFile`. It needs no server and
   opens by double-click; the Google Fonts load in the user's browser.

## Brand quick reference

- **UI colors (locked):** coral `#FE5950` (primary accent — deliberate, not
  everywhere), teal `#088092` (secondary/links/terms), ink `#15181D` (text +
  dark bands), paper `#F7F8FA` (page), surface `#FFFFFF` (cards). Coral is the
  star, teal the co-star, the rest neutral.
  Coral e teal sono **campionati direttamente dal marchio**: interfaccia e logo
  usano gli stessi valori. Le tinte derivate (soft, bordi, testi su fondo scuro)
  sono ricalcolate di conseguenza — tabella completa in `references/brand.md`.
- **Fonts:** Space Grotesk (display/headings/labels), Inter (body), JetBrains
  Mono (code, chips, ids, versions). Never swap them. Il wordmark del logo usa
  un carattere geometrico proprio: **non ricostruirlo mai** con Space Grotesk —
  usa il file.
- **Tone:** precise, technical, confident, low-fluff. Short leads, concrete
  labels, prose over bullet walls.

For the complete palette table, logo rules, and component catalog, read
`references/brand.md`.

## Do / Don't

- Do keep the layout, tokens, and components consistent across every ALUM guide.
- Do use the stepper for sequences and the coral `.rule` for the single key point.
- Don't invent a new color scheme, swap fonts, recolor or distort the logo, or
  put a dark-wordmark lockup on a dark background.
- Don't reintroduce the retired hexagonal mark, and don't rebuild the wordmark
  in a substitute typeface.
- Don't pull in third-party logos, licensed fonts, or stock imagery.
- Don't use this skill — or any other company's brand skill/templates — for
  non-ALUM projects.
