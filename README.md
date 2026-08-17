# kitchener-address-import

The **City of Kitchener checkout** of the address-import family — dataset #18
in the onboarding pass, scaffolded 2026-08-17 by the breadth-first loop
(engine `future-work/multi-city/onboarding-queue.md`), the last of the
2026-08-16 licence-review admits and the strongest-licensed of them: the
city's OGL makes attribution voluntary AND the city granted explicit OSM
permission ([Waterloo_region/Kitchener_authorization](https://wiki.openstreetmap.org/wiki/Waterloo_region/Kitchener_authorization)).
Status: **onboarding**. No proposal published, no uploads made.

The pipeline lives in the engine repo,
[`address-importer-friend`](https://github.com/skfd/address-importer-friend)
(see its README for setup). This repo carries only Kitchener's `config.toml`,
credentials (`.env.*`, gitignored, from the `.example` files), and — locally,
gitignored — `data/` with the OSM extract and `data/kitchener/tool.db`.

```bash
cd ../address-importer-friend
python run.py --city-dir ../kitchener-address-import
```

Source data: City of Kitchener `Addresses` via the sibling
[`ontario-address-changes`](https://github.com/skfd/ontario-address-changes)
tracker (`data/kitchener/kitchener.db`, 132,060 rows / ~70,113 civic at
snapshot 20, 2026-08-03 — the family's most mature tracker config: real
key, tuned ignore_fields, status/boundary change classes).

Structural facts (details in config comments): **45% unit rows** (59,848 —
the portfolio high; deepest stack 552 at 30 Francis St S), collapsed to
civic with the cleanest stack hygiene in the family; **the status filter is
load-bearing** — 4,380 `PENDING` rows are excluded in-query; int ward 1-10;
`full` synthesized because ADDRESS embeds the unit prefix ("1B-32 ELMSDALE
DR"); ALL-CAPS abbreviated streets (TODO §9 gates upload). Tiles ride the
55 Planning Communities at 99.98% (the Hamilton fabric shape; the
23-polygon Neighbourhood Association layer is a member-org fabric at 76%).

Entry state probed 2026-08-17 (`onboarding/entry-state-2026-08-17.json`):
**brownfield-active (organic)** — this is NOT a greenfield. **jtracey** has
been improving Kitchener addresses continuously since 2021, explicitly
citing "City of Kitchener" and StatCan as sources (891 of 1,615 sampled
elements; downtown is substantially addressed, mostly on buildings — 775
ways). Mojgan Jadidi's 2016 StatCan GTHA campaign seeded the suburbs
(fourth confirmed city, TODO §3). **i_e_leibowitz was editing addresses
2026-08-15/16** — the week of this probe. No import tags, no import wiki
page. Any work here is coordination-first: talk to jtracey (who also
anchors the waterloo checkout's contacts — one mapping community across
both cities) and i_e_leibowitz before anything visible; the likely
consumer is QA/gap-fill alongside the incumbents, not a bulk import.

Before any production upload: coordination above, then wiki proposal page,
forum announcement, and feedback window per the
[OSM Import Guidelines](https://wiki.openstreetmap.org/wiki/Import/Guidelines)
— Toronto's [`IMPORT_PROPOSAL.mediawiki`](https://github.com/skfd/toronto-2-address-import/blob/main/IMPORT_PROPOSAL.mediawiki)
is the template.

MIT licensed.
