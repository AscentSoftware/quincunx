# Getting Traits

## Introduction

Polygenic scores (PGSs) are annotated with information about the
phenotype that it predicts, i.e. the reported trait (as reported in the
original publication). This can be found as the column `reported_trait`
in slot `scores` of `scores` objects:

``` r

pgs_01 <- get_scores('PGS000001')
pgs_01@scores
#> # A tibble: 1 × 12
#>   pgs_id    pgs_name scoring_file             matches_publication reported_trait
#>   <chr>     <chr>    <chr>                    <lgl>               <chr>         
#> 1 PGS000001 PRS77_BC https://ftp.ebi.ac.uk/p… TRUE                Breast cancer 
#> # ℹ 7 more variables: trait_additional_description <chr>,
#> #   pgs_method_name <chr>, pgs_method_params <chr>, n_variants <int>,
#> #   n_variants_interactions <int>, assembly <chr>, license <chr>
```

The predicted phenotype is also mapped to Experimental Factor Ontology
(EFO) terms (a controlled vocabulary for the unambiguous identification
of traits and diseases, and their relationships), namely, the EFO trait.
The EFO traits associated with a polygenic score can also be found in
`scores` objects in the slot `traits`, column `trait`:

``` r

pgs_01@traits
#> # A tibble: 1 × 5
#>   pgs_id    efo_id        trait            description                     url  
#>   <chr>     <chr>         <chr>            <chr>                           <chr>
#> 1 PGS000001 MONDO_0004989 breast carcinoma A carcinoma that arises from e… http…
```

Many PGSs have been developed and demonstrated to be predictive of
common complex traits, e.g. body mass index (BMI)¹, blood lipids² and
educational attainment³.

Similarly, PGSs for various diseases have been shown to be predictive of
disease incidence, defining marked increases in risk over the life
course or at earlier ages for people with high PGSs, e.g. coronary
artery disease^(4,5), breast cancer⁶ and schizophrenia⁷.

## Getting catalogued traits from PGS Catalog

