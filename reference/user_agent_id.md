# User agent identification

Generates an S3 `request` object as defined by the package `httr`, that
is used to identify this package as the user agent in requests to the
PGS REST API. The user agent identification string is:
`"quincunx: R Client for the PGS REST API"`.

## Usage

``` r
user_agent_id()
```

## Value

An S3 `request` object as defined by the package `httr`.
