# Getting PGS Sample Sets

## Sample sets

A sample set is a group of samples used in a polygenic score
evaluation.Each sample set is identified in the PGS Catalog by a unique
sample set identifier (`pss_id`). See
[`vignette('cohorts-samples-sample-sets')`](https://ascentsoftware.github.io/quincunx/articles/cohorts-samples-sample-sets.md)
for more details on the relationship between cohorts, samples, and
sample sets.

## Getting sample sets

To get information on sample sets you can either search by the
associated polygenic score identifiers, or by the sample set identifiers
themselves (if you know them beforehand).

### By the PGS identifier

``` r

# Sample sets used in the evaluation of the PGS000013
(pgs_13_sset <- get_sample_sets(pgs_id = 'PGS000013'))
#> An object of class "sample_sets"
#> Slot "sample_sets":
#> # A tibble: 63 × 1
#>    pss_id   
#>    <chr>    
#>  1 PSS000015
#>  2 PSS000019
#>  3 PSS000020
#>  4 PSS000021
#>  5 PSS000022
#>  6 PSS000219
#>  7 PSS000227
#>  8 PSS000228
#>  9 PSS000229
#> 10 PSS000230
#> # ℹ 53 more rows
#> 
#> Slot "samples":
#> # A tibble: 74 × 15
#>    pss_id    sample_id stage sample_size sample_cases sample_controls
#>    <chr>         <int> <chr>       <int>        <int>           <int>
#>  1 PSS000015         1 eval       288978         8676          280302
#>  2 PSS000019         1 eval         5762          173            5589
#>  3 PSS000020         1 eval          862          446             416
#>  4 PSS000020         2 eval         2333          937            1396
#>  5 PSS000021         1 eval         1964          974             976
#>  6 PSS000022         1 eval         3309         2492             817
#>  7 PSS000219         1 eval        11010          126           10884
#>  8 PSS000227         1 eval          544           40             504
#>  9 PSS000228         1 eval         1298          336             962
#> 10 PSS000229         1 eval          919          168             751
#> # ℹ 64 more rows
#> # ℹ 9 more variables: sample_percent_male <dbl>, phenotype_description <chr>,
#> #   ancestry_category <chr>, ancestry <chr>, country <chr>,
#> #   ancestry_additional_description <chr>, study_id <chr>, pubmed_id <int>,
#> #   cohorts_additional_description <chr>
#> 
#> Slot "demographics":
#> # A tibble: 23 × 11
#>    pss_id    sample_id variable estimate_type unit  variability_type variability
#>    <chr>         <int> <chr>    <chr>         <chr> <chr>                  <dbl>
#>  1 PSS000365         1 age      mean          years NA                        NA
#>  2 PSS000365         2 age      mean          years NA                        NA
#>  3 PSS000366         1 age      mean          years NA                        NA
#>  4 PSS000366         2 age      mean          years NA                        NA
#>  5 PSS000367         1 age      mean          years NA                        NA
#>  6 PSS000367         2 age      mean          years NA                        NA
#>  7 PSS011378         1 age      median        years NA                        NA
#>  8 PSS011379         1 age      median        years NA                        NA
#>  9 PSS011380         1 age      median        years NA                        NA
#> 10 PSS000331         1 follow_… median        years NA                        NA
#> # ℹ 13 more rows
#> # ℹ 4 more variables: estimate <dbl>, interval_type <chr>,
#> #   interval_lower <dbl>, interval_upper <dbl>
#> 
#> Slot "cohorts":
#> # A tibble: 139 × 4
#>    pss_id    sample_id cohort_symbol cohort_name                                
#>    <chr>         <int> <chr>         <chr>                                      
#>  1 PSS000015         1 UKB           UK Biobank                                 
#>  2 PSS000019         1 CARTaGENE     CARTaGENE cohort (CHU Sainte-Justine, Queb…
#>  3 PSS000020         1 MHI           Montreal Heart Institute Biobank           
#>  4 PSS000020         2 MHI           Montreal Heart Institute Biobank           
#>  5 PSS000021         1 MHI           Montreal Heart Institute Biobank           
#>  6 PSS000022         1 MHI           Montreal Heart Institute Biobank           
#>  7 PSS000219         1 CG            Color Genomics                             
#>  8 PSS000227         1 MESA          Multi-Ethnic Study of Atherosclerosis      
#>  9 PSS000227         1 VIRGO         Variation in Recovery: Role of Gender on O…
#> 10 PSS000228         1 MESA          Multi-Ethnic Study of Atherosclerosis      
#> # ℹ 129 more rows
```

### By the sample set identifier

``` r

# Sample set PSS000020
(pss_20 <- get_sample_sets(pss_id = 'PSS000020'))
#> An object of class "sample_sets"
#> Slot "sample_sets":
#> # A tibble: 1 × 1
#>   pss_id   
#>   <chr>    
#> 1 PSS000020
#> 
#> Slot "samples":
#> # A tibble: 2 × 15
#>   pss_id    sample_id stage sample_size sample_cases sample_controls
#>   <chr>         <int> <chr>       <int>        <int>           <int>
#> 1 PSS000020         1 eval          862          446             416
#> 2 PSS000020         2 eval         2333          937            1396
#> # ℹ 9 more variables: sample_percent_male <dbl>, phenotype_description <chr>,
#> #   ancestry_category <chr>, ancestry <chr>, country <chr>,
#> #   ancestry_additional_description <chr>, study_id <chr>, pubmed_id <int>,
#> #   cohorts_additional_description <chr>
#> 
#> Slot "demographics":
#> # A tibble: 0 × 11
#> # ℹ 11 variables: pss_id <chr>, sample_id <int>, variable <chr>,
#> #   estimate_type <chr>, unit <chr>, variability_type <chr>, variability <dbl>,
#> #   estimate <dbl>, interval_type <chr>, interval_lower <dbl>,
#> #   interval_upper <dbl>
#> 
#> Slot "cohorts":
#> # A tibble: 2 × 4
#>   pss_id    sample_id cohort_symbol cohort_name                     
#>   <chr>         <int> <chr>         <chr>                           
#> 1 PSS000020         1 MHI           Montreal Heart Institute Biobank
#> 2 PSS000020         2 MHI           Montreal Heart Institute Biobank
```

### By trait or disease

If you wish to search by other criteria other than the PGS identifier or
the PSS identifier, then you will need to do it in several steps. The
general approach is to map your criteria to matching PGS identifiers and
from those PGS IDs to sample sets using
[`get_sample_sets()`](https://ascentsoftware.github.io/quincunx/reference/get_sample_sets.md).

Let’s say that you want to retrieve all sample sets used in the
evaluation of polygenic scores for the disease Vitiligo (loss of skin
melanocytes that causes areas of skin depigmentation).

![Vitiligo of the hands in a person with dark skin. Source (CC BY-SA
3.0):
https://pt.wikipedia.org/wiki/Vitiligo.](../reference/figures/vitiligo.png)

Vitiligo of the hands in a person with dark skin. Source (CC BY-SA 3.0):
<https://pt.wikipedia.org/wiki/Vitiligo>.

We start by searching for this disease in the PGS Catalog with
[`get_traits()`](https://ascentsoftware.github.io/quincunx/reference/get_traits.md):

``` r

(traits_vitiligo <- get_traits(trait_term = 'vitiligo'))
#> An object of class "traits"
#> Slot "traits":
#> # A tibble: 1 × 6
#>   efo_id        parent_efo_id is_child trait    description                url  
#>   <chr>         <chr>         <lgl>    <chr>    <chr>                      <chr>
#> 1 MONDO_0008661 NA            FALSE    vitiligo Generalized well circumsc… http…
#> 
#> Slot "pgs_ids":
#> # A tibble: 3 × 4
#>   efo_id        parent_efo_id is_child pgs_id   
#>   <chr>         <chr>         <lgl>    <chr>    
#> 1 MONDO_0008661 NA            FALSE    PGS000738
#> 2 MONDO_0008661 NA            FALSE    PGS000760
#> 3 MONDO_0008661 NA            FALSE    PGS001536
#> 
#> Slot "child_pgs_ids":
#> # A tibble: 0 × 4
#> # ℹ 4 variables: efo_id <chr>, parent_efo_id <chr>, is_child <lgl>,
#> #   child_pgs_id <chr>
#> 
#> Slot "trait_categories":
#> # A tibble: 1 × 4
#>   efo_id        parent_efo_id is_child trait_categories
#>   <chr>         <chr>         <lgl>    <chr>           
#> 1 MONDO_0008661 NA            FALSE    Other trait     
#> 
#> Slot "trait_synonyms":
#> # A tibble: 0 × 4
#> # ℹ 4 variables: efo_id <chr>, parent_efo_id <chr>, is_child <lgl>,
#> #   trait_synonyms <chr>
#> 
#> Slot "trait_mapped_terms":
#> # A tibble: 0 × 4
#> # ℹ 4 variables: efo_id <chr>, parent_efo_id <chr>, is_child <lgl>,
#> #   trait_mapped_terms <chr>
```

The slot `pgs_ids` contains the polygenic score identifiers associated
with Vitiligo.

``` r

traits_vitiligo@pgs_ids
#> # A tibble: 3 × 4
#>   efo_id        parent_efo_id is_child pgs_id   
#>   <chr>         <chr>         <lgl>    <chr>    
#> 1 MONDO_0008661 NA            FALSE    PGS000738
#> 2 MONDO_0008661 NA            FALSE    PGS000760
#> 3 MONDO_0008661 NA            FALSE    PGS001536
```

Now to search for the sample sets, we can pass those PGS identifiers to
[`get_sample_sets()`](https://ascentsoftware.github.io/quincunx/reference/get_sample_sets.md):

``` r

(pss_vitiligo <- get_sample_sets(pgs_id = traits_vitiligo@pgs_ids$pgs_id))
#> An object of class "sample_sets"
#> Slot "sample_sets":
#> # A tibble: 11 × 1
#>    pss_id   
#>    <chr>    
#>  1 PSS000907
#>  2 PSS010968
#>  3 PSS010969
#>  4 PSS010974
#>  5 PSS010977
#>  6 PSS000970
#>  7 PSS004173
#>  8 PSS004174
#>  9 PSS004175
#> 10 PSS004176
#> 11 PSS004177
#> 
#> Slot "samples":
#> # A tibble: 11 × 15
#>    pss_id    sample_id stage sample_size sample_cases sample_controls
#>    <chr>         <int> <chr>       <int>        <int>           <int>
#>  1 PSS000907         1 eval         4008         1827            2181
#>  2 PSS010968         1 eval         4702         3750             952
#>  3 PSS010969         1 eval         4945          243            4702
#>  4 PSS010974         1 eval         4979           34            4945
#>  5 PSS010977         1 eval         4987           NA              NA
#>  6 PSS000970         1 eval         1584           NA              NA
#>  7 PSS004173         1 eval         6497           17            6480
#>  8 PSS004174         1 eval         1704            6            1698
#>  9 PSS004175         1 eval        24905           45           24860
#> 10 PSS004176         1 eval         7831           71            7760
#> 11 PSS004177         1 eval        67425          131           67294
#> # ℹ 9 more variables: sample_percent_male <dbl>, phenotype_description <chr>,
#> #   ancestry_category <chr>, ancestry <chr>, country <chr>,
#> #   ancestry_additional_description <chr>, study_id <chr>, pubmed_id <int>,
#> #   cohorts_additional_description <chr>
#> 
#> Slot "demographics":
#> # A tibble: 0 × 11
#> # ℹ 11 variables: pss_id <chr>, sample_id <int>, variable <chr>,
#> #   estimate_type <chr>, unit <chr>, variability_type <chr>, variability <dbl>,
#> #   estimate <dbl>, interval_type <chr>, interval_lower <dbl>,
#> #   interval_upper <dbl>
#> 
#> Slot "cohorts":
#> # A tibble: 6 × 4
#>   pss_id    sample_id cohort_symbol cohort_name                                 
#>   <chr>         <int> <chr>         <chr>                                       
#> 1 PSS000970         1 GNEHGI2020Q2  Genentech Human Genetics Initiative Cancer …
#> 2 PSS004173         1 UKB           UK Biobank                                  
#> 3 PSS004174         1 UKB           UK Biobank                                  
#> 4 PSS004175         1 UKB           UK Biobank                                  
#> 5 PSS004176         1 UKB           UK Biobank                                  
#> 6 PSS004177         1 UKB           UK Biobank
```
