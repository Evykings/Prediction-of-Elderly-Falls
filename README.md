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

## 🧹 Data Cleaning
I made the following changes and created the following variables:

*	Renamed the Decision column. Whitespace was found in the Decision column, making it difficlt to call out entries from the column. 
*	Apply normalization on the numerical columns to bring the values into a comparable range, especially if distance has high variability.
*	Created new features by combining features like HRV * SpO2, distance/pressure, and accelerometer * pressure to capture relationships between variables.
*   Edited the Decision column to (0- no fall detected, 1- person slipped/tripped/prediction of fall and 2- definite fall) 

## 📊 EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables. 

![alt text](https://github.com/Evykings/Prediction-of-Elderly-Falls/blob/main/images/Distribution%20of%20HRV.png)
![alt text](https://github.com/Evykings/Prediction-of-Elderly-Falls/blob/main/images/Distribution%20of%20SpO2.png)
![alt text](https://github.com/Evykings/Prediction-of-Elderly-Falls/blob/main/images/Distribution%20of%20Sugar%20Level.png)
![alt text](https://github.com/Evykings/Prediction-of-Elderly-Falls/blob/main/images/correlation%20Heatmap.png)


## ⚙️ Model Building 

The predictive modeling phase of this project focused on using Stochastic Gradient Descent Classifier (SGDClassifier), a fast and efficient linear classifier for large-scale datasets. Below are the key steps involved in training and optimizing the model:

**1.**  **Baseline Model**
The initial model was trained with default parameters to establish a baseline performance.
Basic metrics like accuracy, precision, recall, and F1-score were used to evaluate the baseline.

**2.**  **Hyperparameter Tuning**
**Objective:** Optimize the performance of the SGDClassifier by tuning key hyperparameters such as:
  *  Learning rate  ```(eta0)``` 
  *  Regularization parameter  ```(alpha)``` 
  *  Loss function  ```(hinge)```
  *  Number of iterations  ```(max_iter)```

**Approach:**
Leveraged Grid Search Cross-Validation (GridSearchCV) to perform an exhaustive search over hyperparameter combinations.
Used a stratified k-fold cross-validation approach to ensure robust performance evaluation and prevent overfitting.

## 💡Model performance
The model was evaluated using the following metrics to assess its effectiveness in predicting falls:

* **Accuracy:** Percentage of correctly classified instances.
* **Precision:** Ability to minimize false positives (important for fall prediction).
* **Recall (Sensitivity):** Ability to correctly identify actual falls.
* **F1-Score:** Balance between precision and recall.

The result from the models classification is shown below:
![alt text](https://github.com/Evykings/Prediction-of-Elderly-Falls/blob/main/images/fall.png)

The confusion matrix for the classification is show below:
![alt text](https://github.com/Evykings/Prediction-of-Elderly-Falls/blob/main/images/fall.png)




## Productionization 
In this step, I built a flask API endpoint that was hosted on a local webserver by following along with the TDS tutorial in the reference section above. The API endpoint takes in a request with a list of values from a job listing and returns an estimated salary. 


