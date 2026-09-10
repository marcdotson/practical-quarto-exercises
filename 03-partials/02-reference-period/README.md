# Your turn 2: add the period and region

A statistical release reports on a period of time and an area. A reader must be
able to see both without opening the tables.

Both values are already in the YAML of `report.qmd`, and have been since the
start of the module:

```yaml
release:
  period: "Q3 2026"
  region: Oregon
```

Nothing shows them yet. The template has never asked for them.

1. Copy, then complete, this line in `title-block.html`, below the `$endif$`
   that closes the subtitle:

   ```html
   <p class="report-period">______ &middot; ______</p>
   ```

   Each blank becomes a reference to one of the values above. To reach a key
   that sits inside another key, join the names with a dot.

2. Render. The period and the region show below the subtitle.

## Notes

`release` is a name someone invented, and so is everything under it. Quarto has
no `release` option, so nothing collides.

One nested key is safer than two top-level keys. Every top-level name you invent
is a bet that Quarto will never claim that name. Nest under one key, and you
place that bet once instead of once per field.

You are writing HTML here, not Markdown. That is why the separator is the
character entity `&middot;` and not a typed `·`.

The document now carries two times. Quarto formats `date` for you. It shows
`release.period` exactly as you wrote it.

## If the output looks wrong

The render will not fail. A partial answer gives you a page that shows you what
went wrong.

Blanks left alone show as themselves:

```html
<p class="report-period">______ · ______</p>
```

A name without its dollar signs is text, not a reference:

```html
<p class="report-period">release.period · Oregon</p>
```

One half of that line was substituted and the other half was not. The dollar
signs are what make Pandoc look the name up.

## To think about

Delete the `region:` line from the YAML and render again. What do you get, and
what would you rather have?
