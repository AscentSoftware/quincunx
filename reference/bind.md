# Bind PGS Catalog objects

Binds together PGS Catalog objects of the same class. Note that `bind()`
preserves duplicates whereas
[`union`](https://ascentsoftware.github.io/quincunx/reference/setop.md)
does not.

## Usage

``` r
bind(x, ...)
```

## Arguments

- x:

  An object of either class
  [scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md),
  [publications](https://ascentsoftware.github.io/quincunx/reference/publications-class.md),
  [traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md),
  [performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md),
  [sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md),
  [cohorts](https://ascentsoftware.github.io/quincunx/reference/cohorts-class.md)
  or
  [trait_categories](https://ascentsoftware.github.io/quincunx/reference/trait_categories-class.md).

- ...:

  Objects of the same class as `x`.

## Value

An object of the same class as `x`.

## Examples

``` r
if (FALSE) { # interactive()
# Get some `scores` objects:
my_scores_1 <- get_scores(c('PGS000012', 'PGS000013'))
my_scores_2 <- get_scores(c('PGS000013', 'PGS000014'))

# NB: with `bind()`, PGS000013 is repeated (as opposed to `union()`)
bind(my_scores_1, my_scores_2)@scores
}
```
