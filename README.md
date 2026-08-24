Logistic Regression
=========

We need the **sigmoid** function because the output of a normal linear expression is not a probability.

Suppose logistic regression first calculates:

z=β + 2β

That calculation can produce any number:
−10, −2, 0, 3, 25

But for your fraud classifier, you want:

Probability of fraud between 0 and 1.


Important Concerns for Logistic Regression
=========

1. Scaling
Logistic Regression can use continuous variables, but features with different ranges should be standardized:
 `StandardScaler()`
2. Skew and Outliers
amount and balance variables can be highly skewed. A log transformation may help:

`df["log_amount"] = np.log1p(df["amount"])`

Logistic Regression does not require normally distributed features. However, severe skew and extreme values can affect model training and coefficient interpretation.

3. Multicollinearity

Balance variables may be strongly related. 
For example:
`oldbalanceOrg - amount ≈ newbalanceOrig`

Highly correlated predictors can make Logistic Regression coefficients unstable. 

Regularization, feature selection, or balance-change features may help:

`df["orig_balance_change"] = (
    df["oldbalanceOrg"] - df["newbalanceOrig"]
)`

4. Linear Decision Boundary

Logistic Regression assumes that features have a roughly linear relationship with the log-odds of fraud.

Fraud may involve nonlinear interactions, such as:

`TRANSFER + high amount + unusual balance change`

Logistic Regression may not capture these patterns unless interaction features are explicitly engineered.


