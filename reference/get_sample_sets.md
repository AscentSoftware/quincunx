# Get PGS Catalog Sample Sets

Retrieves sample sets via the PGS Catalog REST API. The REST API is
queried multiple times with the criteria passed as arguments (see
below). By default all sample sets that match the criteria supplied in
the arguments are retrieved: this corresponds to the default option
`set_operation` set to `'union'`. If you rather have only the
associations that match simultaneously all criteria provided, then set
`set_operation` to `'intersection'`.

## Usage

``` r
get_sample_sets(
  pss_id = NULL,
  pgs_id = NULL,
  set_operation = "union",
  interactive = TRUE,
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- pss_id:

  A character vector of PGS Catalog sample sets accession identifiers.

- pgs_id:

  A `character` vector of PGS Catalog score accession identifiers.

- set_operation:

  Either `'union'` or `'intersection'`. This tells how performance
  metrics retrieved by different criteria should be combined: `'union'`
  binds together all results removing duplicates and `'intersection'`
  only keeps same sample sets found with different criteria.

- interactive:

  A logical. If all sample sets are requested, whether to ask
  interactively if we really want to proceed.

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
[sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md)
object.

## Details

Please note that all search criteria are vectorised, thus allowing for
batch mode search.

## Examples

``` r
if (FALSE) { # \dontrun{
# Search by PGS identifier
get_sample_sets(pgs_id = 'PGS000013')

# Search by the PSS identifier
get_sample_sets(pss_id = 'PSS000068')
} # }
```
