# Map PGS identifiers to PPM identifiers

Map PGS identifiers to PPM identifiers.

## Usage

``` r
pgs_to_ppm(pgs_id, verbose = FALSE, warnings = TRUE, progress_bar = TRUE)
```

## Arguments

- pgs_id:

  A character vector of PGS identifiers, e.g., "PGS000001".

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar as the queries are performed.

## Value

A data frame of two columns: `pgs_id` and `ppm_id`.

## Examples

``` r
if (FALSE) { # \dontrun{
pgs_to_ppm('PGS000001')
pgs_to_ppm(c('PGS000017', 'PGS000042'))
} # }
```
