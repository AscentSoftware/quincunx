# Read a polygenic scoring file

This function imports a PGS scoring file. For more information about the
scoring file schema check
[`vignette("pgs-scoring-file", package = "quincunx")`](https://ascentsoftware.github.io/quincunx/articles/pgs-scoring-file.md).

## Usage

``` r
read_scoring_file(
  source,
  harmonized = FALSE,
  assembly = c("GRCh38", "GRCh37"),
  protocol = "http",
  metadata_only = FALSE
)
```

## Arguments

- source:

  PGS scoring file. This can be specified in three forms: (i) a PGS
  identifier, e.g. `"PGS000001"`, (ii) a path to a local file, e.g.
  `"~/PGS000001.txt"` or `"~/PGS000001.txt.gz"` or (iii) a direct URL to
  the PGS Catalog FTP server, e.g.
  `"http://ftp.ebi.ac.uk/pub/databases/spot/pgs/scores/PGS000001/ScoringFiles/PGS000001.txt.gz"`.

- harmonized:

  Whether to read an alternative, harmonized version of the PGS scoring
  file. This version contains harmonized variant information. This
  information is provided in extra columns whose names are prefixed with
  `"hm_"`.

- assembly:

  If `harmonized` is `TRUE`, `assembly` indicates which the genome
  assembly to choose for the harmonized variant data. `assembly` must be
  either `"GRCh38"` (default) or `"GRCh37"`.

- protocol:

  Network protocol for communication with the PGS Catalog FTP server:
  either `"http"` or `"ftp"`.

- metadata_only:

  Whether to read only the comment block (header) from the scoring file.

## Value

The returned value is a named list. The names are copied from the
arguments passed in `source`. Each element of the list contains another
list of two elements: `"metadata"` and `"data"`. The "metadata" element
contains data parsed from the header of the PGS scoring file. The "data"
element contains a data frame with as many rows as variants that
constitute the PGS score. The columns can vary. There are mandatory and
optional columns. The mandatory columns are those that identify the
variant, effect allele (`effect_allele`), and its respective weight
(`effect_weight`) in the score. The columns that identify the variant
can either be the `rsID` or the combination of `chr_name` and
`chr_position`. The "data" element will be `NULL` is argument
`metadata_only` is `TRUE`. For more information about the scoring file
schema check
[`vignette("pgs-scoring-file", package = "quincunx")`](https://ascentsoftware.github.io/quincunx/articles/pgs-scoring-file.md).

## Examples

``` r
if (FALSE) { # \dontrun{
# Read a PGS scoring file by PGS ID
# (internally, it translates the PGS ID
#  to the corresponding FTP URL)
try(read_scoring_file("PGS000655"))

# Equivalent to `read_scoring_file("PGS000655")`
url <- paste0(
  "http://ftp.ebi.ac.uk/",
  "pub/databases/spot/pgs/scores/",
  "PGS000655/ScoringFiles/",
  "PGS000655.txt.gz"
)
read_scoring_file(url)


# Reading from a local file
try(read_scoring_file("~/PGS000655.txt.gz"))
} # }
```
