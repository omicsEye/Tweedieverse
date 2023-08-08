# Tweedieverse

Tweedieverse is an R package to test associations between omics data and phenotypes (metadata). 
We keep the source code under [Tweedieverse source code](https://github.com/himelmallick/Tweedieverse). Here we provide examples and tutorials on configuring the runs, interpreting results, and combining figures for scientific reports and manuscripts. 


Citation
--------

To cite **`Tweedieverse`** in publications, please use:

Mallick, H, Chatterjee, S, Chowdhury, S, Chatterjee, S, Rahnavard, A, Hicks, SC. [Differential expression of single-cell RNA-seq data using Tweedie models](https://onlinelibrary.wiley.com/doi/10.1002/sim.9430). Statistics in Medicine. 2022; 41( 18): 3492- 3510. doi:10.1002/sim.9430

To cite the **`Tweedieverse`** software, please use:

Mallick, H; Rahnavard, A (2021). [Tweedieverse - A Unified Statistical Framework for Differential Analysis of Multi-omics Data](https://github.com/himelmallick/Tweedieverse). R package, <https://github.com/himelmallick/Tweedieverse>.

----
## Contents ##
* Applications
    * [Biomarkers and Pathways for COVID-19](https://omicseye.github.io/Tweedieverse/)
  
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
