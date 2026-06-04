# Constructor for the S4 performance_metrics object.

Constructor for the S4
[performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md)
object.

## Usage

``` r
performance_metrics(
  performance_metrics = s4ppm_performance_metrics_tbl(),
  publications = s4ppm_publications_tbl(),
  sample_sets = s4ppm_sample_sets_tbl(),
  samples = s4ppm_samples_tbl(),
  demographics = s4ppm_demographics_tbl(),
  cohorts = s4ppm_pgs_cohorts_tbl(),
  pgs_effect_sizes = s4ppm_pgs_effect_sizes_tbl(),
  pgs_classification_metrics = s4ppm_pgs_classification_metrics_tbl(),
  pgs_other_metrics = s4ppm_pgs_other_metrics_tbl()
)
```

## Arguments

- performance_metrics:

  A `s4ppm_performance_metrics_tbl` tibble.

- publications:

  A `s4ppm_publications_tbl` tibble.

- sample_sets:

  A `s4ppm_sample_sets_tbl` tibble.

- samples:

  A `s4ppm_samples_tbl` tibble.

- demographics:

  A `s4ppm_demographics_tbl` tibble.

- cohorts:

  A `s4ppm_pgs_cohorts_tbl` tibble.

- pgs_effect_sizes:

  A `s4ppm_pgs_effect_sizes_tbl` tibble.

- pgs_classification_metrics:

  A `s4ppm_pgs_classification_metrics_tbl` tibble.

- pgs_other_metrics:

  A `s4ppm_pgs_other_metrics_tbl` tibble.

## Value

An object of class
[performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md).
