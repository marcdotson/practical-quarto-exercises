# Your turn 1: add the agency masthead

A statistical release must carry the mark of the agency that published it.

The `title-block.html` file in this folder is an unedited copy of Quarto's own
partial, already registered in `report.qmd`. Add the masthead to it.

1. Add this key to the YAML of `report.qmd`:

   ```yaml
   masthead: _brand/brs-logo.svg
   ```

2. Open `title-block.html`. Add this line directly after the `<header>` tag:

   ```html
   <img src="$masthead$" alt="Bureau of Regional Statistics" class="report-masthead">
   ```

3. Render `report.qmd`. The masthead shows above the title.

## Notes

`$masthead$` is a Pandoc template variable. Pandoc replaces it with the value of
the `masthead` key in your YAML. The name is yours. Quarto has no `masthead`
option, and it never reads the key.

`logo` is the obvious name for this, and it is the wrong one. `logo` is a real
Quarto option in `beamer`, `revealjs`, `typst`, and dashboards. It is unclaimed
in `format: html`, so it would work here and then behave differently the moment
you render the same file to another format.

The image file arrived with the brand, in `_brand/`. HTML partials cannot read
brand keys, so you write the path yourself.

The class `report-masthead` does nothing yet. It is a hook for the style step at
the end of this module.

The YAML also holds a `release:` key that nothing shows. Leave it alone for now.
Your document knows more than your template asks for.

## To think about

The author line already names the agency, so the masthead repeats it. Is the
image informative or decorative? Try `alt=""` and decide which is correct.
