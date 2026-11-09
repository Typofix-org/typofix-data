# Typofix rules database

The public database of typographic correction rules behind [Typofix](https://typofix.org). It holds the rules,
their language definitions and the variables they use, exported from the Typofix CMS in two equivalent forms: XML
(primary, in the style of [CLDR](https://cldr.unicode.org/) / LDML) and JSON (derived, in the style of
[`cldr-json`](https://github.com/unicode-org/cldr-json)).

The data is published for anyone building typography or proofreading tools. The rules convert plain text into
properly typeset text — correct quotation marks, dashes, non-breaking spaces, units and the like — per language.

## This repository is generated

Every file here is the **output of an export from the Typofix CMS**. Nothing is edited by hand and nothing is
committed between releases. Corrections are made in Typofix and reach a new release through
`tasks:dataset-release`, which exports, validates, writes a `CHANGELOG` and pushes a signed tag.

As a result, **pull requests are not accepted** and are closed automatically. If you found a wrong, missing or
mistaken rule, please [open an issue](https://github.com/Typofix-org/typofix-data/issues/new/choose). See
[CONTRIBUTING.md](CONTRIBUTING.md).

## Structure

```
dtd/typofix.dtd                     DTD for the XML files
xsd/typofix.xsd                     XSD schema for the XML files

common/main/{code}.xml              per language (BCP 47 code): identity, rules,
                                    language-specific variable definitions
common/supplemental/variables.xml   shared variable base
common/supplemental/languages.xml   the list of exported languages

json/main/{code}/rules.json         the same, as JSON, per language
json/supplemental/variables.json
json/supplemental/languages.json

schema/v1/*.json                    JSON Schema (version 1) for the JSON files
```

- `{code}` is the language's BCP 47 tag (e.g. `sk`, `cs`, `en-GB`).
- XML is the source of truth; JSON carries the identical content. Regular expressions are stored in `CDATA`; the
  GREP and ECMAScript variants of a pattern sit side by side.
- Only **approved** rule/language pairs and the variables they actually use are exported. Rules whose pattern is
  empty after variable substitution are left out.
- Output is deterministic: a stable order of languages, rules, variables and values, so diffs between releases
  show only real changes.
- URLs inside the data (`$schema`, the DOCTYPE, the report-a-problem link) point to `https://typofix.org/…`, not
  to GitHub.

## Using the data

**JavaScript / npm** — only `json/` is shipped:

```bash
npm install @typofix/data
```

```js
import rules from '@typofix/data/json/main/sk/rules.json' with { type: 'json' };
```

**PHP / Composer:**

```bash
composer require typofix/data
```

The package installs the whole dataset; read the files under `vendor/typofix/data/`.

**Direct download** — each [release](https://github.com/Typofix-org/typofix-data/releases) attaches a zip of the
full dataset, and every release has a DOI via [Zenodo](https://zenodo.org/) for citation.

## Versioning

[Semantic Versioning](https://semver.org/):

- **major** — a change to the schema,
- **minor** — new rules or languages,
- **patch** — fixes to existing rules.

Removed rule IDs are never reused. The `CHANGELOG` lists added, changed and removed rules per language.

## Licence

The data is released under the **[Creative Commons Attribution 4.0 International](LICENSE)** (CC BY 4.0) licence.
You may use it, including commercially, as long as you credit the source:

> Typofix rules database — https://typofix.org — CC BY 4.0

The full legal text is in [LICENSE](LICENSE).
