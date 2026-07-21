# Publishing offline POI packages

## Purpose

This repository is a static distribution surface for versioned offline POI databases. Up Ahead discovers the currently recommended package through the catalogue; it never discovers files by listing repository directories.

## Canonical layout

```text
catalogue/
  v1.json
packages/
  <country>/
    <region>/
      <package-version>/
        upahead-poi-<region>-<package-version>.zip
```

- `<country>` is the lower-case ISO 3166-1 alpha-2 country code, such as `de`.
- `<region>` is a stable, lower-case ASCII slug, such as `baden-wuerttemberg`.
- `<package-version>` is exactly the unique `datasetVersion` in the archive's `manifest.json`.

The archive path is immutable. Never overwrite, rename, or delete a published archive. To correct data, build a new package with a new `datasetVersion` and publish it alongside the older one. The catalogue selects the recommended version and permits a safe rollback without changing old URLs.

## Catalogue policy

`catalogue/v1.json` is the sole mutable rider-facing entry point. It contains one current package per region, with:

- an absolute HTTPS URL for the ZIP;
- the ZIP byte length and SHA-256;
- the embedded package manifest expected by Up Ahead.

Update the catalogue only after the ZIP has been uploaded and independently verified at its final URL. The Baden-Württemberg catalogue, complete public download, activation, and offline lookup have passed their developer-only Karoo probes. Normal Up Ahead `0.1.35` has also passed the rider-facing catalogue, download/validation, and separate activation journey as a signed in-place update, with the package persistently listed as installed. The app verifies the external ZIP hash and length before it installs anything; the route-dependent offline-enrichment UI check awaits a safely available active route.

## Publication checklist

1. Build the archive with `poi-packager`; do not edit its contents by hand.
2. Verify the ZIP checksum and archive integrity against the generated manifest.
3. Confirm the ZIP includes `manifest.json`, `pois.sqlite`, and `ATTRIBUTION.txt` naming OpenStreetMap contributors.
4. Upload it to its final immutable path and verify the uploaded bytes have the same SHA-256.
5. The Baden-Württemberg entry passed developer-only catalogue, full ZIP download/validation, activation, and offline lookup probes, plus the manual normal-app flow and storage/update UX. Before broad rider release, complete the route-dependent offline-enrichment UI check on a safely loaded route.

The archive is a derived OpenStreetMap database. Keep its OpenStreetMap attribution and the ODbL 1.0 URI intact; see the repository [LICENSE](../LICENSE).
