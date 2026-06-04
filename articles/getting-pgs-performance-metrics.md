# Getting PGS Performance Metrics

## PGS performance metrics

Performance metrics assess the validity of a PGS in a Sample Set. This
assessment is performed on samples not used for score development.

Performance metrics are retrieved with the function
[`get_performance_metrics()`](https://ascentsoftware.github.io/quincunx/reference/get_performance_metrics.md).
The returned data is provided as an S4 object of class
`performance_metrics`.

Common metrics include:

- standardized effect sizes: odds ratios or hazard ratios, and
  regression coefficients $`\beta`$, see slot `pgs_effect_sizes`;
- classification accuracy metrics: area under the receiver operating
  characteristic curve, C-index and area under the precision-recall
  curve, see slot `pgs_classification_metrics`;
- other relevant metrics: calibration ($`\chi^2`$)), see slot
  `pgs_other_metrics`.

The covariates used in the model (most commonly age, sex and genetic
principal components to account for the population structure) are also
recorded for each set of metrics. These can be found in the slot
`demographics`.

## Getting PGS performance metrics

In the PGS Catalog, performance metrics have been catalogued and have an
associated identifier that starts with the prefix `"PPM"`. To retrieve
the performance metrics associated with one assessment of a polygenic
score, you can use directly its identifier:

``` r

library(quincunx)

get_performance_metrics(ppm_id = 'PPM000001')
#> An object of class "performance_metrics"
#> Slot "performance_metrics":
#> # A tibble: 1 × 5
#>   ppm_id    pgs_id    reported_trait    covariates comments
#>   <chr>     <chr>     <chr>             <chr>      <chr>   
#> 1 PPM000001 PGS000001 All breast cancer NA         NA      
#> 
#> Slot "publications":
#> # A tibble: 1 × 8
#>   ppm_id    pgp_id  pubmed_id publication_date publication title author_fullname
#>   <chr>     <chr>       <int> <date>           <chr>       <chr> <chr>          
#> 1 PPM000001 PGP000…  25855707 2015-04-08       J Natl Can… Pred… Mavaddat N     
#> # ℹ 1 more variable: doi <chr>
#> 
#> Slot "sample_sets":
#> # A tibble: 1 × 2
#>   ppm_id    pss_id   
#>   <chr>     <chr>    
#> 1 PPM000001 PSS000001
#> 
#> Slot "samples":
#> # A tibble: 1 × 16
#>   ppm_id    pss_id    sample_id stage sample_size sample_cases sample_controls
#>   <chr>     <chr>         <int> <chr>       <int>        <int>           <int>
#> 1 PPM000001 PSS000001         1 eval        67054        33673           33381
#> # ℹ 9 more variables: sample_percent_male <dbl>, phenotype_description <chr>,
#> #   ancestry_category <chr>, ancestry <chr>, country <chr>,
#> #   ancestry_additional_description <chr>, study_id <chr>, pubmed_id <int>,
#> #   cohorts_additional_description <chr>
#> 
#> Slot "demographics":
#> # A tibble: 0 × 12
#> # ℹ 12 variables: ppm_id <chr>, pss_id <chr>, sample_id <int>, variable <chr>,
#> #   estimate_type <chr>, unit <chr>, variability_type <chr>, variability <dbl>,
#> #   estimate <dbl>, interval_type <chr>, interval_lower <dbl>,
#> #   interval_upper <dbl>
#> 
#> Slot "cohorts":
#> # A tibble: 33 × 5
#>    ppm_id    pss_id    sample_id cohort_symbol cohort_name                      
#>    <chr>     <chr>         <int> <chr>         <chr>                            
#>  1 PPM000001 PSS000001         1 ABCFS         Australian Breast Cancer Family …
#>  2 PPM000001 PSS000001         1 MCCS          Melbourne Collaborative Cohort S…
#>  3 PPM000001 PSS000001         1 HMBCS         Hannover-Minsk Breast Cancer Stu…
#>  4 PPM000001 PSS000001         1 LMBC          Leuven Multidisciplinary Breast …
#>  5 PPM000001 PSS000001         1 MTLGEBCS      Montreal Gene-Environment Breast…
#>  6 PPM000001 PSS000001         1 CGPS          Copenhagen General Population St…
#>  7 PPM000001 PSS000001         1 KBCP          Kuopio Breast Cancer Project     
#>  8 PPM000001 PSS000001         1 OBCS          Oulu Breast Cancer Study         
#>  9 PPM000001 PSS000001         1 CECILE        CECILE Breast Cancer Study       
#> 10 PPM000001 PSS000001         1 BBCC          Bavarian Breast Cancer Cases and…
#> # ℹ 23 more rows
#> 
#> Slot "pgs_effect_sizes":
#> # A tibble: 1 × 11
#>   ppm_id    effect_size_id estimate_type_long estimate_type estimate unit 
#>   <chr>              <int> <chr>              <chr>            <dbl> <chr>
#> 1 PPM000001              1 Odds Ratio         OR                1.55 NA   
#> # ℹ 5 more variables: variability_type <chr>, variability <dbl>,
#> #   interval_type <chr>, interval_lower <dbl>, interval_upper <dbl>
#> 
#> Slot "pgs_classification_metrics":
#> # A tibble: 1 × 11
#>   ppm_id  classification_metri…¹ estimate_type_long estimate_type estimate unit 
#>   <chr>                    <int> <chr>              <chr>            <dbl> <chr>
#> 1 PPM000…                      1 Concordance Stati… C-index          0.622 NA   
#> # ℹ abbreviated name: ¹​classification_metrics_id
#> # ℹ 5 more variables: variability_type <chr>, variability <dbl>,
#> #   interval_type <chr>, interval_lower <dbl>, interval_upper <dbl>
#> 
#> Slot "pgs_other_metrics":
#> # A tibble: 0 × 11
#> # ℹ 11 variables: ppm_id <chr>, other_metrics_id <int>,
#> #   estimate_type_long <chr>, estimate_type <chr>, estimate <dbl>, unit <chr>,
#> #   variability_type <chr>, variability <dbl>, interval_type <chr>,
#> #   interval_lower <dbl>, interval_upper <dbl>
```

