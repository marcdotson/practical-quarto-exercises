# Your turn 3: a second format, and a logo

The release now has to be presented as well as read. Same numbers, same brand,
a deck instead of a page.

Two SVGs arrived from the agency's design team and are sitting in this folder,
unused: `brs-logo.svg` and `brs-logo-white.svg`.

1. Add a deck as a second format in `report.qmd`, keeping the HTML:

   ```yaml
   format:
     html:
       respect-user-color-scheme: true
     revealjs:
       output-file: slides.html
   ```

2. Render both. Use **Quarto: Render Format…** or:

   ```bash
   quarto render report.qmd
   ```

   The deck already has the agency colors and typeface. You wrote no revealjs
   theme.

3. Teach the brand about the logo. Add this above the `color:` block in
   `_brand.yml`:

   ```yaml
   logo:
     images:
       mark:
         path: brs-logo.svg
         alt: Bureau of Regional Statistics
     small: mark
     medium: mark
   ```

4. Render both again. The deck puts the mark in the corner of every slide. The
   HTML report has no logo anywhere.

5. Put it in the report yourself, at the top of the body, above `## Summary`:

   ```markdown
   ::: {.content-hidden when-format="revealjs"}
   {{< brand logo medium >}}
   :::
   ```

6. Render. Switch your system appearance to dark and look at the report again.
   The mark is dark ink on a dark background.

7. Register the reversed mark and hand both sizes a value per mode:

   ```yaml
   logo:
     images:
       mark:
         path: brs-logo.svg
         alt: Bureau of Regional Statistics
       mark-reversed:
         path: brs-logo-white.svg
         alt: Bureau of Regional Statistics
     small:
       light: mark
       dark: mark-reversed
     medium:
       light: mark
       dark: mark-reversed
   ```

8. Render and switch appearance again. The logo swaps with the page.

## Notes

`output-file` is not optional. Both formats write `report.html` by default, and
the second render silently overwrites the first — you end up with one file and
wonder where your report went.

The deck placed the logo and the report did not. Placement is a format decision:
revealjs, Typst, and dashboards each have a place for a brand logo, and
`format: html` has none. The shortcode is how you put one somewhere in HTML.

`{{< brand logo medium >}}` asks for a size. `{{< brand logo mark >}}` asks for
an image by name — it works, and it always gives you that one file, because the
light/dark pair lives on the size, not on the image.

`content-hidden when-format="revealjs"` keeps the shortcode out of the deck,
which already has its own copy in the corner. `when-format="html"` would not
have worked: revealjs *is* HTML, so the div would have shown up in both.

Look at what the shortcode emits: two `<img>` tags, classed `light-content` and
`dark-content`. Quarto ships both and hides one.

The logo landed under the title, not above it. The body starts where the title
block ends, so a shortcode in the body cannot get any higher up the page.

## To think about

The size names are `small`, `medium`, and `large`, and every format decides which
one it wants. You gave `small` and `medium` the same image. When would you not?

## Optional extra, if you finish early

Add `brand-mode: dark` under `revealjs:` and render the deck. The whole deck
turns, and the corner mark turns with it — that is why step 7 gave `small` a dark
value and not only `medium`. This is the one place a mode is fixed at render
time rather than chosen by the reader: a projector has no system appearance.
