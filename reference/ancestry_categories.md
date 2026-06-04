# Ancestry categories and classes

A dataset containing the ancestry categories defined in NHGRI-EBI GWAS
Catalog framework (Table 1,
[doi:10.1186/s13059-018-1396-2](https://doi.org/10.1186/s13059-018-1396-2)
). Ancestry categories are assigned to samples with distinct and
well-defined patterns of genetic variation. You will find these
categories in the variable `ancestry_category` of the following objects:
[scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md),
[performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md)
and
[sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md).
Ancestry categories (`ancestry_category`) are further clustered into
ancestry classes (`ancestry_class`).

## Usage

``` r
ancestry_categories
```

## Format

A data frame with 19 ancestry categories (rows) and 6 columns:

- ancestry_category:

  Ancestry category.

- ancestry_class:

  To reduce the complexity associated with the many ancestry categories,
  some have been merged into higher-level groupings (`ancestry_class`).
  These groupings represent the current breadth of data in the PGS
  Catalog and are likely to change as more data is added.

- ancestry_class_symbol:

  3-letter code for the `ancestry_class` e.g. `"EUR"` or `"MAE"`.

- ancestry_class_colour:

  Hexadecimal colour code associated with ancestry groupings
  (`ancestry_class`). This can be useful when visually communicating
  about ancestries.

- definition:

  Description of the ancestry category.

- examples:

  Examples of detailed descriptions of sample ancestries included in the
  category.

## Source

- Table 1 of Moralles et al. (2018)::

  [doi:10.1186/s13059-018-1396-2](https://doi.org/10.1186/s13059-018-1396-2)

- PGS Catalog Ancestry Documentation::

  <http://www.pgscatalog.org/docs/ancestry/>

## Examples

``` r
ancestry_categories
#> # A tibble: 19 × 6
#>    ancestry_category  ancestry_class ancestry_class_symbol ancestry_class_colour
#>    <chr>              <chr>          <chr>                 <chr>                
#>  1 Aboriginal Austra… Additional Di… OTH                   #999999              
#>  2 African American … African        AFR                   #FFD900              
#>  3 African unspecifi… African        AFR                   #FFD900              
#>  4 Asian unspecified  Additional As… ASN                   #B15928              
#>  5 Central Asian      Additional As… ASN                   #B15928              
#>  6 East Asian         East Asian     EAS                   #4DAF4A              
#>  7 European           European       EUR                   #377EB8              
#>  8 Greater Middle Ea… Greater Middl… GME                   #00CED1              
#>  9 Hispanic or Latin… Hispanic or L… AMR                   #E41A1C              
#> 10 Native American    Additional Di… OTH                   #999999              
#> 11 Not reported       Ancestry Not … NR                    #BBBBBB              
#> 12 Oceanian           Additional Di… OTH                   #999999              
#> 13 Other              Additional Di… OTH                   #999999              
#> 14 Other admixed anc… Additional Di… OTH                   #999999              
#> 15 South Asian        South Asian    SAS                   #984EA3              
#> 16 South East Asian   Additional As… ASN                   #B15928              
#> 17 Sub-Saharan Afric… African        AFR                   #FFD900              
#> 18 Multi-Ancestry (i… Multi-Ancestr… MAE                   #A6CEE3              
#> 19 Multi-Ancestry (e… Multi-Ancestr… MAO                   #FF7F00              
#> # ℹ 2 more variables: definition <chr>, examples <chr>
```
