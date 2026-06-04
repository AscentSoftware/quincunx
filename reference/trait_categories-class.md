# An S4 class to represent a set of PGS Catalog Trait Categories

The trait_categories object consists of two tables (slots) that combined
form a relational database of a subset of PGS Catalog trait categories.
Each score is an observation (row) in the `trait_categories` table
(first table).

## Slots

- `trait_categories`:

  A table of trait categories. Columns:

  trait_category

  :   Trait category name.

- `traits`:

  A table of associated traits. Columns:

  trait_category

  :   Trait category name.

  efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier.

  trait

  :   Trait name.

  description

  :   Detailed description of the trait from EFO.

  url

  :   External link to the EFO entry.
