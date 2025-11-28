# Metab8D: A metabolic regulome network from oct-omics and machine learning
<img width="400" height="400" alt="Recon8D_icon (3)" src="https://github.com/user-attachments/assets/d18f1913-a5e9-4e98-a1f5-dd427094625f" />

## Introduction

Metabolite variation across cells may arise due to differences in regulation at the transcriptional, post-transcriptional, translational, and post-translational levels. Recon8D utilizes eight omics classes (genomics (CNV and mutations), histone PTMs, DNA methylation, transcriptomics, RNA splicing, miRNA, lncRNA, proteomics, and phosphoproteomics) to predict metabolomic variation across cancer cell lines from the Cancer Cell Line Encyclopedia, thereby inferring a multiomic metabolic regulatory network. This repository contains the machine learning workflow Recon8D employs to assess the relationship between features and their respective predicted metabolites. The primary output for this work is captured in the Recon8D_network.xlsx file, which contains the top 20 features in predicting each metabolite across 9 omics datasets. 

## Methods

As outlined in the ML_function.ipynb file, Metab8D network generation involves training ML models, assessing their accuracy, and obtaining feature importances thereof. This process is repeated for each individual omics input. An example of model generation is provided at the bottom of the ML_function.ipynb file using the histone PTM data. A requirements.txt file is provided, specifying all necessary packages for running this code. 

## Results

The resultant proposed regulome network can be found in the Metab8D_network.xlsx file, where the top 20 features for all 2,025 trained metabolite models, along with their respective confidence scores, may be found. Features with high confidence scores and no previously identified mechanistic relationship should be prioritized for further study. 

## Conclusions

By comparing accuracies and assessing feature importance scores from multiomic inputs, Metab8D proposes systems-level relationships between omics features and metabolites across the CCLE cell line panel, and validates such relationships in independent data. 

## File descriptions

Metab8D_network.xlsx: Top 20 features for 225 RF metabolite models from 9 omics inputs along with confidence scores (0 through 8) based on the number of controls (out of 8 experiments) for which each feature appeared in the top 20 most imoprtant features.

ML_function.ipynb: ML script for random forests, XGBoost, ridge regression, and lasso regression, as well as feature importance generation. Includes example code for using histone PTM data as input. 

RF_results: Pearson's correlations and P values for all metabolite models from each of 8 omics classes. Significance is determined by Bonferroni-corrected P value. 

recon_mapping: MATLAB and Python scripts for extracting genes from reactions involving metabolites of interest and matching them with top feature lists, as well as a csv containing common gene name to BiggID translations. 

human_1_mapping.csv: List of metabolites from Recon3D with mapped Human1 IDs. 

example_datasets: metabolomics and histone PTM data that can be used to test the machine lerning code present in this repository. The rest of the CCLE data and trained models may be found here: https://doi.org/10.7303/syn68236153
