# Subset a cohorts object

You can subset
[cohorts](https://ascentsoftware.github.io/quincunx/reference/cohorts-class.md)
by identifier or by position using the `` `[` `` operator.

## Usage

``` r
# S4 method for class 'cohorts,missing,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'cohorts,numeric,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'cohorts,character,missing,missing'
x[i, j, ..., drop = FALSE]
```

## Arguments

- x:

  A
  [cohorts](https://ascentsoftware.github.io/quincunx/reference/cohorts-class.md)
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
[cohorts](https://ascentsoftware.github.io/quincunx/reference/cohorts-class.md)
object.

## Examples

``` r
if (FALSE) { # interactive()
# Get a few cohorts by their symbol:
my_cohorts <- get_cohorts(c('23andMe', 'BioImage', 'Rotterdam-SI', 'SGWAS'),
                progress_bar = FALSE)

#
# Subsetting by position
#
my_cohorts[c(1, 3)]

#
# Subsetting by cohort symbol (character)
#
my_cohorts[c('23andMe', 'SGWAS')]
}
```
