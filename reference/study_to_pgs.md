# Map GWAS studies identifiers to PGS identifiers

Map GWAS studies identifiers to PGS identifiers.

## Usage

``` r
study_to_pgs(study_id, verbose = FALSE, warnings = TRUE, progress_bar = TRUE)
```

## Arguments

- study_id:

  A character vector of GWAS Catalog study accession identifiers, e.g.,
  "GCST001937".

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar as the queries are performed.

## Value

A data frame of two columns: `study_id` and `pgs_id`.

## Examples

``` r
if (FALSE) { # \dontrun{
study_to_pgs('GCST001937')
study_to_pgs(c('GCST000998', 'GCST000338'))
} # }
```
