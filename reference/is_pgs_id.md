# Is a string a PGS Catalog identifier?

Find which strings are valid PGS Catalog identifiers (returns `TRUE`).
Association IDs are tested against the following regular expression:
`^PGS\\d{6}$`.

## Usage

``` r
is_pgs_id(str, convert_NA_to_FALSE = TRUE)
```

## Arguments

- str:

  A character vector of strings.

- convert_NA_to_FALSE:

  Whether to treat `NA` as `NA` (`convert_NA_to_FALSE = FALSE`) or
  whether to return `FALSE` when an `NA` is found
  (`convert_NA_to_FALSE = TRUE`).

## Value

A logical vector.
