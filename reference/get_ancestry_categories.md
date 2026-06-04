# Get ancestry categories and classes

Retrieves ancestry categories and classes. This function simply returns
the object
[`ancestry_categories`](https://ascentsoftware.github.io/quincunx/reference/ancestry_categories.md).

## Usage

``` r
get_ancestry_categories()
```

## Value

A tibble with ancestry categories, classes and associated information.
See
[`ancestry_categories`](https://ascentsoftware.github.io/quincunx/reference/ancestry_categories.md)
for details about each column.

## Examples

``` r
get_ancestry_categories()
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
