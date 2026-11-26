# OFF MAPS — image slots & how to replace the placeholders

All photos live in **`public/images/offmaps/`** and are referenced from one single file:
**`src/content/site.ts`** (`const img = '/images/offmaps'`).

To drop in your own photographs, simply overwrite the `.webp` file with the same file name
(or add a new file and update its `src` in `site.ts`). **Keep the same width × height
dimensions** listed below — the layout, crops and scroll animations read the intrinsic
ratio from these numbers, so same dimensions = zero layout or animation changes.

The current images are **neutral, Morocco-toned placeholder illustrations** (no real
destinations) except the five crew portraits, which are the template's original stock
portraits kept as stand-ins.

| File in `public/images/offmaps/` | Dimensions (w × h) | Where it appears | `site.ts` field |
| --- | --- | --- | --- |
| `opening-stage.webp` | 1536 × 1024 | Opening hero stage (smeared into vertical slabs) **and** the two photo slabs behind the booking form | `opening.photo` + `contact.slab` |
| `universe-atlas.webp` ✅ **real photo** | 1024 × 1536 | Ticket card **ATLAS** — Berber village under the snowy High Atlas (from `originals/berber-village-atlas.jpg`) | `buildings.items[0].photo` |
| `universe-sahara.webp` ✅ **real photo** | 1024 × 1280 | Ticket card **SAHARA** — camel caravan on golden dunes (from `originals/camel-caravan-sahara.jpg`) | `buildings.items[1].photo` |
| `universe-coast.webp` ✅ **real photo** | 1536 × 1152 | Ticket card **COAST** — sunset over the Atlantic (from `originals/coast-sunset-beach.jpg`) | `buildings.items[2].photo` |
| `universe-mystery.webp` | 1024 × 1536 | Ticket card **THE FULL MYSTERY** | `buildings.items[3].photo` |
| `universe-private.webp` | 1536 × 1152 | Ticket card **THE PRIVATE TICKET** | `buildings.items[4].photo` |
| `scan-photo.webp` | 1536 × 1024 | "How it works" photo (crossed by the animated red line) + its motion smear | `scan.photo` + `scan.smear` |
| `travellers.webp` | 1024 × 1536 | Traveller testimonials photo | `neighbours.photo` |
| `ticket-layers.webp` | 1024 × 1792 | "One ticket, layer by layer" — the tall photo cut into 7 sliding slices | `floors.photo` |
| `crew-1.webp` … `crew-5.webp` | 1024 × 1536 | Crew portraits (order: Yasmine, Omar, Nadia, Karim, Lucie) | `studio.people[i].photo` |

## Suggested photography per slot (for remaining slots)

Still on placeholders: `opening-stage`, `universe-mystery`, `universe-private`,
`scan-photo`, `travellers`, `ticket-layers` and the five `crew-*` portraits.

- `opening-stage` — a wide, calm Moroccan landscape that reads well as vertical slabs
  (ridge line or horizon roughly in the middle third works best for the smear effect).
- `universe-atlas` — mountains, valleys, villages (portrait).
- `universe-sahara` — dunes / desert camp (slightly wider portrait).
- `universe-coast` — beach, ocean, fishing village (landscape).
- `universe-mystery` — something deliberately ambiguous (road, sealed envelope, horizon).
- `universe-private` — small group on the road (landscape).
- `scan-photo` — a wide scene that survives a horizontal red scan-line and motion smear.
- `travellers` — travellers / hosts portrait orientation.
- `ticket-layers` — a **tall** image; the 7 sliding slices read top-to-bottom as the
  ticket's layers, so a single vertical subject (a road going up, a tall door, a person)
  works best.
- `crew-*` — five portraits, waist-up, similar framing.

## Brand assets (do not modify — official logo)

- `public/brand/offmaps-logo.png` — the official OFF MAPS logo, background made
  transparent (flood-fill from the edges; the artwork itself is untouched). Used by
  `src/components/site/Wordmark.tsx` in the navigation.
- `public/brand/offmaps-logo-original.webp` — the original file you provided, unmodified.
- `public/favicon.svg` — a ticket favicon drawn in the logo's exact colours.
- `public/og-image.png` — 1200 × 630 social share card (logo + slogan).
