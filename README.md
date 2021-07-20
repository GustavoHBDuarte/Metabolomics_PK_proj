# Rosuvastatin Absorption Estimator - Predicting AUC and C<sub>max</sub>: Project Overview

Rosuvastatin is a quite known lipid-lowering agent generally used for hypercholesterolemia treatment and coronary artery diseases prevention. There is a substantial inter-individual variability in the absorption of statins, which in turn may affect drug therapy safety and efficacy. Therefore, the ability of predicting the individual absorption of Rosuvastin before even taking the drug would be tremendously valuable for optimal drug therapy, minimizing adverse effects and reducing costs associated with unefective drug therapy.This project basically aims to:

* Develop an algorithm to predict interindividual rosuvastatin absorption by predicting the main pharmacokinetic parameters AUC and C<sub>max</sub>.
 
* Optimize Elastic Net regression applying feature selection and GridSearchCV hyperparameters tuning.

* Validate the model by means of Leave-One-Out cross validation    


## Code and Resources Used

**Programming language**: Python 3.7.10

**Packages**: pandas, numpy, sklearn, scipy, matplotlib, plotly



## Datasets

* The datasets used for this project refers to a Liquid Chromatograpy Mass Spectrometry (LC-MS) metabolite profiling experiment in predose human serum specimens, where raw acquisition files will be available on: www.ebi.ac.uk/metabolights/MTBLS3128.

* In this experiment AUC values ranged from 73.59 to 483.40 ng h/mL whereas C<sub>max</sub> ranged from 6.63 to 54.12 ng/mL.

* From .raw instrument experiment files, data were processed using *ProgenesisQI* software generating a .csv file with aligned LC-MS molecular features as well as other experiment-related information. Each molecular feature corresponds to a chemical compound detected in the above mentioned experiment and will be used as atributtes/features for machine learning modeling.

* In order to clean the above mentioned .csv file, first data were normalized by the internal standard feature (performed in MS Excel). Also, data were normalized using the option ‘Normalization by a pooled sample from group’ selecting the QC samples as group, and cubic root scaled (performed in www.metaboanalyst.ca). Then, features with relative standard deviation higher than 25% in quality control samples (samples analized during data acquisition to monitor LC-MS variation over the time course) were removed. 

* Several datasets were generated corresponding to different types of LC-MS analysis (positive and negative modes). Additionally, a dataset containing lab exams results for the enrolled subjects were also included in the analysis in order to compare its performance when using it as attributes/features to predict both AUC and C<sub>max</sub> with the performance of the model using molecular features as attributes. An integrated model using both molecular features and lab exam results as attributes was also evaluated.

* Evaluated datasets are available in the attached notebook as url link.



## Data Preparation for Machine Learning, Basic Data Visualization And Machine Learning Modeling

Since the previous cleaned dataset is pratically a semi-curated dataset, minor data preparation and visualization were performed before runing elastic net regressor.

The overall data analysis pipeline applied was:

1. Data preparation for elastic net regression (dummy variable transformation, when necessary, and data scaling)
2. Basic data inspection (checking number of missing values, correlation analysis, box plot of features before and after scaling, and histogram of scaled features)
3. Machine learning modeling (application of elastic net regressor to predict both AUC and C<sub>max</sub> for each observation)
4. Feature selection to improve the model (removal of features with zero coefficients)
5. Machine learning modeling (evaluating the effect  of feature reduction)
6. Fine feature reduction (optimized feature subset selection and hyperparameters tuning)
7. Machine learning modeling

For data preparation, basic data inspection/visualization, machine learning modeling and feature selection steps, functions were definied to ease each step.



## Main results

Model results were mainly evaluated in terms of explained variance R<sup>2</sup>, root mean square error RMSE and mean absolute percentage error MAPE. The distribution of residuals were also visualized. Due to reduced number of available observations (n=40), the built models were cross-validated by Leave-One-Out approach.
Some important considerations about the achieved results:

* Positive mode analysis models overperformed negative mode models for both AUC and C<sub>max</sub> predictions.

* A better models performance was achieved when using molecular features as attributes over lab exams results models.

* Integrating both molecular features and lab exams results simultaneously does not improve significantly models performance.  

* AUC predictions metrics (positive mode):
  * R<sup>2</sup>: 0.93
  * RMSE: 19.03 ng h/mL
  * MAPE: 10.12%

* C<sub>max</sub> predictions metrics (positive mode):
  * R<sup>2</sup>: 0.94
  * RMSE: 2.54 ng/mL
  * MAPE: 11.56%

## Conclusions

* Application of elastic net regression achieved satisfactory results;
* Promising application of rosuvastatin absorption prediction using predose serum samples;
* Implementation of the workflow herein described represents a step forward towards personalized drug therapy;
