# Get PGS Catalog Performance Metrics

Retrieves performance metrics via the PGS Catalog REST API. The REST API
is queried multiple times with the criteria passed as arguments (see
below). By default all performance metrics that match the criteria
supplied in the arguments are retrieved: this corresponds to the default
option `set_operation` set to `'union'`. If you rather have only the
associations that match simultaneously all criteria provided, then set
`set_operation` to `'intersection'`.

## Usage

``` r
get_performance_metrics(
  ppm_id = NULL,
  pgs_id = NULL,
  set_operation = "union",
  interactive = TRUE,
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- ppm_id:

  A character vector of PGS Catalog performance metrics accession
  identifiers.

- pgs_id:

  A `character` vector of PGS Catalog score accession identifiers.

- set_operation:

  Either `'union'` or `'intersection'`. This tells how performance
  metrics retrieved by different criteria should be combined: `'union'`
  binds together all results removing duplicates and `'intersection'`
  only keeps same performance metrics found with different criteria.

- interactive:

  A logical. If all performance metrics are requested, whether to ask
  interactively if we really want to proceed.

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar as the queries are performed.

## Value

A
[performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md)
object.

## Details

Please note that all search criteria are vectorised, thus allowing for
batch mode search.

## Examples

``` r
if (FALSE) { # \dontrun{
# Get performance metrics catalogued with identifier 'PPM000001'
get_performance_metrics(ppm_id = 'PPM000001')

# Get performance metrics associated with polygenic score id 'PGS000001'
get_performance_metrics(pgs_id = 'PGS000001')

# To retrieve all catalogued performed metrics in PGS Catalog you simply
# leave the parameters `ppm_id` and `pgs_id` as `NULL`.
get_performance_metrics()
} # }
```
