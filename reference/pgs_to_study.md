# Map PGS identifiers to GWAS study identifiers

Map PGS identifiers to GWAS study identifiers. Retrieves GWAS study
identifiers associated with samples used in the discovery stage of
queried PGS identifiers.

## Usage

``` r
pgs_to_study(
  pgs_id = NULL,
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- pgs_id:

  A character vector of PGS Catalog score accession identifiers., e.g.,
  "PGS000001". If `NULL` then returns results for all PGS identifiers in
  the Catalog.

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar as the queries are performed.

## Value

A data frame of two columns: `pgs_id` and `study_id`.

## Examples

``` r
if (FALSE) { # \dontrun{
pgs_to_study('PGS000001')
# Unmappable pgs ids will be missing, e.g., PGS000023
pgs_to_study(c('PGS000013', 'PGS000023'))
} # }
```
