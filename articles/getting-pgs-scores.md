# Getting PGS Scores

## Polygenic scores

A polygenic score (PGS) aggregates the effects of many genetic variants
into a single number which predicts genetic predisposition for a
phenotype. PGS are typically composed of hundreds-to-millions of genetic
variants (usually SNPs) which are combined using a weighted sum of
allele dosages multiplied by their corresponding effect sizes, as
estimated from a relevant genome-wide association study (GWAS).

PGS nomenclature is heterogeneous: they can also be referred to as
genetic scores or genomic scores, and as polygenic risk scores (PRS) or
genomic risk scores (GRS) if they predict a discrete phenotype, such as
a disease.

## PGS Catalog

The PGS Catalog is an open database of published polygenic scores (PGS).
Each PGS in the Catalog is consistently annotated with relevant
metadata; including scoring files (variants, effect alleles/weights),
annotations of how the PGS was developed and applied, and evaluations of
their predictive performance.

## Getting PGS scores

You can search PGS scores by three criteria:

- `pgs_id`: PGS identifier
- `efo_id`: EFO trait identifier
- `pubmed_id`: PubMed identifier

While these criteria are not terribly useful, as normally you do not
know these identifiers beforehand, these are the search criteria
provided by the PGS Catalog REST API (the service quincunx communicates
with).

