# Changelog

## quincunx v0.2.0

- Resubmission after archival due to
  <https://github.com/colearendt/tidyjson/pull/152>.
- Maintainer affiliation changed to include Acuity Analytics.

## quincunx v0.1.10

CRAN release: 2025-05-31

- Removed dependency on package concatenate as it is in risk of being
  archived.

## quincunx 0.1.9

CRAN release: 2025-03-20

- Converted magrittr pipe to native pipe in internal code and in
  vignettes.

## quincunx 0.1.8

- Fixes issue <https://github.com/maialab/quincunx/issues/3> by
  introducing a rate limit on requests of 80 requests per minute.
- Make parsing of `estimate` variable more robust, i.e. parse `estimate`
  values even when the values come as strings with intervals,
  e.g. `"62.4 [48.9, 75.9]"`.
- PubMed ids are now parsed as integers in line with PGS Catalog API
  docs.

## quincunx 0.1.7

CRAN release: 2023-07-04

- Support reading harmonized PGS scoring files with
  [`read_scoring_file()`](https://ascentsoftware.github.io/quincunx/reference/read_scoring_file.md).

## quincunx 0.1.6

- Make official online documentation at <https://rmagno.eu/quincunx/>.

## quincunx 0.1.5

CRAN release: 2022-08-14

- [`read_scoring_file()`](https://ascentsoftware.github.io/quincunx/reference/read_scoring_file.md)
  has been updated to work with version 2.0 of PGS scoring file format.
