# An S4 class to represent a set of PGS Catalog Polygenic Scores

The scores object consists of six tables (slots) that combined form a
relational database of a subset of PGS Catalog polygenic scores. Each
score is an observation (row) in the `scores` table (the first table).

## Slots

- `scores`:

  A table of polygenic scores. Each polygenic score (row) is uniquely
  identified by the `pgs_id` column. Columns:

  pgs_id

  :   Polygenic Score (PGS) identifier. Example: `"PGS000001"`.

  pgs_name

  :   This may be the name that the authors describe the PGS with in the
      source publication, or a name that a curator of the PGS Catalog
      has assigned to identify the score during the curation process
      (before a PGS identifier has been given). Example: `PRS77_BC`.

  scoring_file

  :   URL to the scoring file on the PGS FTP server. Example:
      `"http://ftp.ebi.ac.uk/pub/databases/spot/pgs/scores/PGS000001/ScoringFiles/PGS000001.txt.gz"`.

  matches_publication

  :   Indicate if the PGS data matches the published polygenic score
      (`TRUE`). If not (`FALSE`), the authors have provided an
      alternative polygenic for the Catalog and some other data, such as
      performance metrics, may differ from the publication.

  reported_trait

  :   The author-reported trait that the PGS has been developed to
      predict. Example: `"Breast Cancer"`.

  trait_additional_description

  :   Any additional description not captured in the other columns.
      Example: `"Femoral neck BMD (g/cm2)"`.

  pgs_method_name

  :   The name or description of the method or computational algorithm
      used to develop the PGS.

  pgs_method_params

  :   A description of the relevant inputs and parameters relevant to
      the PGS development method/process.

  n_variants

  :   Number of variants used to calculate the PGS.

  n_variants_interactions

  :   Number of higher-order variant interactions included in the PGS.

  assembly

  :   The version of the genome assembly that the variants present in
      the PGS are associated with. Example: `GRCh37`.

  license

  :   The PGS Catalog distributes its data according to EBI's standard
      Terms of Use. Some PGS have specific terms, licenses, or
      restrictions (e.g. non-commercial use) that we highlight in this
      field, if known.

- `publications`:

  A table of publications. Each publication (row) is uniquely identified
  by the `pgp_id` column. Columns:

  pgs_id

  :   Polygenic Score (PGS) identifier.

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

- `samples`:

  A table of samples. Each sample (row) is uniquely identified by the
  combination of values from the columns: `pgs_id` and `sample_id`.
  Columns:

  pgs_id

  :   Polygenic score identifier. An identifier that starts with `'PGS'`
      and is followed by six digits, e.g. `'PGS000001'`.

  sample_id

  :   Sample identifier. This is a surrogate key to identify each
      sample.

  stage

  :   Sample stage: either `"discovery"` or `"training"`.

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
  columns: `pgs_id`, `sample_id` and `variable`. Columns:

  pgs_id

  :   Polygenic Score (PGS) identifier.

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
  combination of values from the columns: `pgs_id`, `sample_id` and
  `cohort_symbol`. Columns:

  pgs_id

  :   Polygenic Score (PGS) identifier.

  sample_id

  :   Sample identifier. This is a surrogate key to identify each
      sample.

  cohort_symbol

  :   Cohort symbol.

  cohort_name

  :   Cohort full name.

- `traits`:

  A table of EFO traits. Each trait (row) is uniquely identified by the
  combination of the columns `pgs_id` and `efo_id`. Columns:

  pgs_id

  :   Polygenic Score (PGS) identifier.

  efo_id

  :   An [EFO](https://www.ebi.ac.uk/efo/) identifier.

  trait

  :   Trait name.

  description

  :   Detailed description of the trait from EFO.

  url

  :   External link to the EFO entry.

- `stages_tally`:

  A table of sample sizes and number of samples sets at each stage.

  pgs_id

  :   Polygenic Score (PGS) identifier.

  stage

  :   Sample stage: either `"gwas"`, `"dev"` or `"eval"`.

  sample_size

  :   Sample size.

  n_sample_sets

  :   Number of sample sets (only meaningful for the evaluation stage
      `"eval"`)

- `ancestry_frequencies`:

  This table describes the ancestry composition at each stage.

  pgs_id

  :   Polygenic Score (PGS) identifier.

  stage

  :   Sample stage: either `"gwas"`, `"dev"` or `"eval"`.

  ancestry_class_symbol

  :   Ancestry class symbol.

  frequency

  :   Ancestry fraction (percentage).

- `multi_ancestry_composition`:

  A table of a breakdown of the ancestries included in multi-ancestries.

  pgs_id

  :   Polygenic Score (PGS) identifier.

  stage

  :   Sample stage: either `"gwas"`, `"dev"` or `"eval"`.

  multi_ancestry_class_symbol

  :   Multi-ancestry class symbol.

  ancestry_class_symbol

  :   Ancestry class symbol.
