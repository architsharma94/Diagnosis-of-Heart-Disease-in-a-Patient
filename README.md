# Diagnosis-of-Heart-Disease-in-a-Patient
In medical science and healthcare service industry, predicting the health and a person's vulnerability to diseases can make the difference for the life of death for the person. Especially for high risk diseases such as a heart disease which may be fatal, foreseeing a patient's vulnerability to it, is quite vital. Predicting the presence of heart disease in an individual prompts the doctors to provide appropriate healthcare services and gives them an opportunity to adapt their treatment based on the prediction, thereby saving patient's lives. This project focuses on predicting such condition. We use the subset database, Cleveland database, consisting of 14 out the 76 features from the original database. Most of the published experiments done by researchers, make use of the specified subset of 14 features.

## Objective
This project aims to predict the presence of a cardiovascular(heart) disease in a patient within acceptable margin of error using different binary classifiers

## Source of Data
The data taken from the repository of Kaggle at https://www.kaggle.com/ronitf/heart-disease-uci . The dataset includes 13 descriptive features and 1 target feature and a total of 303 observations. The descriptive features have 5 numerical and 9 categorical features.

## Data Description
The description and data types of each descriptive feature is mentioned below

* Age: continuous
* Sex: 0 : Female, 1 : Male
* cp: Type of Chest Pains; 0 : Asymptomatic, 1 : Atypical Angina, 2 : Non-Anginal, 3:Typical Angina
* trestbps: numeric, Resting Blood pressure (in mm Hg on admission to the hospital)
* chol: numeric, serum cholesterol in mg/dl
* fbs: fasting blood sugar; 0 : Less than equal to 120 mg/dl, 1 : Greater than 120 mg/dl
* restecg:resting electrocardiographic results;
0 : Normal, 1 : having ST-T wave abnormality (T wave inversions and/or ST elevation or depression of > 0.05 mV), 2 : showing probable or definite left ventricular hypertrophy by Estes' criteria
* thalach: numeric, maximum heart rate achieved
* exang: Exercise induced angina; 0: No, 1: Yes
* oldpeak: numeric, ST depression induced by exercise relative to rest
* slope: the slope of the peak exercise ST segment; 0: downsloping, 1: flat , 2 : upsloping
* ca: number of major vessels (0-3) colored by flourosopy; 0:'0',1:'1',2:'2',3:'3', 4:'4'
* thal: 0 : missing , 1 : fixed defect , 2 : normal , 3 : reversible defect

### Target Feature
The target field refers to the target feature which identifies whether the patient has a heart disease or not. The target feature is binary with value 0 marking absence of the disease and with 1 indicating its presence. Therefore, this objective is a classification problem.

## Methodology
For predicting the binary target feature, we consider the following classifiers K-Nearest Neighbors (KNN), Decision trees (DT), and Naive Bayes (NB) Random Forest Support Vector Machine

Before modeling, we understand more about the dataset by visualizing the data. The numerical features are converted to the categorical with the respective levels they represent. Also, the outliers are removed from the dataset as omitting outliers still leaves us with 284 values which are currently sufficient to perform Machine learning. After exploring the dataset, the dataset is transformed and the categorical features are encoded to numerical using 'one-hot encoding' for nominal and 'integer' encoding. Since our dataset is quite small, we use the complete dataset with 284 observations and split this into training and test data sets in 70:30 ratio.

198 observation rows are considered as training data to help tune the hyperparameters while modeling
Remaining 86 rows of data is considered as test data used to evaluating the performance of the models and parameters
After label encoding we have 25 features, so we select the best features using the Random Forest Importance method. We consider 5, 10 and complete set of features. This is done as part of pipeline. The pipeline also has search for the best parameters for the respective classifiers.Classification Accuracy: which measures how often the classifier/model makes the correct prediction is used as the first scoring metric to make comparison amongst the classifiers, the final performance is measured using the 'Recall' metric. This is because predicting a 'false Positive' i.e. having a heart disease is less costlier than the model not catching a heart disease positively at all which maybe fatal to the patient.For fine-tuning the parameters cross validation is done with 5 fold with 3 repetitions. With the help of plots hyperparameters are fine tuned and identified using the grid search method on the training data. Then we fit the classifiers with the best parameters on the test data using 5-fold cross-validation. This is done in pairs to perform t-test and help evaluate if difference in performance of different models are statistically significant. Comparing the recall values we decide the most suitable classifier for the prediction.
