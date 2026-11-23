# AGENTS.md

Guidance for AI coding agents working in this repository. For human-oriented setup instructions, see [README.md](README.md) and [CONTRIBUTING.md](CONTRIBUTING.md).

## What this repository is

A single-page [Jekyll](https://jekyllrb.com/) site for GitHub Pages: a table of MATLAB releases (1984 → today) rendered from one data file. Deployed automatically when `main` updates.

## The most common task

Adding or correcting a release entry in `_data/matlab_history.yml`. Read the [data schema](README.md#editing-the-release-data) before editing it — it lists every field, quoting conventions, and the authoritative sources per field. Preferred workflow: one pull request per release, named after it (e.g. *Add R2026a*), with sources linked in the PR description when the data is new.

## Rules

- **Only edit the data and page sources** (`_data/`, `index.markdown`, `_config.yml`, `404.html`). Never commit:
  - `_site/` or `.jekyll-cache/` — generated build output, ignored by the root `.gitignore`.
  - `Gemfile.lock` version bumps that aren't part of your change.
- **Data file conventions** (violating these produces silent rendering bugs):
  - Entries are chronological, oldest first. New releases go at the end of the file; the page template (`index.markdown`) reverses the order.
  - Quote `version`, `release_name`, `release_date`, `jvm`, and `mcr`; leave `license_number` unquoted.
  - Links in data values are raw HTML `<a>` tags, not Markdown, because values are injected into an HTML table.
  - Two rows may share a `version` (service packs, e.g. R14SP1/SP2 are both `7.0.1`) — that's intentional; don't "deduplicate".
  - Entries for not-yet-released versions exist with future dates; a scheduled date isn't final until MathWorks ships.
- **Don't rename fields** in the YAML without updating `index.markdown` (and this repo's docs) in the same change.
- **Match the existing style**: two-space indent, a `-` dash for list items, sentence case for prose, US spelling.

## Verify before you commit

```bash
typos                       # spell check; extra words allowed in typos.toml
markdownlint "**/*.markdown"  # config in .markdownlint.json (MD013/MD025/MD033 off)
bundle exec jekyll build    # must build without errors
```

If Ruby/Bundler isn't available, at minimum run the YAML through a parser and check the new entry's keys against the schema table in the README.

The macOS system Ruby (2.6) cannot run this bundle ("Could not find 'bundler'"). A current Ruby (3.x, e.g. via chruby) with `bundle install` once is required.

## Where the facts come from

The release data is compiled from MathWorks' public pages: the [latest features page](https://www.mathworks.com/products/new_products/latest_features.html) per release (new products, product changes, release date), the [MATLAB Runtime page](https://www.mathworks.com/support/requirements/matlab-runtime.html) (MCR), and per-release system requirements (bundled JVM). Don't invent data: if a field can't be confirmed from MathWorks or the existing data, omit it rather than guessing.

## Feedback and history

Issues track planned enhancements; past PRs show the typical size and style of data changes. When unsure how a field was meant to be used, check how it's rendered in `index.markdown` first.
