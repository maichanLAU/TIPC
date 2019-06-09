# TIPC

``` R
library(devtools)

devtools::install_github("maichanLAU/TIPC")

library(TIPC)

?TIPC```

## step 0: set TIPC result output directory
root_dir <- "C:/Users/Mai Chan Lau/Desktop/TIPC_package/test_run"
dir.create(root_dir)


## step 1: dividing 2D cell space into sub-regions
load(system.file("data", "cell_data.rda", package = "TIPC"))
multiple_hexLen_tessellation(cell_data = cell_data, output_dir = root_dir)

## step 2: couting number of sub-regsions of each of the TIPC spatial category
multiple_hexLen_count_TIPC_cat(root_dir = root_dir)

## step 3: making trend plot to help determine an optimal hexagon length i.e. grid size
trend_plot_hexLen(root_dir = root_dir)

## step 4: calculating normalized TIPC spatial metrics
input_dir <- "C:/Users/Mai Chan Lau/Desktop/TIPC_package/test_run/TIPC_hexLen50"
normalize_metrics(root_dir=input_dir)

## step 5: clustering of TIPC spatical metrics
input_dir <- "C:/Users/Mai Chan Lau/Desktop/TIPC_package/test_run/TIPC_hexLen50"
consensus_clustering(root_dir=input_dir)

## step 6: making heat-map plot of TIPC spatial metrics
input_dir <- "C:/Users/Mai Chan Lau/Desktop/TIPC_package/test_run/TIPC_hexLen50"
clustering_subfolder_nm <- 'ConsensusClusterPlus_test'
plot_TIPC_heatmap(root_dir = input_dir)


