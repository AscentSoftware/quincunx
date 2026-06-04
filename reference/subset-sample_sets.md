# Subset a sample_sets object

You can subset
[sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md)
by identifier or by position using the `` `[` `` operator.

## Usage

``` r
# S4 method for class 'sample_sets,missing,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'sample_sets,numeric,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'sample_sets,character,missing,missing'
x[i, j, ..., drop = FALSE]
```

## Arguments

- x:

  A
  [sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md)
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
[sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md)
object.

## Examples

``` r
if (FALSE) { # interactive()
# Get a few sample sets:
my_pss <- get_sample_sets(sprintf('PSS%06d', 42:48))

#
# Subsetting by position
#
my_pss[c(1, 3)]

#
# Subsetting by sample set identifier (character)
#
my_pss['PSS000042']
}
```
