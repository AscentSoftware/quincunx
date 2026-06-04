# Browse dbSNP from SNP identifiers.

This function launches the web browser at dbSNP and opens a tab for each
SNP identifier.

## Usage

``` r
open_in_dbsnp(variant_id)
```

## Arguments

- variant_id:

  A variant identifier, a character vector.

## Value

Returns `TRUE` if successful. Note however that this function is run for
its side effect.

## Examples

``` r
if (FALSE) { # interactive()
open_in_dbsnp('rs56261590')
}
```
