# RevSpot-Replication-Package

This replication package is created for the paper titled "Where Should I Look at? Recommending Lines that Reviewers Should Pay Attention To", which is published at the 29th IEEE International Conference on Software Analysis, Evolution and Reengineering (SANER).

## Something you need to know before start
Since the limitation of file size that allow to uploading to github, this repo only includes the source code of all scripts and excludes the part of the dataset. To re-generate the result in the paper, please follow "Evaluate result" section below. If the practioners want to train the model by themself, please download the entire replication package from zenodo [here](https://doi.org/10.5281/zenodo.5839022) and follow "Build you own model" section below and commments in the scripts. The replication package in zenodo includes all dataset and model used in the paper. 

## Description

There are two main parts in our work. The first part is data process (see data_process folder) part to process the raw dataset and generate csv files. 
We implement the experiment for this part with Python, Jupyter notebook for IDE and Conda for environment.
The second part is data evaluation(see data_eval folder) part to evaluate the experiment result with csv files generated in previous step. We use R and R studio for IDE in this part. The package structure with respect to RQ is as follows:
```
    .
    ├── ...
    ├── data_eval                 # Data evaluation (R)
    │   ├── RQ1_analysis.R.       # Evaluation for RQ1
    │   ├── RQ2_file_analysis.R   # File level evaluation for RQ2
    │   └── RQ2_line-analysis.R      # Line level evaluation for RQ2	
    ├── data_process              # Data process (Python)
    │   ├── commented             # Predict the inline comment location
    │   │   ├── dataset               # dataset
    │   │   │   ├── csv               # output files of data process
    │   │   │   ├── eval_file         # input and output files for ngram average entropy
    │   │   │   ├── fileLevel         # raw data for file level model
    │   │   │   ├── lime-feature-model    # trained LIME model
    │   │   │   ├── lineLevel             # raw data for line level model
    │   └── └── └──ml-model               # trained file-level model
    │   │   ├── File_Level.ipynb  # File level data process for RQ2
    │   │   ├── Line_level.ipynb  # Line level data process for RQ2
    │   ├── revised               # Predict the lines to be revised
    │   │   ├── dataset               # dataset
    │   │   │   ├── csv               # output files of data process
    │   │   │   ├── eval_file         # input and output files for ngram average entropy
    │   │   │   ├── fileLevel         # raw data for file level model
    │   │   │   ├── lime-feature-model    # trained LIME model
    │   │   │   ├── lineLevel             # raw data for line level model
    │   └── └── └──ml-model               # trained file-level model
    │   │   ├── File_Level.ipynb  # File level data process for RQ2
    │   │   └── Line_level.ipynb  # Line level data process for RQ2
    ├── SLP-Core                  # ngram baseline approach
    ├── RQ3 			# Manual test results for RQ3 
    ├── env                       # Conda environment files
    └── ...

```  

## Getting Started

### System dependencies
* For data process part, we use Ubuntu 20.04.3 LTS
* For data evaluation part, we use macOS Big Sur (11.3)

### Package dependencies
|                      | Packages                                                                                                        |
|----------------------|-----------------------------------------------------------------------------------------------------------------|
| Data Process(Python) | sklearn, numpy, pandas, scipy, lime, time,  pickle, math, warnings, os, operator, matplotlib, csv,math,imblearn |
| Data Evaluation(R)   | ggplot2,dplyr,tidyverse,gridExtra,ggpubr                                                                        |

### Installing

For data process part, we save our conda environment file in env folder. Create the new env with file:
```
conda env create -f environment.yml
```
```
conda activate YOUR_ENV
```
It will install all dependencies need for the experiment.

###  Model Building
To build your own model, please download the entire replication package from zenodo [here](https://doi.org/10.5281/zenodo.5832080) and use scripts in data_process folder.
To get file level model and result: 
run File_level.ipynb from top to bottom in directory data_process/commented/File_level.ipynb for predicting "comment" task
run File_level.ipynb from top to bottom in directory data_process/revised/File_level.ipynb for predicting "revise" task

To get line level model and result: 
run Line_level.ipynb from top to bottom in directory data_process/commented/Line_level.ipynb for predicting "comment" task
run Line_level.ipynb from top to bottom in directory data_process/revised/Line_level.ipynb for predicting "revise" task

###  Results Analysis
To analyze the result, please use the R scripts in data_eval folder.
First, please set the working directory to the source code file. For R studio, you can set by session -> set working directory -> to source file location. Otherwise, the program cannot find the files.

To generate the figures in the paper:
Run RQ1_analysis.R  for Figure 4
Run RQ2_file_analysis.R for Figures 3.
Run RQ2_line_analysis.R for RQ2 Figures 5.

### Executing the scripts

Now we can start running the experiment. Just run each script from top to bottom. 

## Reference

Please use the following reference for this replication package:

    Yang Hong, Chakkrit Tantithamthavorn, Patanamon Thongtanunam, "Where Should I Look at? 
    Recommending Lines that Reviewers Should Pay Attention To", in Proceedings of the 29th 
    IEEE International Conference on Software Analysis, Evolution and Reengineering (SANER), 2022.

