# Bureau of Regional Statistics report format

The finished module 03 title block, bundled as a custom format extension: the
partial, the styles, and the YAML that wires them together.

## Use it

From a folder with a `report.qmd` in it:

```bash
# from GitHub
quarto add posit-conf-2026/practical-quarto-exercises/brs-format

# from this repo, on disk
quarto add ../brs-format
```

Then set the format:

```yaml
format: brs-html
```

The report still needs the brand for its colours and fonts:

```bash
quarto use brand posit-conf-2026/practical-quarto-exercises/brs-brand
```

## What is in it

```
_extensions/brs/
├── _extension.yml     title, version, and what the format contributes
├── title-block.html   the partial, after all four turns
└── brs.scss           the styles for the classes it adds
```

`format: brs-html` names the extension `brs`, which contributes a format built
on `html`. The directory has to be `_extensions/brs/` for that to resolve.

Anything you can write under `format: html:` in a document can go under
`contributes.formats.html:` here — including default metadata, which is a
better home for a default than a conditional in the partial.

## Note

This folder holds the finished `title-block.html` and the finished styles, so
it answers Your turns 1 to 4. Worth avoiding until you have done them.
