# ALUM Brand Reference — HTML guides

Full reference for the `alum-brand-identity` skill. SKILL.md points here for
detail; read the relevant part when composing a guide.

## Colors (locked — never substitute the hex values)

**Riallineati il 14 agosto 2026** al nuovo marchio: coral e teal sono ora
campionati direttamente dal logo, così interfaccia e marchio non divergono.
Valori precedenti, ritirati: coral `#FF6F61`, teal `#0E7C86`.

| Token | Hex | Use |
|---|---|---|
| `--coral` | `#FE5950` | Primary accent: eyebrow, hero rule, section numbers, "important" callouts, one accent letter in the title, links-as-action. The signature ALUM color — use it deliberately, not everywhere. |
| `--teal` | `#088092` | Secondary accent: links, glossary terms, "note" callouts, secondary highlights. Pairs with coral; never competes with it. |
| `--ink` | `#15181D` | Primary text; dark backgrounds (hero, footer, code). |
| `--paper` | `#F7F8FA` | Page background. |
| `--surface` | `#FFFFFF` | Cards, tables. |
| `--muted` | `#5C6470` | Secondary text. |
| `--faint` | `#8A929C` | Tertiary text, meta labels. |
| `--line` | `#E2E7EC` | Borders, dividers. |
| soft tints | `--coral-soft #FFE0DD`, `--teal-soft #E9F5F6` | Callout/pill backgrounds. |

Balance: coral is the star, teal the co-star, everything else is neutral. A
guide should read as mostly paper/ink with coral punctuation and teal support.


### Tinte derivate (ricalcolate, non sceglierle a occhio)

Ogni derivato conserva rispetto al brand lo stesso scarto di tinta, saturazione
e luminosità che aveva nella palette precedente; dove il derivato è **testo**,
la luminosità è stata corretta perché il contrasto non peggiorasse mai.

| Uso | Valore | Contrasto |
|---|---|---|
| `.rule` bordo | `#FFC7C2` | — |
| `.note` bordo | `#D0E9ED` | — |
| `.pill.coral` testo su `--coral-soft` | `#A13A2C` | 5,37:1 (prima 5,17) |
| `.pill.teal` testo su `--teal-soft` | `#087D8F` | 4,34:1 (prima 4,32) |
| `pre .k` (comandi) su `--ink` | `#FE8B83` | 7,82:1 (prima 7,78) |
| `pre .o` (opzioni) su `--ink` | `#7DD8E5` | 10,87:1 (prima 10,65) |
| `.chip.tl` testo / bordo / fondo | `#92D8E2` / `#1B4046` / `#112A31` | 9,39:1 (prima 9,34) |
| link nel footer su `--ink` | `#8DD6E1` | 10,88:1 (prima 10,58) |

Tutti i valori raggiungono o superano il contrasto della palette precedente.

## Typography (Google Fonts, linked in the template)

- **Space Grotesk** (`--disp`) — display: h1/h2/h3, eyebrows, labels, card
  titles, nav. Weights 500/600/700.
- **Inter** (`--body`) — body text. Weights 400/500/600.
- **JetBrains Mono** (`--mono`) — code, chips, RID-style ids, version tags,
  numeric badges.

Never swap these families. If offline rendering matters, the stack falls back
to `system-ui` gracefully, but keep the Google Fonts `<link>`.

## Logo assets (in `assets/`) and where each goes

**Identità aggiornata il 14 agosto 2026** (file fornito da Alberto Boffi). Il
marchio precedente — esagono angolare con chevron teal — è **ritirato**: i suoi
file `.svg` sono stati rimossi da `assets/` e non vanno reintrodotti. Il marchio
corrente è un nodo organico a tre lobi, due coral e uno teal.

