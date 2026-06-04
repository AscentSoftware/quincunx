# Subset a performance_metrics object

You can subset
[performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md)
by identifier or by position using the `` `[` `` operator.

## Usage

``` r
# S4 method for class 'performance_metrics,missing,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'performance_metrics,numeric,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'performance_metrics,character,missing,missing'
x[i, j, ..., drop = FALSE]
```

## Arguments

- x:

  A
  [performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md)
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
[performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md)
object.

## Examples

``` r
if (FALSE) { # interactive()
# Get a few performance metrics:
my_ppm <- get_performance_metrics(sprintf('PPM%06d', 38:42))

#
# Subsetting by position
#
my_ppm[c(1, 4)]

#
# Subsetting by performance metrics identifier (character)
#
my_ppm['PPM000042']
}
```
