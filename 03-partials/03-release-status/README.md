# Your turn 3: add the release status

Statistical releases are marked with their status. A first estimate is
**Provisional**. A corrected estimate is **Revised**. A settled estimate is
**Final**, and by convention a release with no mark at all is Final.

This folder holds the finished work of turn 2: the masthead and the reference
period are both in `title-block.html`.

There is no snippet this time.

1. Add a `status` key under `brs-release:` in `report.qmd`:

   ```yaml
   brs-release:
     period: "Q3 2026"
     region: Oregon
     status: Provisional
   ```

2. In `title-block.html`, below the reference period, show the status inside
   this element:

   ```html
   <span class="report-status"></span>
   ```

   Two things must be true:

   - When `brs-release.status` is set, the badge shows that value.
   - When it is absent, the badge shows `Final`.

3. Render. Then delete the `status:` line and render again. The badge must
   change to `Final` on its own.

## Where to look

The file already contains five conditionals. They all test one value. Only one
of them says what to do when that value is absent. Read that one, then adapt it.

The syntax reference is
[Pandoc's template syntax](https://www.pandoc.org/MANUAL.html#template-syntax).

## If you would rather ask

This is a reasonable thing to ask an assistant for. A prompt that works:

> In my Quarto template partial `title-block.html`, add a status badge. Show the
> `brs-release.status` metadata value in a `<span class="report-status">` when it is
> set, and show `Final` when it is not. Use Pandoc template syntax, like the
> `$if(subtitle)$` block already in this file.

Read what it gives you and make sure you can say what each line does. You will
be asked to change it later.

## Notes

`status` sits under `brs-release:` rather than at the top level, for the reason from
turn 2. One namespace, one bet.

A conditional tests whether a key has a value. It does not compare values. There
is no way to write "if the status is Provisional" in a Pandoc template, which is
why the default lives in the template and the value lives in the YAML.

## Optional extra, if you finish early

Delete the `region:` line and render. The reference period line now ends in a
separator with nothing after it. Fix it, so that the separator only shows when
there is something on both sides of it.
