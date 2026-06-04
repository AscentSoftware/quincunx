# Subset a trait_categories object

You can subset
[trait_categories](https://ascentsoftware.github.io/quincunx/reference/trait_categories-class.md)
by trait category (string) or by position using the `` `[` `` operator.

## Usage

``` r
# S4 method for class 'trait_categories,missing,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'trait_categories,numeric,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'trait_categories,character,missing,missing'
x[i, j, ..., drop = FALSE]
```

## Arguments

- x:

  A
  [trait_categories](https://ascentsoftware.github.io/quincunx/reference/trait_categories-class.md)
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
[trait_categories](https://ascentsoftware.github.io/quincunx/reference/trait_categories-class.md)
object.

## Examples

``` r
if (FALSE) { # interactive()
# Get details about all trait categories:
all_trait_categories <- get_trait_categories(progress_bar = FALSE)

#
# Subsetting by position
#
all_trait_categories[1:5]

#
# Subsetting by trait category (character)
#
all_trait_categories['Liver enzyme measurement']
}
```
