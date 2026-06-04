# Cohorts, Samples and Sample Sets

## Cohorts

A cohort is a group of individuals with a shared characteristic. Cohorts
are identified in quincunx by the `cohort_symbol` variable. See
[`vignette('getting-cohorts')`](https://ascentsoftware.github.io/quincunx/articles/getting-cohorts.md)
on how to find associated polygenic scores.

![cohorts](../reference/figures/cohorts.svg)

Using
[`get_cohorts()`](https://ascentsoftware.github.io/quincunx/reference/get_cohorts.md)
to retrieve associated PGS identifiers with cohort `"PROMIS"`:

``` r

get_cohorts('PROMIS')
#> An object of class "cohorts"
#> Slot "cohorts":
#> # A tibble: 1 × 2
#>   cohort_symbol cohort_name                                     
#>   <chr>         <chr>                                           
#> 1 PROMIS        The Pakistan Risk Of Myocardial Infarction Study
#> 
#> Slot "pgs_ids":
#> # A tibble: 38 × 3
#>    cohort_symbol pgs_id    stage   
#>    <chr>         <chr>     <chr>   
#>  1 PROMIS        PGS000011 gwas/dev
#>  2 PROMIS        PGS000012 gwas/dev
#>  3 PROMIS        PGS000013 gwas/dev
#>  4 PROMIS        PGS000018 gwas/dev
#>  5 PROMIS        PGS000019 gwas/dev
#>  6 PROMIS        PGS000020 gwas/dev
#>  7 PROMIS        PGS000058 gwas/dev
#>  8 PROMIS        PGS000059 gwas/dev
#>  9 PROMIS        PGS000116 gwas/dev
#> 10 PROMIS        PGS000117 gwas/dev
#> # ℹ 28 more rows
```

## Samples

A sample is a group of participants associated with none, one or more
catalogued cohorts. The selection from a cohort can be either a subset
or its totality. Samples are not identified in PGS Catalog with a global
unique identifier, but quincunx assigns a surrogate identifier
(`sample_id`) to allow relations between tables.

![samples](../reference/figures/samples.svg)

Sample composition is provided in slot `cohorts` from objects `scores`
returned by the
[`get_scores()`](https://ascentsoftware.github.io/quincunx/reference/get_scores.md)
function.

``` r

library(dplyr, warn.conflicts = FALSE)

# PGS000011 is one of the polygenic scores that is based upon participants from
# cohort PROMIS
pgs_11 <- get_scores('PGS000011')

# Cohort PROMIS is included in sample no. 2, along with LOLIPOP
filter(pgs_11@cohorts, sample_id == 2L)
#> # A tibble: 2 × 4
#>   pgs_id    sample_id cohort_symbol cohort_name                                 
#>   <chr>         <int> <chr>         <chr>                                       
#> 1 PGS000011         2 PROMIS        The Pakistan Risk Of Myocardial Infarction …
#> 2 PGS000011         2 LOLIPOP       London Life Sciences Population Study
```

To know a few more details about samples, look into the `samples` slot
of the object `scores`:

``` r

filter(pgs_11@samples, sample_id == 2L)
#> # A tibble: 1 × 15
#>   pgs_id    sample_id stage sample_size sample_cases sample_controls
#>   <chr>         <int> <chr>       <int>        <int>           <int>
#> 1 PGS000011         2 gwas         8653         4394            4259
#> # ℹ 9 more variables: sample_percent_male <dbl>, phenotype_description <chr>,
#> #   ancestry_category <chr>, ancestry <chr>, country <chr>,
#> #   ancestry_additional_description <chr>, study_id <chr>, pubmed_id <int>,
#> #   cohorts_additional_description <chr>
```

## Sample sets

A sample set is a group of samples used in a polygenic score evaluation.
Each sample set is identified in the PGS Catalog by a unique sample set
identifier (`pss_id`).

![sample sets](../reference/figures/sample_sets.svg)

To find the sample sets that included a specific cohort, we start by
getting the PGS identifiers associated with a cohort, e.g. MHI:

``` r

# Note that by the definition of sample set, samples included in sample sets
# are only used at PGS evaluation stages.
filter(get_cohorts('MHI')@pgs_ids, stage == 'eval')
#> # A tibble: 22 × 3
#>    cohort_symbol pgs_id    stage
#>    <chr>         <chr>     <chr>
#>  1 MHI           PGS000013 eval 
#>  2 MHI           PGS000018 eval 
#>  3 MHI           PGS005287 eval 
#>  4 MHI           PGS005288 eval 
#>  5 MHI           PGS005289 eval 
#>  6 MHI           PGS005290 eval 
#>  7 MHI           PGS005291 eval 
#>  8 MHI           PGS005292 eval 
#>  9 MHI           PGS005293 eval 
#> 10 MHI           PGS005294 eval 
#> # ℹ 12 more rows
```

PGS000013 is one of the polygenic scores whose evaluation used
participants from the cohort MHI. We retrieve now the sample sets used
in the evaluation of PGS000013:

``` r

# Sample sets used in the evaluation of the PGS000013
pgs_13_sset <- get_sample_sets(pgs_id = 'PGS000013')
glimpse(pgs_13_sset@sample_sets)
#> Rows: 63
#> Columns: 1
#> $ pss_id <chr> "PSS000015", "PSS000019", "PSS000020", "PSS000021", "PSS000022"…
```

One of the sample sets used to evaluate PGS000013 is PSS000020. We can
retrieve a `sample_set` object that contains its composition, i.e., the
samples and cohorts included, along with other details:

``` r

get_sample_sets('PSS000020')
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
