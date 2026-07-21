# Up Ahead POI Packages

Static offline regional OpenStreetMap POI packages for **Up Ahead** on Hammerhead Karoo. The repository will host a public HTTPS catalogue and checksum-verified regional ZIP downloads.

It deliberately contains no rider routes, account data, or personal data.

## Data licence and attribution

The offline POI databases are derived from OpenStreetMap data and are made available under the [Open Data Commons Open Database License (ODbL) v1.0](https://opendatacommons.org/licenses/odbl/1-0/).

> Contains information from OpenStreetMap, which is made available under the Open Database License (ODbL).

OpenStreetMap contributors must be credited as follows:

- [OpenStreetMap copyright and attribution](https://www.openstreetmap.org/copyright)
- [ODbL 1.0 licence text](https://opendatacommons.org/licenses/odbl/1-0/)

Every distributed POI-package archive must also include an `ATTRIBUTION.txt` file with this attribution and the ODbL licence URI.

## Repository layout

- `catalogue/v1.json` — legacy unsigned catalogue retained only for historical development evidence.
- `catalogue/v2.json` — the signed public catalogue used by current Up Ahead releases.
- `packages/<country>/<region>/<package-version>/…zip` — immutable regional POI packages.
- `docs/PUBLISHING.md` — rules for publishing, replacing, and retiring packages.

The developer-only public catalogue and ZIP transport path have passed their Karoo hardware gates.

## Published packages

| Region | Dataset version | Archive |
| --- | --- | --- |
| Baden-Württemberg, Germany | `260719` | `packages/de/baden-wuerttemberg/260719/upahead-poi-baden-wuerttemberg-260719.zip` |

The archive is checksum-verified by Up Ahead before it is installed. Current Up Ahead releases fetch `catalogue/v2.json` and verify its Ed25519 signature before trusting an archive URL, length, SHA-256, or embedded manifest. `catalogue/v1.json`, the complete ZIP, explicit activation, and a local Water lookup passed developer-only Karoo probes. Normal Up Ahead `0.1.35` then completed the rider-facing catalogue, download/validation, and separate activation journey on the Karoo as an in-place update; the persistent installed list shows Baden-Württemberg `260719`. The final route-dependent offline-enrichment UI check awaits an active route and will not alter a rider's navigation merely to force that test.
