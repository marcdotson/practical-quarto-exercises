# Your turn 4: stop writing the brand

You wrote this brand by hand. Four other teams at the agency did the same, and
five hand-written brands are five slightly different brands.

The agency now publishes one:
[`brs-brand`](https://github.com/posit-conf-2026/practical-quarto-exercises/tree/main/brs-brand).

1. Delete the brand you wrote and the two SVGs. All of it:

   ```bash
   rm _brand.yml brs-logo.svg brs-logo-white.svg
   ```

2. Render `report.qmd`. Default Quarto, in both formats. Everything came from
   those files.

3. See what the agency brand would do before you take it:

   ```bash
   quarto use brand posit-conf-2026/practical-quarto-exercises/brs-brand --dry-run
   ```

4. Take it. Answer the prompt:

   ```bash
   quarto use brand posit-conf-2026/practical-quarto-exercises/brs-brand
   ```

5. Look at what arrived in `_brand/`, then render both formats.

6. Compare `_brand/_brand.yml` with the one you wrote in turns 1 to 3. Switch
   your system appearance to dark and look at the report.

## Notes

The colors and fonts came back. Dark mode did not, and the reversed mark is not
in the agency brand at all — `_brand/` holds `brs-logo.svg` and nothing else.
Your document lost something real by adopting the shared brand.

Resist the urge to fix that by editing `_brand/_brand.yml`. That file is a copy.
The next `quarto use brand` overwrites it, your fix disappears, and until then
you are the only team whose brand has a dark mode. Dark mode is a request to
whoever owns `brs-brand`.

`quarto use brand` takes a local directory, a GitHub `org/repo`, an `org/repo/path`
within one, or a URL to a zip. It copies files into `_brand/` and it does not
subscribe you to anything — nothing updates until you run it again. `--force`
skips the prompts, which is what you want in CI and not what you want at a
keyboard.

Every file a brand needs must live inside your project. That is why the SVG is
copied rather than linked.

`{{< brand logo medium >}}` still works, unchanged, now pointing at a file you
did not write and a path you never typed.

## To think about

Five teams, one brand file, one central owner. What does a team do the week it
needs a color the agency has not defined?

## Optional extra, if you finish early

Get dark mode back without touching `_brand/`. Write a `brand-dark.yml` in this
folder with `background`, `foreground`, and `primary` set for a dark page, then
point each mode at a different brand file in `report.qmd`:

```yaml
brand:
  light: _brand/_brand.yml
  dark: brand-dark.yml
```

Render and switch appearance. The report toggles again. Notice the logo does not,
because the dark brand file has no `logo` — and notice you now maintain a second
brand file, which is the thing you were trying to avoid.

## Where this goes next

The deck places its logo. The HTML report only has one because you put a
shortcode in the body, and it landed *under* the title — a masthead belongs
above it, and the body cannot reach above the title block. Getting it there means
editing the piece of the HTML template that draws that block, which is the next
module.
