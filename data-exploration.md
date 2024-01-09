Data Exploration
================
Miao Fu
2023-12-03

``` r
df=read_csv("data/Project_1_data.csv")|>
  janitor::clean_names()
```

``` r
sum_stats_cat = function(data) {
  results = list()
  
  for (col in colnames(data)) {
    freq_table = table(data[[col]])
    results[[col]] = as.data.frame(freq_table)
  }
  
  return(results)
}

results_cat=df|>
  select(-nr_siblings,-math_score,-reading_score,-writing_score)|>
  sum_stats_cat()

for (i in seq_along(results_cat)) {
  cat("Frequency table for column", names(results_cat)[i], ":\n")
  print(results_cat[[i]])
  cat("\n")
}
```

    ## Frequency table for column gender :
    ##     Var1 Freq
    ## 1 female  488
    ## 2   male  460
    ## 
    ## Frequency table for column ethnic_group :
    ##      Var1 Freq
    ## 1 group A   80
    ## 2 group B  171
    ## 3 group C  277
    ## 4 group D  237
    ## 5 group E  124
    ## 
    ## Frequency table for column parent_educ :
    ##                 Var1 Freq
    ## 1 associate's degree  198
    ## 2  bachelor's degree  104
    ## 3        high school  176
    ## 4    master's degree   55
    ## 5       some college  199
    ## 6   some high school  163
    ## 
    ## Frequency table for column lunch_type :
    ##           Var1 Freq
    ## 1 free/reduced  331
    ## 2     standard  617
    ## 
    ## Frequency table for column test_prep :
    ##        Var1 Freq
    ## 1 completed  322
    ## 2      none  571
    ## 
    ## Frequency table for column parent_marital_status :
    ##       Var1 Freq
    ## 1 divorced  146
    ## 2  married  516
    ## 3   single  213
    ## 4  widowed   24
    ## 
    ## Frequency table for column practice_sport :
    ##        Var1 Freq
    ## 1     never  112
    ## 2 regularly  343
    ## 3 sometimes  477
    ## 
    ## Frequency table for column is_first_child :
    ##   Var1 Freq
    ## 1   no  314
    ## 2  yes  604
    ## 
    ## Frequency table for column transport_means :
    ##         Var1 Freq
    ## 1    private  337
    ## 2 school_bus  509
    ## 
    ## Frequency table for column wkly_study_hours :
    ##     Var1 Freq
    ## 1    < 5  253
    ## 2   > 10  150
    ## 3 10-May  508
