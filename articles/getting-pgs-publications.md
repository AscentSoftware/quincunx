# Getting PGS Publications

## PGS Publications

PGS publications are those published works that underlie the data
provided by the PGS Catalog.

To retrieve these publications use the function
[`get_publications()`](https://ascentsoftware.github.io/quincunx/reference/get_publications.md).
You may use one of the following search criteria (or a combination
thereof):

- `pgp_id`: the publication identifier assigned by the PGS Catalog;
- `pgs_id`: the polygenic score identifier;
- `pubmed_id`: PubMed identifier;
- `author`: an author last name.

If you do not pass any of the criteria above, then
[`get_publications()`](https://ascentsoftware.github.io/quincunx/reference/get_publications.md)
will retrieve all publications in the Catalog.

## Getting PGS Publications

Getting PGS publications by their identifiers:

``` r

library(quincunx)

get_publications(pgp_id = c('PGP000001', 'PGP000002'))
#> An object of class "publications"
#> Slot "publications":
#> # A tibble: 2 × 8
#>   pgp_id    pubmed_id publication_date publication   title author_fullname doi  
#>   <chr>         <int> <date>           <chr>         <chr> <chr>           <chr>
#> 1 PGP000001  25855707 2015-04-08       J Natl Cance… Pred… Mavaddat N      10.1…
#> 2 PGP000002  30554720 2018-12-13       Am J Hum Gen… Poly… Mavaddat N      10.1…
#> # ℹ 1 more variable: authors <chr>
#> 
#> Slot "pgs_ids":
#> # A tibble: 21 × 3
#>    pgp_id    pgs_id    stage   
#>    <chr>     <chr>     <chr>   
#>  1 PGP000001 PGS000001 gwas/dev
#>  2 PGP000001 PGS000002 gwas/dev
#>  3 PGP000001 PGS000003 gwas/dev
#>  4 PGP000001 PGS000001 eval    
#>  5 PGP000001 PGS000002 eval    
#>  6 PGP000001 PGS000003 eval    
#>  7 PGP000002 PGS000004 gwas/dev
#>  8 PGP000002 PGS000005 gwas/dev
#>  9 PGP000002 PGS000006 gwas/dev
#> 10 PGP000002 PGS000007 gwas/dev
#> # ℹ 11 more rows
```

By `pgs_id`:

``` r

get_publications(pgs_id = 'PGS000003')
#> An object of class "publications"
#> Slot "publications":
#> # A tibble: 1 × 8
#>   pgp_id    pubmed_id publication_date publication   title author_fullname doi  
#>   <chr>         <int> <date>           <chr>         <chr> <chr>           <chr>
#> 1 PGP000001  25855707 2015-04-08       J Natl Cance… Pred… Mavaddat N      10.1…
#> # ℹ 1 more variable: authors <chr>
#> 
#> Slot "pgs_ids":
#> # A tibble: 6 × 3
#>   pgp_id    pgs_id    stage   
#>   <chr>     <chr>     <chr>   
#> 1 PGP000001 PGS000001 gwas/dev
#> 2 PGP000001 PGS000002 gwas/dev
#> 3 PGP000001 PGS000003 gwas/dev
#> 4 PGP000001 PGS000001 eval    
#> 5 PGP000001 PGS000002 eval    
#> 6 PGP000001 PGS000003 eval
```

By `pubmed_id`:

``` r

get_publications(pubmed_id = '30554720')
#> An object of class "publications"
#> Slot "publications":
#> # A tibble: 1 × 8
#>   pgp_id    pubmed_id publication_date publication   title author_fullname doi  
#>   <chr>         <int> <date>           <chr>         <chr> <chr>           <chr>
#> 1 PGP000002  30554720 2018-12-13       Am J Hum Gen… Poly… Mavaddat N      10.1…
#> # ℹ 1 more variable: authors <chr>
#> 
#> Slot "pgs_ids":
#> # A tibble: 15 × 3
#>    pgp_id    pgs_id    stage   
#>    <chr>     <chr>     <chr>   
#>  1 PGP000002 PGS000004 gwas/dev
#>  2 PGP000002 PGS000005 gwas/dev
#>  3 PGP000002 PGS000006 gwas/dev
#>  4 PGP000002 PGS000007 gwas/dev
#>  5 PGP000002 PGS000008 gwas/dev
#>  6 PGP000002 PGS000009 gwas/dev
#>  7 PGP000002 PGS000001 eval    
#>  8 PGP000002 PGS000002 eval    
#>  9 PGP000002 PGS000003 eval    
#> 10 PGP000002 PGS000004 eval    
#> 11 PGP000002 PGS000005 eval    
#> 12 PGP000002 PGS000006 eval    
#> 13 PGP000002 PGS000007 eval    
#> 14 PGP000002 PGS000008 eval    
#> 15 PGP000002 PGS000009 eval
```

By `author`:

``` r

get_publications(author = 'Natarajan')
#> An object of class "publications"
#> Slot "publications":
#> # A tibble: 29 × 8
#>    pgp_id    pubmed_id publication_date publication  title author_fullname doi  
#>    <chr>         <int> <date>           <chr>        <chr> <chr>           <chr>
#>  1 PGP000006  30104762 2018-08-13       Nat Genet    Geno… Khera AV        10.1…
#>  2 PGP000030  31676865 2019-11-01       Nat Genet    Geno… Klarin D        10.1…
#>  3 PGP000042  28223407 2017-02-21       Circulation  Poly… Natarajan P     10.1…
#>  4 PGP000060  30586733 2019-03-01       Circulation  Whol… Khera AV        10.1…
#>  5 PGP000076  27959714 2016-11-13       N Engl J Med Gene… Khera AV        10.1…
#>  6 PGP000116  32498804 2020-06-01       J Am Coll C… Limi… Aragam KG       10.1…
#>  7 PGP000127  33021622 2020-10-06       JAMA Cardiol Clin… Trinder M       10.1…
#>  8 PGP000159  32981348 2020-09-28       Circulation  Gene… Klarin D        10.1…
#>  9 PGP000230  34887591 2021-12-09       Nature       The … Graham SE       http…
#> 10 PGP000252  33433237 2021-01-12       Circ Genom … Inte… Ye Y            10.1…
#> # ℹ 19 more rows
#> # ℹ 1 more variable: authors <chr>
#> 
#> Slot "pgs_ids":
#> # A tibble: 505 × 3
#>    pgp_id    pgs_id    stage   
#>    <chr>     <chr>     <chr>   
#>  1 PGP000006 PGS000013 gwas/dev
#>  2 PGP000006 PGS000014 gwas/dev
#>  3 PGP000006 PGS000015 gwas/dev
#>  4 PGP000006 PGS000016 gwas/dev
#>  5 PGP000006 PGS000017 gwas/dev
#>  6 PGP000006 PGS000013 eval    
#>  7 PGP000006 PGS000014 eval    
#>  8 PGP000006 PGS000015 eval    
#>  9 PGP000006 PGS000016 eval    
#> 10 PGP000006 PGS000017 eval    
#> # ℹ 495 more rows
```

## Getting PGS Publications by other criteria

The PGS Catalog REST API only supports searches by those criteria
mentioned above. If you would like to get results by other criteria,
e.g., `publication_date`, then you need to retrieve all publications and
filter them afterwards.

As an example, let’s download all publications and then keep only those
publications published in 2021:

``` r

all_pub <- get_publications(interactive = FALSE)
all_pub@publications
#> # A tibble: 790 × 8
#>    pgp_id    pubmed_id publication_date publication  title author_fullname doi  
#>    <chr>         <int> <date>           <chr>        <chr> <chr>           <chr>
#>  1 PGP000001  25855707 2015-04-08       J Natl Canc… Pred… Mavaddat N      10.1…
#>  2 PGP000002  30554720 2018-12-13       Am J Hum Ge… Poly… Mavaddat N      10.1…
#>  3 PGP000003  25748612 2015-03-04       Lancet       Gene… Mega JL         10.1…
#>  4 PGP000004  26392438 2015-09-20       Eur Heart J  Risk… Tada H          10.1…
#>  5 PGP000005  27655226 2016-09-21       Eur Heart J  Geno… Abraham G       10.1…
#>  6 PGP000006  30104762 2018-08-13       Nat Genet    Geno… Khera AV        10.1…
#>  7 PGP000007  30309464 2018-10-01       J Am Coll C… Geno… Inouye M        10.1…
#>  8 PGP000008  31184202 2019-06-11       Circ Genom … Vali… Wünnemann F     10.1…
#>  9 PGP000009  28456682 2017-04-06       J Clin Lipi… Poly… Paquette M      10.1…
#> 10 PGP000010  27513194 2016-08-11       Genet Med    Pers… Läll K          10.1…
#> # ℹ 780 more rows
#> # ℹ 1 more variable: authors <chr>
```

Filtering based on the year 2021:

``` r

library(dplyr, warn.conflicts = FALSE)

# Determine the PGP ids whose publication date falls within 2021.
pgp_ids_2021 <-
  filter(
    all_pub@publications,
    publication_date >= '2021-01-01' &
      publication_date <= '2021-12-31'
  ) |>
  pull('pgp_id')

# Filtering based on the PGP ids
pub_2021 <- all_pub[pgp_ids_2021]

# Print the first 10 PGS publications
pub_2021@publications
#> # A tibble: 99 × 8
#>    pgp_id    pubmed_id publication_date publication title  author_fullname doi  
#>    <chr>         <int> <date>           <chr>       <chr>  <chr>           <chr>
#>  1 PGP000050  33579919 2021-02-12       Nat Commun  Cross… Graff RE        10.1…
#>  2 PGP000058  33623038 2021-02-23       Nat Commun  Polyg… Huynh-Le MP     10.1…
#>  3 PGP000121  33608049 2021-02-19       Genome Med  Devel… Tam CHT         10.1…
#>  4 PGP000122  33398198 2021-01-04       Nat Genet   Trans… Conti DV        10.1…
#>  5 PGP000128  33462484 2021-01-18       Nat Genet   Genet… Sinnott-Armstr… 10.1…
#>  6 PGP000137  34750571 2021-11-08       Nat Metab   Integ… Ritchie SC      10.1…
#>  7 PGP000138  33420020 2021-01-08       Nat Commun  Disea… Fontanillas P   10.1…
#>  8 PGP000146  33495597 2021-01-25       Nat Genet   Commo… Harper AR       10.1…
#>  9 PGP000147  33623009 2021-02-23       Nat Commun  Whole… Thareja G       10.1…
#> 10 PGP000148  33472890 2021-01-20       Cancer Res  Asses… Hung RJ         10.1…
#> # ℹ 89 more rows
#> # ℹ 1 more variable: authors <chr>
```
