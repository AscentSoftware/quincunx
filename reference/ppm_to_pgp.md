# Map PPM identifiers to PGP identifiers

Map PPM identifiers to PGP identifiers.

## Usage

``` r
ppm_to_pgp(ppm_id, verbose = FALSE, warnings = TRUE, progress_bar = TRUE)
```

## Arguments

- ppm_id:

  A character vector of PPM identifiers, e.g., "PPM000001".

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar as the queries are performed.

## Value

A data frame of two columns: `ppm_id` and `pgp_id`.

## Examples

``` r
if (FALSE) { # \dontrun{
ppm_to_pgp('PPM000001')
ppm_to_pgp(c('PPM000017', 'PPM000042'))
} # }
```
