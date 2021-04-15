# Tweedieverse

Tweedieverse is an R package to test associations between omics data and phenotypes (metadata). 
We keep the source code under [Tweedieverse source code](https://github.com/himelmallick/Tweedieverse). Here we provide examples and tutorials on configuring the runs, interpreting results, and combining figures for scientific reports and manuscripts. 

# Demo run code

```
library(Tweedieverse)
# use your path
setwd("~/path-to-your-working-directory/")

metadata <- read.table(
  'data//metadata.txt',
  sep = '\t',
  header = TRUE,
  fill = FALSE,
  comment.char = "" ,
  check.names = FALSE,
  row.names = 1
)

metabolites <- read.delim(
  'data/metabolites.txt',
  sep = '\t',
  header = TRUE,
  fill = T,
  comment.char = "" ,
  check.names = F,
  row.names = 1
)

### Run Tweedieverse 

#  imputation strategy 
metabolites[is.na(metabolites)] <- 0 #min(metabolites, na.rm = T)/2.0

Tweedieverse::Tweedieverse(metabolites, 
                           metadata, 
                           'analysis/my_meatbolites_Tweedieverse',
                           max_significance = 0.1,
                           plot_heatmap = T,
                           plot_scatter = T,
                           standardize = F)
```
