# Get PGS Catalog Releases

This function retrieves PGS Catalog release information. Note that the
columns `pgs_id`, `ppm_id` and `pgp_id` contain in each element a
vector. These columns can be unnested using
[`unnest_longer`](https://tidyr.tidyverse.org/reference/unnest_longer.html)
(see Examples).

## Usage

``` r
get_releases(
  date = "latest",
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- date:

  One or more dates formatted as `"YYYY-MM-DD"` for respective releases,
  `"latest"` for the latest release, or `"all"` for all releases.

- verbose:

  Whether to print information about the underlying requests to the REST
  API server.

- warnings:

  Whether to print warnings about the underlying requests to the REST
  API server.

- progress_bar:

  Whether to show a progress bar indicating download progress from the
  REST API server.

## Value

A data frame where each row is a release. Columns are:

- date:

  Release date.

- n_pgs:

  Number of released Polygenic Score (PGS) identifiers (`pgs_id`).

- n_ppm:

  Number of released Performance Metric (PPM) identifiers (`ppm_id`).

- n_pgp:

  Number of released PGS Catalog Publication (PGP) identifiers
  (`pgp_id`).

- pgs_id:

  Released Polygenic Score (PGS) identifiers.

- ppm_id:

  Released Performance Metric (PPM) identifiers.

- pgp_id:

  Released PGS Catalog Publication (PGP) identifiers.

- notes:

  News about the release.

## Examples

``` r
if (FALSE) { # \dontrun{
# Get the latest release
get_releases()
get_releases(date = 'latest')

# Get all releases
get_releases(date = 'all')

# Get a specific release by date
get_releases(date = '2020-08-19')
} # }
```
