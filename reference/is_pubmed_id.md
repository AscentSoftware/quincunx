# Is a string a PubMed ID?

Find which strings are valid PubMed IDs (returns `TRUE`). PubMed IDs are
tested against the following regular expression: `^\\d+$`.

## Usage

``` r
is_pubmed_id(str, convert_NA_to_FALSE = TRUE)
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
