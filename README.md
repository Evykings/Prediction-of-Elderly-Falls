# Fall Prediction 🧑🏼‍🦯📉 
Welcome to the **Fall Prediction** project! This repository showcases a data science project aimed at predicting falls using machine learning techniques, focusing on providing valuable insights for healthcare and safety applications.


# 📌 Project Overview
Falls can have serious consequences, especially for the elderly and individuals with certain health conditions. This project leverages data science to predict falls using sensor data. By accurately predicting falls, this model aims to aid in proactive interventions, improving safety and quality of life.


## 🛠️ Tools and Resources Used 
**Python Version:** 3.7  

**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, pipeline

**For Web Framework Requirements:**  ```pip install -r requirements.txt``` 

## 📊 Key Features

*   **Exploratory Data Analysis (EDA):** Understand patterns and relationships in the dataset.
*   **Feature Engineering:** Extract meaningful features for accurate predictions.
*   **Modeling:** Train and evaluate various machine learning models, including Random Forest, SVM, and Neural Networks.
*   **Evaluation Metrics:** Precision, Recall, F1-Score, and ROC-AUC to assess model performance.

## 📖 Dataset

*    **Source:** The dataset used for this project was gotten from readings recorded from a cStick. The cStick is a calm stick that monitors the grasping pressure that
is applied on the cane,monitors the blood sugar levels of the older adults, the blood oxygen level, and the heart rate variation. These vitals was recorded and collected from the wearable sensors 
*    **Description:** The dataset used for this project has the following columns- Distance, Pressure (0-small, 1- medium and 2- high pressures), Heart Rate Variation (HRV), Sugar Levels, Oxygen Saturation (SpO2) levels and Accelerometer reading (<+-3g, i.e., threshold is 0 and >Threshold is 1). In relationship to the decision of falls (0- no fall detected, 1- person slipped/tripped/prediction of fall and 2- definite fall).

## Data Cleaning
I made the following changes and created the following variables:

*	Renamed the Decision column. Whitespace was found in the Decision column, making it difficlt to call out entries from the column. 
*	Apply normalization on the numerical columns to bring the values into a comparable range, especially if distance has high variability.
*	Created new features by combining features like HRV * SpO2, distance/pressure, and accelerometer * pressure to capture relationships between variables.
*   Edited the Decision column to (0- no fall detected, 1- person slipped/tripped/prediction of fall and 2- definite fall) 

## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables. 

![]([https://github.com/PlayingNumbers/ds_salary_proj/blob/master/salary_by_job_title.PNG "Salary by Position"](https://github.com/Evykings/Prediction-of-Elderly-Falls/blob/a3456de054833849f92789e43775a999ddda958e/Distribution%20of%20HRV.png)
![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/positions_by_state.png "Job Opportunities by State")
![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/correlation_visual.png "Correlations")

## Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.   

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.   

I tried three different models:
*	**Multiple Linear Regression** – Baseline for the model
*	**Lasso Regression** – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
*	**Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit. 

## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets. 
*	**Random Forest** : MAE = 11.22
*	**Linear Regression**: MAE = 18.86
*	**Ridge Regression**: MAE = 19.67

## Productionization 
In this step, I built a flask API endpoint that was hosted on a local webserver by following along with the TDS tutorial in the reference section above. The API endpoint takes in a request with a list of values from a job listing and returns an estimated salary. 


