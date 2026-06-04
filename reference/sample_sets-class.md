# An S4 class to represent a set of PGS Catalog Sample Sets

The sample_sets object consists of four tables (slots) that combined
form a relational database of a subset of PGS Catalog sample sets. Each
sample set is an observation (row) in the `sample_sets` table (first
table).

## Slots

- `sample_sets`:

  A table of sample sets. Each sample set (row) is uniquely identified
  by the column `pss_id`. Columns:

  pss_id

  :   A PGS Sample Set identifier. Example: `"PSS000042"`.

- `samples`:

  A table of samples. Each sample (row) is uniquely identified by the
  combination of values from the columns: `pss_id` and `sample_id`.
  Columns:

  pss_id

  :   A PGS Sample Set identifier. Example: `"PSS000042"`.

  sample_id

  :   Sample identifier. This is a surrogate key to identify each
      sample.

  stage

  :   Sample stage: should be always Evaluation (`"eval"`).

  sample_size

  :   Number of individuals included in the sample.

  sample_cases

  :   Number of cases.

  sample_controls

  :   Number of controls.

  sample_percent_male

  :   Percentage of male participants.

  phenotype_description

  :   Detailed phenotype description.

  ancestry_category

  :   Author reported ancestry is mapped to the best matching ancestry
      category from the NHGRI-EBI GWAS Catalog framework (see
      [`ancestry_categories`](https://ascentsoftware.github.io/quincunx/reference/ancestry_categories.md))
      for possible values.

  ancestry

  :   A more detailed description of sample ancestry that usually
      matches the most specific description described by the authors
      (e.g. French, Chinese).

  country

  :   Author reported countries of recruitment (if available).

  ancestry_additional_description

  :   Any additional description not captured in the other columns (e.g.
      founder or genetically isolated populations, or further
      description of admixed samples).

  study_id

  :   Associated GWAS Catalog study accession identifier, e.g.,
      `"GCST002735"`.

  pubmed_id

  :   [PubMed](https://en.wikipedia.org/wiki/PubMed) identifier.

  cohorts_additional_description

  :   Any additional description about the samples (e.g. sub-cohort
      information).

- `demographics`:

  A table of sample demographics' variables. Each demographics' variable
  (row) is uniquely identified by the combination of values from the
  columns: `pss_id`, `sample_id`, and `variable`. Columns:

  pss_id

  :   A PGS Sample Set identifier. Example: `"PSS000042"`.

  sample_id

  :   Sample identifier. This is a surrogate identifier to identify each
      sample.

  variable

  :   Demographics variable. Following columns report about the
      indicated variable.

  estimate_type

  :   Type of statistical estimate for variable.

  estimate

  :   The variable's statistical value.

  unit

  :   Unit of the variable.

  variability_type

  :   Measure of statistical dispersion for variable, e.g. standard
      error (se) or standard deviation (sd).

  variability

  :   The value of the measure of dispersion.

  interval_type

  :   Type of statistical interval for variable: range, iqr
      (interquartile), ci (confidence interval).

  interval_lower

  :   Interval lower bound.

  interval_upper

  :   Interval upper bound.

- `cohorts`:

  A table of cohorts. Each cohort (row) is uniquely identified by the
  combination of values from the columns: `pss_id`, `sample_id` and
  `cohort_symbol`. Columns:

  pss_id

  :   A PGS Sample Set identifier. Example: `"PSS000042"`.

  sample_id

  :   Sample identifier. This is a surrogate key to identify each
      sample.

  cohort_symbol

  :   Cohort symbol.

  cohort_name

  :   Cohort full name.
