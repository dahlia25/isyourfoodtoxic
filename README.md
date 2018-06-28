# isyourfoodtoxic
This is a Capstone Project for Springboard's Intermerdiate Data Science course. 
The **isyourfoodtoxic** repo will contain all code and work done for the project.

---

Below is a milestone on what will be covered in this project.

## Background
According to the Centers for Disease Control and Prevention (CDC), it is estimated that 1 in 6 Americans get sick from contaminated foods and beverages each year, and about 3000 die from it.

Foodborne illnesses are common, but costly. The U.S. Department of Agriculture (USDA) estimates that foodborne illnesses cost more than $15.6 billion each year.

A foodborne disease outbreak occurs when two or more people become ill from the same contaminated food or beverage. By understanding how foodborne disease spreads, we can take preventative actions and control the spread.

## About the Dataset
The dataset is obtained from the Centers for Disease Control and Prevention (CDC) and provided on Kaggle. 

[Click here for Outbreaks.csv](https://www.kaggle.com/cdc/foodborne-diseases)

## The Problem
Based on historical data, can we predict whether certain features caused hospitalizations?

## Abstract
This project analyzes a foodborne outbreaks dataset that is originally from the Centers for Disease Control and Prevention (CDC) that occurs between the years 1998 and 2015. Exploratory data analysis (EDA) was achieved by visualizations to provide quick understanding and insight on the dataset. Hypotheses were formulated based on findings from EDA. Chi-squared testing was performed on the hypotheses for independence. No inferential statistics were performed because it is ineffective on categorical data. 

The data was wrangled and standardized by:
1. Removing missing values
2. Unstacking multiple cell entries into rows 
3. Removing all leading and trailing white spaces; so all variables were consistent. 

Feature engineering was employed to transform the data into a usable structure for machine learning. The data was transformed into a One Hot Encoding (OHE) structure where the data only consists of binary vectors. After data transformation, the RandomForest Classifier and SVM SVC models were used to predict whether features caused hospitalization or not. To achieve the best accuracy and precision, GridSearchCV was used for model tuning and parameter optimization. The RandomForest Classifier and SVM SVC were selected based on their abilities to process high dimensional data structures, as OHE increases data dimensions.

## Who Should Care?
- Restaurant/ business/ food producers should care because foods that are more likely to harbor foodborne diseases and pathogens will decrease in demand and sales; this can also affect the methods involved in food production and handling. 

- The U.S. Government care because the federal government establishes food regulations to protect the health and safety of U.S. consumers. To protect U.S. consumers, the federal government also spends money on preventive and health measures against foodborne diseases. Estimates from the USDA and CDC (in year 2014) show that foodborne illnesses cost the U.S. economy $15.6 billion or more. This analysis could affect federal law regulations on food production/ handling. 

- Consumers (general public) care because they would like to stay healthy and avoid paying more hospital bills. This analysis could allow consumers to take preventive and cautious measures when purchasing food products to stay healthy and avoid medical costs.

