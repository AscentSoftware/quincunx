# Set operations on PGS Catalog objects

Performs set union, intersection, and (asymmetric!) difference on two
objects of either class
[scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md),
[publications](https://ascentsoftware.github.io/quincunx/reference/publications-class.md),
[traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md),
[performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md),
[sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md),
[cohorts](https://ascentsoftware.github.io/quincunx/reference/cohorts-class.md)
or
[trait_categories](https://ascentsoftware.github.io/quincunx/reference/trait_categories-class.md).
Note that `union()` removes duplicated entities, whereas
[`bind()`](https://ascentsoftware.github.io/quincunx/reference/bind.md)
does not.

## Usage

``` r
union(x, y, ...)

intersect(x, y, ...)

setdiff(x, y, ...)

setequal(x, y, ...)
```

## Arguments

- x, y:

  Objects of either class
  [scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md),
  [publications](https://ascentsoftware.github.io/quincunx/reference/publications-class.md),
  [traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md),
  [performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md),
  [sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md),
  [cohorts](https://ascentsoftware.github.io/quincunx/reference/cohorts-class.md)
  or
  [trait_categories](https://ascentsoftware.github.io/quincunx/reference/trait_categories-class.md).

- ...:

  other arguments passed on to methods.

## Value

In the case of `union()`, `intersect()`, or `setdiff()`: an object of
the same class as `x` and `y`. In the case of `setequal()`, a logical
scalar.

## Examples

``` r
if (FALSE) { # interactive()
# Get some `scores` objects:
my_scores_1 <- get_scores(c('PGS000012', 'PGS000013'))
my_scores_2 <- get_scores(c('PGS000013', 'PGS000014'))

#
# union()
#
# NB: with `union()`, PGS000013 is not repeated.
union(my_scores_1, my_scores_2)@scores

#
# intersect()
#
intersect(my_scores_1, my_scores_2)@scores

#
# setdiff()
#
setdiff(my_scores_1, my_scores_2)@scores

#
# setequal()
#
setequal(my_scores_1, my_scores_2)
setequal(my_scores_1, my_scores_1)
setequal(my_scores_2, my_scores_2)
}
```
