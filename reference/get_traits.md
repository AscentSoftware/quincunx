# Get PGS Catalog Traits

Retrieves traits via the PGS Catalog REST API. The REST API is queried
multiple times with the criteria passed as arguments (see below). By
default all traits that match the criteria supplied in the arguments are
retrieved: this corresponds to the default option `set_operation` set to
`'union'`. If you rather have only the traits that match simultaneously
all criteria provided, then set `set_operation` to `'intersection'`.

## Usage

``` r
get_traits(
  efo_id = NULL,
  trait_term = NULL,
  exact_term = TRUE,
  include_children = FALSE,
  set_operation = "union",
  interactive = TRUE,
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- efo_id:

  A character vector of [EFO](https://www.ebi.ac.uk/efo/) identifiers.

- trait_term:

  A character vector of terms to be matched against trait identifiers
  (`efo_id`), trait descriptions, synonyms thereof, externally mapped
  terms, or even trait categories.

- exact_term:

  A logical value, indicating whether to match the `trait_term` exactly
  (`TRUE`) or not (`FALSE`).

- include_children:

  A logical value, indicating whether to include child traits or not.

- set_operation:

  Either `'union'` or `'intersection'`. This tells how performance
  metrics retrieved by different criteria should be combined: `'union'`
  binds together all results removing duplicates and `'intersection'`
  only keeps same sample sets found with different criteria.

- interactive:

  A logical. If all traits are requested, whether to ask interactively
  if we really want to proceed.

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
[traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md)
object.

## Details

Please note that all search criteria are vectorised, thus allowing for
batch mode search.

## Examples

``` r
if (FALSE) { # \dontrun{
# Get a trait by its EFO identifier
get_traits(efo_id = 'EFO_0004631')

# Get a trait by matching a term in EFO identifier (`efo_id`), label,
# description synonyms, categories, or external mapped terms
get_traits(trait_term = 'stroke', exact_term = FALSE)

# Get a trait matching its name (`trait`) exactly (default)
get_traits(trait_term = 'stroke', exact_term = TRUE)

# Get traits, excluding its children traits (default)
get_traits(trait_term = 'breast cancer')

# Get traits, including its children traits (check column `is_child` for
# child traits)
get_traits(trait_term = 'breast cancer', include_children = TRUE)
} # }
```
