# Map PSS identifiers to PGS identifiers

Map PSS identifiers to PGS identifiers. This is a slow function because
it starts by downloading first all Performance Metrics, as this is the
linkage between PSS and PGS.

## Usage

``` r
pss_to_pgs(pss_id, verbose = FALSE, warnings = TRUE, progress_bar = TRUE)
```

## Arguments

- pss_id:

  A character vector of PSS identifiers, e.g., "PSS000001".

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar as the queries are performed.

## Value

A data frame of two columns: `pss_id` and `pgs_id`.

## Examples

``` r
if (FALSE) { # \dontrun{
pss_to_pgs('PSS000001')
pss_to_pgs(c('PSS000017', 'PSS000042'))
} # }
```
