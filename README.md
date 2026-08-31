# roundside-catalog

The published fight catalogue for the [Roundside](https://github.com/michaelfery/roundside) Android
app. Generated content only — nothing here is edited by hand.

| File | What it is |
|---|---|
| `manifest.json` | The header the app polls: schema version, data version, generation time |
| `catalog.json` | Organizations, fighters, events with their segments and bouts |

The app reads these directly over `raw.githubusercontent.com`. They have to be publicly readable:
Roundside has no backend and no API, by design, so a static file on a CDN *is* the distribution.

Both are written by a scheduled job in a separate private repository, which owns the parsing, the
normalisation and the identity ledger.

## Data

Fight data is factual: fighters, cards, results. It is derived from
[Greco1899/scrape_ufc_stats](https://github.com/Greco1899/scrape_ufc_stats), a mirror of
ufcstats.com.

Roundside is not affiliated with, endorsed by, or connected to any fight promotion. Promotion names
appear here descriptively, to say which organization ran which event.

## Contract

`manifest.schemaVersion` is the compatibility guard. An app that meets a version it does not know
keeps the data it already has and tries again after its next update, so a breaking change to the
format is safe to ship as long as the version moves with it.

Entity ids are stable across generations and are never reused. The app keys the user's watched
status and follows on them.
