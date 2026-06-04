# Constructor for the S4 sample_sets object.

Constructor for the S4
[sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md)
object.

## Usage

``` r
sample_sets(
  sample_sets = s4pss_sample_sets_tbl(),
  samples = s4pss_samples_tbl(),
  demographics = s4pss_demographics_tbl(),
  cohorts = s4pss_pgs_cohorts_tbl()
)
```

## Arguments

- sample_sets:

  A `s4pss_sample_sets_tbl` tibble.

- samples:

  A `s4pss_samples_tbl` tibble.

- demographics:

  A `s4pss_demographics_tbl` tibble.

- cohorts:

  A `s4pss_pgs_cohorts_tbl` tibble.

## Value

An object of class
[sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md).
