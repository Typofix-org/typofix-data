# Contributing

Thank you for helping to improve the Typofix rules database.

## This repository is generated — please use issues, not pull requests

Every file here is exported from the Typofix CMS. The rules are maintained in Typofix and published here only as a
release. Because of that:

- **Pull requests are not accepted.** A bot closes them automatically with a link back to the issues. Any change
  pushed here would be overwritten by the next release.
- **The way to contribute is to open an issue.** The Typofix team reviews it, makes the correction in the CMS, and
  it ships in the next release.

[Open an issue →](https://github.com/Typofix-org/typofix-data/issues/new/choose)

## What makes a good issue

Pick the matching template and fill it in:

- **Rule bug** — a rule changes text it should not, or misses text it should change. Include the rule **ID**, the
  **language**, the **input** text, the **expected** result and the **actual** result, and the **data version** you
  used (the release tag).
- **Rule proposal** — a correction Typofix does not make yet. Describe the typographic rule, the language it
  applies to, and give before/after examples.
- **Data or schema bug** — something wrong in the files themselves: an invalid document against the XSD or JSON
  Schema, a mismatch between the XML and JSON, a broken link, and so on. Include the file path and the version.

The more precise the example, the faster the fix. Concrete before/after text beats a description.

## Reporting from a Typofix client

If you hit the problem inside a Typofix plugin or the web editor, the quickest path is the report link shown there.
It carries the rule ID, language and data version for you.

## Licence of contributions

The database is published under [CC BY 4.0](LICENSE). By describing a rule or correction in an issue you agree that
it may be incorporated into the database and released under that licence.
