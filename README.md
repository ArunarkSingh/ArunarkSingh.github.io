# ArunarkSingh.github.io

My personal website and blog, built with Quarto and published with GitHub Pages from the `docs/` folder. It includes computational posts in R and Python with pinned environments so the site can be rebuilt from a clean clone.

Live site: <https://arunarksingh.github.io>

## Requirements

| Tool   | Version I used | Install |
|--------|----------------|---------|
| Quarto | 1.10.18        | https://quarto.org/docs/get-started/ |
| uv     | 0.12.9         | https://docs.astral.sh/uv/getting-started/installation/ |
| R      | 4.6.1          | https://cran.r-project.org/ |

Python 3.14 is installed by uv automatically (pinned in `.python-version`). renv installs itself the first time R starts in this folder.

## Build the site

Run every command from the top level of the repository (the folder with `_quarto.yml`).

1. Clone the repository (terminal):

```bash
   git clone https://github.com/ArunarkSingh/ArunarkSingh.github.io.git
   cd ArunarkSingh.github.io
```

2. Create the Python environment from `uv.lock` (terminal):

```bash
   uv sync
```

3. Restore the R packages from `renv.lock` (terminal):

```bash
   Rscript -e 'renv::restore(prompt = FALSE)'
```

4. Render the site (terminal):

```bash
   uv run quarto render
```

   `uv run` is required so Quarto and reticulate use the project's `.venv`.

## View the site locally

The built site is written to `docs/`. Open `docs/index.html` in a browser, or run `quarto preview` for a local server.

## Data

All data ships inside packages. No data files are committed, and the build needs no network access after `uv sync` and `renv::restore()`.

- Wine recognition dataset, bundled with scikit-learn (UCI Machine Learning Repository, CC BY 4.0).
- gapminder, from the `gapminder` R package (CC0; underlying data from Gapminder, CC BY 4.0).
- mtcars, built into R.

## Troubleshooting

If Python chunks use the wrong environment:

```bash
rm -r .quarto
uv run quarto render
```