Instead of using these criteria directly, we show you how you may
retrieve polygenic score information by starting with a trait or disease
of interest. See
[`vignette('pgs-scores-mavaddat')`](https://ascentsoftware.github.io/quincunx/articles/pgs-scores-mavaddat.md)
for how to get polygenic scores if starting with a publication of
interest.

Let’s say you are interested in
[basophil](https://en.wikipedia.org/wiki/Basophil) count. Basophils are
one of the several kinds of white blood cells and make up less than 1%
of all circulating white blood cells. Basophils play a part in immune
surveillance, and varying levels of basophils are associated with
different medical conditions, e.g., allergies, inflammation, infection,
leukemia or anemia.

We start by querying the PGS Catalog for traits with the term
`"basophil"` — you may check
[`vignette('getting-traits')`](https://ascentsoftware.github.io/quincunx/articles/getting-traits.md)
for more details on how to use the
[`get_traits()`](https://ascentsoftware.github.io/quincunx/reference/get_traits.md)
function.

``` r

(basophil_traits <- get_traits(trait_term = 'basophil', exact_term = FALSE))
#> An object of class "traits"
#> Slot "traits":
#> # A tibble: 3 × 6
#>   efo_id      parent_efo_id is_child trait                     description url  
#>   <chr>       <chr>         <lgl>    <chr>                     <chr>       <chr>
#> 1 EFO_0005090 NA            FALSE    basophil count            The number… http…
#> 2 EFO_0803539 NA            FALSE    basophil measurement      Quantifica… http…
#> 3 EFO_0007992 NA            FALSE    basophil percentage of l… A calculat… http…
#> 
#> Slot "pgs_ids":
#> # A tibble: 14 × 4
#>    efo_id      parent_efo_id is_child pgs_id   
#>    <chr>       <chr>         <lgl>    <chr>    
#>  1 EFO_0005090 NA            FALSE    PGS000088
#>  2 EFO_0005090 NA            FALSE    PGS000163
#>  3 EFO_0005090 NA            FALSE    PGS001378
#>  4 EFO_0005090 NA            FALSE    PGS003940
#>  5 EFO_0005090 NA            FALSE    PGS004727
#>  6 EFO_0005090 NA            FALSE    PGS004728
#>  7 EFO_0005090 NA            FALSE    PGS004729
#>  8 EFO_0005090 NA            FALSE    PGS004730
#>  9 EFO_0005090 NA            FALSE    PGS005175
#> 10 EFO_0007992 NA            FALSE    PGS000089
#> 11 EFO_0007992 NA            FALSE    PGS000164
#> 12 EFO_0007992 NA            FALSE    PGS001377
#> 13 EFO_0007992 NA            FALSE    PGS003945
#> 14 EFO_0007992 NA            FALSE    PGS005181
#> 
#> Slot "child_pgs_ids":
#> # A tibble: 19 × 4
#>    efo_id      parent_efo_id is_child child_pgs_id
#>    <chr>       <chr>         <lgl>    <chr>       
#>  1 EFO_0005090 NA            FALSE    PGS000089   
#>  2 EFO_0005090 NA            FALSE    PGS000164   
#>  3 EFO_0005090 NA            FALSE    PGS001377   
#>  4 EFO_0005090 NA            FALSE    PGS003945   
#>  5 EFO_0005090 NA            FALSE    PGS005181   
#>  6 EFO_0803539 NA            FALSE    PGS000088   
#>  7 EFO_0803539 NA            FALSE    PGS000089   
#>  8 EFO_0803539 NA            FALSE    PGS000163   
#>  9 EFO_0803539 NA            FALSE    PGS000164   
#> 10 EFO_0803539 NA            FALSE    PGS001377   
#> 11 EFO_0803539 NA            FALSE    PGS001378   
#> 12 EFO_0803539 NA            FALSE    PGS003940   
#> 13 EFO_0803539 NA            FALSE    PGS003945   
#> 14 EFO_0803539 NA            FALSE    PGS004727   
#> 15 EFO_0803539 NA            FALSE    PGS004728   
#> 16 EFO_0803539 NA            FALSE    PGS004729   
#> 17 EFO_0803539 NA            FALSE    PGS004730   
#> 18 EFO_0803539 NA            FALSE    PGS005175   
#> 19 EFO_0803539 NA            FALSE    PGS005181   
#> 
#> Slot "trait_categories":
#> # A tibble: 5 × 4
#>   efo_id      parent_efo_id is_child trait_categories         
#>   <chr>       <chr>         <lgl>    <chr>                    
#> 1 EFO_0005090 NA            FALSE    Hematological measurement
#> 2 EFO_0005090 NA            FALSE    Inflammatory measurement 
#> 3 EFO_0803539 NA            FALSE    Hematological measurement
#> 4 EFO_0007992 NA            FALSE    Hematological measurement
#> 5 EFO_0007992 NA            FALSE    Inflammatory measurement 
#> 
#> Slot "trait_synonyms":
#> # A tibble: 6 × 4
#>   efo_id      parent_efo_id is_child trait_synonyms                             
#>   <chr>       <chr>         <lgl>    <chr>                                      
#> 1 EFO_0005090 NA            FALSE    blood basophil count                       
#> 2 EFO_0007992 NA            FALSE    basophil count as percentage of total whit…
#> 3 EFO_0007992 NA            FALSE    basophil count to total WBC count ratio    
#> 4 EFO_0007992 NA            FALSE    basophil percentage                        
#> 5 EFO_0007992 NA            FALSE    basophil percentage of white cells         
#> 6 EFO_0007992 NA            FALSE    blood basophil count to total leukocyte co…
#> 
#> Slot "trait_mapped_terms":
#> # A tibble: 5 × 4
#>   efo_id      parent_efo_id is_child trait_mapped_terms
#>   <chr>       <chr>         <lgl>    <chr>             
#> 1 EFO_0005090 NA            FALSE    CMO:0000034       
#> 2 EFO_0005090 NA            FALSE    CMO:0000111       
#> 3 EFO_0005090 NA            FALSE    MedDRA:10049695   
#> 4 EFO_0005090 NA            FALSE    SNOMEDCT:42351005 
#> 5 EFO_0007992 NA            FALSE    CMO:0000368
```

The table (slot) `pgs_ids` in `basophil_traits` provides the associated
PGS identifiers.

``` r

basophil_traits@pgs_ids
#> # A tibble: 14 × 4
#>    efo_id      parent_efo_id is_child pgs_id   
#>    <chr>       <chr>         <lgl>    <chr>    
#>  1 EFO_0005090 NA            FALSE    PGS000088
#>  2 EFO_0005090 NA            FALSE    PGS000163
#>  3 EFO_0005090 NA            FALSE    PGS001378
#>  4 EFO_0005090 NA            FALSE    PGS003940
#>  5 EFO_0005090 NA            FALSE    PGS004727
#>  6 EFO_0005090 NA            FALSE    PGS004728
#>  7 EFO_0005090 NA            FALSE    PGS004729
#>  8 EFO_0005090 NA            FALSE    PGS004730
#>  9 EFO_0005090 NA            FALSE    PGS005175
#> 10 EFO_0007992 NA            FALSE    PGS000089
#> 11 EFO_0007992 NA            FALSE    PGS000164
#> 12 EFO_0007992 NA            FALSE    PGS001377
#> 13 EFO_0007992 NA            FALSE    PGS003945
#> 14 EFO_0007992 NA            FALSE    PGS005181
```

These identifiers can now be used to query score information using the
function
[`get_scores()`](https://ascentsoftware.github.io/quincunx/reference/get_scores.md):

``` r

get_scores(pgs_id = basophil_traits@pgs_ids$pgs_id)
#>  ■■■■■                             14% |  ETA: 12s
#>  ■■■■■■■■■■                        29% |  ETA: 12s
#>  ■■■■■■■■■■■■■■■■                  50% |  ETA:  8s
#>  ■■■■■■■■■■■■■■■■■■■■              64% |  ETA:  6s
#>  ■■■■■■■■■■■■■■■■■■■■■■■■■■■       86% |  ETA:  2s
#> An object of class "scores"
#> Slot "scores":
#> # A tibble: 14 × 12
#>    pgs_id    pgs_name            scoring_file matches_publication reported_trait
#>    <chr>     <chr>               <chr>        <lgl>               <chr>         
#>  1 PGS000088 baso                https://ftp… TRUE                Basophil count
#>  2 PGS000163 baso                https://ftp… TRUE                Basophil count
#>  3 PGS001378 GBE_INI30160        https://ftp… TRUE                Basophil count
#>  4 PGS003940 INI30160            https://ftp… TRUE                Basophil count
#>  5 PGS004727 Basophils_PRSmix_e… https://ftp… TRUE                Basophil count
#>  6 PGS004728 Basophils_PRSmix_s… https://ftp… TRUE                Basophil count
#>  7 PGS004729 Basophils_PRSmixPl… https://ftp… TRUE                Basophil count
#>  8 PGS004730 Basophils_PRSmixPl… https://ftp… TRUE                Basophil count
#>  9 PGS005175 VPGS_BASO           https://ftp… TRUE                Basophil coun…
#> 10 PGS000089 baso_p              https://ftp… TRUE                Basophil perc…
#> 11 PGS000164 baso_p              https://ftp… TRUE                Basophil perc…
#> 12 PGS001377 GBE_INI30220        https://ftp… TRUE                Basophil perc…
#> 13 PGS003945 INI30220            https://ftp… TRUE                Basophil perc…
#> 14 PGS005181 VPGS_BASO_P         https://ftp… TRUE                Basophil perc…
#> # ℹ 7 more variables: trait_additional_description <chr>,
#> #   pgs_method_name <chr>, pgs_method_params <chr>, n_variants <int>,
#> #   n_variants_interactions <int>, assembly <chr>, license <chr>
#> 
#> Slot "publications":
#> # A tibble: 14 × 8
#>    pgs_id    pgp_id pubmed_id publication_date publication title author_fullname
#>    <chr>     <chr>      <int> <date>           <chr>       <chr> <chr>          
#>  1 PGS000088 PGP00…  35072137 2022-01-12       Cell Genom  Mach… Xu Y           
#>  2 PGS000163 PGP00…  32888494 2020-09-01       Cell        The … Vuckovic D     
#>  3 PGS001378 PGP00…  35324888 2022-03-24       PLoS Genet  Sign… Tanigawa Y     
#>  4 PGS003940 PGP00…  37890495 2023-09-19       AJHG        Powe… Tanigawa Y     
#>  5 PGS004727 PGP00…  38508198 2024-03-12       Cell Genom  Inte… Truong B       
#>  6 PGS004728 PGP00…  38508198 2024-03-12       Cell Genom  Inte… Truong B       
#>  7 PGS004729 PGP00…  38508198 2024-03-12       Cell Genom  Inte… Truong B       
#>  8 PGS004730 PGP00…  38508198 2024-03-12       Cell Genom  Inte… Truong B       
#>  9 PGS005175 PGP00…  40335489 2025-05-07       Nat Commun  Geno… Xiang R        
#> 10 PGS000089 PGP00…  35072137 2022-01-12       Cell Genom  Mach… Xu Y           
#> 11 PGS000164 PGP00…  32888494 2020-09-01       Cell        The … Vuckovic D     
#> 12 PGS001377 PGP00…  35324888 2022-03-24       PLoS Genet  Sign… Tanigawa Y     
#> 13 PGS003945 PGP00…  37890495 2023-09-19       AJHG        Powe… Tanigawa Y     
#> 14 PGS005181 PGP00…  40335489 2025-05-07       Nat Commun  Geno… Xiang R        
#> # ℹ 1 more variable: doi <chr>
#> 
#> Slot "samples":
#> # A tibble: 16 × 15
#>    pgs_id    sample_id stage sample_size sample_cases sample_controls
#>    <chr>         <int> <chr>       <int>        <int>           <int>
#>  1 PGS000088         1 gwas       404718           NA              NA
#>  2 PGS000088         2 dev        323774           NA              NA
#>  3 PGS000163         1 gwas       408112           NA              NA
#>  4 PGS001378         1 dev        261890           NA              NA
#>  5 PGS003940         1 dev        315523           NA              NA
#>  6 PGS004727         1 dev         13541           NA              NA
#>  7 PGS004728         1 dev         28384           NA              NA
#>  8 PGS004729         1 dev         13541           NA              NA
#>  9 PGS004730         1 dev         28384           NA              NA
#> 10 PGS005175         1 dev        404717           NA              NA
#> 11 PGS000089         1 gwas       404532           NA              NA
#> 12 PGS000089         2 dev        323626           NA              NA
#> 13 PGS000164         1 gwas       408112           NA              NA
#> 14 PGS001377         1 dev        261893           NA              NA
#> 15 PGS003945         1 dev        315527           NA              NA
#> 16 PGS005181         1 dev        404531           NA              NA
#> # ℹ 9 more variables: sample_percent_male <dbl>, phenotype_description <chr>,
#> #   ancestry_category <chr>, ancestry <chr>, country <chr>,
#> #   ancestry_additional_description <chr>, study_id <chr>, pubmed_id <int>,
#> #   cohorts_additional_description <chr>
#> 
#> Slot "demographics":
#> # A tibble: 4 × 11
#>   pgs_id    sample_id variable estimate_type unit  variability_type variability
#>   <chr>         <int> <chr>    <chr>         <chr> <chr>                  <dbl>
#> 1 PGS000088         1 age      mean          years NA                        NA
#> 2 PGS000088         2 age      mean          years NA                        NA
#> 3 PGS000089         1 age      mean          years NA                        NA
#> 4 PGS000089         2 age      mean          years NA                        NA
#> # ℹ 4 more variables: estimate <dbl>, interval_type <chr>,
#> #   interval_lower <dbl>, interval_upper <dbl>
#> 
#> Slot "cohorts":
#> # A tibble: 16 × 4
#>    pgs_id    sample_id cohort_symbol cohort_name                                
#>    <chr>         <int> <chr>         <chr>                                      
#>  1 PGS000088         1 UKB           UK Biobank                                 
#>  2 PGS000088         2 UKB           UK Biobank                                 
#>  3 PGS000163         1 UKB           UK Biobank                                 
#>  4 PGS001378         1 UKB           UK Biobank                                 
#>  5 PGS003940         1 UKB           UK Biobank                                 
#>  6 PGS004727         1 AllofUs       All of Us Research Program | National Inst…
#>  7 PGS004728         1 G&H           Genes & Health                             
#>  8 PGS004729         1 AllofUs       All of Us Research Program | National Inst…
#>  9 PGS004730         1 G&H           Genes & Health                             
#> 10 PGS005175         1 UKB           UK Biobank                                 
#> 11 PGS000089         1 UKB           UK Biobank                                 
#> 12 PGS000089         2 UKB           UK Biobank                                 
#> 13 PGS000164         1 UKB           UK Biobank                                 
#> 14 PGS001377         1 UKB           UK Biobank                                 
#> 15 PGS003945         1 UKB           UK Biobank                                 
#> 16 PGS005181         1 UKB           UK Biobank                                 
#> 
#> Slot "traits":
#> # A tibble: 14 × 5
#>    pgs_id    efo_id      trait                             description     url  
#>    <chr>     <chr>       <chr>                             <chr>           <chr>
#>  1 PGS000088 EFO_0005090 basophil count                    The number of … http…
#>  2 PGS000163 EFO_0005090 basophil count                    The number of … http…
#>  3 PGS001378 EFO_0005090 basophil count                    The number of … http…
#>  4 PGS003940 EFO_0005090 basophil count                    The number of … http…
#>  5 PGS004727 EFO_0005090 basophil count                    The number of … http…
#>  6 PGS004728 EFO_0005090 basophil count                    The number of … http…
#>  7 PGS004729 EFO_0005090 basophil count                    The number of … http…
#>  8 PGS004730 EFO_0005090 basophil count                    The number of … http…
#>  9 PGS005175 EFO_0005090 basophil count                    The number of … http…
#> 10 PGS000089 EFO_0007992 basophil percentage of leukocytes A calculated m… http…
#> 11 PGS000164 EFO_0007992 basophil percentage of leukocytes A calculated m… http…
#> 12 PGS001377 EFO_0007992 basophil percentage of leukocytes A calculated m… http…
#> 13 PGS003945 EFO_0007992 basophil percentage of leukocytes A calculated m… http…
#> 14 PGS005181 EFO_0007992 basophil percentage of leukocytes A calculated m… http…
#> 
#> Slot "stages_tally":
#> # A tibble: 30 × 4
#>    pgs_id    stage sample_size n_sample_sets
#>    <chr>     <chr>       <int>         <int>
#>  1 PGS000088 gwas       404718            NA
#>  2 PGS000088 dev        323774            NA
#>  3 PGS000088 eval           NA             2
#>  4 PGS000163 gwas       408112            NA
#>  5 PGS000163 eval           NA             2
#>  6 PGS001378 dev        261890            NA
#>  7 PGS001378 eval           NA             5
#>  8 PGS003940 dev        315523            NA
#>  9 PGS003940 eval           NA             5
#> 10 PGS004727 dev         13541            NA
#> # ℹ 20 more rows
#> 
#> Slot "ancestry_frequencies":
#> # A tibble: 42 × 4
#>    pgs_id    stage ancestry_class_symbol frequency
#>    <chr>     <chr> <chr>                     <dbl>
#>  1 PGS000088 gwas  EUR                         100
#>  2 PGS000088 dev   EUR                         100
#>  3 PGS000088 eval  EUR                         100
#>  4 PGS000163 gwas  EUR                         100
#>  5 PGS000163 eval  EUR                         100
#>  6 PGS001378 dev   EUR                         100
#>  7 PGS001378 eval  AFR                          20
#>  8 PGS001378 eval  EAS                          20
#>  9 PGS001378 eval  EUR                          40
#> 10 PGS001378 eval  SAS                          20
#> # ℹ 32 more rows
#> 
#> Slot "multi_ancestry_composition":
#> # A tibble: 12 × 4
#>    pgs_id    stage multi_ancestry_class_symbol ancestry_class_symbol
#>    <chr>     <chr> <chr>                       <chr>                
#>  1 PGS003940 dev   MAE                         EUR                  
#>  2 PGS003940 dev   MAE                         SAS                  
#>  3 PGS003940 dev   MAE                         AFR                  
#>  4 PGS003940 dev   MAE                         OTH                  
#>  5 PGS003940 eval  MAO                         EAS                  
#>  6 PGS003940 eval  MAO                         OTH                  
#>  7 PGS003945 dev   MAE                         EUR                  
#>  8 PGS003945 dev   MAE                         SAS                  
#>  9 PGS003945 dev   MAE                         AFR                  
#> 10 PGS003945 dev   MAE                         OTH                  
#> 11 PGS003945 eval  MAO                         EAS                  
#> 12 PGS003945 eval  MAO                         OTH
```
