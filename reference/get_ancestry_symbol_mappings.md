# Get PGS Catalog Ancestry Symbol Mappings

Retrieves the mappings between the ancestry class symbols and ancestry
class via the PGS Catalog REST API. Note: this function is not exported
and should only be used for debugging reasons. Use in alternative
[`get_ancestry_categories`](https://ascentsoftware.github.io/quincunx/reference/get_ancestry_categories.md).

## Usage

``` r
get_ancestry_symbol_mappings(
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar indicating download progress from the
  REST API server.

## Value

Return a tibble of mappings between the ancestry symbols and their name,
e.g. EUR and European, respectively.