| File | Cosa | Fondo |
|---|---|---|
| `alum-mark.png` | Solo marchio, senza wordmark. PNG con trasparenza, 601×554 | **Qualsiasi** — chiaro o scuro. Marchio di default per topbar, filigrana, favicon. |
| `alum-stacked.png` | Marchio sopra il wordmark, wordmark **ink** | Solo fondi **chiari**. |
| `alum-stacked-light.png` | Marchio sopra il wordmark, wordmark **paper** | Fondi **scuri** (es. il footer). |
| `alum-logo-source.png` | Originale a piena risoluzione come fornito, 1254×1254 RGBA | Fonte di verità: rigenerare da qui le altre varianti. |

**Non esiste un lockup orizzontale** nella nuova identità. Se un layout ne ha
bisogno, richiederlo — non assemblarlo accostando marchio e wordmark a mano.

**Regole.** Incorporare il PNG come data URL base64 per avere una guida in file
singolo (il template lo fa già). Mai mettere il lockup con wordmark ink su fondo
scuro: usare la variante `-light`. Spazio di rispetto attorno al logo ≥ altezza
del marchio. Non ricolorare coral e teal del marchio, non stirare, non aggiungere
effetti, non incorniciare su un colore che confligge. Su foto o aree affollate
usare il marchio nudo, non il lockup.

**Il wordmark ha un carattere geometrico proprio** (la A senza traversa): non
ricostruirlo mai con Space Grotesk o altri font: usare il file immagine.

### Stato degli asset

1. **Nessun originale vettoriale.** Alberto ha confermato il 14 agosto 2026 che
   esiste solo il PNG. Gli asset attuali reggono bene fino a circa 600 px di
   lato; oltre si vede la sgranatura. Per stampa, grandi formati o incisioni
   serve chiedere un `.svg`/`.ai`/`.pdf` a chi ha disegnato il marchio. Quando
   arriverà, sostituire i PNG e tornare a inlineare l'SVG nel template.
2. **Colori: questione chiusa.** La palette UI è stata riallineata ai valori del
   marchio (vedi la sezione Colors). Non esiste più divergenza fra logo e
   interfaccia: non reintrodurre i vecchi `#FF6F61` / `#0E7C86`.

## Component catalog (all in `guide-template.html`)

- **Hero** — dark band, coral bottom rule, mark + `ALUM · <area>` label, optional
  version chip, coral eyebrow, big Space Grotesk title (optionally one letter in
  `.s` coral, echoing how the wordmark accents a letter), lede with one bold
  phrase, mono meta chips (`.chip`, `.chip.tl` for a teal highlight), faint mark
  watermark.
- **Sidebar TOC** (`nav.toc`) — sticky, auto-numbered, active item tracked by the
  bundled IntersectionObserver script. One `<a href="#id">` per section.
- **Section** — `.kicker` with a coral `.num`, `h2`, `.sub` lead.
- **Cards** (`.grid.g2/.g3` + `.card`) — for parallel concepts/features.
- **Rule callout** (`.rule`, coral) — the ONE must-not-miss point per section. Use
  sparingly; overuse kills the signal.
- **Note callout** (`.note`, teal) — helpful aside.
- **Code** (`<pre>`) — dark; wrap commands in `.k`, options/strings in `.o`,
  comments in `.c`; `.inline` for inline code in prose.
- **Tables** — `th` in Space Grotesk; `td.cmd code` renders commands in coral.
- **Pills** (`.pill.coral/.teal/.gray`) — compact status/type tags.
- **Stepper** (`.flow` > `.steps` > `.step`) — the signature pattern for any
  ordered sequence, pipeline, or lifecycle. `.step.accent` (coral) and
  `.step.accent2` (teal) highlight key stages.
- **Footer** — dark, `alum-stacked-light.png` (altezza consigliata ≥56px perché il
  wordmark resti leggibile), riga di contesto, mono meta a destra.

## Tone

Precise, technical, confident, low-fluff — matches how ALUM writes. Short leads,
concrete labels, no marketing filler. Prefer prose + the components above over
walls of bullets.

## Content safety

These are ALUM's own brand assets. Do not import third-party logos, licensed
fonts beyond the three above, or stock imagery into an ALUM guide.
