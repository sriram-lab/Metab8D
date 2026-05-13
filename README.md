# Metab8D: A metabolic regulome network from multiomics and machine learning
<img width="400" height="400" alt="Recon8D_icon (3)" src="https://github.com/user-attachments/assets/d18f1913-a5e9-4e98-a1f5-dd427094625f" />

## Introduction

Metabolite variation across cells may arise due to differences in regulation at the transcriptional, post-transcriptional, translational, and post-translational levels. Metab8D utilizes ten feature sets from eight biomolecular classes: 1. genomic copy number variation (CNV), 2. genomic mutations, 3. epigenomic DNA methylation, 4. epigenomic histone PTMs, transcriptomics – 5a. coding transcripts and 5b. RNA splicing, non-coding transcriptomics – 6a. miRNA and 6b. lncRNA, 7. proteomics, and 8. phosphoproteomics to train machine learning (ML) models for predicting relative levels of each metabolite across matched cell lines from the Cancer Cell Line Encyclopedia, thereby inferring a multiomic metabolic regulatory network. Mutations were excluded from random forest model results due to their binary structure (as discussed in the associated Metab8D manuscript referenced here). This repository contains the machine learning workflow Metab8D employs to assess the relationship between features and their respective predicted metabolites. The primary output for this work is captured in the Metab8D_network.xlsx file, which contains the top 20 features in predicting each metabolite across nine feature sets. 

## Methods

As outlined in the ML_function.ipynb file, Metab8D network generation involves training ML models, assessing their accuracy, and obtaining feature importances thereof. This process is repeated for each individual feature set. An example of model generation is provided at the bottom of the ML_function.ipynb file using the histone PTM data. A requirements.txt file is provided, specifying all necessary packages for running this code.

## Results

The resultant proposed regulome network can be found in the Metab8D_network.xlsx file, where the top 20 features for all 2,025 trained metabolite models (nine feature sets for 225 metabolites), along with their respective confidence scores, may be found. Features with high confidence scores and no previously identified mechanistic relationship should be prioritized for further study.

## Conclusions

By comparing accuracies and assessing feature importance scores from multiomic inputs, Metab8D proposes systems-level relationships between omics features and metabolites across the CCLE cell line panel, and validates such relationships in independent data.

## File descriptions

Metab8D_network.xlsx: Top 20 features for 225 RF metabolite models from nine feature sets (excluding genomic mutations) along with confidence scores (0 through 8) based on the number of controls (out of 8 experiments) for which each feature appeared in the top 20 most imoprtant features.

ML_function.ipynb: ML script for random forests, XGBoost, ridge regression, and lasso regression, as well as feature importance generation. Includes example code for using histone PTM data as input.

RF_results: Pearson's correlations and P values for all metabolite models from each of nine feature sets. Significance is determined by Bonferroni-corrected P value.

recon_mapping: MATLAB and Python scripts for extracting genes from reactions involving metabolites of interest and matching them with top feature lists, as well as a csv containing common gene name to BiggID translations.

human_1_mapping.csv: List of metabolites from Recon3D with mapped Human1 IDs.

example_datasets: Metabolomics and histone PTM (original and zero imputed) data that can be used to test the machine lerning code. 

preprocessing_example.ipynb: Example code for preprocessing the original histone PTM data along with examples of z-score normalization and KNN imputation.
