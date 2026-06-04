# Get PGS Catalog Trait Categories

Retrieves all trait categories via the PGS Catalog REST API.

## Usage

``` r
get_trait_categories(verbose = FALSE, warnings = TRUE, progress_bar = TRUE)
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

A
[trait_categories](https://ascentsoftware.github.io/quincunx/reference/trait_categories-class.md)
object.

## Examples

``` r
if (FALSE) { # interactive()
get_trait_categories(progress_bar = FALSE)
}
```