## Searching by PGS identifier

Alternatively, you could also search by the associated PGS identifier,
i.e. `"PGS000001"`:

``` r

get_performance_metrics(pgs_id = 'PGS000001')
#> An object of class "performance_metrics"
#> Slot "performance_metrics":
#> # A tibble: 19 × 5
#>    ppm_id    pgs_id    reported_trait                        covariates comments
#>    <chr>     <chr>     <chr>                                 <chr>      <chr>   
#>  1 PPM000001 PGS000001 All breast cancer                     NA         NA      
#>  2 PPM000011 PGS000001 Invasive breast cancer                study, ge… NA      
#>  3 PPM000114 PGS000001 Breast cancer in BRCA1 mutation carr… Country, … NA      
#>  4 PPM000117 PGS000001 Breast cancer in BRCA2 mutation carr… Country, … NA      
#>  5 PPM000944 PGS000001 Metachronous contralateral breast ca… Country    NA      
#>  6 PPM000945 PGS000001 Invasive metachronous contralateral … Country    NA      
#>  7 PPM000961 PGS000001 Metachronous contralateral breast ca… Country    NA      
#>  8 PPM000962 PGS000001 Invasive metachronous contralateral … Country    NA      
#>  9 PPM002150 PGS000001 Breast cancer in CHEK2 mutation carr… Year of b… Only 70…
#> 10 PPM002151 PGS000001 Breast cancer in CHEK2 mutation carr… Year of b… Only 70…
#> 11 PPM002152 PGS000001 Breast cancer in CHEK2 mutation carr… Year of b… Only 70…
#> 12 PPM002153 PGS000001 Breast cancer in CHEK2 mutation carr… Year of b… Only 70…
#> 13 PPM002154 PGS000001 Breast cancer in CHEK2 mutation carr… Year of b… Only 70…
#> 14 PPM017270 PGS000001 breast cancer                         NA         NA      
#> 15 PPM021128 PGS000001 Incident invasive breast cancer (10-… NA         NA      
#> 16 PPM021129 PGS000001 Incident invasive breast cancer (10-… Questionn… NA      
#> 17 PPM021130 PGS000001 Incident invasive breast cancer (10-… Age, perc… NA      
#> 18 PPM021131 PGS000001 Incident invasive breast cancer (10-… Age, mamm… NA      
#> 19 PPM021132 PGS000001 Incident invasive breast cancer (10-… Age, BIRA… NA      
#> 
#> Slot "publications":
#> # A tibble: 19 × 8
#>    ppm_id    pgp_id pubmed_id publication_date publication title author_fullname
#>    <chr>     <chr>      <int> <date>           <chr>       <chr> <chr>          
#>  1 PPM000001 PGP00…  25855707 2015-04-08       J Natl Can… Pred… Mavaddat N     
#>  2 PPM000011 PGP00…  30554720 2018-12-13       Am J Hum G… Poly… Mavaddat N     
#>  3 PPM000114 PGP00…  28376175 2017-07-01       J Natl Can… Eval… Kuchenbaecker …
#>  4 PPM000117 PGP00…  28376175 2017-07-01       J Natl Can… Eval… Kuchenbaecker …
#>  5 PPM000944 PGP00…  33022221 2020-10-05       Am J Hum G… Brea… Kramer I       
#>  6 PPM000945 PGP00…  33022221 2020-10-05       Am J Hum G… Brea… Kramer I       
#>  7 PPM000961 PGP00…  33022221 2020-10-05       Am J Hum G… Brea… Kramer I       
#>  8 PPM000962 PGP00…  33022221 2020-10-05       Am J Hum G… Brea… Kramer I       
#>  9 PPM002150 PGP00…  33372680 2020-12-29       J Natl Can… Perf… Borde J        
#> 10 PPM002151 PGP00…  33372680 2020-12-29       J Natl Can… Perf… Borde J        
#> 11 PPM002152 PGP00…  33372680 2020-12-29       J Natl Can… Perf… Borde J        
#> 12 PPM002153 PGP00…  33372680 2020-12-29       J Natl Can… Perf… Borde J        
#> 13 PPM002154 PGP00…  33372680 2020-12-29       J Natl Can… Perf… Borde J        
#> 14 PPM017270 PGP00…  36862830 2023-03-02       Cancer Pre… Vali… Spaeth EL      
#> 15 PPM021128 PGP00…  33277321 2020-12-04       Cancer Epi… Simp… Rosner B       
#> 16 PPM021129 PGP00…  33277321 2020-12-04       Cancer Epi… Simp… Rosner B       
#> 17 PPM021130 PGP00…  33277321 2020-12-04       Cancer Epi… Simp… Rosner B       
#> 18 PPM021131 PGP00…  33277321 2020-12-04       Cancer Epi… Simp… Rosner B       
#> 19 PPM021132 PGP00…  33277321 2020-12-04       Cancer Epi… Simp… Rosner B       
#> # ℹ 1 more variable: doi <chr>
#> 
#> Slot "sample_sets":
#> # A tibble: 19 × 2
#>    ppm_id    pss_id   
#>    <chr>     <chr>    
#>  1 PPM000001 PSS000001
#>  2 PPM000011 PSS000004
#>  3 PPM000114 PSS000070
#>  4 PPM000117 PSS000071
#>  5 PPM000944 PSS000484
#>  6 PPM000945 PSS000486
#>  7 PPM000961 PSS000484
#>  8 PPM000962 PSS000486
#>  9 PPM002150 PSS001054
#> 10 PPM002151 PSS001054
#> 11 PPM002152 PSS001054
#> 12 PPM002153 PSS001054
#> 13 PPM002154 PSS001054
#> 14 PPM017270 PSS010184
#> 15 PPM021128 PSS011536
#> 16 PPM021129 PSS011536
#> 17 PPM021130 PSS011536
#> 18 PPM021131 PSS011535
#> 19 PPM021132 PSS011536
#> 
#> Slot "samples":
#> # A tibble: 19 × 16
#>    ppm_id    pss_id    sample_id stage sample_size sample_cases sample_controls
#>    <chr>     <chr>         <int> <chr>       <int>        <int>           <int>
#>  1 PPM000001 PSS000001         1 eval        67054        33673           33381
#>  2 PPM000011 PSS000004         1 eval        29751        11428           18323
#>  3 PPM000114 PSS000070         1 eval        15252         7797            7455
#>  4 PPM000117 PSS000071         1 eval         8211         4330            3881
#>  5 PPM000944 PSS000484         1 eval        56068         1027           55041
#>  6 PPM000945 PSS000486         1 eval        56068          923           55145
#>  7 PPM000961 PSS000484         1 eval        56068         1027           55041
#>  8 PPM000962 PSS000486         1 eval        56068          923           55145
#>  9 PPM002150 PSS001054         1 eval          760          561             199
#> 10 PPM002151 PSS001054         1 eval          760          561             199
#> 11 PPM002152 PSS001054         1 eval          760          561             199
#> 12 PPM002153 PSS001054         1 eval          760          561             199
#> 13 PPM002154 PSS001054         1 eval          760          561             199
#> 14 PPM017270 PSS010184         1 eval       200195         3138          197057
#> 15 PPM021128 PSS011536         1 eval         1166          533             633
#> 16 PPM021129 PSS011536         1 eval         1166          533             633
#> 17 PPM021130 PSS011536         1 eval         1166          533             633
#> 18 PPM021131 PSS011535         1 eval         1336          438             898
#> 19 PPM021132 PSS011536         1 eval         1166          533             633
#> # ℹ 9 more variables: sample_percent_male <dbl>, phenotype_description <chr>,
#> #   ancestry_category <chr>, ancestry <chr>, country <chr>,
#> #   ancestry_additional_description <chr>, study_id <chr>, pubmed_id <int>,
#> #   cohorts_additional_description <chr>
#> 
#> Slot "demographics":
#> # A tibble: 1 × 12
#>   ppm_id    pss_id    sample_id variable estimate_type unit  variability_type
#>   <chr>     <chr>         <int> <chr>    <chr>         <chr> <chr>           
#> 1 PPM017270 PSS010184         1 age      NA            years NA              
#> # ℹ 5 more variables: variability <dbl>, estimate <dbl>, interval_type <chr>,
#> #   interval_lower <dbl>, interval_upper <dbl>
#> 
#> Slot "cohorts":
#> # A tibble: 224 × 5
#>    ppm_id    pss_id    sample_id cohort_symbol cohort_name                      
#>    <chr>     <chr>         <int> <chr>         <chr>                            
#>  1 PPM000001 PSS000001         1 ABCFS         Australian Breast Cancer Family …
#>  2 PPM000001 PSS000001         1 MCCS          Melbourne Collaborative Cohort S…
#>  3 PPM000001 PSS000001         1 HMBCS         Hannover-Minsk Breast Cancer Stu…
#>  4 PPM000001 PSS000001         1 LMBC          Leuven Multidisciplinary Breast …
#>  5 PPM000001 PSS000001         1 MTLGEBCS      Montreal Gene-Environment Breast…
#>  6 PPM000001 PSS000001         1 CGPS          Copenhagen General Population St…
#>  7 PPM000001 PSS000001         1 KBCP          Kuopio Breast Cancer Project     
#>  8 PPM000001 PSS000001         1 OBCS          Oulu Breast Cancer Study         
#>  9 PPM000001 PSS000001         1 CECILE        CECILE Breast Cancer Study       
#> 10 PPM000001 PSS000001         1 BBCC          Bavarian Breast Cancer Cases and…
#> # ℹ 214 more rows
#> 
#> Slot "pgs_effect_sizes":
#> # A tibble: 18 × 11
#>    ppm_id    effect_size_id estimate_type_long estimate_type estimate unit 
#>    <chr>              <int> <chr>              <chr>            <dbl> <chr>
#>  1 PPM000001              1 Odds Ratio         OR               1.55  NA   
#>  2 PPM000011              1 Odds Ratio         OR               1.46  NA   
#>  3 PPM000114              1 Hazard Ratio       HR               1.13  NA   
#>  4 PPM000117              1 Hazard Ratio       HR               1.22  NA   
#>  5 PPM000944              1 Hazard Ratio       HR               1.21  NA   
#>  6 PPM000945              1 Hazard Ratio       HR               1.21  NA   
#>  7 PPM000961              1 Hazard Ratio       HR               1.21  NA   
#>  8 PPM000962              1 Hazard Ratio       HR               1.21  NA   
#>  9 PPM002150              1 Hazard Ratio       HR               1.71  NA   
#> 10 PPM002151              1 Hazard Ratio       HR               2.29  NA   
#> 11 PPM002152              1 Hazard Ratio       HR               1.43  NA   
#> 12 PPM002153              1 Hazard Ratio       HR               2.32  NA   
#> 13 PPM002154              1 Hazard Ratio       HR               1.59  NA   
#> 14 PPM017270              1 Hazard Ratio       HR               1.38  NA   
#> 15 PPM021128              1 Odds Ratio         OR               1.41  NA   
#> 16 PPM021128              2 Beta               β                0.343 NA   
#> 17 PPM021129              1 Odds Ratio         OR               1.37  NA   
#> 18 PPM021129              2 Beta               β                0.315 NA   
#> # ℹ 5 more variables: variability_type <chr>, variability <dbl>,
#> #   interval_type <chr>, interval_lower <dbl>, interval_upper <dbl>
#> 
#> Slot "pgs_classification_metrics":
#> # A tibble: 6 × 11
#>   ppm_id  classification_metri…¹ estimate_type_long estimate_type estimate unit 
#>   <chr>                    <int> <chr>              <chr>            <dbl> <chr>
#> 1 PPM000…                      1 Concordance Stati… C-index          0.622 NA   
#> 2 PPM000…                      1 Area Under the Re… AUROC            0.603 NA   
#> 3 PPM017…                      1 Concordance Stati… C-index          0.628 NA   
#> 4 PPM021…                      1 Area Under the Re… AUROC            0.658 NA   
#> 5 PPM021…                      1 Area Under the Re… AUROC            0.687 NA   
#> 6 PPM021…                      1 Area Under the Re… AUROC            0.659 NA   
#> # ℹ abbreviated name: ¹​classification_metrics_id
#> # ℹ 5 more variables: variability_type <chr>, variability <dbl>,
#> #   interval_type <chr>, interval_lower <dbl>, interval_upper <dbl>
#> 
#> Slot "pgs_other_metrics":
#> # A tibble: 0 × 11
#> # ℹ 11 variables: ppm_id <chr>, other_metrics_id <int>,
#> #   estimate_type_long <chr>, estimate_type <chr>, estimate <dbl>, unit <chr>,
#> #   variability_type <chr>, variability <dbl>, interval_type <chr>,
#> #   interval_lower <dbl>, interval_upper <dbl>
```

