# Map PGP identifiers to PPM identifiers

Map PGP identifiers to PPM identifiers.

## Usage

``` r
pgp_to_ppm(
  pgp_id = NULL,
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- pgp_id:

  A character vector of PGS Catalog Publication identifiers, e.g.,
  "PGP000001". If `NULL` then returns results for all PGP identifiers in
  the Catalog.

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar as the queries are performed.

## Value

A data frame of two columns: `pgp_id` and `ppm_id`.

## Examples

``` r
if (FALSE) { # \dontrun{
pgp_to_ppm('PGP000001')
pgp_to_ppm(c('PGP000017', 'PGP000042'))
} # }
```
