# Generate offset values

Generate offset values to be passed to the PGS Catalog REST API
endpoints. The offset parameter, together with the limit parameter,
allow to access to a desired range of results. The offset parameter
specifies the starting index of the range of results desired. It is a
zero based index.

## Usage

``` r
offsets(count, limit)
```

## Arguments

- count:

  total number of results.

- limit:

  number of results per page.

## Value

Offset values, an integer vector.
