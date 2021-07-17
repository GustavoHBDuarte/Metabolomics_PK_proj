# Rosuvastatin Absorption Estimator - Predicting AUC and Cmax: Project Overview

Rosuvastatin is a quite known lipid-lowering agent generally used for hypercholesterolemia treatment and coronary artery diseases prevention. There is a substantial inter-individual variability in the absorption of statins, which in turn may affect drug therapy safety and efficacy. Therefore, the ability of predicting the individual absorption of Rosuvastin before even taking the drug would be tremendously valuable for optimal drug therapy, minimizing adverse effects.This project basically aims to:

* Develop an algorithm to predict interindividual rosuvastatin absorption by predicting the main pharmacokinetic parameters AUC and Cmax.
 
* Optimize Elastic Net regression applying feature selection and GridSearchCV hyperparameters tuning.

* Validate the model by means of Leave-One-Out cross validation    


## Code and Resources Used

**Programming language**: Python 3.7.10

**Packages**: pandas, numpy, sklearn, scipy, matplotlib, plotly


## Dataset

* The dataset used for this project refers to a Liquid Chromatograpy Mass Spectrometry metabolite profiling experiment, where raw acquisition files will be available on: www.ebi.ac.uk/metabolights/MTBLS3128.

* From .raw files data were processed using *ProgenesisQI* software generating a .csv file with aligned LC-MS molecular features as well as other experiment-related information.

* In order to clean the above mentioned .csv file, first data was normalized by the internal standard feature. Then, features with relative standard deviation higher than 25% were removed. This step was performed outside Python environment, using MS Excel.

* Resulting dataset is available in the attached notebook


## Data Preparation for Machine Learning, Basic Data Visualization And Machine Learning Modeling

Since the previous cleaned datased is pratically a semi-curated dataset, minor data preparation and visualization were performed before runing elastic net regressor.

The overall data analysis pipeline applied was:

1. Data preparation for elastic net regression
2. Basic data inspection (checking number of missing values, correlation analysis, box plot of features before and after scaling, and histogram of scaled features)
3. Machine learning modeling (application of elastic net regressor)
4. Feature selection to improving the model (removal of features with zero coefficients)
5. Machine learning modeling (evaluating the effect  of feature reduction)
6. Fine feature reduction and hyperparameters tuning
7. Machine learning modeling


For data preparation, basic data inspection/visualization, machine learning modeling and feature selection steps, functions were definied to ease each step.

Data visualization 


