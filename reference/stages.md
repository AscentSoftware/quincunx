# Study stages

A dataset containing the various study stages assigned to samples in the
PGS Catalog.

## Usage

``` r
stages
```

## Format

A data frame with 5 stages (rows) and 4 columns:

- stage:

  Study stage.

- symbol:

  One-letter symbol for the stage, or a comma separated combination
  thereof.

- name:

  Stage name.

- definition:

  Stage description.

## Source

<https://www.pgscatalog.org/docs/ancestry>

## Examples

``` r
stages
#> # A tibble: 5 × 4
#>   stage         symbol name                                  definition         
#>   <chr>         <chr>  <chr>                                 <chr>              
#> 1 gwas          G      Source of Variant Associations (GWAS) "Describes the sam…
#> 2 dev           D      Score Development/Training            "Describes the sam…
#> 3 eval          E      PGS Evaluation                        "Information about…
#> 4 gwas/dev      G,D    Development                           "Combination of th…
#> 5 gwas/dev/eval G,D,E  All stages                            "Combination of al…
```
