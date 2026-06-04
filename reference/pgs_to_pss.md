# Map PGS identifiers to PSS identifiers

Map PGS identifiers to PSS identifiers.

## Usage

``` r
pgs_to_pss(
  pgs_id = NULL,
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- pgs_id:

  A character vector of PGS identifiers, e.g., "PGS000001". If `NULL`
  then returns results for all PGS identifiers in the Catalog.

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar as the queries are performed.

## Value

A data frame of two columns: `pgs_id` and `pss_id`.

## Examples

``` r
if (FALSE) { # \dontrun{
pgs_to_pss('PGS000001')
pgs_to_pss(c('PGS000017', 'PGS000042'))
} # }
```
