# MATLAB Release Info

A single-page reference site listing every MATLAB release from 1984 to today: version number, release name, FLEXlm release number, release date, bundled JVM version (Windows), MATLAB Runtime (MCR) version, new product introductions, and product changes.

The site is built with [Jekyll](https://jekyllrb.com/) and deployed via [GitHub Pages](https://pages.github.com/):

**[https://jorikcaljouw.github.io/MATLAB-Release-Info/](https://jorikcaljouw.github.io/MATLAB-Release-Info/)**

## Repository layout

```text
├── _data/
│   └── matlab_history.yml   # All release data — the file that changes most
├── _posts/                  # Empty; part of the default Jekyll theme scaffold
├── _site/                   # Jekyll build output (generated, git-ignored)
├── .vscode/                 # Recommended extensions and spell-check words
├── .markdownlint.json       # markdownlint config (MD013/MD025/MD033 disabled)
├── typos.toml               # typos spell-check config
├── 404.html                 # 404 page
├── Gemfile / Gemfile.lock   # Ruby dependencies (github-pages gem)
├── _config.yml              # Jekyll site configuration
└── index.markdown           # The page; renders the table from the YAML data
```

Most changes — and nearly all contributions — are data updates to `_data/matlab_history.yml`. The page in `index.markdown` rarely changes.

## Working on the site locally

Prerequisites: [Ruby](https://www.ruby-lang.org/) 3.x with Bundler. All dependencies come from the `github-pages` gem, which pins Jekyll to the version GitHub Pages runs. Note that the macOS system Ruby (2.6) is too old — use a current Ruby via [chruby](https://github.com/postmodern/chruby), rbenv or similar (`chruby ruby-3.4.8` on this machine).

```bash
bundle install
bundle exec jekyll serve
```

Then open <http://127.0.0.1:4000/MATLAB-Release-Info/>. The site regenerates as you edit (`_config.yml` changes require a restart).

GitHub Pages publishes the `main` branch; changes are live a few minutes after merge.

## Editing the release data

All content lives in [`_data/matlab_history.yml`](_data/matlab_history.yml). Entries are listed **chronologically, oldest first**; the page renders them newest first.

Each entry uses these fields (only `version` and `release_date` are required; omit a field when not applicable):

| Field | Example | Description |
| --- | --- | --- |
| `version` | `"25.1"` | MATLAB version number, quoted |
| `release_name` | `R2025a` | Marketing release name (releases since R11.1) |
| `release_date` | `"May 14, 2025"` | Free-form date string — year only for early releases, full date for recent ones |
| `license_number` | `53` | FLEXlm release number, unquoted integer |
| `jvm` | `"1.8.0_202"` | Bundled JVM version (Windows) |
| `mcr` | `"25.1"` | MATLAB Runtime (MCR) version |
| `new_product` | list of strings | Products introduced in this release, since R2012b |
| `product_changes` | list of strings | Renamings, discontinuations, and similar product-level changes, since R2011a |

Example entry:

```yaml
- version: "25.1"
  release_name: "R2025a"
  release_date: "May 14, 2025"
  license_number: 53
  jvm: "1.8.0_202"
  mcr: "25.1"
  new_product:
    - <a href="https://www.mathworks.com/products/matlab-copilot.html">MATLAB Copilot</a>
  product_changes:
    - Filter Design HDL Coder is <a href="https://www.mathworks.com/products/new_products/r2025a-transition.html">discontinued</a>.
```

### Conventions and gotchas

- **Quote** `version`, `release_date`, `jvm`, and `mcr`; leave `license_number` unquoted.
- **Links**: product names may contain raw HTML `<a>` anchors rather than Markdown, because the values are rendered inside the HTML table.
- **Version numbers are not unique per row**: service packs share the base version (e.g. R14SP1 and R14SP2 are both `7.0.1`) and are separate entries.
- **Ordering**: insert new releases at the end of the file; the template reverses the order for display.
- **Pre-release rows for future releases** appear with the scheduled release date before it is known to be final.

### Adding a new release (the most common change)

1. Create an issue or pull request named after the release (e.g. *Add R2026a*).
2. Append an entry to `_data/matlab_history.yml` following the schema above.
3. Sources for the fields:
   - Release name, date, new products, product changes: [MathWorks latest-features page](https://www.mathworks.com/products/new_products/latest_features.html) and the release's transition page.
   - MATLAB version and FLEXlm release number: MathWorks documentation of MATLAB versions; the FLEXlm number also appears in license files.
   - MATLAB Runtime (MCR): the [Supported MATLAB Runtime Versions](https://www.mathworks.com/support/requirements/matlab-runtime.html) page.
   - Bundled JVM version: the release's system requirements page for Windows.
4. Run the checks described in [CONTRIBUTING.md](CONTRIBUTING.md) and preview locally.

## Checks

Before committing:

- `typos` — spell check (see `typos.toml` for accepted words like `FLEXlm` and `SerDes`).
- `markdownlint` — Markdown linting (see `.markdownlint.json`).
- `bundle exec jekyll build` — must succeed without warnings about missing data fields.

The spell-checker and linter are also available in VS Code via the recommended extensions in `.vscode/extensions.json`.

## Feedback

Feedback and planned enhancements are tracked in the repository's [issues](https://github.com/jorikcaljouw/MATLAB-Release-Info/issues). See [CONTRIBUTING.md](CONTRIBUTING.md) for how to contribute. AI agents working in this repository should also read [AGENTS.md](AGENTS.md).
