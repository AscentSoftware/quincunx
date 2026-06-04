# Export a PGS Catalog object to xlsx

This function exports a PGS Catalog object to Microsoft Excel xlsx file.
Each table (slot) is saved in its own sheet.

## Usage

``` r
write_xlsx(x, file = stop("`file` must be specified"))
```

## Arguments

- x:

  A
  [scores](https://ascentsoftware.github.io/quincunx/reference/scores-class.md),
  [publications](https://ascentsoftware.github.io/quincunx/reference/publications-class.md),
  [traits](https://ascentsoftware.github.io/quincunx/reference/traits-class.md),
  [performance_metrics](https://ascentsoftware.github.io/quincunx/reference/performance_metrics-class.md),
  [sample_sets](https://ascentsoftware.github.io/quincunx/reference/sample_sets-class.md),
  [cohorts](https://ascentsoftware.github.io/quincunx/reference/cohorts-class.md),
  [trait_categories](https://ascentsoftware.github.io/quincunx/reference/trait_categories-class.md)
  or
  [releases](https://ascentsoftware.github.io/quincunx/reference/releases-class.md)
  object.

- file:

  A file name to write to.

## Value

No return value, called for its side effect.
