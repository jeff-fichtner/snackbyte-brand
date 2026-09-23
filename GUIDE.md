# snackbyte brand guide

How snackbyte looks, sounds, and why. Decided 2026-09-21.

The values in this document are also `tokens.json`, which is what an
implementation reads; the two say the same things and change together. The
readable version, with the reasoning laid out visually, is the live page at
<https://snackbyte.io/style/>. The exploration that led here — three rounds of
options, eliminated — is `artifacts/brand-directions.html` in `snackbyte-site`.

## The idea

Bounded pieces, and the seam between them. snackbyte makes small, whole tools,
each doing one job and knowing only what it needs. The name says it: a byte is
eight bits, the smallest whole unit; a byte is two nibbles of four, a bounded
piece inside a bounded piece; a snack is a portion complete on its own. The
mark is a byte, drawn as two nibbles, with a bite out of it.

## Colour

Eight roles. Each has a day value and a night value; nothing else changes
between themes. Ground and ink swap; the accents lift enough to read. Every
text role passes 4.5:1 on its ground in both themes.

| Role          | Day                 | Night            | Use                                                    |
| ------------- | ------------------- | ---------------- | ------------------------------------------------------ |
| `ground`      | Alkali `#ECEDEA`    | Basalt `#2A2724` | Page and surface background; the tile.                 |
| `ink`         | Granite `#45423E`   | Alkali `#ECEDEA` | Text; the first nibble.                                |
| `muted`       | Shale `#6B6762`     | Ash `#A8A49D`    | Secondary text, captions.                              |
| `sky`         | `#38639A`           | `#7FA7D3`        | Accent; the second nibble. Links, statuses, focus.     |
| `sage`        | `#8B9B86`           | `#9DAE98`        | Marks and surfaces only. 2.9:1 on Alkali — never text. |
| `sage-text`   | Sagebrush `#5F6E5A` | Sage `#9DAE98`   | Sage where it must carry words.                        |
| `bitterbrush` | `#D2A93A`           | `#DDB447`        | Held in reserve. Never text.                           |
| `rule`        | `#cfd1cb`           | `#4a4642`        | Hairlines and borders.                                 |

Sky by day was nudged from `#3F6FA3` to `#38639A` to pass as small text. The
names are the Owens Valley's: the dry lake, the Sierra, the valley floor, the
May bloom, the tablelands north of Bishop.

Day is the default. Night applies under `prefers-color-scheme: dark` unless
`html[data-theme="light"]`, and always under `html[data-theme="dark"]`.

These are screen values. Print needs its own, chosen on a proof rather than
converted by a formula; when that happens it is recorded here beside them.

## Geometry

Both forms of the mark are built from four numbers and nothing else, in one
unit:

| Name | Value | Where                                                                      |
| ---- | ----- | -------------------------------------------------------------------------- |
| cell | 10    | Every cell is 10 × 10 with corner radius 2.                                |
| gap  | 3     | Between cells within a nibble.                                             |
| seam | 7     | Between the two nibbles — in the row, and between the rows of the stack.   |
| bite | r 8   | A circle removed, centred 1 unit outside the last cell's top-right corner. |

Cells fill from `ink` (first nibble) and `sky` (second nibble). The bite is
computed as a path, not a mask, so every exported file renders in any consumer.

### The row (the logo)

viewBox `0 0 105 10`. Cells at x = 0, 13, 26, 39 (ink) and 56, 69, 82, 95
(sky), y = 0. Bite: circle at (106, −1), r 8.

### The stack (the icon)

viewBox `0 0 49 27`. Sky row at y = 0, ink row at y = 17 (cell 10 + seam 7),
cells at x = 0, 13, 26, 39. Bite: circle at (50, −1), r 8. Sky is on top so
the bite stays at the top right, exactly where the row has it, full size and
outward-facing; read top to bottom it is a horizon.

### The tile

viewBox `0 0 64 64`, a square of `ground` with corner radius 14, the stack
centred. For app icons and favicons. It follows the theme: Alkali by day,
Basalt at night.

## Lockups

Two, and the only thing that decides between them is height.

- **Above** (primary): the row above the name, left edges aligned on ink, the row
  three quarters of the name's ink width, one seam between them. Posters, the site,
  anywhere with room.
- **Beside** (low-height alternative): the row to the left of the name, standing on
  the baseline exactly as tall as the x-height, one seam before the name. Letterhead,
  headers, a site header.

Both derive from the font's metrics, so they hold at any size.

