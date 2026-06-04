# Get PGS Catalog Scores

Retrieves polygenic scores via the PGS Catalog REST API. The REST API is
queried multiple times with the criteria passed as arguments (see
below). By default all scores that match the criteria supplied in the
arguments are retrieved: this corresponds to the default option
`set_operation` set to `'union'`. If you rather have only the
associations that match simultaneously all criteria provided, then set
`set_operation` to `'intersection'`.

## Usage

``` r
get_scores(
  pgs_id = NULL,
  efo_id = NULL,
  pubmed_id = NULL,
  set_operation = "union",
  interactive = TRUE,
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- pgs_id:

  A `character` vector of PGS Catalog score accession identifiers.

- efo_id:

  A character vector of [EFO](https://www.ebi.ac.uk/efo/) identifiers.

- pubmed_id:

  An `integer` vector of [PubMed](https://en.wikipedia.org/wiki/PubMed)
  identifiers.

- set_operation:

  Either `'union'` or `'intersection'`. This tells how scores retrieved
  by different criteria should be combined: `'union'` binds together all
  results removing duplicates and `'intersection'` only keeps same
  scores found with different criteria.

- interactive:

  A logical. If all scores are requested, whether to ask interactively
  if we really want to proceed.

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar as the queries are performed.

## Value

A
[scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md)
object.

## Details

Please note that all search criteria are vectorised, thus allowing for
batch mode search.

## Examples

``` r
if (FALSE) { # \dontrun{
# By `pgs_id`
get_scores(pgs_id = 'PGS000088')

# By `efo_id`
get_scores(efo_id = 'EFO_0007992')

# By `pubmed_id`
get_scores(pubmed_id = '25748612')
} # }
```
