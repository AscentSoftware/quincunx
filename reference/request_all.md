# Request a paginated resource from the PGS REST API

Performs a GET request on the specified `resource_url` and all its
pages.

## Usage

``` r
request_all(
  resource_url = "/",
  base_url = pgs_server(),
  limit = 20L,
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- resource_url:

  Endpoint URL. The endpoint is internally appended to the `base_url`.
  It should start with a forward slash (`/`).

- base_url:

  The PGS REST API base URL (one should not need to change its default
  value).

- limit:

  number of results per page.

- verbose:

  whether to print information about each API request.

- warnings:

  whether to print warnings related to API requests.

- progress_bar:

  whether to show a progress bar as the paginated resources are
  retrieved.

## Value

A list four named elements:

- resource:

  The URL endpoint.

- code:

  [HTTP status
  code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes).

- message:

  A string describing the status of the response obtained. It is "OK" if
  everything went OK or some other string describing the problem.

- json:

  A list of JSON responses (each response is a string).
