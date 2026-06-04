# Request a resource from the PGS REST API

Performs a [`GET`](https://httr.r-lib.org/reference/GET.html) request on
the endpoint as specified by `resource_url`.

## Usage

``` r
request(
  resource_url,
  base_url = pgs_server(),
  user_agent = user_agent_id(),
  verbose = FALSE,
  warnings = TRUE
)
```

## Arguments

- resource_url:

  Endpoint URL. The endpoint is internally appended to the `base_url`.
  It should start with a forward slash (`'/'`).

- base_url:

  The PGS REST API base URL.

- user_agent:

  User agent.

- verbose:

  Whether to be verbose.

- warnings:

  Whether to print warnings.

## Value

A named list of four elements:

- resource:

  The URL endpoint.

- code:

  [HTTP status
  code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes).

- message:

  A string describing the status of the response obtained: `'OK'` if
  successful or a description of the error.

- json:

  JSON response as string.
