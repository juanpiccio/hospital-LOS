# hospital-LOS
 ## <font color='red'>Read Me:</font>

In this project, I use decision tree models to predict the length of stay (in days) of patients entering an ICU (Intensive Care Unit).

The dataset comes from MIMIC project (https://mimic.physionet.org/), a database comprising deidentified health-related data associated with over 40,000 patients who stayed in critical care units of the Beth Israel Deaconess Medical Center between 2001 and 2012.

The following tasks are done throughout the notebook:

**1. Pre-processing**:
- Creating new features from the data, such as:
  - `age`: from Date of Birth and Date of Admission.
  - `weekday of admission`: from Date of Admission.
  - `re-admitted patient indicator`: by analyzing if there exist previous admissions for the same patient.
- Additional information from other CSVs is merged into the main dataframe, employing common keys.
- Imputing missing values with different strategies (mean, medians, modes). This is done in both the training and testing sets, avoiding information leak by fitting the imputer only with the former.
- Dummifying categorical features.
- Feature engineering and dimesionality reduction: analyzing how informative the features are and dropping those less important.
- No standarization is carried out, since decision tree models do not consider distances.

**2. Models:**

Two main predictions were made:

- Death predictions: we used the HOSPITAL_EXPIRE_FLAG data in our training set to predict if patients in our test set would die. <font color='green'>Classification problem</font>.

- LOS predictions: we used the previous predictions -and all the other pertinent features- to predict lengths of stay. <font color='green'>Regression problem</font>.

The following models were employed:

- Random Forest Classifier.
- Balanced Random Forest Classifier.
- Stacking:
  - Weak learners:
    - KNN.
    - LinearSVR.
    - Random Forest Regressor.
  - Meta learner: Extra Trees Regressor
- XGBoosting.
- Bagged XGBoosters.

In all cases, the hyperparameters were optimized.

As performance metric, *RMSE* (root mean squared error) was used.

The predictions were submitted to [this kaggle competition](https://www.kaggle.com/competitions/b-gse-dt-los/leaderboard), achieving the first place in the leaderboard.Predicting length of stay in hospital employing pandas and sklearn as main libraries. Lots of data wrangling and decision trees models

