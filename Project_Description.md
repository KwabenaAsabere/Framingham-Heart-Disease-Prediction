### **Framingham Heart Disease Prediction**

A machine learning project using the Framingham Heart Study dataset to predict the 10-year risk of coronary heart disease (CHD). The project focuses on preprocessing, handling class imbalance with SMOTE, model training, evaluation, and interpretation of model performance and feature importance.

**Dataset Overview**

The dataset includes 4,240 records with 16 features.  

`Target`: TenYearCHD – whether the individual developed CHD in 10 years.  

`Features` include demographics, behavioral factors, and clinical measurements, such as:  

age, BMI, glucose, sysBP, diaBP  

male, currentSmoker, BPMeds, prevalentHyp, diabetes, etc.  

Some features have missing values, which are handled during preprocessing.  
quarto render Project_Description.md


**Preprocessing**

Missing values are imputed using `SimpleImputer`  

Numeric features: mean  
Categorical features: most frequent  

Numeric features are scaled using `StandardScaler`.  

Categorical features are encoded using `OneHotEncoder`  

All transformations are combined using `ColumnTransformer`  

Class imbalance is addressed using `SMOTE` (Synthetic Minority Oversampling Technique)  

**Model Building**

Models are trained using a pipeline structure and optimized with `GridSearchCV`:
*Logistic Regression*
*Random Forest*
*XGBoost*

Each model pipeline includes:      
- *Preprocessing (ColumnTransformer)*   
- *SMOTE oversampling*    
- *Classification model*    
- *Hyperparameter Tuning*    

Performed with 5-fold cross-validation

Optimized using ROC AUC as the scoring metric

**Evaluation Metrics**  
Each model is evaluated using:  
- Accuracy    
- Precision, Recall, F1-score    
-  ROC AUC    
-  Confusion Matrix    
-  Precision-Recall Curve      

**Best Model**
Logistic Regression (with C=0.01) yielded the best ROC AUC with a good balance between recall and precision for the minority class.
ROC AUC: 0.697  
Precision (positive class): 0.25  
Recall (positive class): 0.60  

Confusion Matrix:
[[490 229]
[ 51 78]]

**Visualizations**

* Histograms of continuous variables  

* Bar charts of categorical value counts  

* ROC and Precision-Recall curves  

* Feature importance plots (Logistic Regression coefficients)  

**Key Takeaways**

* Strong class imbalance required use of SMOTE for meaningful model training  

* Logistic Regression performed well when regularized and paired with proper preprocessing  

* Random Forest and XGBoost models had high accuracy but low recall for the minority class  