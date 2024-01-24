# Loan-Default-Prediction
Solution to MachineHack Deloitte Machine Learning Challenge


## Problem Statement
Banks run into losses when a customer doesn't pay their loans on time. Because of this, every year, banks have losses in crores, and this also impacts the country's economic growth to a large extent. In this hackathon, we look at various attributes such as funded amount, location, loan, balance, etc., to predict if a person will be a loan defaulter or not. 

The challenge is to predict the Loan Status.


## Data Dictionary
Variable | Definition
--- | ---
ID | unique ID of representative
Loan Amount | loan amount applied
Funded Amount | loan amount funded
Funded Amount Investor | loan amount approved by the investors
Term | term of loan (in months)
Batch Enrolled | batch numbers to representatives
Interest Rate | interest rate (%) on loan
Grade | grade by the bank
Sub Grade | sub-grade by the bank
Employment Duration | duration
Home Ownership | Owner ship of home
Verification Status | Income verification by the bank
Payment Plan | if any payment plan has started against loan
Loan Title | loan title provided
Debit to Income | ratio of representative's total monthly debt repayment divided by self reported monthly income excluding mortgage
Delinquency - two years | number of 30+ days delinquency in past 2 years
Inquires - six months | total number of inquiries in last 6 months
Open Account | number of open credit line in representative's credit line
Public Record | number of derogatory public records
Revolving Balance | total credit revolving balance
Revolving Utilities | amount of credit a representative is using relative to revolving_balance
Total Accounts | total number of credit lines available in representatives credit line
Initial List Status | unique listing status of the loan - W(Waiting), F(Forwarded)
Total Received Interest | total interest received till date
Total Received Late Fee | total late fee received till date
Recoveries | post charge off gross recovery
Collection Recovery Fee | post charge off collection fee
Collection 12 months Medical | total collections in last 12 months excluding medical collections
Application Type | indicates when the representative is an individual or joint
Last week Pay | indicates how long (in weeks) a representative has paid EMI after batch enrolled
Accounts Delinquent | number of accounts on which the representative is delinquent
Total Collection Amount | total collection amount ever owed
Total Current Balance | total current balance from all accounts
Total Revolving Credit Limit | total revolving credit limit
Loan Status | 1 = Defaulter, 0 = Non Defaulters

- Train.csv - 67463 rows x 35 columns (Includes target column as Loan Status)
- Test.csv - 28913 rows x 34 columns(Includes target column as Loan Status)


## Data Pre-processing
- Variables that are usually generated once the loan is approved are removed. 
- Incorrect values of Loan Amount and Funded Amount Investor are rectified.
- As the values of columns Employment Duration and Home Ownership are interchanged, these columns are renamed to their correct names. 
- Inconsistent labels of Verification Status and Loan Title are grouped using a dictionary. 
- Categorical attributes are encoded using LabelEncoder as we will using Random Forest for building the model. 
- StandardScaler is used to scale the numerical variables.

### Feature Generation
Used accounts - number of used credit lines, is generated from Total Accounts and Open Account.


## Evaluation Metric
The competition evaluation metric used is Log-loss. 

## Approach
- As this is a classification problem that involves prediction of whether a loan applicant will default or not, Logistic Regression and Random Forest models are built. 
- Stratified K-fold cross validation with 5 folds and shuffle is utilised for model evaluation. It ensures that both classes of target variable Loan Status are equally distributed during evaluating model performance. 
- Although, Logistic Regression and Random Forest with tuned hyperparameters achieve identical log loss scores~0.308 during cross validation, Random Forest is chosen as the final model. 


## Leaderboard
- [Public Leaderboard](https://machinehack.com/hackathons/deloitte_presents_machine_learning_challenge_predict_loan_defaulters/leaderboard): 40th Rank
- [Private Leaderboard](https://machinehack.com/hackathons/deloitte_presents_machine_learning_challenge_predict_loan_defaulters/leaderboard): 38th Rank
