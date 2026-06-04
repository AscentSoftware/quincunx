# An S4 class to represent a set of PGS Catalog Traits

The traits object consists of six slots, each a table
([`tibble`](https://tibble.tidyverse.org/reference/tibble.html)), that
combined form a relational database of a subset of PGS Catalog traits.
Each trait is an observation (row) in the `traits` table — main table.
All tables have the column `efo_id` as primary key.

## Slots

- `traits`:

  A table of traits. Columns:

  efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier.

  parent_efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier of
      the parent trait.

  is_child

  :   Is this trait obtained because it is a child of other trait?

  trait

  :   Trait name.

  description

  :   Detailed description of the trait from EFO.

  url

  :   External link to the EFO entry.

- `pgs_ids`:

  A table of associated polygenic score identifiers. Columns:

  efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier.

  parent_efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier of
      the parent trait.

  is_child

  :   Is this trait obtained because it is a child of other trait?

  pgs_id

  :   Polygenic Score (PGS) identifier.

- `child_pgs_ids`:

  A table of polygenic score identifiers associated with the child
  traits. Columns:

  efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier.

  parent_efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier of
      the parent trait.

  is_child

  :   Is this trait obtained because it is a child of other trait?

  child_pgs_id

  :   Polygenic Score (PGS) identifiers associated with child traits.

- `trait_categories`:

  A table of associated trait categories. Columns:

  efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier.

  parent_efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier of
      the parent trait.

  is_child

  :   Is this trait obtained because it is a child of other trait?

  trait_category

  :   Trait category name.

- `trait_synonyms`:

  A table of associated trait synonyms. Columns:

  efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier.

  parent_efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier of
      the parent trait.

  is_child

  :   Is this trait obtained because it is a child of other trait?

  trait_synonyms

  :   Trait synonyms.

- `trait_mapped_terms`:

  A table of associated external references, identifiers or other terms.
  Columns:

  efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier.

  parent_efo_id

  :   An [EFO](https://www.ebi.ac.uk/ols4/ontologies/efo/) identifier of
      the parent trait.

  is_child

  :   Is this trait obtained because it is a child of other trait?

  trait_mapped_terms

  :   Trait mapped terms.
