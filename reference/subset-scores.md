# Subset a scores object

You can subset
[scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md)
by identifier or by position using the `` `[` `` operator.

## Usage

``` r
# S4 method for class 'scores,missing,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'scores,numeric,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'scores,character,missing,missing'
x[i, j, ..., drop = FALSE]
```

## Arguments

- x:

  A
  [scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md)
  object.

- i:

  Position of the identifier or the name of the identifier itself.

- j:

  Not used.

- ...:

  Additional arguments not used here.

- drop:

  Not used.

## Value

A
[scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md)
object.

## Examples

``` r
if (FALSE) { # interactive()
# Get a few polygenic scores:
my_scores <- get_scores(sprintf('PGS%06d', 10:14), progress_bar = FALSE)

#
# Subsetting by position
#
my_scores[c(1, 3, 5)]@scores

#
# Subsetting by PGS identifier (character)
#
my_scores[c('PGS000011', 'PGS000014')]@scores
}
```
