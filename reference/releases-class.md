# An S4 class to represent a set of PGS Catalog Releases

The releases object consists of four tables (slots) that combined form a
relational database of a subset of PGS Catalog releases. Each release is
an observation (row) in the `releases` table (first table).

## Slots

- `releases`:

  A table of PGS Catalog releases. Each release (row) is uniquely
  identified by the release date (`date`). Columns:

  date

  :   Release date.

  n_pgs

  :   Number of newly released Polygenic Scores.

  n_ppm

  :   Number of newly released PGS Performance Metrics.

  n_pgp

  :   Number of newly released PGS Publications.

- `pgs_ids`:

  A table of released Polygenic Scores (PGS) identifiers. Columns:

  date

  :   Release date.

  pgs_id

  :   Polygenic Score (PGS) identifier. Example: `"PGS000001"`.

- `ppm_ids`:

  A table of the released PGS Performance Metrics identifiers. Columns:

  date

  :   Release date.

  ppm_id

  :   A PGS Performance Metrics identifier. Example: `"PPM000001"`.

- `pgp_ids`:

  A table of the released PGS Publication identifiers. Columns:

  date

  :   Release date.

  pgp_id

  :   PGS Publication identifier. Example: `"PGP000001"`.
