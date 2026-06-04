# Get PGS Catalog Publications

Retrieves PGS publications via the PGS Catalog REST API. The REST API is
queried multiple times with the criteria passed as arguments (see
below). By default all publications that match the criteria supplied in
the arguments are retrieved: this corresponds to the default option
`set_operation` set to `'union'`. If you rather have only the
associations that match simultaneously all criteria provided, then set
`set_operation` to `'intersection'`.

## Usage

``` r
get_publications(
  pgp_id = NULL,
  pgs_id = NULL,
  pubmed_id = NULL,
  author = NULL,
  set_operation = "union",
  interactive = TRUE,
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- pgp_id:

  A character vector of PGS Catalog publication accession identifiers.

- pgs_id:

  A `character` vector of PGS Catalog score accession identifiers.

- pubmed_id:

  An `integer` vector of [PubMed](https://en.wikipedia.org/wiki/PubMed)
  identifiers.

- author:

  A character vector of author names, any author in the list of authors
  in a publication, .e.g. `'Mavaddat'`.

- set_operation:

  Either `'union'` or `'intersection'`. This tells how publications
  retrieved by different criteria should be combined: `'union'` binds
  together all results removing duplicates and `'intersection'` only
  keeps same publications found with different criteria.

- interactive:

  A logical. If all publications are requested, whether to ask
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
[publications](https://ascentsoftware.github.io/quincunx/reference/publications-class.md)
object.

## Details

Please note that all search criteria are vectorised, thus allowing for
batch mode search. For more details see the help vignette:
[`vignette("getting-pgs-publications", package = "quincunx")`](https://ascentsoftware.github.io/quincunx/articles/getting-pgs-publications.md).

## Examples

``` r
if (FALSE) { # \dontrun{
# Get PGS publications by their identifier
get_publications(pgp_id = c('PGP000001', 'PGP000002'))

# By polygenic score identifier
get_publications(pgs_id = 'PGS000003')

# By PubMed identifier
get_publications(pubmed_id = '30554720')

# By author's last name
get_publications(author = 'Natarajan')
} # }
```
