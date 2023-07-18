# Credit-Risk-Model

#### Goal: To estimate Expected Loss (EL) for each loan, which represents the potential loss the lender might incur if the loan defaults. 

##### Data Import and Exploration:

Python libraries are imported, including NumPy and Pandas.
The loan data is read from a CSV file into a Pandas DataFrame.
Basic statistics and null value counts for 'loan_data_defaults' are displayed.

##### Data Preprocessing:

Some independent variables ('mths_since_last_delinq' and 'mths_since_last_record') are filled with zero for missing values.
Two dependent variables are created, 'recovery_rate' and 'CCF'.
The 'recovery_rate' is adjusted to ensure it stays within the range [0, 1].
'CCF' is calculated as a fraction of the unfunded principal amount.
The preprocessed data is saved to a new CSV file.

##### Exploratory Data Analysis:

Matplotlib and Seaborn libraries are imported for data visualization.
Histograms are plotted for 'recovery_rate' and 'CCF'.
A new binary variable 'recovery_rate_0_1' is created, which equals 1 if 'recovery_rate' is non-zero and 0 otherwise.

##### LGD Model (Loss Given Default):

Data is split into training and testing sets using train_test_split from scikit-learn.
The feature set is defined as 'features_all', and reference categories are specified in 'features_reference_cat'.
A Logistic Regression model class is created ('LogisticRegression_with_p_values'), which computes p-values for the coefficients.
The LGD Stage 1 model is trained on 'lgd_inputs_stage_1_train' and 'lgd_targets_stage_1_train', and p-values for the coefficients are calculated.

##### EAD Model (Exposure at Default):

Data is split into training and testing sets for the EAD model.
Linear Regression is used to estimate the EAD model coefficients.
The model's performance is evaluated on the test set.

##### Estimating Expected Loss (EL):

Predicted Probability of Default (PD) from the PD model is combined with LGD and EAD predictions to calculate EL for each loan.
EL is summed up to get the total Expected Loss for the entire dataset.
Finally, the Expected Loss as a percentage of the total funded amount is computed.
