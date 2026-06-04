# Constructor for the S4 traits object.

Constructor for the S4
[traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md)
object.

## Usage

``` r
traits(
  traits = s4traits_traits_tbl(),
  pgs_ids = s4traits_pgs_ids_tbl(),
  child_pgs_ids = s4traits_child_pgs_ids_tbl(),
  trait_categories = s4traits_trait_categories_tbl(),
  trait_synonyms = s4traits_trait_synonyms_tbl(),
  trait_mapped_terms = s4traits_trait_mapped_terms_tbl()
)
```

## Arguments

- traits:

  A `s4traits_traits_tbl` tibble.

- pgs_ids:

  A `s4traits_pgs_ids_tbl` tibble.

- child_pgs_ids:

  A `s4traits_child_pgs_ids_tbl` tibble.

- trait_categories:

  A `s4traits_trait_categories_tbl` tibble.

- trait_synonyms:

  A `s4traits_trait_synonyms_tbl` tibble.

- trait_mapped_terms:

  A `s4traits_trait_mapped_terms_tbl` tibble.

## Value

An object of class
[traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md).
