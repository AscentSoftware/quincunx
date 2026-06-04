# Subset a releases object

You can subset
[releases](https://ascentsoftware.github.io/quincunx/reference/releases-class.md)
by identifier (release date) or by position using the `` `[` ``
operator.

## Usage

``` r
# S4 method for class 'releases,missing,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'releases,numeric,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'releases,character,missing,missing'
x[i, j, ..., drop = FALSE]

# S4 method for class 'releases,Date,missing,missing'
x[i, j, ..., drop = FALSE]
```

## Arguments

- x:

  A
  [releases](https://ascentsoftware.github.io/quincunx/reference/releases-class.md)
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
[releases](https://ascentsoftware.github.io/quincunx/reference/releases-class.md)
object.

## Examples

``` r
if (FALSE) { # interactive()
# Get details about all PGS Catalog data releases thus far:
all_releases <- get_releases(date = 'all', progress_bar = FALSE)

#
# Subsetting by position
#
# Releases are, by default, sorted by date in descending order, thus the
# first PGS Catalog release is in the last position of the returned
# `all_releases` object. Here's how you can extract that first release (last
# position in `all_releases`):
all_releases[n(all_releases)]

#
# Subsetting by date (character)
#
date_of_interest <- '2021-06-11'
class(date_of_interest)
all_releases[date_of_interest]

#
# Subsetting by date (Date object)
#
date_of_interest <- as.Date('2021-06-11')
class(date_of_interest)
all_releases[date_of_interest]
}
```
