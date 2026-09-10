# practical-quarto-exercises

Exercises for [Level up your Quarto](https://github.com/posit-conf-2026/practical-quarto),
a one-day workshop at posit::conf(2026).

## Get the exercises

### Positron / VS Code

**File** > **New Folder from Git**: `https://github.com/posit-conf-2026/practical-quarto-exercises.git`

### RStudio

**File** > **New Project** > **Version Control** > **Git**: `https://github.com/posit-conf-2026/practical-quarto-exercises.git`

### Other IDE

[Download this folder as a zip file](https://github.com/posit-conf-2026/practical-quarto-exercises/archive/refs/heads/main.zip),
unzip it, and open it in your IDE.

## How the folders work

One folder per exercise, named for the module and the step:

```
03-partials/01-masthead/
```

Each folder is a complete, working starting point. It already holds the finished
work of the step before it. If your last exercise went sideways, open the next
folder and continue from a clean state.

Render the `report.qmd` inside a folder. Each folder stands alone, so you do not
need to render the whole repository.

## The brand

[`brs-brand/`](brs-brand) holds the brand for the Bureau of Regional Statistics,
the fictional agency in these exercises. Most exercise folders already have it
in place, in `_brand/`. To add it to a folder yourself:

```bash
quarto use brand posit-conf-2026/practical-quarto-exercises/brs-brand
```

## License

The exercises are released under the same license as the workshop materials.
