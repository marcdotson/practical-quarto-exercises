# Your turn 3: add the release status

Statistical releases are marked with their status. A first estimate is
**Provisional**. A corrected estimate is **Revised**. A settled estimate is
**Final**. Not every release carries one.

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

   Show it only when `brs-release.status` is set.

3. Render. Then delete the `status:` line and render again. The badge should
   disappear, leaving nothing behind.

## Where to look

The file already contains five conditionals. Any of them is a model —
`$if(subtitle)$` is the closest.

The syntax reference is
[Pandoc's template syntax](https://www.pandoc.org/MANUAL.html#template-syntax).

## If you would rather ask

This is a reasonable thing to ask an assistant for. A prompt that works:

> In my Quarto template partial `title-block.html`, show the
> `brs-release.status` metadata value in a `<span class="report-status">`, but
> only when it is set. Use Pandoc template syntax, like the `$if(subtitle)$`
> block already in this file.

Read what it gives you and make sure you can say what each line does. You will
be asked to change it later.

## Notes

`status` sits under `brs-release:` rather than at the top level, for the reason
from turn 2. One namespace, one bet.

A conditional tests whether a key has a value. It does not compare values.
There is no way to write "if the status is Provisional" in a Pandoc template.

## Optional extra, if you finish early

Delete the `region:` line and render. The reference period line now ends in a
separator with nothing after it. Fix it, so that the separator only shows when
there is something on both sides of it.
