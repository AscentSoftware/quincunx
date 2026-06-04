# PGS Catalog Releases

The function
[`get_releases()`](https://ascentsoftware.github.io/quincunx/reference/get_releases.md)
gets you information about PGS Catalog releases; namely, the number of
newly released polygenic scores, publications and performance metrics,
as well as their respective associated identifiers (i.e., new `pgs_ids`,
`pgp_ids` and `ppm_ids`).

## Latest release of the PGS Catalog

To get information about the latest release, run
[`get_releases()`](https://ascentsoftware.github.io/quincunx/reference/get_releases.md)
with default argument values:

``` r

get_releases() # Or get_releases(date = 'latest')
#> An object of class "releases"
#> Slot "releases":
#> # A tibble: 1 × 5
#>   date       n_pgs n_ppm n_pgp notes                                            
#>   <date>     <int> <int> <int> <chr>                                            
#> 1 2026-05-07     5    30     9 This release contains 5 new Score(s), 9 new Publ…
#> 
#> Slot "pgs_ids":
#> # A tibble: 5 × 2
#>   date       pgs_id   
#>   <date>     <chr>    
#> 1 2026-05-07 PGS005397
#> 2 2026-05-07 PGS012555
#> 3 2026-05-07 PGS012562
#> 4 2026-05-07 PGS012563
#> # ℹ 1 more row
#> 
#> Slot "ppm_ids":
#> # A tibble: 30 × 2
#>   date       ppm_id   
#>   <date>     <chr>    
#> 1 2026-05-07 PPM023440
#> 2 2026-05-07 PPM030675
#> 3 2026-05-07 PPM030676
#> 4 2026-05-07 PPM030677
#> # ℹ 26 more rows
#> 
#> Slot "pgp_ids":
#> # A tibble: 9 × 2
#>   date       pgp_id   
#>   <date>     <chr>    
#> 1 2026-05-07 PGP000780
#> 2 2026-05-07 PGP000798
#> 3 2026-05-07 PGP000802
#> 4 2026-05-07 PGP000803
#> # ℹ 5 more rows
```

## Release by date

You can use the argument `date` to select a specific date (if a release
exists for this day) in the format `"YYYY-MM-DD"`, e.g., `"2020-11-20"`:

``` r

get_releases(date = '2020-11-20')
#> An object of class "releases"
#> Slot "releases":
#> # A tibble: 1 × 5
#>   date       n_pgs n_ppm n_pgp notes                                            
#>   <date>     <int> <int> <int> <chr>                                            
#> 1 2020-11-20     4    50     5 This release contains 4 new Score(s), 5 new Publ…
#> 
#> Slot "pgs_ids":
#> # A tibble: 4 × 2
#>   date       pgs_id   
#>   <date>     <chr>    
#> 1 2020-11-20 PGS000340
#> 2 2020-11-20 PGS000341
#> 3 2020-11-20 PGS000342
#> 4 2020-11-20 PGS000343
#> 
#> Slot "ppm_ids":
#> # A tibble: 50 × 2
#>   date       ppm_id   
#>   <date>     <chr>    
#> 1 2020-11-20 PPM000923
#> 2 2020-11-20 PPM000924
#> 3 2020-11-20 PPM000925
#> 4 2020-11-20 PPM000926
#> # ℹ 46 more rows
#> 
#> Slot "pgp_ids":
#> # A tibble: 5 × 2
#>   date       pgp_id   
#>   <date>     <chr>    
#> 1 2020-11-20 PGP000107
#> 2 2020-11-20 PGP000108
#> 3 2020-11-20 PGP000109
#> 4 2020-11-20 PGP000110
#> # ℹ 1 more row
```

## All releases

``` r

(all_releases <- get_releases(date = 'all'))
#> An object of class "releases"
#> Slot "releases":
#> # A tibble: 107 × 5
#>   date       n_pgs n_ppm n_pgp notes                                            
#>   <date>     <int> <int> <int> <chr>                                            
#> 1 2026-05-07     5    30     9 This release contains 5 new Score(s), 9 new Publ…
#> 2 2026-04-13    36    96    13 This release contains 36 new Score(s), 13 new Pu…
#> 3 2026-02-26    45   282     6 This release contains 45 new Score(s), 6 new Pub…
#> 4 2026-01-19    30    47     6 This release contains 30 new Score(s), 6 new Pub…
#> # ℹ 103 more rows
#> 
#> Slot "pgs_ids":
#> # A tibble: 5,337 × 2
#>   date       pgs_id   
#>   <date>     <chr>    
#> 1 2026-05-07 PGS005397
#> 2 2026-05-07 PGS012555
#> 3 2026-05-07 PGS012562
#> 4 2026-05-07 PGS012563
#> # ℹ 5,333 more rows
#> 
#> Slot "ppm_ids":
#> # A tibble: 20,839 × 2
#>   date       ppm_id   
#>   <date>     <chr>    
#> 1 2026-05-07 PPM023440
#> 2 2026-05-07 PPM030675
#> 3 2026-05-07 PPM030676
#> 4 2026-05-07 PPM030677
#> # ℹ 20,835 more rows
#> 
#> Slot "pgp_ids":
#> # A tibble: 790 × 2
#>   date       pgp_id   
#>   <date>     <chr>    
#> 1 2026-05-07 PGP000780
#> 2 2026-05-07 PGP000798
#> 3 2026-05-07 PGP000802
#> 4 2026-05-07 PGP000803
#> # ℹ 786 more rows
```
