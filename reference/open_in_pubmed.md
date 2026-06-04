# Browse PubMed from PubMed identifiers.

This function launches the web browser and opens a tab for each PubMed
citation.

## Usage

``` r
open_in_pubmed(pubmed_id)
```

## Arguments

- pubmed_id:

  A PubMed identifier, either a character or an integer vector.

## Value

Returns `TRUE` if successful. Note however that this function is run for
its side effect.

## Examples

``` r
if (FALSE) { # interactive()
open_in_pubmed(c('26301688', '30595370'))
}
```
