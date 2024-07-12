# CNBE Election Analysis Project

## Overview

This project is developed for CNBE, a leading news channel, to analyze recent election data. The aim is to build a predictive model to determine which party a voter is likely to vote for based on survey data from 1525 voters. The project includes data ingestion, preparation, model building, tuning, and evaluation to create an exit poll prediction system.

## Data Ingestion

### Descriptive Statistics
- Dataset contains 1525 rows and 10 columns.
- Data types include integers (`int64`) and objects.
- The dataset contains 8 duplicate rows.
- No null values in the dataset.
- Two columns contain outliers.

  ![image](https://github.com/user-attachments/assets/9c5ef10f-4642-4a4b-ba12-b255824a02bf)

  ![image](https://github.com/user-attachments/assets/f6b10d94-74e1-4282-9f7b-6ad72b8796c8)
 
- The column `Unnamed: 0` is dropped due to insignificance.
- Skewness:
  - Positively skewed: `age`, `Hague`
  - Negatively skewed: Remaining columns
- Correlation:

  ![image](https://github.com/user-attachments/assets/5b9a75b0-a5a1-4b81-8c43-626bc76c6ffa)

  - No high positive or high negative correlations among columns.
  - Generated IQR, Standard deviation, and Variance.

### Null Value Condition Check
- No null values in the dataset.

### Exploratory Data Analysis
- Univariate Analysis:
  - Frequency Polygon

    ![image](https://github.com/user-attachments/assets/ffff33d0-e889-46fb-814b-16368893bcce)

  - Violin Plot
 
    ![image](https://github.com/user-attachments/assets/4171b6ef-72c2-407e-bf81-d4a84b8017c1)

  - Cumulative Distribution
 
    ![image](https://github.com/user-attachments/assets/50e8eadf-4864-4845-b4c9-f96bc291558d)

- Multivariate Analysis:
  - Pair Plot

    ![image](https://github.com/user-attachments/assets/f91ff771-dfb8-4198-a606-8ac09c5d382f)

## Data Preparation

### Encoding and Scaling
- Encoded string values for modelling.
- Scaling performed using `StandardScaler` due to the need for distance calculations in certain algorithms.
 
### Data Split
- Data split into training (70%) and testing (30%) sets.

## Modelling

### Logistic Regression and LDA
- **Logistic Regression:**
  - Score: 0.8355
  - Accuracy: 0.84
- **Linear Discriminant Analysis (LDA):**
  - Score: 0.8399
  - Accuracy: 0.83
- Both models perform similarly.

### KNN and Naive Bayes
- **KNN Model:**
  - Score: 0.8157
- **Naive Bayes Model:**
  - Accuracy (Train): 0.8351
  - Accuracy (Test): 0.8224

### Model Tuning
- **GridSearchCV** used for tuning.

  Confusion Matrix for Decision Tree

  ![image](https://github.com/user-attachments/assets/f838f650-c50f-4daf-8901-9963bd343fae)

- **Bagging:**
  - Random Forest Score: 0.8245
 
    Confusion Matrix for Random Forest

    ![image](https://github.com/user-attachments/assets/7094731c-ac9e-48d0-ae52-51d70147efcf)

- **Boosting:**
  - Adaboost Score: 0.8201
  - Gradientboost Score: 0.8289

### Performance Metrics
- Metrics evaluated:
  - Precision
  - Recall
  - Accuracy
  - F1 Score
- ROC-AUC Curve Analysis:
  - Higher AUC indicates better model performance.
- Model tuning improves AUC scores and reduces overfitting.

AUC before Model Tuning:

   ![image](https://github.com/user-attachments/assets/4f7a83f1-133d-4ba3-86fd-d59fe7847161)

   ![image](https://github.com/user-attachments/assets/22bfb496-c618-42e2-86ba-c78f1e9b1cdd)

AUC after Model Tuning:

   ![image](https://github.com/user-attachments/assets/f12bd2e6-07eb-4ff5-9ded-af891ef908df)

   ![image](https://github.com/user-attachments/assets/97020597-4620-4594-b568-a2163bc2c4a5)

## Inference

Based on predictions:
- **Conservative voters tend to:**
  - Assess national economic condition as 4.
  - Assess household economic condition as 3.
  - Assess Tony Blair as 2.
  - Assess William Hague as 4.
  - Have high Eurosceptic sentiment.
  - Are often female.
- **Labour voters tend to:**
  - Assess national economic condition as 3.
  - Assess household economic condition as 4.
  - Assess Tony Blair as 4.
  - Assess William Hague as 2.
  - Have moderate Eurosceptic sentiment.
  - Gender distribution is nearly equal.

## Conclusion

The predictive models, especially after tuning, provide accurate insights into voter behavior, aiding in the prediction of election outcomes. The Gradient Boosting model, with its superior performance metrics, is identified as the best model for this task.
