# The Silent Emergency - Predicting Preterm Birth
[Erdős Institute](https://www.erdosinstitute.org/) | [Data Science Boot Camp Fall 2023](https://www.erdosinstitute.org/programs/fall-2023/data-science-boot-camp)

- View our [5-minute recorded presentation]()
- Download our [Executive Summary](https://github.com/kgrillaert/preterm_birth/blob/main/Preterm_Birth_Exec%20_Summary.pdf)

## Team Members:
- [Katherine Grillaert](https://www.linkedin.com/in/kgrillaert/)
- [Divya Joshi](https://www.linkedin.com/in/divya-joshi-phd-candidate/)
- [Noah Rahman](https://www.linkedin.com/in/noah-rahman-01504257/)
- [Alex Sutherland](https://www.linkedin.com/in/alexander-sutherland-math/)
- [Kristina Zvolanek](https://www.linkedin.com/in/kristina-zvolanek/)

# Project Description

### ***“The world is facing a silent emergency. . . of preterm births.” - UNICEF[<sup>1</sup>](https://www.who.int/publications/i/item/9789240073890)***

Preterm birth is a primary cause of infant mortality and morbidity in the United States, affecting approximately 1 in 10 births.[<sup>2</sup>](https://pubmed.ncbi.nlm.nih.gov/36170979/) This rate is notably higher among Black women (14.6%), compared to White (9.4%) and Hispanic women (10.1%).[<sup>3</sup>](https://www.cdc.gov/reproductivehealth/maternalinfanthealth/pretermbirth.htm) These rates have recently declined for White women but remained unchanged for other groups.[<sup>4</sup>](https://pubmed.ncbi.nlm.nih.gov/35072604/) Despite its prevalence, predicting preterm birth remains challenging due to its multifaceted etiology rooted in environmental, biological, genetic, and behavioral interactions.[<sup>5</sup>](https://pubmed.ncbi.nlm.nih.gov/28941962) Our project harnesses machine learning techniques to predict preterm birth using electronic health records. This data intersects with social determinants of health, reflecting some of the interactions contributing to preterm birth.[<sup>6</sup>](https://pubmed.ncbi.nlm.nih.gov/19000029/) Recognizing that under-representation in healthcare research perpetuates racial and ethnic health disparities, we take care to use diverse data to ensure equitable model performance across underrepresented populations.[<sup>7</sup>](https://ses.library.usyd.edu.au/handle/2123/30841)

# Project Stakeholders
Pregnant individuals, prospective parents, medical professionals involved with maternal care and births, hospital systems, insurance companies

# Approach
We constructed two models to predict preterm birth, one with demographic features and one with health and lifestyle features. Our data source was the National Institute of Health’s [_All of Us_ Research Program](https://allofus.nih.gov/) controlled tier of de-identified medical data. The Demographics model was trained on a dataset of 13690 births between the years 2009 and 2022. Most demographic information for each individual was available only as summary statistics based on their zip code. Race and ethnicity were available on the individual level. The Lifestyle model was trained on a dataset of 8771 births between the years 2011 and 2022. Features included drinking, smoking, drug use, body mass index, diabetes, and mental health.

# Model Details
***Baseline model:*** Our baseline model was a weighted coin flip that reflected the ratio of preterm births in our data.

***Demographics model:*** The Demographics model was trained on a dataset of 13690 births between the years 2009 and 2022. Most demographic information for each individual was available only as summary statistics based on their zip code. Race and ethnicity were available on the individual level. We used a Support Vector Classifier with class weights to prioritize prediction of preterm birth. GridSearch CV was used to tune hyperparameters. 

***Lifestyle model:*** The Lifestyle model was trained on a dataset of 8771 births between the years 2011 and 2022. Features explored included drinking, smoking, drug use, body mass index, diabetes, and mental health. We used a logistic regression with class weights to prioritize prediction of preterm birth.

For both models, we used the package [AI Fairness 360](https://aif360.res.ibm.com/) to ensure that our model predictions performed equally well
across protected classes (race and ethnicity).

# Data Access
The data used to train these models was accessed from the [_All of Us_ Research Hub](https://www.researchallofus.org/). You must [register for the Researcher Workbench](https://www.researchallofus.org/register/) to access the data. We specifically used individual-level data from the [Controlled Access Tier](https://www.researchallofus.org/data-tools/data-access/), which requires the completion of additional training. To facilitate testing without access to this protected health data, we have also provided a synthetic data frame.

# Interacting with this Code (in progress)

### Dependencies
Running the code requires the following Python packages: 
```
scikit-learn, pandas, numpy, matplotlib, aif360
```
### Jupyter notebooks are organized into different folders:

#### Data Cleaning

- ` 01.Data_Cleaning/`
  -  `Data_Cleaning_Demographics.ipynb`:
  -  `Data_Cleaning_Lifestyle.ipynb`:
 
#### Exploratory Data Analysis

- `02.Exploratory_Data_Analysis/`
  - `EDA_Demographics.ipynb`:
  - `EDA_Lifestyle.ipynb`:

#### Applying the Models

- `03.Models/`
  - `Preterm_Birth_Demographics_Models.ipynb`:
  - `Preterm_Birth_Lifestyle_Models.ipynb`:

# Model Workflows

# Key Performance Indicators (KPIs)
We prioritized minimizing costly false negatives, accepting the possibility of increased false positives.

| Demographic Model | Final SVC | Baseline |
|---|---|---|
| Recall | 0.413 | 0.145 |
| F1 |0.242 | 0.137| 
|PR-AUC | 0.172 | 0.192 |
|Equalized Odds | 0.0| |

| Health and Lifestyle Model | Final Log | Baseline|
|---|---|---|
| Recall | 0.473 | 0.137|
|F1 | 0.247 | 0.136|
|PR-AUC | 0.197 | 0.196|
|Equalized Odds| 0.0| |

# Conclusion and Future Work
Our models performed only as well as the baseline model, highlighting the challenges of predicting preterm birth with only electronic health records. Predictive models may need to incorporate features from more than one domain, including environmental, behavioral, biological, and genetic factors.[<sup>6</sup>](https://pubmed.ncbi.nlm.nih.gov/19000029) Future work should consider the collection of thorough, individual-level data, observed during the pregnancy, in order to provide a high-quality data source for machine learning predictions.

# Acknowledgements
Thank you to Evelyn Huszar for her enthusiastic mentorship during this project. Our gratitude also to
Roman Holowinsky, Matt Osborne, Alec Clott, and The Erdős Institute for their support during this
boot camp. Finally, thank you to the NIH and the All of Us program for collecting, anonymizing, and
allowing us to use the data for this project

# References
1. World Health Organization et al. Born too soon: decade of action on preterm birth. World Health Organization, 2023.
   
2. Csaba Siffel, Andrew K Hirst, Sujata P Sarda, Michael W Kuzniewicz, and De-Kun Li. The clinical burden of extremely preterm birth in a large medical records database in the united states: Mortality and survival associated with selected complications. Early Human Development, 171:105613, 2022.

3. Preterm birth. https://www.cdc.gov/reproductivehealth/maternalinfanthealth/pretermbirth.htm, October 2023. Accessed: 2023-11-18.

4. Martin JA, Osterman M. Exploring the Decline in the Singleton Preterm Birth Rate in the United States, 2019-2020. NCHS Data Brief, (430):1-8, 2021. 

5. Tracy A Manuck. Racial and ethnic differences in preterm birth: a complex, multifactorial problem. In Seminars in perinatology, volume 41, pages 511–518. Elsevier, 2017.

6. Dhelia M Williamson, Karon Abe, Christopher Bean, Cynthia Ferré, Zsakeba Henderson, and Eve Lackritz. Current research in preterm birth. Journal of Women’s Health, 17(10):1545–1549, 2008.

7. CM Vajdic, A Kricker, M Giblin, J McKenzie, J Aitken, GG Giles, and BK Armstrong. Reaching the hard-to-reach: a systematic review of strategies for improving health and medical research with socially disadvantaged groups. 2013.

