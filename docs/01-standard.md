# (PART\*) The Proteomics Workflow 



# Overview







# Data Handling 




## Import 



```r
Datasets[["dataset_SILAC"]] <-
  import2new_dataset_diann_precursor_SILAC(
    raw.data = Info$Imports$dataset_SILAC,
    variables.data = c("Protein.Group",
                       "Protein.Ids",
                       "Protein.Names",
                       "Genes",
                       "First.Protein.Description",
                       "Proteotypic",
                       "Stripped.Sequence",
                       "Modified.Sequence",
                       "Precursor.Mz",
                       "Precursor.Charge",
                       "Precursor.Id"),
    observations = c("name01" = "sample_name01",
                     "name02" = "sample_name02",
                     "name03" = "sample_name03",
                     "name04" = "sample_name04",
                     "name05" = "sample_name05",
                     "name06" = "sample_name06",
                     "name07" = "sample_name07",
                     "name08" = "sample_name08"),
    data.frames = c("Precursor.Quantity", 
                    "Precursor.Normalised", 
                    "Ms1.Area", 
                    "Ms1.Normalised"))
```






```r
# pull all sample names 
Info$Imports$sta10_6mz$Run %>% 
  # keep individual names in desired order 
  unique() %>% 
  sort(decreasing = T) %>% 
  # add names to vector 
  setNames(., strsplit_keep_last(., "_")) %>% 
  # print vector to copy to script 
  .cat_character_named()
```

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button1" aria-expanded="false" aria-controls="button1"> plain </button> <div id="button1" class="collapse">  
\

```r
Info$Imports$sta10_6mz$Run %>% 
  unique() %>% 
  sort(decreasing = T) %>% 
  setNames(., strsplit_keep_last(., "_")) %>% 
  .cat_character_named()
```
</div>

\
abc



## Preprocessing 









