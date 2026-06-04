# An S4 class to represent a set of cohorts

The cohorts object consists of two tables (slots) that combined form a
relational database of a subset of cohorts. Each cohort is an
observation (row) in the `cohorts` table (first table).

## Slots

- `cohorts`:

  A table of cohorts. Each cohort (row) is identified by its
  `cohort_symbol`. Columns:

  cohort_symbol

  :   Cohort symbol. Example: `"CECILE"`.

  cohort_name

  :   Cohort full name. Example: `"CECILE Breast Cancer Study"`.

- `pgs_ids`:

  A table of cohorts and their associated polygenic scores identifiers.
  Columns:

  cohort_symbol

  :   Cohort symbol. Example: `"CECILE"`.

  pgs_id

  :   Polygenic Score (PGS) identifier.

  stage

  :   Sample stage: either `"gwas/dev"` or `"eval"`.
