# The Silent Emergency - Predicting Preterm Birth
[Erdős Institute](https://www.erdosinstitute.org/) | [Data Science Boot Camp Fall 2023](https://www.erdosinstitute.org/programs/fall-2023/data-science-boot-camp)

- View our [5-minute recorded presentation]()

## Team Members:
- [Katherine Grillaert]()
- [Divya Joshi]()
- [Noah Rahman]()
- [Alex Sutherland]()
- [Kristina Zvolanek](https://www.linkedin.com/in/kristina-zvolanek/)

# Project Description

### ***“The world is facing a silent emergency. . . of preterm births.” - UNICEF[<sup>1</sup>](https://www.who.int/publications/i/item/9789240073890)***

Premature infants are at risk for many negative, long-term health issues.[<sup>2</sup>](https://www.thelancet.com/journals/lancet/article/PIIS0140-6736(08)60074-4/fulltext) The preterm birth
rate in the United States is approximately 10% overall, with highest rates occurring among Black women
(14.6%), and lowest rates occurring among White (9.4%) and Hispanic women (10.1%).[<sup>3</sup>](https://www.cdc.gov/reproductivehealth/maternalinfanthealth/pretermbirth.htm) These rates have
recently declined for White women but remained unchanged for other groups.[<sup>4</sup>](https://pubmed.ncbi.nlm.nih.gov/35072604/) Under-representation in
healthcare research contributes to racial and ethnic health disparities.[<sup>5</sup>](https://bmcmedresmethodol.biomedcentral.com/articles/10.1186/1471-2288-14-42) Therefore, by using a representative 
dataset and non-invasive metrics, and ensuring our model’s equitable performance across diverse
racial and ethnic groups, we aim to contribute to a healthier start for all children.

We constructed two models to predict preterm birth, one with demographic features and
one with lifestyle features. Our data source was the National Institute of Health’s [_All of Us_ Research
Program](https://allofus.nih.gov/) controlled tier of de-identified medical data. The Demographics model was trained on a dataset
of 13690 births between the years 2009 and 2022. Most demographic information for each individual was
available only as summary statistics based on their zip code. Race and ethnicity were available on the
individual level. The Lifestyle model was trained on a dataset of 7XXX births between the years X and
Z. Features explored include drinking, smoking, body mass index, and XYZZZ.

# Model Details
**Demographics model:** We used a Support Vector Classifier with class weights to prioritize prediction of preterm birth. As our recall rates were initially poor, we used Synthetic Minority Over-sampling Technique to oversample our data from preterm births. 

**Lifestyle model:** 

For both models, we used the package [Fairness AI 360](https://aif360.res.ibm.com/) to ensure that our model predictions performed equally well
across protected classes (race and ethnicity).

# Data Access
The data used to train these models was accessed from the [_All of Us_ Research Hub](https://www.researchallofus.org/). You must [register for the Researcher Workbench](https://www.researchallofus.org/register/) to access the data. We specifically used individual-level data from the [Controlled Access Tier](https://www.researchallofus.org/data-tools/data-access/), which requires the completion of additional training. To facilitate testing without access to this protected health data, we have also provided a synthetic data frame.

# Interacting with this Code

- Data Cleaning
- Exploratory Data Analysis
- Applying the Models
