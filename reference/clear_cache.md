# Clear quincunx cache of memoised functions

quincunx uses memoised functions for the REST API calls. Use this
function to reset the cache.

## Usage

``` r
clear_cache()
```

## Value

Returns a logical value, indicating whether the resetting of the cache
was successful (`TRUE`) or not `FALSE`.

## Examples

``` r
clear_cache()
#> [1] TRUE
```
