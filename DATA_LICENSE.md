# Data licensing

The app's source code is licensed under Apache-2.0 (see the `LICENSE` file in
the [app repo](https://github.com/rachitabrol/italian-akebi)). The
**dictionary database** (`akebi-it.db.gz`, built by the app repo's
`tools/build_dict.py` and published here as a release asset) is derived from
third-party data under different, share-alike terms. If you redistribute the
database — not just the app — these terms travel with it.

## Sources

| Source | Content used | License |
|---|---|---|
| [Wiktionary](https://en.wiktionary.org) via [kaikki.org](https://kaikki.org/dictionary/Italian/) (wiktextract) | Italian word senses, glosses, part of speech, inflections, IPA | [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) and [GFDL](https://www.gnu.org/licenses/fdl-1.3.html) |
| [Tatoeba](https://tatoeba.org) | Italian example sentences and their English translations | [CC BY 2.0 FR](https://creativecommons.org/licenses/by/2.0/fr/) (per-sentence attribution; see [Tatoeba's terms](https://tatoeba.org/en/terms_of_use)) |

## What this means

- **Attribution is required.** The app shows an in-app Attributions screen
  (Settings → Attributions) crediting Wiktionary/Wiktionary contributors and
  Tatoeba and its contributors. Do not remove this screen from derivative apps.
- **Share-alike (CC BY-SA) applies to the database.** If you modify
  `akebi-it.db` or the pipeline's output and redistribute it, the result must
  remain under CC BY-SA 3.0 (or a later compatible version) with the same
  attribution requirement. This does not require the *app code* to be
  copyleft — only the generated dictionary data.
- **Tatoeba sentences carry per-sentence attribution** to their original
  authors; the pipeline preserves the Tatoeba sentence ID so this can be
  displayed or looked up if needed.
- Rebuilding the database yourself with the app repo's `tools/build_dict.py`
  pulls fresh data directly from these sources under the same terms.
