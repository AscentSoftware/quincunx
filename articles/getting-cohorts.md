# Getting Cohorts

## Cohorts

A cohort is a group of individuals with a shared characteristic. Cohorts
are identified in quincunx by the `cohort_symbol` variable. Participants
in cohorts are used to define samples, which in turn, are used to
assemble sample sets. For more details on the relationship between the
concepts of cohorts, samples and sample sets, see
[`vignette('cohorts-samples-sample-sets')`](https://ascentsoftware.github.io/quincunx/articles/cohorts-samples-sample-sets.md).

Given that study participants typically come from one or more catalogued
cohorts and that cohorts can have a strong bias ancestry composition —
i.e., most cohorts are mostly composed of European-ancestry individuals
—, it can be really important to know which cohorts have been used at
the different stages of a Polygenic Score (PGS) life cycle to assess the
transferability of PGS performance^(1–3).

## Getting cohorts

If you know beforehand the cohort acronyms (e.g., `"23andMe"`) that you
are interested in, then you can get their full name and associated PGS
identifiers using the
[`get_cohorts()`](https://ascentsoftware.github.io/quincunx/reference/get_cohorts.md)
function by providing their symbols with the parameter `cohort_symbol`:

``` r

library(quincunx)
get_cohorts(cohort_symbol = '23andMe')
#> An object of class "cohorts"
#> Slot "cohorts":
#> # A tibble: 1 × 2
#>   cohort_symbol cohort_name
#>   <chr>         <chr>      
#> 1 23andMe       23andMe    
#> 
#> Slot "pgs_ids":
#> # A tibble: 42 × 3
#>    cohort_symbol pgs_id    stage   
#>    <chr>         <chr>     <chr>   
#>  1 23andMe       PGS000079 gwas/dev
#>  2 23andMe       PGS000157 gwas/dev
#>  3 23andMe       PGS000336 gwas/dev
#>  4 23andMe       PGS000730 gwas/dev
#>  5 23andMe       PGS000731 gwas/dev
#>  6 23andMe       PGS000732 gwas/dev
#>  7 23andMe       PGS000766 gwas/dev
#>  8 23andMe       PGS000767 gwas/dev
#>  9 23andMe       PGS000780 gwas/dev
#> 10 23andMe       PGS000790 gwas/dev
#> # ℹ 32 more rows
```

The `pgs_ids` slot contains a tibble of associated PGS identifiers with
the queried cohorts. The `stage` variable indicates the PGS stage in
which the cohort was used.

To get all catalogued cohorts in the PGS Catalog, leave the
`cohort_symbol` parameter as `NULL` (default). Note that, in this case,
it may take a few minutes for the download to complete.

## References

1\.

Reisberg, S., Iljasenko, T., Läll, K., Fischer, K. & Vilo, J. [Comparing
distributions of polygenic risk scores of type 2 diabetes and coronary
heart disease within different
populations](https://doi.org/10.1371/journal.pone.0179238). *PLOS ONE*
**12**, e0179238 (2017).

2\.

Martin, A. R. *et al.* [Clinical use of current polygenic risk scores
may exacerbate health
disparities](https://doi.org/10.1038/s41588-019-0379-x). *Nature
Genetics* **51**, 584–591 (2019).

3\.

Duncan, L. *et al.* [Analysis of polygenic risk score usage and
performance in diverse human
populations](https://doi.org/10.1038/s41467-019-11112-0). *Nature
Communications* **10**, (2019).
