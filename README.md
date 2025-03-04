# Customer-Churn-ML-Model
Final TripleTen Project. Project Summary: Created a comprehensive solution to predict customer churn for a telecom operator by training and tuning multiple machine learning models using GridSearchCV. Technical Skills: Advanced machine learning, classification modeling, customer churn prediction, hyperparameter tuning, and model selection.

## Project Description
The telecom operator Interconnect would like to be able to forecast their churn of clients. If it's discovered that a user is planning to leave, they will be offered promotional codes and special plan options. Interconnect's marketing team has collected some of their clientele's personal data, including information about their plans and contracts.

Interconnect's services Interconnect mainly provides two types of services:

Landline communication. The telephone can be connected to several lines simultaneously.
Internet. The network can be set up via a telephone line (DSL, digital subscriber line) or through a fiber optic cable.
Some other services the company provides include:

Internet security: antivirus software (DeviceProtection) and a malicious website blocker (OnlineSecurity)
dedicated technical support line (TechSupport)
Cloud file storage and data backup (OnlineBackup)
TV streaming (StreamingTV) and a movie directory (StreamingMovies)
The clients can choose either a monthly payment or sign a 1- or 2-year contract. They can use various payment methods and receive an electronic invoice after a transaction.
Data Description The data consists of files obtained from different sources:

contract.csv — contract information personal.csv — the client's personal data internet.csv — information about Internet services phone.csv — information about telephone services In each file, the column customerID contains a unique code assigned to each client.

The contract information is valid as of February 1, 2020.

Clarification: Summary Target feature: the 'EndDate' column equals 'No'.

Primary metric: AUC-ROC.

Additional metric: Accuracy.

Assessment criteria:

AUC-ROC < 0.75 — 0 SP
0.75 ≤ AUC-ROC < 0.81 — 4 SP
0.81 ≤ AUC-ROC < 0.85 — 4.5 SP
0.85 ≤ AUC-ROC < 0.87 — 5 SP
0.87 ≤ AUC-ROC < 0.88 — 5.5 SP
AUC-ROC ≥ 0.88 — 6 SP

## Work Plan

**STEPS**

1. Import libraries and download the data.

2. Perform EDA 
- Pre-Processing
    - Merge all data into one DataFrame
    - Change column names to snake_case
    - Convert BeginDate column to datetime
    - Change datatype in TotalCharges column to "float64'
    - Drop cutsomer_ID column as it will not be needed for the model
    - Treat missing values 
    - Replace end_date column with customer_churn for target
    - Check for class imbalance
- Conduct Data Visualizations to dig deeper into Data
    - Explore correlation between total and monthly charges
    - Explore churn with age and gender correlation
    - Explore churn with senior citizens 

3. Feature Engineering
    - OHE coding
    - Check seasonality for BeginDate column
    - Upsample for class imbalance   

4. Model Training
    - Create a dummy benchmark to test various classification models
    - Utilize ROC-AUC accuracy scores for evaluation metrics
    - Add gradient boosting techniques
    - Fine tune with cross-validation
    - Evaluate final model on test set
    
5. Conclusion

## Conclusion

1. After pre-processing and exploring the data through visualizations, we can claim the following insights:

- If you were a senior citizen who was a Interconnect client, it was very likely that you would drop out of your subscription.
- Higher total charges did not correlate with high customer churn.
- Most of the features had mostly balanced classes.
- Monthly charges decreased significantly in 2020. Most likely to help with all the customer churn in 2018 and 2019.
- Due to very little chnages in the monthly charges, we can assume the contract locked in customers at a fixed rate.

2. Feature Engineering
- OHE coding
- Checked seasonality for BeginDate column
- Upsampled for class imbalance
- I added three new features (year, month, and day of the week) to replace begin_date to check for seasonality and I also think this helped the model with accuracy since it highlighted meaningful data points in the dataset. I also encoded categorical features and lastly, scaled the data to help prepare for model training.

3. Model Training
- Created a dummy benchmark to test various classification models
- Utilized ROC-AUC accuracy scores for evaluation metrics
- Added gradient boosting techniques
- Fine tuned with cross-validation
- Evaluated final model on test set

  4. After evaluating multiple models, I found that XGBoost was the best model through the AUC-SCORE and Accuracy. I achieved and AUC - ROC Score of 0.9188 and Accuracy Score for the Training Set at 0.8877. I was pleased with these results so I left it at that.
