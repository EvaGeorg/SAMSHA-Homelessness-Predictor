<h2>Treatment Episode Data Set: Discharges (TEDS-D)</h2>

The Treatment Episode Data Set -- Discharges (TEDS-D) is a national data system of annual discharges from substance abuse treatment
facilities. These data provide information on the demographic and substance abuse characteristics of substance abuse treatment 
discharges and their corresponding admissions aged 12 and older in facilities that report to individual state administrative data systems.

TEDS-D does not include all admissions/discharges to substance abuse treatment. 
It includes admissions to facilities that are licensed or certified by a state substance abuse agency to provide 
substance abuse treatment (or are administratively tracked for other reasons). In general, facilities reporting TEDS 
data are those that receive state alcohol and/or drug agency funds (including federal block grant funds) for the provision
of alcohol and/or drug treatment services. Some states report only publicly funded admissions; others are able to report all
admissions (both public and private) in facilities that receive public funds. All data reported to TEDS comes from the state 
administrative data systems.

TEDS-D records represent discharges rather than individuals, as a person may be admitted to and discharged from treatment 
more than once.

The limitations to be kept in mind when analyzing this dataset include:
- TEDS is an admission based system and therefore admissions and discharge do not represent individuals. Meaning an individual admitted and discharged twice in a year, would be counted as 2 admissions and 2 discharges.
- This data provides info on the treatment presented in specific facility, does not necessarily represent complete treatment episodes, which may include stays in multiple types of services and would require analysis of series of linked pairs of records.
- The primary, secondary and tertiary substances of abuse reported to the TEDS are those substances that led to the treatment episode and not necessarily a complete enumeration of all drugs used at the time of admission.
- The way an admission is defined may vary from state to state.
- Public funding constraints may direct states to selectively target special populations for example pregnant women or adolescents.
- Some states have no Opioid Treatment Programs that provide medication assistance therapy using methadone and/or buprenorphine.


Variables are elaborated in this file:
<a href="https://www.icpsr.umich.edu/icpsrweb/ICPSR/studies/30122/variables?start=0&sort=VARLABEL_SORT%20asc&STUDYQ=30122&EXTERNAL_FLAG=1&ARCHIVE=ICPSR&rows=50#"> Codebook for TEDS-D 2017 dataset </a>

This project uses machine learning techniques to analyze, cluster, visualize and classify data. 

Steps in developing the project:
<h3>Data Analysis and Exploration</h3>

Getting introduced with the dataset. From the analysis, observed the dataset consists of 1661207 rows and 76 attributes. All the features are categorical and the features include general descriptors such as gender, age, educ, marriage status, but also drug flags which indicate what kind of substance was the patient using at the time of entrance in rehabilitation and at the time of discharge. 

<h3>Clustering</h3>

Clustering data using K-Modes clustering for categorical data. Divided in 10 clusters. Missing data extracted and working on pure dataset with 371933 examples (rows). Created dummy variables of all columns before doing the clustering.
input: dataset
output: 10 clusters

<h3>Feature selection</h3>

<h4>Chi-Square Test</h4>

Here a chi-squared test is applied to detect the features with the strongest relation to the target attribute "TREATMENT SUCCESSFULL. 
In this method the same data used for clustering is fed to the algorthim with the goal to see if the most frequent attributes that appear in the clusters are also the attributes that have the strongest relation with the attribute 'TREATMENT SUCCESSFULL' 
The results obtained indicate that half (5/10) of the first 10 most important attributes also appear in the clusters with a frequency showed in the below bar chart.

<h4>Permutation Importance</h4>

Applying Permutation Importance on fitted models to determine the most important features in the dataset in relation to the target feature "LIVARAG_D". 
The permutation feature importance is defined to be the decrease in a model score when a single feature value is randomly shuffled. This procedure breaks the relationship between the feature and the target, thus the drop in the model score is indicative of how much the model depends on the feature.

<h4>Classifier</h4>

This dataset has two important features on which we focused for our classifier. Living arrangement on admission and living arrangements on discharge. What this classifier does is predicts the living arrangements on discharge. The input it takes is several features and if the patient is homeless or not at the time of admission. The output it provides is if the patient will end up homeless or will be able to obtain household at the end of the treatment. This is with the goal to help housing agencies which implement "Housing First Model" to better prioritize patients, so it's determined earlier if a patient needs housing assistance or not.   
