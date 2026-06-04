# Get PGS Catalog Cohorts

Retrieves cohorts via the PGS Catalog REST API. Please note that all
`cohort_symbol` is vectorised, thus allowing for batch mode search.

## Usage

``` r
get_cohorts(
  cohort_symbol = NULL,
  verbose = FALSE,
  warnings = TRUE,
  progress_bar = TRUE
)
```

## Arguments

- cohort_symbol:

  A cohort symbol or `NULL` if all cohorts are intended.

- verbose:

  A `logical` indicating whether the function should be verbose about
  the different queries or not.

- warnings:

  A `logical` indicating whether to print warnings, if any.

- progress_bar:

  Whether to show a progress bar indicating download progress from the
  REST API server.

## Value

A
[cohorts](https://ascentsoftware.github.io/quincunx/reference/cohorts-class.md)
object.

## Examples

``` r
# Get information about specific cohorts by their symbols (acronyms)
get_cohorts(cohort_symbol = c('23andMe', 'IPOBCS'))
#> An object of class "cohorts"
#> Slot "cohorts":
#> # A tibble: 2 × 2
#>   cohort_symbol cohort_name                                            
#>   <chr>         <chr>                                                  
#> 1 23andMe       23andMe                                                
#> 2 IPOBCS        Portuguese Oncology Institute-Porto Breast Cancer Study
#> 
#> Slot "pgs_ids":
#> # A tibble: 69 × 3
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
#> # ℹ 59 more rows
#> 

# Get info on all cohorts (may take a few minutes to download)
if (FALSE) { # \dontrun{
get_cohorts()
} # }
```
