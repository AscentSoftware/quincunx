# Extract the count field from a JSON response

This function takes a string with a JSON response and returns the value
of the count field. If it fails to match the pattern then it returns
`NA_integer_`.

## Usage

``` r
count(json_string)
```

## Arguments

- json_string:

  a string.

## Value

An integer value.
