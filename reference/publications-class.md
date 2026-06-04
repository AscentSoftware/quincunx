# An S4 class to represent a set of PGS Catalog Publications

The publications object consists of two tables (slots), each a table
that combined form a relational database of a subset of PGS Catalog
Publications. Each publication is an observation (row) in the
`publications` table (first table).

## Slots

- `publications`:

  A table of publications. Each publication (row) is uniquely identified
  by the `pgp_id` column. Columns:

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

  authors

  :   Concatenated list of all the publication authors.

- `pgs_ids`:

  A table of publication and associated PGS identifiers. Columns:

  pgp_id

  :   PGS Publication identifier. Example: `"PGP000001"`.

  pgs_id

  :   Polygenic Score (PGS) identifier.

  stage

  :   PGS stage: either "gwas/dev" or "eval".
