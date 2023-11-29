# The Silent Emergency - Predicting Preterm Birth
[Erdős Institute](https://www.erdosinstitute.org/) | [Data Science Boot Camp Fall 2023](https://www.erdosinstitute.org/programs/fall-2023/data-science-boot-camp)

- View our [5-minute recorded presentation]()

## Team Members:
- [Katherine Grillaert](https://www.linkedin.com/in/kgrillaert/)
- [Divya Joshi](https://www.linkedin.com/in/divya-joshi-phd-candidate/)
- [Noah Rahman](https://www.linkedin.com/in/noah-rahman-01504257/)
- [Alex Sutherland](https://www.linkedin.com/in/alexander-sutherland-math/)
- [Kristina Zvolanek](https://www.linkedin.com/in/kristina-zvolanek/)

# Project Description

### ***“The world is facing a silent emergency. . . of preterm births.” - UNICEF[<sup>1</sup>](https://www.who.int/publications/i/item/9789240073890)***

Preterm birth is a primary cause of infant mortality and morbidity in the United States, affecting approximately 1 in 10 births.1 This rate is notably higher among Black women (14.6%), compared to White (9.4%) and Hispanic women (10.1%).[<sup>3</sup>](https://www.cdc.gov/reproductivehealth/maternalinfanthealth/pretermbirth.htm) These rates have
recently declined for White women but remained unchanged for other groups.[<sup>4</sup>](https://pubmed.ncbi.nlm.nih.gov/35072604/)

Despite its prevalence, predicting preterm birth remains challenging due to its multifaceted etiology rooted in environmental, biological, genetic, and behavioral interactions.3 Our project harnesses machine learning techniques to predict preterm birth using electronic health records. This data intersects with social determinants of health, reflecting some of the interactions contributing to preterm birth.4 Recognizing that under-representation in healthcare research perpetuates racial and ethnic health disparities, we take care to use diverse data to ensure equitable model performance across underrepresented populations.5

# Project Stakeholders:
Pregnant individuals, prospective parents, medical professionals involved with maternal care and births, hospital systems, insurance companies


We constructed two models to predict preterm birth, one with demographic features and
one with lifestyle features. Our data source was the National Institute of Health’s [_All of Us_ Research
Program](https://allofus.nih.gov/) controlled tier of de-identified medical data.


# Model Details
***Baseline model:*** Our baseline model was a weighted coin flip that reflected the ratio of preterm births in our data.

***Demographics model:*** The Demographics model was trained on a dataset of 13690 births between the years 2009 and 2022. Most demographic information for each individual was available only as summary statistics based on their zip code. Race and ethnicity were available on the individual level. We used a Support Vector Classifier with class weights to prioritize prediction of preterm birth.

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
