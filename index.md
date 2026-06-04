# quincunx

The goal of [quincunx](https://github.com/ascentsoftware/quincunx/) is
to provide programmatic access to the [Polygenic Score (PGS)
Catalog](https://www.pgscatalog.org/), an open resource for [polygenic
scores](https://en.wikipedia.org/wiki/Polygenic_score) and associated
metadata describing their development and respective assessment.

Browse the online documentation at
[ascentsoftware.github.io/quincunx](https://ascentsoftware.github.io/quincunx)
to get started.

## Installation

Install [quincunx](https://github.com/ascentsoftware/quincunx/) from
CRAN:

``` r

# Install from CRAN
install.packages("quincunx")
```

You can instead install the development version with:

``` r

# install.packages("pak")
pak::pak("ascentsoftware/quincunx")
```

## Cheatsheet

[![](https://raw.githubusercontent.com/ascentsoftware/cheatsheets/master/quincunx/quincunx_cheatsheet.png)](https://github.com/ascentsoftware/cheatsheets/blob/master/quincunx/quincunx_cheatsheet.pdf)

## Citing this work

[quincunx](https://github.com/ascentsoftware/quincunx/) was published in
Bioinformatics in 2021:
<https://doi.org/10.1093/bioinformatics/btab522>.

To generate a citation for this publication from within R:

``` r

citation('quincunx')
#> To cite quincunx in publications use:
#> 
#>   Ramiro Magno, Isabel Duarte, Ana-Teresa Maia, quincunx: an R package
#>   to query, download and wrangle PGS Catalog data, Bioinformatics,
#>   btab522, 16 July 2021, Pages 1-3,
#>   https://doi.org/10.1093/bioinformatics/btab522
#> 
#> A BibTeX entry for LaTeX users is
#> 
#>   @Article{,
#>     title = {quincunx: an R package to query, download and wrangle PGS Catalog data},
#>     author = {Ramiro Magno and Isabel Duarte and Ana-Teresa Maia},
#>     journal = {Bioinformatics},
#>     year = {2021},
#>     volume = {38},
#>     number = {1},
#>     pages = {1--3},
#>     url = {https://doi.org/10.1093/bioinformatics/btab522},
#>   }
```

## Citing PGS Catalog publications

Also, please do not forget to cite the authors behind the original
studies and the papers associated with the PGS Catalog project:

- Lambert, S.A., Gil, L., Jupp, S. et al. The Polygenic Score Catalog as
  an open database for reproducibility and systematic evaluation. Nat
  Genet 53, 420–425 (2021). doi:
  [10.1038/s41588-021-00783-5](https://doi.org/10.1038/s41588-021-00783-5)
- Wand, H., Lambert, S.A., Tamburro, C. et al. Improving reporting
  standards for polygenic scores in risk prediction studies. Nature 591,
  211–219 (2021). doi:
  [10.1038/s41586-021-03243-6](https://doi.org/10.1038/s41586-021-03243-6)

## Terms of use

Please note that if you use the data provided by the PGS Catalog either
directly or via [quincunx](https://github.com/ascentsoftware/quincunx/)
you agree to abide to the [EMBL-EBI Terms of
Use](https://www.ebi.ac.uk/about/terms-of-use/).

## Code of Conduct

Please note that the `{quincunx`} project is released with a
[Contributor Code of
Conduct](https://ascentsoftware.github.io/quincunx/CODE_OF_CONDUCT.html).
By contributing to this project, you agree to abide by its terms.

## Acknowledgements

This work would have not been possible without the precious feedback
from the [PGS Catalog team](https://www.pgscatalog.org/), particularly
[Samuel Lambert](https://www.ebi.ac.uk/about/people/samuel-lambert) and
[Laurent Gil](https://www.sanger.ac.uk/person/gil-laurent/).