As you can see, when you search by `'PGS000001'`, we get multiple PPM
identifiers (PPM000001 included). This is because a PGS could have been
assessed multiple independent times, each assessment resulting in its
own performance metrics data entry, with its own associated identifier.

## Vectorised search

The function
[`get_performance_metrics()`](https://ascentsoftware.github.io/quincunx/reference/get_performance_metrics.md)
is vectorised over `ppm_id` and `pgs_id` and you could readily retrieve
performance metrics for a set of polygenic scores by providing a vector
of identifiers (e.g. PGSes 42 thru 46):

``` r

ppm <- get_performance_metrics(pgs_id = sprintf("PGS%06d", 42:46))
#>  ■■■■■■■■■■■■■■■■■■■               60% |  ETA:  3s
print(ppm@performance_metrics, n = Inf)
#> # A tibble: 28 × 5
#>    ppm_id    pgs_id    reported_trait                        covariates comments
#>    <chr>     <chr>     <chr>                                 <chr>      <chr>   
#>  1 PPM000101 PGS000042 Coeliac disease in HLA-DQ2.5 carriers NA         NA      
#>  2 PPM000102 PGS000043 Venous thromboembolism                age, sex,… NA      
#>  3 PPM000103 PGS000043 Venous thromboembolism                age, 10 P… NA      
#>  4 PPM001639 PGS000043 Thromboembolic disease event in indi… Age at la… Include…
#>  5 PPM001640 PGS000043 Thromboembolic disease event in indi… Disease d… Include…
#>  6 PPM001641 PGS000043 Thromboembolic disease event in in i… Age at la… Include…
#>  7 PPM001939 PGS000043 Venous Thromboembolism                Age, sex,… 273 of …
#>  8 PPM001940 PGS000043 Venous Thromboembolism                Age, sex,… 273 of …
#>  9 PPM001941 PGS000043 Venous Thromboembolism                NA         273 of …
#> 10 PPM001942 PGS000043 Venous Thromboembolism                Age, obes… 273 of …
#> 11 PPM001943 PGS000043 Venous Thromboembolism in individual… Age, sex,… 273 of …
#> 12 PPM001944 PGS000043 Venous Thromboembolism in individual… Age, sex,… 273 of …
#> 13 PPM014990 PGS000043 Early onset stroke                    10 princi… NA      
#> 14 PPM014991 PGS000043 Late onset stroke                     10 princi… NA      
#> 15 PPM000104 PGS000044 Elevated serum prostate-specific ant… cancer st… NA      
#> 16 PPM000105 PGS000044 aggressive prostate cancer (Gleason … NA         NA      
#> 17 PPM000106 PGS000045 Breast cancer in BRCA1 mutation carr… Country, … NA      
#> 18 PPM000107 PGS000045 Breast cancer in BRCA2 mutation carr… Country, … NA      
#> 19 PPM000120 PGS000045 Breast cancer in male carriers of BR… 3 PCs of … PGS pre…
#> 20 PPM002155 PGS000045 Breast cancer in CHEK2 mutation carr… Year of b… Only 81…
#> 21 PPM002156 PGS000045 Breast cancer in CHEK2 mutation carr… Year of b… Only 81…
#> 22 PPM002157 PGS000045 Breast cancer in CHEK2 mutation carr… Year of b… Only 81…
#> 23 PPM002158 PGS000045 Breast cancer in CHEK2 mutation carr… Year of b… Only 81…
#> 24 PPM002159 PGS000045 Breast cancer in CHEK2 mutation carr… Year of b… Only 81…
#> 25 PPM014912 PGS000045 Breast cancer in BRAC1 PV carriers    NA         effecti…
#> 26 PPM000108 PGS000046 Breast cancer in BRCA1 mutation carr… Country, … NA      
#> 27 PPM000109 PGS000046 Breast cancer in BRCA2 mutation carr… Country, … NA      
#> 28 PPM000121 PGS000046 Breast cancer in male carriers of BR… 3 PCs of … PGS pre…
```
