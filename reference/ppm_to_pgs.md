# Map PPM identifiers to PGS identifiers

Map PPM identifiers to PGS identifiers.

## Usage

``` r
ppm_to_pgs(ppm_id, verbose = FALSE, warnings = TRUE, progress_bar = TRUE)
```

## Arguments

- ppm_id:

  A character vector of PPM identifiers, e.g., "PPPM000001".

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar as the queries are performed.

## Value

A data frame of two columns: `ppm_id` and `pgs_id`.

## Examples

``` r
if (FALSE) { # \dontrun{
ppm_to_pgs('PPM000001')
ppm_to_pgs(c('PPM000017', 'PPM000042'))
} # }
```
