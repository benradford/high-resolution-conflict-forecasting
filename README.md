High Resolution Conflict Forecasting with Spatial Convolutions and Long Short-Term Memory
===================

Replication Archive
-------------------

Benjamin J. Radford  
Assistant Professor  
UNC Charlotte  
bradfor7@uncc.edu  
[Personal Website](https://www.benradford.com)  


## Table of Contents

* [Preface](#preface)
* [Requirements](#requirements)
* [Setup](#setup)
* [Replication](#replication)
* [Full Replication from Scratch](#full-replication-from-scratch)
* [Directory Structure](#directory-structure)
* [Citation](#citation)


## Preface

This repository contains replication code for the article "High Resolution Conflict Forecasting with Spatial Convolutions and Long Short-Term Memory" in *International Interactions* (2022). The paper describes an entry to the [Violence Early-Warning System (ViEWS) Prediction Competition](https://www.pcr.uu.se/research/views/news/?tarContentId=844492) held in 2020. The entry was a convolutional long short-term memory (ConvLSTM) solution to the challenge that ranked second in overall performance among all entrants.  

The requisite data are distributed separately from this repository and can be downloaded from Harvard Dataverse: [replication data](https://doi.org/10.7910/DVN/DQKCA9) and [supplemental replication data](https://doi.org/10.7910/DVN/PD3XWV).  

I appologize for the poor code quality and, in particular, the lack of properly parameterized file paths. In order to run any of the files below, all necessary data must be loaded in the correct relative directories. Please see the Directory Structure section below for details.

I **strongly recommend** that replication efforts start with the code found in the `./replication` directory. The files in this folder will produce the tables and figures from the paper. 

I **strongly advise against** attempting a full replication from scratch. A full replication can be undertaken by first running all files in `./supplemental_replication_files` and then all files in `./replication`. However, this may take many days of compute time (not counting any user time) on a relatively powerful desktop computer (>= 64Gb RAM) with a GPU (e.g., RTX 2080 Ti). Furthermore, perfect replication results are not guaranteed due to (1) updates to the data provided by the ViEWS team during and after the competition and (2) differences that arise due to randomness while fitting the model in different hardware and software environments.


## Requirements

* **Required:** [Anaconda Python](https://www.anaconda.com)
* **Required:** 64Gb of RAM. 128Gb preferable. 
* **Required:** `data.part001.rar` through `data.part030.rar` from [Harvard Dataverse](https://doi.org/10.7910/DVN/DQKCA9).
* **Required:** [OpenViEWS2](https://github.com/UppsalaConflictDataProgram/OpenViEWS2) [[1]](#hegre-etal-2019)
* **Optional:** A GPU equivalent to or better than an RTX 2080 Ti. Only necessary for a full replication. See warnings in README before attempting.
* **Optional:** `supplemental_data.part01.rar` through `supplemental_data.part43.rar` from [Harvard Dataverse](https://doi.org/10.7910/DVN/PD3XWV). Only necessary for a full replication. See warnings in this README before attempting.
* **Optional:** Ubuntu 18.04. Note that the analyses have not been tested in other software environments.


## Setup

1. Download (clone) this repository to your local computer. If you have git installed, you can do this by running `git clone https://github.com/benradford/high-resolution-conflict-forecasting` in the terminal.
2. Download (clone) [OpenViEWS2](https://github.com/UppsalaConflictDataProgram/OpenViEWS2.git) to your local computer. If you have git installed, you can do so by running `git clone https://github.com/UppsalaConflictDataProgram/OpenViEWS2.git` in the terminal.
3. Make sure that you have [Anaconda Python](https://www.anaconda) installed.
4. Create a new conda environment called `views2` with the requirements found in `environment.yml`. You can do so by first changing your directory to the root of `high-resolution-conflict-forecasting/` and then running `conda env create --file environment.yml` in the terminal. 
5. Once your environment is created, change your directory to the root of `OpenViEWS2`. Activate the conda environment by running `conda activate views2`. Then, install the `views` module by running `pip install --editable ./`. 
6. Download all replication data files, `data.part001.rar` through `data.part030.rar`, from [Harvard Dataverse](https://doi.org/10.7910/DVN/DQKCA9).
7. Use a rar utility to extract the contents of these files into the directory `high-resolution-conflict-forecasting/data`. The directory tree can be found below to verify that the files are extracted in the correct place.
8. If doing a full replication, download all supplemental data files, `supplemental_data.part01.rar` through `supplemental_data.part43.rar`, from [Harvard Dataverse](https://doi.org/10.7910/DVN/PD3XWV). 
9. Use a rar utility to extract the contents of these files into the directory `high-resolution-conflict-forecasting/supplemental_data`. The directory tree can be found below to verify that the files are extracted in the correct place.


## Replication

Estimated completion time: 3--6 hours.

These steps will reproduce all figures and tables from "High Resolution Conflict Forecasting with Spatial Convolutions and Long Short-Term Memory." I recommend starting here for replication purposes.

1. Follow steps 1 through 7 outlined above in the Setup section.
2. Start a new instance of juypyter notebook by typing `jupyter notebook` in the terminal.
3. Load the desired file from the `./replication` directory. Verify that the `views2` kernel is running.
4. Run all code chunks from top to bottom.


## Full Replication from Scratch

Estimated completion time: 48--96 hours.

I **strongly recommend** that you do not attempt to replicate all models from scratch. Doing so will take many days even with a relatively high performance computer with sufficient RAM (>= 64Gb) and GPU (>= RTX 2080 Ti). Furthermore, perfect replication results are not guaranteed due to (1) updates to the data provided by the ViEWS team during and after the competition and (2) differences that arise due to randomness while fitting the model in different hardware and software environments. 

If you are intent upon performing a full replication, begin by following steps 1 through 9 outlined above in the Setup section. Then, following the same procedure as in the Replication section, run all .ipynb files in the `./supplemental_replication_files` directory.


## Directory Structure

Verify that your `views2020/` directory has the following structure. Note that the files contained within `./data` and `./supplemental_data` are provided separately via Harvard Dataverse.

```
high-resolution-conflict-forecasting/
├── data
│   ├── attention_model
│   │   └── attention_values.npy
│   ├── competition_model
│   │   ├── feature_dropout
│   │   │   └── bjr_all_preds_drop.csv
│   │   └── forecasts
│   │       ├── updated_ViEWSpred_competition_radford_set1.csv
│   │       ├── updated_ViEWSpred_competition_radford_set2.csv
│   │       └── updated_ViEWSpred_competition_radford_set3.csv
│   ├── expanded_features
│   │   └── forecasts
│   │       ├── updated_ViEWSpred_competition_radford_set1.csv
│   │       ├── updated_ViEWSpred_competition_radford_set2.csv
│   │       └── updated_ViEWSpred_competition_radford_set3.csv
│   ├── single_feature
│   │   └── forecasts
│   │       ├── updated_ViEWSpred_competition_radford_set1.csv
│   │       ├── updated_ViEWSpred_competition_radford_set2.csv
│   │       └── updated_ViEWSpred_competition_radford_set3.csv
│   ├── pgm.csv
│   └── t1_pgm.csv
├── figures
│   ├── actual_vs_predicted.png
│   ├── count_vs_predicted.png
│   ├── linegraphs.pdf
│   ├── map_actual_dec2018.pdf
│   ├── map_predicted_dec2018.pdf
│   ├── map_predicted_mar.pdf
│   ├── map_predicted_max.pdf
│   ├── map_predicted_oct.pdf
│   ├── task1_benchmark_actual_vs_predicted.pdf
│   └── task1_radford_actual_vs_predicted.pdf
├── replication
│   ├── table2a_figure4_figure5_figure6.ipynb
│   ├── table2b_figure3.ipynb
│   ├── table3.ipynb
│   ├── table4_expanded_features.ipynb
│   ├── table4_single_feature.ipynb
│   └── table5.ipynb
├── supplemental_data
│   ├── attention_model
│   │   └── model_attention.h5
│   ├── competition_model
│   │   ├── competition_entry_predictions.npy
│   │   └── model_competition_entry.h5
│   ├── expanded_features
│   │   ├── expanded_features_predictions.npy
│   │   └── model_expanded_features.h5
│   ├── feature_dropout
│   │   ├── bjr_all_preds_addone_ln_ged_best_sb.npy
│   │   ├── bjr_all_preds_addone_pgd_agri_ih.npy
│   │   ├── bjr_all_preds_addone_pgd_barren_ih.npy
│   │   ├── bjr_all_preds_addone_pgd_bdist3.npy
│   │   ├── bjr_all_preds_addone_pgd_capdist.npy
│   │   ├── bjr_all_preds_addone_pgd_forest_ih.npy
│   │   ├── bjr_all_preds_addone_pgd_gcp_mer.npy
│   │   ├── bjr_all_preds_addone_pgd_pasture_ih.npy
│   │   ├── bjr_all_preds_addone_pgd_pop_gpw_sum.npy
│   │   ├── bjr_all_preds_addone_pgd_savanna_ih.npy
│   │   ├── bjr_all_preds_addone_pgd_ttime_mean.npy
│   │   ├── bjr_all_preds_addone_pgd_urban_ih.npy
│   │   ├── bjr_all_preds_addone_spdist_pgd_diamsec.npy
│   │   ├── bjr_all_preds_drop_in_ln_ged_best_sb.npy
│   │   ├── bjr_all_preds_drop_in_pgd_agri_ih.npy
│   │   ├── bjr_all_preds_drop_in_pgd_barren_ih.npy
│   │   ├── bjr_all_preds_drop_in_pgd_bdist3.npy
│   │   ├── bjr_all_preds_drop_in_pgd_capdist.npy
│   │   ├── bjr_all_preds_drop_in_pgd_forest_ih.npy
│   │   ├── bjr_all_preds_drop_in_pgd_gcp_mer.npy
│   │   ├── bjr_all_preds_drop_in_pgd_pasture_ih.npy
│   │   ├── bjr_all_preds_drop_in_pgd_pop_gpw_sum.npy
│   │   ├── bjr_all_preds_drop_in_pgd_savanna_ih.npy
│   │   ├── bjr_all_preds_drop_in_pgd_ttime_mean.npy
│   │   ├── bjr_all_preds_drop_in_pgd_urban_ih.npy
│   │   ├── bjr_all_preds_drop_in_spdist_pgd_diamsec.npy
│   │   ├── bjr_all_preds_drop_out_ln_ged_best_sb.npy
│   │   ├── bjr_all_preds_drop_out_pgd_agri_ih.npy
│   │   ├── bjr_all_preds_drop_out_pgd_barren_ih.npy
│   │   ├── bjr_all_preds_drop_out_pgd_bdist3.npy
│   │   ├── bjr_all_preds_drop_out_pgd_capdist.npy
│   │   ├── bjr_all_preds_drop_out_pgd_forest_ih.npy
│   │   ├── bjr_all_preds_drop_out_pgd_gcp_mer.npy
│   │   ├── bjr_all_preds_drop_out_pgd_pasture_ih.npy
│   │   ├── bjr_all_preds_drop_out_pgd_pop_gpw_sum.npy
│   │   ├── bjr_all_preds_drop_out_pgd_savanna_ih.npy
│   │   ├── bjr_all_preds_drop_out_pgd_ttime_mean.npy
│   │   ├── bjr_all_preds_drop_out_pgd_urban_ih.npy
│   │   ├── bjr_all_preds_drop_out_spdist_pgd_diamsec.npy
│   │   ├── bjr_all_preds_median_ln_ged_best_sb.npy
│   │   ├── bjr_all_preds_median_pgd_agri_ih.npy
│   │   ├── bjr_all_preds_median_pgd_barren_ih.npy
│   │   ├── bjr_all_preds_median_pgd_bdist3.npy
│   │   ├── bjr_all_preds_median_pgd_capdist.npy
│   │   ├── bjr_all_preds_median_pgd_forest_ih.npy
│   │   ├── bjr_all_preds_median_pgd_gcp_mer.npy
│   │   ├── bjr_all_preds_median_pgd_pasture_ih.npy
│   │   ├── bjr_all_preds_median_pgd_pop_gpw_sum.npy
│   │   ├── bjr_all_preds_median_pgd_savanna_ih.npy
│   │   ├── bjr_all_preds_median_pgd_ttime_mean.npy
│   │   ├── bjr_all_preds_median_pgd_urban_ih.npy
│   │   └── bjr_all_preds_median_spdist_pgd_diamsec.npy
│   └── single_feature
│       ├── model_single_feature.h5
│       └── single_feature_predictions.npy
├── supplemental_replication_files
│   ├── attention_model
│   │   └── fit_model.ipynb
│   ├── competition_model
│   │   ├── fit_model.ipynb
│   │   └── make_predictions.ipynb
│   ├── expanded_features
│   │   ├── fit_model.ipynb
│   │   └── make_predictions.ipynb
│   ├── feature_dropout
│   │   └── run_feature_dropout.ipynb
│   └── single_feature
│       ├── fit_model.ipynb
│       └── make_predictions.ipynb
├── environment.yml
└── README
```


## Citation

Radford, Benjamin J. 2022. "High Resolution Conflict Forecasting with Spatial Convolutions and Long Short-Term Memory." *International Interactions*. 


## References

<a name="hegre-etal-2019">1.</a> Hegre, Håvard, Marie Allansson, Matthias Basedau, Michael Colaresi, Mihai Croicu, Hanne Fjelde, Frederick Hoyles, et al. "ViEWS: A Political Violence Early-Warning System." *Journal of Peace Research* 56, no. 2 (March 2019): 155–74. https://doi.org/10.1177/0022343319823860.