The stack is for square places only and is never set beside the name.

## Type

Bricolage Grotesque, one family at two optical sizes. The wordmark is always
lowercase `snackbyte`: weight 800, `opsz` 96, letter-spacing −0.045em.
Headlines take the display cut (800, `opsz` 96, tight tracking); anything
read at length takes the text cut (400, `opsz` 12–14). Sentence case
everywhere; no small caps, no tracked-out labels.

The type scale is the cell-to-seam ratio, 10/7, from a 16px base: 16, 23, 33,
47, 67, 95. The spacing scale is the seam unit at 4px, so every step is one of
the mark's own numbers: 12 (gap), 28 (seam), 40 (cell), 68 (cell and seam),
108 (the stack's height).

Loaded from Google Fonts as
`Bricolage+Grotesque:opsz,wght@12..96,300..800`; the font is OFL.

## Voice

Extracted from the docs, which were already sounding like this.

- **Say what it does, then what it doesn't.** "It reports; it does not score." "It
  stores no passwords." The negative clause is the signature move: the seam, in prose.
  Every tool gets one.
- **Short declaratives, semicolons doing logic.** No adjectives that sell. "A console
  over the systems you already use" is a complete pitch with no praise in it.
- **Name from the concept, never the domain.** Slate, Grimoire, Cue; spells, lanes;
  lit, banked, out. A product's name is what it means, not what it handles.
- **Explain before you show.** The concept comes before the code; the style page opens
  with the idea before the mark. The site does the same.
- **Specific over general.** Bishop's community theatre. The 395. Two WEN 56360iX
  generators. A real noun beats a category.
- **Sentence case, plain verbs, one job per sentence.** No all-caps, no "Submit," no
  exclamation marks. Dry humour allowed, rare, never signalled.
- **Two registers, one voice.** The site explains; the tools just say. Same rules,
  fewer of them.
- **The name is lowercase, always.** `snackbyte` in the wordmark and in prose, including
  as the first word of a sentence. The only exception is the legal name (Snackbyte LLC)
  on legal and financial paper.

**The headline:** "Software that knows where it ends." (also in `tokens.json` under `copy`, with the lines as they break and the sentence under it.) Under it: "snackbyte builds
tools for the community around Bishop, California. Each one does one job, knows only
what it needs, and stops there." "Building something good" is retired.

## Rules

- The row is for wide places; the stack is for square places.
- Above the name whenever there is room; beside it when there is not.
- Cells of ten, gaps of three, a seam of seven, a bite of radius eight.
- The bite is always at the end, always at the top right, always full size.
- Ground and ink swap at night; the accents lift.
- Sage and Bitterbrush are for marks and surfaces, not for words.
- One family, two optical sizes, sentence case.
- The name is lowercase, always; say what it does, then what it doesn't.

## Still open

- The type and spacing scales are a first cut, held by one page. They are settled
  when the real site has run on them.
- Print values for the palette, chosen on a proof.

## Rollout

Where the brand has landed and where it has not. This is the one place that
tracks it, across repositories.

| Surface                          | Status                                                                                                                          |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Homepage (`snackbyte.io`)        | Done 2026-09-21: holding page on the brand. Links nothing.                                                                      |
| `/style`                         | Done: the readable guide. Unlinked; reached by URL.                                                                             |
| Favicons, touch icon, link card  | Done: generated and served.                                                                                                     |
| The guide, extracted             | Done 2026-09-22: this repository is the authority.                                                                              |
| `@snackbyte/brand`               | In progress: `snackbyte-brand-render` reads this and publishes it.                                                              |
| The real site                    | Next. Constitution ratified; first spec pending.                                                                                |
| `snackbyte-links` QR centre mark | Waiting: every link today carries a client's mark, not ours. When a snackbyte resource is linked, the centre mark is the stack. |
| Email signature                  | Waiting on the real site. Beside lockup.                                                                                        |
| Letterhead                       | Waiting on the real site. Beside lockup.                                                                                        |
| Business cards                   | Waiting on the real site. Needs CMYK chosen on a proof.                                                                          |
| Social covers                    | Waiting on the real site.                                                                                                       |
| Old deliverables                 | To archive as retired so nothing picks them up.                                                                                 |

## The old brand

Retired 2026-09-21: the interlocking knot mark, Montserrat wordmark, indigo
`#2E3192` and grey `#B3B3B3` (both Illustrator default swatches). Source files
remain in the designer's deliverables (`Snackbyte logo_E`, January 2026).
