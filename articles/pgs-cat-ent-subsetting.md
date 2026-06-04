# PGS Catalog Entity Subsetting

## Introduction

PGS Catalog entities are represented in quincunx as S4 objects. In this
article, we explain how to subset these objects using the `[` operator.
In a nutshell, we provide subsetting by either position or by the
object’s respective identifier. The main entities/objects are:

- Scores
- Publications
- Traits
- Sample Sets
- Performance Metrics

The general approach to subset the various S4 objects is the same.
Hence, to avoid repetition, we only provide a set of comprehensive
examples for the scores object. Subsetting with the other objects is
only illustrated when subsetting with identifiers to emphasise that
different objects have different associated identifiers.

If you do not know how to subset the tables included in the S4 objects,
please take a look at [Subsetting
tibbles](https://tibble.tidyverse.org/reference/subsetting.html).

Start by loading quincunx:

``` r

library(quincunx)
```

## Subsetting scores

### Subsetting scores by position

For illustrative purposes, let us get some arbitrary polygenic scores
objects, say, the first 10 PGSs in the catalog:

``` r

pgs_ids <- sprintf('PGS%06d', 1:10)
my_scores <- get_scores(pgs_ids)
#>  ■■■■■■■■■■                        30% |  ETA:  8s
#>  ■■■■■■■■■■■■■■■■                  50% |  ETA:  6s
#>  ■■■■■■■■■■■■■■■■■■■■■■            70% |  ETA:  4s
```

The object `my_scores` is an S4 object of class `scores`, see
[`class?scores`](https://ascentsoftware.github.io/quincunx/reference/scores-class.md)
for details. In quincunx, each S4 object contains at least one (the
first) table where each observation refers to an entity. To access
tables in S4 objects you use the `@` operator. The first table in
`my_scores` is `scores`:

``` r

my_scores@scores
#> # A tibble: 10 × 12
#>    pgs_id    pgs_name      scoring_file       matches_publication reported_trait
#>    <chr>     <chr>         <chr>              <lgl>               <chr>         
#>  1 PGS000001 PRS77_BC      https://ftp.ebi.a… TRUE                Breast cancer 
#>  2 PGS000002 PRS77_ERpos   https://ftp.ebi.a… TRUE                ER-positive b…
#>  3 PGS000003 PRS77_ERneg   https://ftp.ebi.a… TRUE                ER-negative b…
#>  4 PGS000004 PRS313_BC     https://ftp.ebi.a… TRUE                Breast cancer 
#>  5 PGS000005 PRS313_ERpos  https://ftp.ebi.a… TRUE                ER-positive b…
#>  6 PGS000006 PRS313_ERneg  https://ftp.ebi.a… TRUE                ER-negative b…
#>  7 PGS000007 PRS3820_BC    https://ftp.ebi.a… TRUE                Breast cancer 
#>  8 PGS000008 PRS3820_ERpos https://ftp.ebi.a… TRUE                ER-positive b…
#>  9 PGS000009 PRS3820_ERneg https://ftp.ebi.a… TRUE                ER-negative b…
#> 10 PGS000010 GRS27         https://ftp.ebi.a… TRUE                Coronary hear…
#> # ℹ 7 more variables: trait_additional_description <chr>,
#> #   pgs_method_name <chr>, pgs_method_params <chr>, n_variants <int>,
#> #   n_variants_interactions <int>, assembly <chr>, license <chr>

nrow(my_scores@scores)
#> [1] 10
```

This table has as many rows as polygenic scores. This is one way of
knowing how many scores there are in the object. Alternatively, you can
use the function
[`n()`](https://ascentsoftware.github.io/quincunx/reference/n.md) on the
object:

``` r

quincunx::n(my_scores)
#> [1] 10
```

It is important to know the number of scores if you plan to subset the
`my_scores` object by position. In this case there are 10 scores. If you
want to subset the first, fifth, and tenth score, then you could do:

``` r

my_scores[c(1, 5, 10)]@scores[1:2]
#> # A tibble: 3 × 2
#>   pgs_id    pgs_name    
#>   <chr>     <chr>       
#> 1 PGS000001 PRS77_BC    
#> 2 PGS000005 PRS313_ERpos
#> 3 PGS000010 GRS27
```

This returns a new object containing only the data for the scores
`"PGS000001"`, `"PGS000005"` and `"PGS000010"`.

Notice that this operation automatically traverses all tables in the
`my_scores` object and subsets all tables accordingly keeping only those
rows corresponding to the first, fifth and tenth scores. For example,
compare the table `samples` from the `my_scores` object before and after
the subsetting.

Before subsetting:

``` r

my_scores@samples[1:4]
#> # A tibble: 16 × 4
#>    pgs_id    sample_id stage sample_size
#>    <chr>         <int> <chr>       <int>
#>  1 PGS000001         1 gwas        22627
#>  2 PGS000002         1 gwas        22627
#>  3 PGS000003         1 gwas        22627
#>  4 PGS000004         1 gwas       158648
#>  5 PGS000004         2 dev         10444
#>  6 PGS000005         1 gwas        87368
#>  7 PGS000005         2 dev          5159
#>  8 PGS000006         1 gwas        87368
#>  9 PGS000006         2 dev          5159
#> 10 PGS000007         1 gwas       158648
#> 11 PGS000007         2 dev         10444
#> 12 PGS000008         1 gwas        87368
#> 13 PGS000008         2 dev          5159
#> 14 PGS000009         1 gwas        87368
#> 15 PGS000009         2 dev          5159
#> 16 PGS000010         1 gwas        86995
```

After subsetting with `c(1, 5, 10)`:

``` r

my_scores[c(1, 5, 10)]@samples[1:4]
#> # A tibble: 4 × 4
#>   pgs_id    sample_id stage sample_size
#>   <chr>         <int> <chr>       <int>
#> 1 PGS000001         1 gwas        22627
#> 2 PGS000005         1 gwas        87368
#> 3 PGS000005         2 dev          5159
#> 4 PGS000010         1 gwas        86995
```

### Subsetting scores by identifer

To subset by identifier you simply use a character vector with the
identifiers of interest. Let us say now you want two identifiers:
`"PGS000002"` and `"PGS000008"`. Then only you need to do is:

``` r

my_scores[c('PGS000002', 'PGS000008')]@scores[1:2]
#> # A tibble: 2 × 2
#>   pgs_id    pgs_name     
#>   <chr>     <chr>        
#> 1 PGS000002 PRS77_ERpos  
#> 2 PGS000008 PRS3820_ERpos
```

### Subsetting using repeated positions or identifiers

Please note that if you repeat the same position or identifier, you will
get that score repeated:

``` r

my_scores[c('PGS000003', 'PGS000003')]@scores[1:2]
#> # A tibble: 2 × 2
#>   pgs_id    pgs_name   
#>   <chr>     <chr>      
#> 1 PGS000003 PRS77_ERneg
#> 2 PGS000003 PRS77_ERneg

quincunx::n(my_scores[c('PGS000003', 'PGS000003')])
#> [1] 2
```

Or using the third position twice:

``` r

my_scores[c(3, 3)]@scores[1:2]
#> # A tibble: 2 × 2
#>   pgs_id    pgs_name   
#>   <chr>     <chr>      
#> 1 PGS000003 PRS77_ERneg
#> 2 PGS000003 PRS77_ERneg

quincunx::n(my_scores[c(3, 3)])
#> [1] 2
```

### Subsetting using negative positions

Just like with basic R objects, we can also use negative indices to drop
elements of an object. This is also supported with quincunx’s S4
objects. For example, to drop now the first, fifth and tenth score:

``` r

# Notice the minus sign before c(1, 5, 10)
my_scores[-c(1, 5, 10)]@scores[1:2]
#> # A tibble: 7 × 2
#>   pgs_id    pgs_name     
#>   <chr>     <chr>        
#> 1 PGS000002 PRS77_ERpos  
#> 2 PGS000003 PRS77_ERneg  
#> 3 PGS000004 PRS313_BC    
#> 4 PGS000006 PRS313_ERneg 
#> 5 PGS000007 PRS3820_BC   
#> 6 PGS000008 PRS3820_ERpos
#> 7 PGS000009 PRS3820_ERneg
```

### Subsetting with non-existing positions or identifiers

If you request a position or identifier that does not match in the
object, the result is an empty object. For example, the 11th position is
not present in `my_scores` so the returned object is empty:

``` r

my_scores[11]@scores[1:2]
#> # A tibble: 0 × 2
#> # ℹ 2 variables: pgs_id <chr>, pgs_name <chr>

quincunx::n(my_scores[11])
#> [1] 0
```

Please note that the returned object is still a valid `scores` object
and that it contains all the expected tables of such an object. It is
just that all tables have no rows. The same behaviour is to be expected
if you try to subset with non-existing identifiers:

``` r

my_scores['PGS000011']@scores[1:2]
#> # A tibble: 0 × 2
#> # ℹ 2 variables: pgs_id <chr>, pgs_name <chr>

quincunx::n(my_scores['PGS000011'])
#> [1] 0
```

## Subsetting Publications

Subsetting publications objects, or any other S4 object in quincunx,
works exactly the same way as described for scores. The only difference
is that identifiers have to be changed accordingly. So in the next
sections we only show how to subset using the respective identifiers.

``` r

# Get all publications where Abraham G is an author
my_publ <- get_publications(author = 'Abraham G')

# Note that the column `author_fullname` corresponds to the first author.
my_publ@publications[c('pgp_id', 'pubmed_id', 'publication_date', 'author_fullname')]
#> # A tibble: 11 × 4
#>    pgp_id    pubmed_id publication_date author_fullname
#>    <chr>         <int> <date>           <chr>          
#>  1 PGP000005  27655226 2016-09-21       Abraham G      
#>  2 PGP000007  30309464 2018-10-01       Inouye M       
#>  3 PGP000027  31862893 2019-12-20       Abraham G      
#>  4 PGP000028  24550740 2014-02-13       Abraham G      
#>  5 PGP000029  26244058 2015-07-16       Abraham G      
#>  6 PGP000052  32887683 2020-09-04       Cánovas R      
#>  7 PGP000137  34750571 2021-11-08       Ritchie SC     
#>  8 PGP000209  34039031 2021-05-27       Neumann JT     
#>  9 PGP000423  36655558 2023-01-19       Bakker MK      
#> 10 PGP000628  33444330 2021-01-14       Sun L          
#> 11 PGP000656        NA 2024-08-22       Ritchie SC
```

By visual inspection we can see that Abraham G is the first author in
PGP000005, PGP000027, PGP000028, and PGP000029.

To keep only those publications we subset the publication object
`my_publ` by those PGP identifiers:

``` r

my_publ[c('PGP000005', 'PGP000027', 'PGP000028', 'PGP000029')]@publications[c('pgp_id', 'pubmed_id', 'publication_date', 'author_fullname')]
#> # A tibble: 4 × 4
#>   pgp_id    pubmed_id publication_date author_fullname
#>   <chr>         <int> <date>           <chr>          
#> 1 PGP000005  27655226 2016-09-21       Abraham G      
#> 2 PGP000027  31862893 2019-12-20       Abraham G      
#> 3 PGP000028  24550740 2014-02-13       Abraham G      
#> 4 PGP000029  26244058 2015-07-16       Abraham G
```

## Subsetting Traits

To illustrate subsetting of a traits object with EFO identifiers, let us
say you’d like to create a traits object with traits whose trait name
contained the keyword `"lymph"`. To do this, we will start by
downloading all traits into a traits object. Then we look for the term
`"lymph"` in the `trait` column, and find which EFO identifiers are
matched. Finally, we will use those identifiers to create a traits
object containing only those matched identifiers.

Get all traits:

``` r

all_traits <- get_traits(interactive = FALSE)
```

Find which traits have in their name (`trait` column of `traits` table)
the term `"lymph"` (we use `grep` for this):

``` r

lymph_traits_positions <- grep('lymph', all_traits@traits$trait)

all_traits[lymph_traits_positions]@traits[c('efo_id', 'trait')]
#> # A tibble: 11 × 2
#>    efo_id        trait                              
#>    <chr>         <chr>                              
#>  1 MONDO_0004967 acute lymphoblastic leukemia       
#>  2 MONDO_0004948 B-cell chronic lymphocytic leukemia
#>  3 MONDO_0018905 diffuse large B-cell lymphoma      
#>  4 MONDO_0018906 follicular lymphoma                
#>  5 MONDO_0004952 Hodgkins lymphoma                  
#>  6 EFO_0004587   lymphocyte count                   
#>  7 EFO_0007993   lymphocyte percentage of leukocytes
#>  8 MONDO_0005402 lymphoid leukemia                  
#>  9 MONDO_0017604 marginal zone lymphoma             
#> 10 EFO_0008447   neutrophil-to-lymphocyte ratio     
#> 11 MONDO_0018908 non-Hodgkin lymphoma
```

Select only those EFO identifiers whose trait name contained `"lymph"`:

``` r

my_efo_ids <- all_traits[lymph_traits_positions]@traits$efo_id
my_efo_ids
#>  [1] "MONDO_0004967" "MONDO_0004948" "MONDO_0018905" "MONDO_0018906"
#>  [5] "MONDO_0004952" "EFO_0004587"   "EFO_0007993"   "MONDO_0005402"
#>  [9] "MONDO_0017604" "EFO_0008447"   "MONDO_0018908"
```

Finally, create a new traits object (`traits_only_lymph`) with only
those traits matching `"lymph"` by subsetting by identifier:

``` r

traits_only_lymph <- all_traits[my_efo_ids]
```

Confirm that indeed only those traits with `"lymph"` in the name are
present:

``` r

traits_only_lymph@traits[c(1, 4)]
#> # A tibble: 11 × 2
#>    efo_id        trait                              
#>    <chr>         <chr>                              
#>  1 MONDO_0004967 acute lymphoblastic leukemia       
#>  2 MONDO_0004948 B-cell chronic lymphocytic leukemia
#>  3 MONDO_0018905 diffuse large B-cell lymphoma      
#>  4 MONDO_0018906 follicular lymphoma                
#>  5 MONDO_0004952 Hodgkins lymphoma                  
#>  6 EFO_0004587   lymphocyte count                   
#>  7 EFO_0007993   lymphocyte percentage of leukocytes
#>  8 MONDO_0005402 lymphoid leukemia                  
#>  9 MONDO_0017604 marginal zone lymphoma             
#> 10 EFO_0008447   neutrophil-to-lymphocyte ratio     
#> 11 MONDO_0018908 non-Hodgkin lymphoma
```

You might have noticed that we could have used `lymph_traits_positions`
to subset `all_traits` by position instead to the same effect. That
would have been more straightforward, but the point here is to
illustrate subsetting with EFO identifiers. Moreover, as an exercise,
you might want to compare the results obtained with this example with:

``` r

# Get traits containing the term 'lymph' in the name or its description
get_traits(trait_term = 'lymph', exact_term = FALSE)

# Get traits whose name is exactly 'lymph'
get_traits(trait_term = 'lymph', exact_term = TRUE)
```

## Subsetting Sample Sets

To subset PGS Sample Sets you use identifiers of the form:
`"PSS000000"`. Here’s a simple example where we download two Sample Sets
(`"PSS000008"` and `"PSS000042"`), and afterwards we take `"PSS000008"`:

``` r

my_sample_sets <- get_sample_sets(pss_id = c('PSS000008', 'PSS000042'))

# Table `samples` contains the samples that comprise this Sample Set
my_sample_sets['PSS000008']@samples[1:6]
#> # A tibble: 3 × 6
#>   pss_id    sample_id stage sample_size sample_cases sample_controls
#>   <chr>         <int> <chr>       <int>        <int>           <int>
#> 1 PSS000008         1 eval        27271           NA              NA
#> 2 PSS000008         2 eval         8749          108            8641
#> 3 PSS000008         3 eval         6978          149            6829
```

## Subsetting Performance Metrics

Without much more creativity, you subset Performance Metrics objects
with identifiers of the form: `"PPM000000"`. Example:

``` r

my_perf_metrics <- get_performance_metrics(ppm_id = c('PPM000001', 'PPM000002'))

# Table `samples` contains the samples that comprise this Performance Metrics
my_perf_metrics['PPM000002']@samples[1:6]
#> # A tibble: 1 × 6
#>   ppm_id    pss_id    sample_id stage sample_size sample_cases
#>   <chr>     <chr>         <int> <chr>       <int>        <int>
#> 1 PPM000002 PSS000003         1 eval        53923        21365
```
