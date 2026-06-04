# Number of PGS Catalog entities

This function returns the number of entities in a PGS Catalog object. To
avoid ambiguity with
[`dplyr::n()`](https://dplyr.tidyverse.org/reference/context.html) use
`quincunx::n()`.

## Usage

``` r
n(x, unique = FALSE)

# S4 method for class 'scores'
n(x, unique = FALSE)

# S4 method for class 'publications'
n(x, unique = FALSE)

# S4 method for class 'traits'
n(x, unique = FALSE)

# S4 method for class 'performance_metrics'
n(x, unique = FALSE)

# S4 method for class 'sample_sets'
n(x, unique = FALSE)

# S4 method for class 'cohorts'
n(x, unique = FALSE)

# S4 method for class 'trait_categories'
n(x, unique = FALSE)

# S4 method for class 'releases'
n(x, unique = FALSE)
```

## Arguments

- x:

  A
  [scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md),
  [publications](https://ascentsoftware.github.io/quincunx/reference/publications-class.md),
  [traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md),
  [performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md),
  [sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md),
  [cohorts](https://ascentsoftware.github.io/quincunx/reference/cohorts-class.md),
  [trait_categories](https://ascentsoftware.github.io/quincunx/reference/trait_categories-class.md)
  or
  [releases](https://ascentsoftware.github.io/quincunx/reference/releases-class.md)
  object.

- unique:

  Whether to count only unique entries (`TRUE`) or not (`FALSE`).

## Value

An integer scalar.

## Examples

``` r
if (FALSE) { # interactive()
# Return the number of polygenic scores in a scores object:
my_scores <- get_scores(pgs_id = c('PGS000007', 'PGS000007', 'PGS000042'))
n(my_scores)

# If you want to count unique scores only, then use the `unique` parameter:
n(my_scores, unique = TRUE)

# Total number of curated publications in the PGS Catalog:
all_pub <- get_publications(interactive = FALSE, progress_bar = FALSE)
n(all_pub)

# Total number of curated traits in the PGS Catalog:
all_traits <- get_traits(interactive = FALSE, progress_bar = FALSE)
n(all_traits)
}
```