If you are interested in retrieving polygenic scores from the Catalog,
you might want to search them by the trait they predict.
[`get_scores()`](https://ascentsoftware.github.io/quincunx/reference/get_scores.md)
is the function that searches for `PGSs`, however, this function only
allows to search by `pgs_id`, `efo_id` or `pubmed_id`. So in order to
search by a trait term, we need to first find the associated EFO
identifiers (`efo_id`).

To search for traits (or diseases), you use the function
[`get_traits()`](https://ascentsoftware.github.io/quincunx/reference/get_traits.md).
With this function you can search by:

- The EFO trait identifier: `efo_id`;
- or by the trait term: a term to be matched in the EFO identifier
  (`efo_id`), label, description synonyms, trait categories, or external
  mapped terms.

The most useful search criteria is the trait term, and that is typically
want you will want to use. Unless you already know the EFO trait you are
interested in, and are looking for extra details about it, you won’t
search directly with the EFO identifier.

### Basic example

Let’s say you are interested in PGSs related to medical condition,
stroke. Then you can search for `"stroke"` with
[`get_traits()`](https://ascentsoftware.github.io/quincunx/reference/get_traits.md):

``` r

get_traits(trait_term = 'stroke')
#> An object of class "traits"
#> Slot "traits":
#> # A tibble: 2 × 6
#>   efo_id        parent_efo_id is_child trait                   description url  
#>   <chr>         <chr>         <lgl>    <chr>                   <chr>       <chr>
#> 1 MONDO_0011057 NA            FALSE    cerebrovascular disord… A disorder… http…
#> 2 MONDO_0005098 NA            FALSE    stroke disorder         A sudden l… http…
#> 
#> Slot "pgs_ids":
#> # A tibble: 31 × 4
#>    efo_id        parent_efo_id is_child pgs_id   
#>    <chr>         <chr>         <lgl>    <chr>    
#>  1 MONDO_0011057 NA            FALSE    PGS002053
#>  2 MONDO_0005098 NA            FALSE    PGS000038
#>  3 MONDO_0005098 NA            FALSE    PGS000039
#>  4 MONDO_0005098 NA            FALSE    PGS000665
#>  5 MONDO_0005098 NA            FALSE    PGS000911
#>  6 MONDO_0005098 NA            FALSE    PGS001793
#>  7 MONDO_0005098 NA            FALSE    PGS001798
#>  8 MONDO_0005098 NA            FALSE    PGS002259
#>  9 MONDO_0005098 NA            FALSE    PGS002724
#> 10 MONDO_0005098 NA            FALSE    PGS002725
#> # ℹ 21 more rows
#> 
#> Slot "child_pgs_ids":
#> # A tibble: 42 × 4
#>    efo_id        parent_efo_id is_child child_pgs_id
#>    <chr>         <chr>         <lgl>    <chr>       
#>  1 MONDO_0011057 NA            FALSE    PGS000038   
#>  2 MONDO_0011057 NA            FALSE    PGS000039   
#>  3 MONDO_0011057 NA            FALSE    PGS000665   
#>  4 MONDO_0011057 NA            FALSE    PGS000911   
#>  5 MONDO_0011057 NA            FALSE    PGS001179   
#>  6 MONDO_0011057 NA            FALSE    PGS001793   
#>  7 MONDO_0011057 NA            FALSE    PGS001798   
#>  8 MONDO_0011057 NA            FALSE    PGS002052   
#>  9 MONDO_0011057 NA            FALSE    PGS002259   
#> 10 MONDO_0011057 NA            FALSE    PGS002724   
#> # ℹ 32 more rows
#> 
#> Slot "trait_categories":
#> # A tibble: 2 × 4
#>   efo_id        parent_efo_id is_child trait_categories
#>   <chr>         <chr>         <lgl>    <chr>           
#> 1 MONDO_0011057 NA            FALSE    Other trait     
#> 2 MONDO_0005098 NA            FALSE    Other trait     
#> 
#> Slot "trait_synonyms":
#> # A tibble: 16 × 4
#>    efo_id        parent_efo_id is_child trait_synonyms                  
#>    <chr>         <chr>         <lgl>    <chr>                           
#>  1 MONDO_0011057 NA            FALSE    CVA                             
#>  2 MONDO_0011057 NA            FALSE    CVA (cerebral vascular accident)
#>  3 MONDO_0011057 NA            FALSE    cerebral infarction             
#>  4 MONDO_0011057 NA            FALSE    cerebrovascular accident        
#>  5 MONDO_0011057 NA            FALSE    cerebrovascular disease         
#>  6 MONDO_0011057 NA            FALSE    cerebrovascular disorder        
#>  7 MONDO_0011057 NA            FALSE    stroke                          
#>  8 MONDO_0005098 NA            FALSE    CVA                             
#>  9 MONDO_0005098 NA            FALSE    CVA, cerebrovascular accident   
#> 10 MONDO_0005098 NA            FALSE    cerebral infarction             
#> 11 MONDO_0005098 NA            FALSE    cerebrovascular accident        
#> 12 MONDO_0005098 NA            FALSE    cerebrovascular accident, (CVA) 
#> 13 MONDO_0005098 NA            FALSE    stroke                          
#> 14 MONDO_0005098 NA            FALSE    stroke syndrome                 
#> 15 MONDO_0005098 NA            FALSE    syndrome, stroke                
#> 16 MONDO_0005098 NA            FALSE    undetermined stroke             
#> 
#> Slot "trait_mapped_terms":
#> # A tibble: 0 × 4
#> # ℹ 4 variables: efo_id <chr>, parent_efo_id <chr>, is_child <lgl>,
#> #   trait_mapped_terms <chr>
```

As can be seen from the returned `traits` object, we get a set of six
tables (slots) that include several details about stroke.

In the first table `traits` we got only one row, indicating that this
query returned only one trait in the Catalog. This trait is named
`"stroke"` (column `trait`), and is unambiguously identified by the EFO
identifier EFO_0000712.

### Exact matching

By default, the trait term is matched exactly. If you want to relax the
matching, then indicate with the parameter `exact_term` set to `FALSE`.
This way you will get, potentially, more results, in this example case,
ischemic stroke (HP_0002140) is now also returned:

``` r

get_traits(trait_term = 'stroke', exact_term = FALSE)
#> An object of class "traits"
#> Slot "traits":
#> # A tibble: 7 × 6
#>   efo_id        parent_efo_id is_child trait                   description url  
#>   <chr>         <chr>         <lgl>    <chr>                   <chr>       <chr>
#> 1 MONDO_0011057 NA            FALSE    cerebrovascular disord… A disorder… http…
#> 2 MONDO_1060199 NA            FALSE    hemorrhagic stroke      A stroke d… http…
#> 3 MONDO_0013792 NA            FALSE    intracerebral hemorrha… A cerebrov… http…
#> 4 HP_0002140    NA            FALSE    Ischemic stroke         Acute isch… http…
#> 5 EFO_0010555   NA            FALSE    left ventricular strok… Quantifica… http…
#> 6 HP_0001297    NA            FALSE    Stroke                  Sudden imp… http…
#> 7 MONDO_0005098 NA            FALSE    stroke disorder         A sudden l… http…
#> 
#> Slot "pgs_ids":
#> # A tibble: 43 × 4
#>    efo_id        parent_efo_id is_child pgs_id   
#>    <chr>         <chr>         <lgl>    <chr>    
#>  1 MONDO_0011057 NA            FALSE    PGS002053
#>  2 MONDO_0013792 NA            FALSE    PGS003457
#>  3 MONDO_0013792 NA            FALSE    PGS004943
#>  4 HP_0002140    NA            FALSE    PGS000039
#>  5 HP_0002140    NA            FALSE    PGS000665
#>  6 HP_0002140    NA            FALSE    PGS000911
#>  7 HP_0002140    NA            FALSE    PGS002724
#>  8 HP_0002140    NA            FALSE    PGS002725
#>  9 HP_0002140    NA            FALSE    PGS004322
#> 10 HP_0002140    NA            FALSE    PGS004597
#> # ℹ 33 more rows
#> 
#> Slot "child_pgs_ids":
#> # A tibble: 53 × 4
#>    efo_id        parent_efo_id is_child child_pgs_id
#>    <chr>         <chr>         <lgl>    <chr>       
#>  1 MONDO_0011057 NA            FALSE    PGS000038   
#>  2 MONDO_0011057 NA            FALSE    PGS000039   
#>  3 MONDO_0011057 NA            FALSE    PGS000665   
#>  4 MONDO_0011057 NA            FALSE    PGS000911   
#>  5 MONDO_0011057 NA            FALSE    PGS001179   
#>  6 MONDO_0011057 NA            FALSE    PGS001793   
#>  7 MONDO_0011057 NA            FALSE    PGS001798   
#>  8 MONDO_0011057 NA            FALSE    PGS002052   
#>  9 MONDO_0011057 NA            FALSE    PGS002259   
#> 10 MONDO_0011057 NA            FALSE    PGS002724   
#> # ℹ 43 more rows
#> 
#> Slot "trait_categories":
#> # A tibble: 9 × 4
#>   efo_id        parent_efo_id is_child trait_categories          
#>   <chr>         <chr>         <lgl>    <chr>                     
#> 1 MONDO_0011057 NA            FALSE    Other trait               
#> 2 MONDO_1060199 NA            FALSE    Other trait               
#> 3 MONDO_0013792 NA            FALSE    Other trait               
#> 4 HP_0002140    NA            FALSE    Cardiovascular disease    
#> 5 HP_0002140    NA            FALSE    Neurological disorder     
#> 6 EFO_0010555   NA            FALSE    Cardiovascular measurement
#> 7 HP_0001297    NA            FALSE    Cardiovascular disease    
#> 8 HP_0001297    NA            FALSE    Neurological disorder     
#> 9 MONDO_0005098 NA            FALSE    Other trait               
#> 
#> Slot "trait_synonyms":
#> # A tibble: 23 × 4
#>    efo_id        parent_efo_id is_child trait_synonyms                  
#>    <chr>         <chr>         <lgl>    <chr>                           
#>  1 MONDO_0011057 NA            FALSE    CVA                             
#>  2 MONDO_0011057 NA            FALSE    CVA (cerebral vascular accident)
#>  3 MONDO_0011057 NA            FALSE    cerebral infarction             
#>  4 MONDO_0011057 NA            FALSE    cerebrovascular accident        
#>  5 MONDO_0011057 NA            FALSE    cerebrovascular disease         
#>  6 MONDO_0011057 NA            FALSE    cerebrovascular disorder        
#>  7 MONDO_0011057 NA            FALSE    stroke                          
#>  8 MONDO_1060199 NA            FALSE    haemorrhagic stroke             
#>  9 MONDO_0013792 NA            FALSE    stroke, hemorrhagic             
#> 10 HP_0002140    NA            FALSE    Ischaemic stroke                
#> # ℹ 13 more rows
#> 
#> Slot "trait_mapped_terms":
#> # A tibble: 3 × 4
#>   efo_id      parent_efo_id is_child trait_mapped_terms   
#>   <chr>       <chr>         <lgl>    <chr>                
#> 1 HP_0002140  NA            FALSE    SNOMEDCT_US:422504002
#> 2 HP_0002140  NA            FALSE    UMLS:C0948008        
#> 3 EFO_0010555 NA            FALSE    PMID:31554410
```

### Subtraits (child traits)

By default, subtraits (child traits), are not retrieved by
[`get_traits()`](https://ascentsoftware.github.io/quincunx/reference/get_traits.md).
If you want to get all matching traits and those that are child traits
thereof, then indicate with the parameter `include_children` set to
`TRUE`. Here is an example with `"breast cancer"`:

``` r

get_traits(trait_term = 'breast cancer', include_children = TRUE)
#> An object of class "traits"
#> Slot "traits":
#> # A tibble: 17 × 6
#>    efo_id        parent_efo_id is_child trait                  description url  
#>    <chr>         <chr>         <lgl>    <chr>                  <chr>       <chr>
#>  1 MONDO_0007254 NA            FALSE    breast cancer          "A primary… http…
#>  2 MONDO_0000618 MONDO_0007254 TRUE     Her2-receptor negativ… ""          http…
#>  3 MONDO_0004989 MONDO_0007254 TRUE     breast carcinoma       "A carcino… http…
#>  4 MONDO_0005494 MONDO_0007254 TRUE     triple-negative breas… "An invasi… http…
#>  5 MONDO_0006244 MONDO_0007254 TRUE     HER2 positive breast … "A biologi… http…
#>  6 MONDO_0006512 MONDO_0007254 TRUE     estrogen-receptor pos… "A subtype… http…
#>  7 MONDO_0006513 MONDO_0007254 TRUE     estrogen-receptor neg… "A subtype… http…
#>  8 MONDO_0021115 MONDO_0007254 TRUE     luminal B breast carc… "A biologi… http…
#>  9 MONDO_0021116 MONDO_0007254 TRUE     luminal A breast carc… "A biologi… http…
#> 10 MONDO_0004989 NA            FALSE    breast carcinoma       "A carcino… http…
#> 11 MONDO_0000618 MONDO_0004989 TRUE     Her2-receptor negativ… ""          http…
#> 12 MONDO_0005494 MONDO_0004989 TRUE     triple-negative breas… "An invasi… http…
#> 13 MONDO_0006244 MONDO_0004989 TRUE     HER2 positive breast … "A biologi… http…
#> 14 MONDO_0006512 MONDO_0004989 TRUE     estrogen-receptor pos… "A subtype… http…
#> 15 MONDO_0006513 MONDO_0004989 TRUE     estrogen-receptor neg… "A subtype… http…
#> 16 MONDO_0021115 MONDO_0004989 TRUE     luminal B breast carc… "A biologi… http…
#> 17 MONDO_0021116 MONDO_0004989 TRUE     luminal A breast carc… "A biologi… http…
#> 
#> Slot "pgs_ids":
#> # A tibble: 356 × 4
#>    efo_id        parent_efo_id is_child pgs_id   
#>    <chr>         <chr>         <lgl>    <chr>    
#>  1 MONDO_0000618 MONDO_0007254 TRUE     PGS000213
#>  2 MONDO_0004989 MONDO_0007254 TRUE     PGS000001
#>  3 MONDO_0004989 MONDO_0007254 TRUE     PGS000004
#>  4 MONDO_0004989 MONDO_0007254 TRUE     PGS000007
#>  5 MONDO_0004989 MONDO_0007254 TRUE     PGS000015
#>  6 MONDO_0004989 MONDO_0007254 TRUE     PGS000028
#>  7 MONDO_0004989 MONDO_0007254 TRUE     PGS000029
#>  8 MONDO_0004989 MONDO_0007254 TRUE     PGS000045
#>  9 MONDO_0004989 MONDO_0007254 TRUE     PGS000050
#> 10 MONDO_0004989 MONDO_0007254 TRUE     PGS000051
#> # ℹ 346 more rows
#> 
#> Slot "child_pgs_ids":
#> # A tibble: 278 × 4
#>    efo_id        parent_efo_id is_child child_pgs_id
#>    <chr>         <chr>         <lgl>    <chr>       
#>  1 MONDO_0007254 NA            FALSE    PGS000001   
#>  2 MONDO_0007254 NA            FALSE    PGS000002   
#>  3 MONDO_0007254 NA            FALSE    PGS000003   
#>  4 MONDO_0007254 NA            FALSE    PGS000004   
#>  5 MONDO_0007254 NA            FALSE    PGS000005   
#>  6 MONDO_0007254 NA            FALSE    PGS000006   
#>  7 MONDO_0007254 NA            FALSE    PGS000007   
#>  8 MONDO_0007254 NA            FALSE    PGS000008   
#>  9 MONDO_0007254 NA            FALSE    PGS000009   
#> 10 MONDO_0007254 NA            FALSE    PGS000015   
#> # ℹ 268 more rows
#> 
#> Slot "trait_categories":
#> # A tibble: 17 × 4
#>    efo_id        parent_efo_id is_child trait_categories
#>    <chr>         <chr>         <lgl>    <chr>           
#>  1 MONDO_0007254 NA            FALSE    Other trait     
#>  2 MONDO_0000618 MONDO_0007254 TRUE     Other trait     
#>  3 MONDO_0004989 MONDO_0007254 TRUE     Other trait     
#>  4 MONDO_0005494 MONDO_0007254 TRUE     Other trait     
#>  5 MONDO_0006244 MONDO_0007254 TRUE     Other trait     
#>  6 MONDO_0006512 MONDO_0007254 TRUE     Other trait     
#>  7 MONDO_0006513 MONDO_0007254 TRUE     Other trait     
#>  8 MONDO_0021115 MONDO_0007254 TRUE     Other trait     
#>  9 MONDO_0021116 MONDO_0007254 TRUE     Other trait     
#> 10 MONDO_0004989 NA            FALSE    Other trait     
#> 11 MONDO_0000618 MONDO_0004989 TRUE     Other trait     
#> 12 MONDO_0005494 MONDO_0004989 TRUE     Other trait     
#> 13 MONDO_0006244 MONDO_0004989 TRUE     Other trait     
#> 14 MONDO_0006512 MONDO_0004989 TRUE     Other trait     
#> 15 MONDO_0006513 MONDO_0004989 TRUE     Other trait     
#> 16 MONDO_0021115 MONDO_0004989 TRUE     Other trait     
#> 17 MONDO_0021116 MONDO_0004989 TRUE     Other trait     
#> 
#> Slot "trait_synonyms":
#> # A tibble: 85 × 4
#>    efo_id        parent_efo_id is_child trait_synonyms                  
#>    <chr>         <chr>         <lgl>    <chr>                           
#>  1 MONDO_0007254 NA            FALSE    BC                              
#>  2 MONDO_0007254 NA            FALSE    breast cancer                   
#>  3 MONDO_0007254 NA            FALSE    breast tumor                    
#>  4 MONDO_0007254 NA            FALSE    breast tumour                   
#>  5 MONDO_0007254 NA            FALSE    cancer of breast                
#>  6 MONDO_0007254 NA            FALSE    malignant breast neoplasm       
#>  7 MONDO_0007254 NA            FALSE    malignant breast tumor          
#>  8 MONDO_0007254 NA            FALSE    malignant breast tumour         
#>  9 MONDO_0007254 NA            FALSE    malignant neoplasm of breast    
#> 10 MONDO_0007254 NA            FALSE    malignant neoplasm of the breast
#> # ℹ 75 more rows
#> 
#> Slot "trait_mapped_terms":
#> # A tibble: 14 × 4
#>    efo_id        parent_efo_id is_child trait_mapped_terms
#>    <chr>         <chr>         <lgl>    <chr>             
#>  1 MONDO_0021115 MONDO_0007254 TRUE     DOID:0080674      
#>  2 MONDO_0021115 MONDO_0007254 TRUE     MEDGEN:770986     
#>  3 MONDO_0021115 MONDO_0007254 TRUE     NCIT:C53555       
#>  4 MONDO_0021115 MONDO_0007254 TRUE     UMLS:C3642346     
#>  5 MONDO_0021116 MONDO_0007254 TRUE     MEDGEN:770985     
#>  6 MONDO_0021116 MONDO_0007254 TRUE     NCIT:C53554       
#>  7 MONDO_0021116 MONDO_0007254 TRUE     UMLS:C3642345     
#>  8 MONDO_0021115 MONDO_0004989 TRUE     DOID:0080674      
#>  9 MONDO_0021115 MONDO_0004989 TRUE     MEDGEN:770986     
#> 10 MONDO_0021115 MONDO_0004989 TRUE     NCIT:C53555       
#> 11 MONDO_0021115 MONDO_0004989 TRUE     UMLS:C3642346     
#> 12 MONDO_0021116 MONDO_0004989 TRUE     MEDGEN:770985     
#> 13 MONDO_0021116 MONDO_0004989 TRUE     NCIT:C53554       
#> 14 MONDO_0021116 MONDO_0004989 TRUE     UMLS:C3642345
```

The column `is_child` indicates whether that trait is being retrieved
because it is a direct result of the query or not. `is_child` is `TRUE`
when the trait is returned because it is a child trait of a matching
trait, and `FALSE` if a direct result of the query.

In the case of child traits, the column `parent_efo_id` indicates the
EFO trait identifier of the parent trait, i.e. the direct matching
trait, or `NA` otherwise.

## Getting all traits

To retrieve all traits simply leave the parameters `efo_id` and
`trait_term` as `NULL` (default):

``` r

get_traits()
```

## References

1\.

Khera, A. V. *et al.* [Polygenic prediction of weight and obesity
trajectories from birth to
adulthood](https://doi.org/10.1016/j.cell.2019.03.028). *Cell* **177**,
587–596.e9 (2019).

2\.

Kuchenbaecker, K. *et al.* [The transferability of lipid loci across
african, asian and european
cohorts](https://doi.org/10.1038/s41467-019-12026-7). *Nature
Communications* **10**, (2019).

3\.

Lee, J. J. *et al.* [Gene discovery and polygenic prediction from a
genome-wide association study of educational attainment in 1.1 million
individuals](https://doi.org/10.1038/s41588-018-0147-3). *Nature
Genetics* **50**, 1112–1121 (2018).

4\.

Inouye, M. *et al.* [Genomic risk prediction of coronary artery disease
in 480,000 adults](https://doi.org/10.1016/j.jacc.2018.07.079). *Journal
of the American College of Cardiology* **72**, 1883–1893 (2018).

5\.

Khera, A. V. *et al.* [Genome-wide polygenic scores for common diseases
identify individuals with risk equivalent to monogenic
mutations](https://doi.org/10.1038/s41588-018-0183-z). *Nature Genetics*
**50**, 1219–1224 (2018).

6\.

Mavaddat, N. *et al.* [Polygenic Risk Scores for Prediction of Breast
Cancer and Breast Cancer
Subtypes](https://doi.org/10.1016/j.ajhg.2018.11.002). *The American
Journal of Human Genetics* **104**, 21–34 (2019).

7\.

Zheutlin, A. B. *et al.* [Penetrance and pleiotropy of polygenic risk
scores for schizophrenia in 106,160 patients across four health care
systems](https://doi.org/10.1176/appi.ajp.2019.18091085). *American
Journal of Psychiatry* **176**, 846–855 (2019).
