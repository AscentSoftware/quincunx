# Constructor for the S4 scores object.

Constructor for the S4
[scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md)
object.

## Usage

``` r
scores(
  scores = s4scores_scores_tbl(),
  publications = s4scores_publications_tbl(),
  samples = s4scores_samples_tbl(),
  demographics = s4scores_demographics_tbl(),
  cohorts = s4scores_cohorts_tbl(),
  traits = s4scores_traits_tbl(),
  stages_tally = s4scores_stages_tally_tbl(),
  ancestry_frequencies = s4scores_ancestry_frequencies_tbl(),
  multi_ancestry_composition = s4scores_multi_ancestry_composition_tbl()
)
```

## Arguments

- scores:

  A `s4scores_scores_tbl` tibble.

- publications:

  A `s4scores_publications_tbl` tibble.

- samples:

  A `s4scores_samples_tbl` tibble.

- demographics:

  A `s4scores_demographics_tbl` tibble.

- cohorts:

  A `s4scores_cohorts_tbl` tibble.

- traits:

  A `s4scores_traits_tbl` tibble.

## Value

An object of class
[scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md).
