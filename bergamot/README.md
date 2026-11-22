# Bergamot translation models (Firefox Translations)

English → X translation models that OverHeard runs on the device with the Bergamot translator
(`@browsermt/bergamot-translator`, WebAssembly, in a Web Worker). OverHeard uses them when
Chrome's built-in translator can't translate a language (Safari, Firefox, some Chromebooks, and
languages Chrome lacks such as Urdu).

**Source.** Mozilla's Firefox Translations model registry,
<https://storage.googleapis.com/moz-fx-translations-data--303e-prod-translations-data/db/models.json>
(models built by the [Mozilla translations](https://github.com/mozilla/translations) pipeline,
originally from the EU-funded [Bergamot project](https://browser.mt/)). For each language this
folder has the model Mozilla marks as released, preferring the smaller `base-memory` or `tiny`
architecture.

**Changes.** None to the models. Mozilla serves them gzip-compressed; these are the same files
decompressed, because the runtime needs raw bytes. Each file keeps Mozilla's file name.

**License.** The models and the runtime are licensed under the
[Mozilla Public License 2.0](https://www.mozilla.org/MPL/2.0/) (MPL-2.0).

## Layout

- `registry.json`: every model with its files, exact byte sizes and SHA-256 hashes. GitHub Pages
  gzips these files in transit, so the `Content-Length` header is the compressed size; check a
  download against `bytes` here, not that header.
- `v1/<pair>/`: `model.<pair>.intgemm.alphas.bin`, `lex.50.50.<pair>.s2t.bin` (lexical
  shortlist) and `vocab.<pair>.spm`, or `srcvocab`/`trgvocab` for Chinese and Japanese.
  A changed model gets a new folder (`v2/…`) rather than replacing a file here, so a cached
  copy is never mixed with a new one.

| Pair | OverHeard language | Download |
| --- | --- | --- |
| `enes` | Spanish | 35 MB |
| `enpt` | Portuguese | 35 MB |
| `enfr` | French | 35 MB |
| `enuk` | Ukrainian | 34 MB |
| `enru` | Russian | 34 MB |
| `enar` | Arabic | 34 MB |
| `enzh` | Simplified Chinese | 48 MB |
| `envi` | Vietnamese | 35 MB |
| `enhi` | Hindi | 21 MB |
| `enbn` | Bengali | 20 MB |
| `enur` | Urdu | 34 MB |
| `enid` | Indonesian | 20 MB |
| `enja` | Japanese | 47 MB |
| `entr` | Turkish | 20 MB |
| `enfa` | Dari (approximate: this is Iranian Persian, not Afghan Dari) | 21 MB |

No model exists yet for Haitian Creole, Somali, Pashto or Swahili.
