# Imparo Ank'io — dictionary data

This repo hosts nothing but the downloadable dictionary database for the
**Imparo Ank'io** Android app. There is no app source here — the app is built
in a separate (currently private) repo,
[`italian-akebi`](https://github.com/rachitabrol/italian-akebi), which will be
renamed to match the app in due course.

## What gets published here

A GitHub Actions workflow in the app repo builds and publishes releases here
on every manual dictionary rebuild:

- An **immutable release**, tagged `dict-<YYYY.MM.DD>-<sha7>`, carrying:
  - `akebi-it.db.gz` — the gzipped SQLite dictionary database (~98 MB)
  - `manifest.json` — metadata describing that specific build
- A **rolling release**, tagged `dict-latest`, carrying only `manifest.json`
  — a pointer at the current immutable release.

The app fetches `dict-latest/manifest.json` on first run. That manifest's
`url` field points at the matching immutable `.gz` asset, so the rolling tag
never needs to move the (large) database file itself — only the small JSON
pointer.

## `manifest.json` schema

```json
{
  "version": "2026.08.14-abc1234",
  "url": "https://github.com/rachitabrol/Imparo-Ank-io-dict/releases/download/dict-2026.08.14-abc1234/akebi-it.db.gz",
  "sha256": "…",
  "size_bytes": 102873600
}
```

| Field | Meaning |
|---|---|
| `version` | Build date + short commit SHA of the app repo at build time |
| `url` | Download URL for the matching `akebi-it.db.gz` release asset |
| `sha256` | SHA-256 checksum of `akebi-it.db.gz` |
| `size_bytes` | Size of `akebi-it.db.gz`, in bytes |

## Verifying a download

```bash
sha256sum akebi-it.db.gz
# compare the output against manifest.json's "sha256" field
```

## License

The dictionary database is derived from third-party data under share-alike
terms distinct from the app's own license — see
[`DATA_LICENSE.md`](DATA_LICENSE.md).
