# Subset a traits object

You can subset
[traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md)
by identifier or by position using the `` `[` `` operator.

## Usage

``` r
# S4 method for class 'traits,missing,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'traits,numeric,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'traits,character,missing,missing'
x[i, j, ..., drop = FALSE]
```

## Arguments

- x:

  A
  [traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md)
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
[traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md)
object.

## Examples

``` r
if (FALSE) { # interactive()
# Get a few traits:
my_traits <- get_traits(trait_term = 'stroke', exact_term = FALSE,
               progress_bar = FALSE)

#
# Subsetting by position
#
my_traits[1]

#
# Subsetting by EFO trait identifier (character)
#
my_traits['EFO_0000712']
}
```
