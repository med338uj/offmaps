# OFF MAPS — what was customised (and what was deliberately not touched)

This project started from the 8B "Daylong Architects" one-page template (MIT — see
`LICENSE` and `CREDITS.md`, which are kept). The instruction for this conversion was:
**change only the content; keep the design, structure, animations and interactions exactly
as they are.** That is what was done.

## Untouched (the website itself)

- Every component, section and DOM structure (`src/components/site/*`, `src/pages/*`).
- Every stylesheet (`src/styles/**`, `src/index.css`, Tailwind config) — same layout,
  spacing, typography, colours, hover states, transitions.
- Every animation: the CSS scroll-driven scenes (opening slab smear, horizontal universe
  walk, red scan line with time axis, colour bands, ticket-layer slices, crew portrait
  offsets), the motion kit (`src/motion/motionKit.ts`), the hide-on-scroll navigation and
  the mobile menu overlay.
- The form logic (same field names, same client-side check, same status line behaviour).
- The 404 page, routing and prerender setup.

## Changed (content & brand assets only)

- **`src/content/site.ts`** — every headline, paragraph, navigation label, button, section
  title, card, table row, testimonial, FAQ, footer line now speaks OFF MAPS: mystery
  travel in Morocco, three universes (ATLAS / SAHARA / COAST), the slogan
  "You pick the vibe. We pick the place." Nothing about specific destinations is revealed.
- **Section semantics (same components, new story)**
  - "Buildings" walk → the five ticket cards: ATLAS · SAHARA · COAST · THE FULL MYSTERY ·
    THE PRIVATE TICKET (the per-card `plot` / `h` visual parameters are unchanged, so the
    horizontal scene measures exactly as before).
  - "The scan" method → "How a mystery ticket works" (Pick → Plan → Seal → Go, on the same
    animated time axis).
  - "The gap register" table → "The departure board" (tickets, universes, days, seats,
    status — same columns/rows/badge mechanics).
  - "Borrowed colours" bands → "The colour of every ticket" (same six band keys and
    colours, new names/copy).
  - "Floor by floor" slices → "One ticket, layer by layer" (7 layers, same slice scene).
  - "Studio" team → the OFF MAPS crew; neighbours' quotes → traveller quotes after the reveal.
- **`src/components/site/Wordmark.tsx`** — the template's CSS-bar mark is replaced by the
  official OFF MAPS logo image (transparent PNG) at the same slot in the brand row.
- **Brand assets**: `public/brand/offmaps-logo.png` (official logo, background made
  transparent by flood-fill from the edges — artwork untouched; original kept as
  `offmaps-logo-original.webp`), `public/favicon.svg` (ticket icon in the logo colours),
  `public/og-image.png` (share card with logo + slogan).
- **`index.html`** — title, meta description, Open Graph texts.
- **Images**: `public/images/daylong/` → `public/images/offmaps/` — same slots, same
  dimensions, neutral Morocco-toned placeholder illustrations (no real destinations) so
  your photos can be dropped in later. See **`IMAGE-SLOTS.md`** for the full mapping and
  instructions.
- **Footer**: the giant width-filling wordmark now reads OFF MAPS (it stacks as a bold
  two-line poster — a natural result of the template's length-based sizing with the new
  name); the MIT template credit ("Design: 8B") is kept as required by the license.

## Sample content you may want to replace with real data

These are plausible placeholders (the template used invented data too):

- Email `hello@offmaps.travel`, phone `+212 5 24 00 00 00` (all-zero dummy), base address
  "The OFF MAPS desk, Marrakech" — in `site.ts` (`email`, `phone`, `address`, `contact.lead`,
  `contact.form.sent`).
- Crew names/roles (five sample people + the template's stock portraits).
- Traveller quotes and first names, and the departure-board ticket numbers/seats.

All of them live in the single file `src/content/site.ts`.

## Running the project

```bash
npm install     # or pnpm install
npm run dev     # local dev server
npm run build   # production build into dist/ (a prebuilt dist/ is included)
npm run preview # serve the production build
```

`dist/` is a static build — host it on any static server / CDN (it needs a server root,
not `file://`, because of the React Router setup).
