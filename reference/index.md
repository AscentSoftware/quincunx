# Package index

## Get PGS Catalog Data

Receive data from the PGS Catalog REST API.

- [`get_scores()`](https://ascentsoftware.github.io/quincunx/reference/get_scores.md)
  : Get PGS Catalog Scores
- [`read_scoring_file()`](https://ascentsoftware.github.io/quincunx/reference/read_scoring_file.md)
  : Read a polygenic scoring file
- [`get_publications()`](https://ascentsoftware.github.io/quincunx/reference/get_publications.md)
  : Get PGS Catalog Publications
- [`get_performance_metrics()`](https://ascentsoftware.github.io/quincunx/reference/get_performance_metrics.md)
  : Get PGS Catalog Performance Metrics
- [`get_sample_sets()`](https://ascentsoftware.github.io/quincunx/reference/get_sample_sets.md)
  : Get PGS Catalog Sample Sets
- [`get_traits()`](https://ascentsoftware.github.io/quincunx/reference/get_traits.md)
  : Get PGS Catalog Traits
- [`get_cohorts()`](https://ascentsoftware.github.io/quincunx/reference/get_cohorts.md)
  : Get PGS Catalog Cohorts
- [`get_trait_categories()`](https://ascentsoftware.github.io/quincunx/reference/get_trait_categories.md)
  : Get PGS Catalog Trait Categories
- [`get_ancestry_categories()`](https://ascentsoftware.github.io/quincunx/reference/get_ancestry_categories.md)
  : Get ancestry categories and classes
- [`get_releases()`](https://ascentsoftware.github.io/quincunx/reference/get_releases.md)
  : Get PGS Catalog Releases

## PGS Catalog Entities

S4 classes for scores, publications, performance_metrics, sample_sets
and traits.

- [`scores-class`](https://ascentsoftware.github.io/quincunx/reference/scores-class.md)
  : An S4 class to represent a set of PGS Catalog Polygenic Scores
- [`publications-class`](https://ascentsoftware.github.io/quincunx/reference/publications-class.md)
  : An S4 class to represent a set of PGS Catalog Publications
- [`performance_metrics-class`](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md)
  : An S4 class to represent a set of PGS Catalog Performance Metrics
- [`sample_sets-class`](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md)
  : An S4 class to represent a set of PGS Catalog Sample Sets
- [`traits-class`](https://ascentsoftware.github.io/quincunx/reference/traits-class.md)
  : An S4 class to represent a set of PGS Catalog Traits

## Other Entities

S4 classes for cohorts, trait_categories and releases.

- [`cohorts-class`](https://ascentsoftware.github.io/quincunx/reference/cohorts-class.md)
  : An S4 class to represent a set of cohorts
- [`trait_categories-class`](https://ascentsoftware.github.io/quincunx/reference/trait_categories-class.md)
  : An S4 class to represent a set of PGS Catalog Trait Categories
- [`releases-class`](https://ascentsoftware.github.io/quincunx/reference/releases-class.md)
  : An S4 class to represent a set of PGS Catalog Releases

## Data Wrangling of PGS Catalog Entities

S4 methods for combining and tallying scores, publications,
performance_metrics, sample_set, traits, cohorts, trait_categories and
releases.

- [`n()`](https://ascentsoftware.github.io/quincunx/reference/n.md) :
  Number of PGS Catalog entities
- [`bind()`](https://ascentsoftware.github.io/quincunx/reference/bind.md)
  : Bind PGS Catalog objects
- [`union()`](https://ascentsoftware.github.io/quincunx/reference/setop.md)
  [`intersect()`](https://ascentsoftware.github.io/quincunx/reference/setop.md)
  [`setdiff()`](https://ascentsoftware.github.io/quincunx/reference/setop.md)
  [`setequal()`](https://ascentsoftware.github.io/quincunx/reference/setop.md)
  : Set operations on PGS Catalog objects

## Accession identifier mapping

Translate accession identifiers between scores, publications,
performance_metrics, sample_set, traits and GWAS studies.

- [`pgs_to_pgp()`](https://ascentsoftware.github.io/quincunx/reference/pgs_to_pgp.md)
  : Map PGS identifiers to PGP identifiers
- [`pgs_to_pss()`](https://ascentsoftware.github.io/quincunx/reference/pgs_to_pss.md)
  : Map PGS identifiers to PSS identifiers
- [`pgs_to_ppm()`](https://ascentsoftware.github.io/quincunx/reference/pgs_to_ppm.md)
  : Map PGS identifiers to PPM identifiers
- [`pgs_to_study()`](https://ascentsoftware.github.io/quincunx/reference/pgs_to_study.md)
  : Map PGS identifiers to GWAS study identifiers
- [`study_to_pgs()`](https://ascentsoftware.github.io/quincunx/reference/study_to_pgs.md)
  : Map GWAS studies identifiers to PGS identifiers
- [`pgp_to_pgs()`](https://ascentsoftware.github.io/quincunx/reference/pgp_to_pgs.md)
  : Map PGP identifiers to PGS identifiers
- [`pgp_to_pss()`](https://ascentsoftware.github.io/quincunx/reference/pgp_to_pss.md)
  : Map PGP identifiers to PSS identifiers
- [`pgp_to_ppm()`](https://ascentsoftware.github.io/quincunx/reference/pgp_to_ppm.md)
  : Map PGP identifiers to PPM identifiers
- [`pss_to_pgs()`](https://ascentsoftware.github.io/quincunx/reference/pss_to_pgs.md)
  : Map PSS identifiers to PGS identifiers
- [`pss_to_pgp()`](https://ascentsoftware.github.io/quincunx/reference/pss_to_pgp.md)
  : Map PSS identifiers to PGP identifiers
- [`pss_to_ppm()`](https://ascentsoftware.github.io/quincunx/reference/pss_to_ppm.md)
  : Map PSS identifiers to PPM identifiers
- [`ppm_to_pgs()`](https://ascentsoftware.github.io/quincunx/reference/ppm_to_pgs.md)
  : Map PPM identifiers to PGS identifiers
- [`ppm_to_pgp()`](https://ascentsoftware.github.io/quincunx/reference/ppm_to_pgp.md)
  : Map PPM identifiers to PGP identifiers
- [`ppm_to_pss()`](https://ascentsoftware.github.io/quincunx/reference/ppm_to_pss.md)
  : Map PPM identifiers to PSS identifiers

## Easily navigate web resources

Functions that allow you to quickly browse linked information.

- [`open_in_pgs_catalog()`](https://ascentsoftware.github.io/quincunx/reference/open_in_pgs_catalog.md)
  : Browse PGS Catalog entities from the PGS Catalog Web Graphical User
  Interface
- [`open_in_pubmed()`](https://ascentsoftware.github.io/quincunx/reference/open_in_pubmed.md)
  : Browse PubMed from PubMed identifiers.
- [`open_in_dbsnp()`](https://ascentsoftware.github.io/quincunx/reference/open_in_dbsnp.md)
  : Browse dbSNP from SNP identifiers.

## Export to xlsx

Exporting scores, publications, performance_metrics, sample_set, traits,
cohorts, trait_categories and releases to xlsx.

- [`write_xlsx()`](https://ascentsoftware.github.io/quincunx/reference/write_xlsx.md)
  : Export a PGS Catalog object to xlsx

## Miscellaneous

Other functions.

- [`clear_cache()`](https://ascentsoftware.github.io/quincunx/reference/clear_cache.md)
  : Clear quincunx cache of memoised functions

## Datasets

Datasets shipped with quincunx

- [`stages`](https://ascentsoftware.github.io/quincunx/reference/stages.md)
  : Study stages
- [`ancestry_categories`](https://ascentsoftware.github.io/quincunx/reference/ancestry_categories.md)
  : Ancestry categories and classes
