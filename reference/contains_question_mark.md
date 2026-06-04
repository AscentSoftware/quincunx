# Does a string contain a question mark?

Find which strings contain a question mark. This function uses the
following regular expression: `[\?]`.

## Usage

``` r
contains_question_mark(str, convert_NA_to_FALSE = TRUE)
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
