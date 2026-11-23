# Contributing

Thanks for wanting to improve MATLAB Release Info! The most common contribution is adding or correcting a release entry in `_data/matlab_history.yml`. The [README](README.md) documents the data schema, field conventions, and sources to check.

## Workflow

1. **Open an issue first** for anything bigger than a data correction (new columns, layout changes). This helps agree on the approach before work starts. Data fixes and new releases can go straight to a pull request.
2. **Create a branch** for your change, e.g. `add-r2026a`.
3. **Make the change**:
   - For a new release: append the entry to the end of `_data/matlab_history.yml` (see the [data schema](README.md#editing-the-release-data)).
   - For corrections: keep edits minimal and scoped to the affected entries.
4. **Run the checks** (below) and verify the page renders correctly with `bundle exec jekyll serve`.
5. **Open a pull request** against `main` with a short description and, if there is one, a link to the MathWorks page the data came from.
6. After merge into `main`, GitHub Pages deploys the site automatically.

## Checks

Run before opening a pull request:

```bash
typos                       # spell check; config in typos.toml
markdownlint "**/*.markdown"  # config in .markdownlint.json
bundle exec jekyll build    # must build cleanly
```

If you don't have these installed locally, the recommended VS Code extensions (`.vscode/extensions.json`) cover both checks as you type.

## Style notes

- Raw HTML (`<a href="...">`) is allowed and expected inside YAML values where product names are linked; don't convert these to Markdown.
- Strings that look like numbers (`version`, `jvm`, `mcr`) are quoted in the data file so YAML doesn't reinterpret them.
- The site is in English; use "US" spelling, consistent with MathWorks terminology.
