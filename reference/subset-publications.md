# Subset a publications object

You can subset
[publications](https://ascentsoftware.github.io/quincunx/reference/publications-class.md)
by identifier or by position using the `` `[` `` operator.

## Usage

``` r
# S4 method for class 'publications,missing,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'publications,numeric,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'publications,character,missing,missing'
x[i, j, ..., drop = FALSE]
```

## Arguments

- x:

  A
  [publications](https://ascentsoftware.github.io/quincunx/reference/publications-class.md)
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
[publications](https://ascentsoftware.github.io/quincunx/reference/publications-class.md)
object.

## Examples

``` r
if (FALSE) { # interactive()
# Get all publications in the PGS Catalog:
all_pub <- get_publications(interactive = FALSE, progress_bar = FALSE)

#
# Subsetting by position
#
all_pub[1:5]

#
# Subsetting by publication identifier (character)
#
all_pub['PGP000001']
}
```
