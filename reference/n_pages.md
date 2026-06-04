# Number of pages

Determine the number of pages to be requested from the total number of
results (`count`) and the number of results per page (`limit`). The
wording used here — `count` and `limit` — is borrowed from the PGS
Catalog REST API documentation.

## Usage

``` r
n_pages(count, limit = 50L)
```

## Arguments

- count:

  total number of results.

- limit:

  number of results per page.

## Value

The number of pages, an integer value.
