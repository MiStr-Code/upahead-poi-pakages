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

## Planned layout

- `catalogue-v1.json` — public package catalogue used by Up Ahead.
- `regions/<region>/<version>/…zip` — immutable regional POI packages.

The catalogue and packages will be added after the first public download path has been tested from a Karoo device.

## Published packages

| Region | Dataset version | Archive |
| --- | --- | --- |
| Baden-Württemberg, Germany | `260719` | `regions/baden-wuerttemberg/260719/upahead-poi-baden-wuerttemberg-260719.zip` |

The archive is checksum-verified by Up Ahead before it is installed. It is intentionally published without a catalogue entry until the public HTTPS download path has passed its on-device test.
