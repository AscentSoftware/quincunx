# Browse PGS Catalog entities from the PGS Catalog Web Graphical User Interface

This function launches the web browser and opens a tab for each
identifier on the PGS Catalog web graphical user interface:
<https://www.pgscatalog.org/>.

## Usage

``` r
open_in_pgs_catalog(
  identifier = NULL,
  pgs_catalog_entity = c("pgs", "pgp", "pss", "efo")
)
```

## Arguments

- identifier:

  A vector of identifiers. The identifiers can be: PGS, PGP, PSS or EFO
  identifiers.

- pgs_catalog_entity:

  Either `'pgs'` (default), `'pgp'`, `'pss'`, `'efo'`. This argument
  indicates the type of the identifiers passed in `identifier`.

## Value

Returns `TRUE` if successful, or `FALSE` otherwise. But note that this
function is run for its side effect.

## Examples

``` r
if (FALSE) { # interactive()
# Open in PGS scores Catalog Web Graphical User Interface
open_in_pgs_catalog(c('PGS000001', 'PGS000002'))

# Open PGS Catalog Publications
open_in_pgs_catalog(c('PGP000001', 'PGP000002'),
  pgs_catalog_entity = 'pgp')

# Open Sample Sets (PSS)
open_in_pgs_catalog(c('PSS000001', 'PSS000002'),
  pgs_catalog_entity = 'pss')

# Open EFO traits (EFO)
open_in_pgs_catalog(c('EFO_0001645', 'MONDO_0007254'),
  pgs_catalog_entity = 'efo')
}
```
