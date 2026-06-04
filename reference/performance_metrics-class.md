# An S4 class to represent a set of PGS Catalog Performance Metrics

The performance_metrics object consists of nine tables (slots) that
combined form a relational database of a subset of performance metrics.
Each performance metric is an observation (row) in the `scores` table
(first table).

## Slots

- `performance_metrics`:

  A table of PGS Performance Metrics (PPM). Each PPM (row) is uniquely
  identified by the `ppm_id` column. Columns:

  ppm_id

  :   A PGS Performance Metrics identifier. Example: `"PPM000001"`.

  pgs_id

  :   Polygenic Score (PGS) identifier.

  reported_trait

  :   The author-reported trait that the PGS has been developed to
      predict. Example: `"Breast Cancer"`.

  covariates

  :   Comma-separated list of covariates used in the prediction model to
      evaluate the PGS.

  comments

  :   Any other information relevant to the understanding of the
      performance metrics.

- `publications`:

  A table of publications. Each publication (row) is uniquely identified
  by the column `pgp_id`. Columns:

  ppm_id

  :   A PGS Performance Metrics identifier. Example: `"PPM000001"`.

  pgp_id

  :   PGS Publication identifier. Example: `"PGP000001"`.

  pubmed_id

  :   [PubMed](https://en.wikipedia.org/wiki/PubMed) identifier.
      Example: `"25855707"`.

  publication_date

  :   Publication date. Example: `"2020-09-28"`. Note that the class of
      `publication_date` is [`Date`](https://rdrr.io/r/base/Dates.html).

  publication

  :   Abbreviated name of the journal. Example: `"Am J Hum Genet"`.

  title

  :   Publication title.

  author_fullname

  :   First author of the publication. Example: `'Mavaddat N'`.

  doi

  :   Digital Object Identifier (DOI). This variable is also curated to
      allow unpublished work (e.g. preprints) to be added to the
      catalog. Example: `"10.1093/jnci/djv036"`.

- `sample_sets`:

  A table of sample sets. Each sample set (row) is uniquely identified
  by the column `pss_id`. Columns:

  ppm_id

  :   A PGS Performance Metrics identifier. Example: `"PPM000001"`.

  pss_id

  :   A PGS Sample Set identifier. Example: `"PSS000042"`.

- `samples`:

  A table of samples. Each sample (row) is uniquely identified by the
  combination of values from the columns: `ppm_id`, `pss_id`, and
  `sample_id`. Columns:

  ppm_id

  :   A PGS Performance Metrics identifier. Example: `"PPM000001"`.

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
  columns: `ppm_id`, `pss_id`, `sample_id`, and `variable`. Columns:

  ppm_id

  :   A PGS Performance Metrics identifier. Example: `"PPM000001"`.

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
  combination of values from the columns: `ppm_id`, `sample_id` and
  `cohort_symbol`. Columns:

  ppm_id

  :   A PGS Performance Metrics identifier. Example: `"PPM000001"`.

  sample_id

  :   Sample identifier. This is a surrogate key to identify each
      sample.

  cohort_symbol

  :   Cohort symbol.

  cohort_name

  :   Cohort full name.

- `pgs_effect_sizes`:

  A table of effect sizes per standard deviation change in PGS. Examples
  include regression coefficients (betas) for continuous traits, odds
  ratios (OR) and/or hazard ratios (HR) for dichotomous traits depending
  on the availability of time-to-event data. Each effect size is
  uniquely identified by the combination of values from the columns:
  `ppm_id` and `effect_size_id`. Columns:

  ppm_id

  :   A PGS Performance Metrics identifier. Example: `"PPM000001"`.

  effect_size_id

  :   Effect size identifier. This is a surrogate identifier to identify
      each effect size.

  estimate_type_long

  :   Long notation of the effect size (e.g. Odds Ratio).

  estimate_type

  :   Short notation of the effect size (e.g. OR).

  estimate

  :   The estimate's value.

  unit

  :   Unit of the estimate.

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

- `pgs_classification_metrics`:

  A table of classification metrics. Examples include the Area under the
  Receiver Operating Characteristic (AUROC) or Harrell's C-index
  (Concordance statistic). Columns:

  ppm_id

  :   A PGS Performance Metrics identifier. Example: `"PPM000001"`.

  classification_metrics_id

  :   Classification metric identifier. This is a surrogate identifier
      to identify each classification metric.

  estimate_type_long

  :   Long notation of the classification metric (e.g. Concordance
      Statistic).

  estimate_type

  :   Short notation classification metric (e.g. C-index).

  estimate

  :   The estimate's value.

  unit

  :   Unit of the estimate.

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

- `pgs_other_metrics`:

  A table of other metrics that are neither effect sizes nor
  classification metrics. Examples include: R² (proportion of the
  variance explained), or reclassification metrics. Columns:

  ppm_id

  :   A PGS Performance Metrics identifier. Example: `"PPM000001"`.

  other_metrics_id

  :   Other metric identifier. This is a surrogate identifier to
      identify each metric.

  estimate_type_long

  :   Long notation of the metric. Example: "Proportion of the variance
      explained".

  estimate_type

  :   Short notation metric. Example: "R²".

  estimate

  :   The estimate's value.

  unit

  :   Unit of the estimate.

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
