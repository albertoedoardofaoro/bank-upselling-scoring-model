# Scoring Model for a Bank's Up-Selling Campaign
 
Group project for a data-driven marketing course. We built a **logistic regression scoring model in R** to support a bank's up-selling campaign, identifying the customers most likely to accept a commercial offer and finding the number of customers to contact that maximises the campaign's profit.
 
## Dataset
 
An anonymized customer-level dataset with **19,120 customers and 35 variables**:
 
- **Target:** `FLG_TARGET`, a binary variable indicating whether the customer accepted the up-selling offer.
- **Predictors:** key performance indicators (KPIs) describing:
  - financial capacity (e.g. assets, inflows, movements),
  - activity and engagement with the bank (e.g. number of logins, transactions),
  - behavioural measures of account usage.
## Objective
 
1. Model the probability that a customer accepts the offer.
2. Rank customers by this probability.
3. Use the ranking to decide which customers the campaign should target.
## Approach
 
### 1. Preliminary analysis
- Checked the dataset structure (rows, columns) and the average acceptance rate.
- Inspected the univariate distributions of selected numerical KPIs to understand the scale and variability of the main predictors.
### 2. Data audit
- Identified variables with zero variance and with a high proportion of missing values.
- Identified sets of highly correlated predictors and removed redundant ones to avoid instability in the model.
### 3. Model estimation
- Split the data into a training set (70%) and a test set (30%).
- Fitted a logistic regression on the training set to predict `FLG_TARGET`.
- Evaluated performance with ROC curves and AUC on both sets to check generalisation.
### 4. Variable selection
- Applied stepwise selection based on AIC, starting from the full model, to remove predictors that did not contribute while balancing fit and complexity.
### 5. Scoring and ranking
- Computed a score for each customer: the estimated probability of acceptance.
- Ranked customers and grouped them into 20 equal-sized groups (ventiles) by score.
### 6. Lift and gain analysis
- Evaluated the ranking with cumulative lift and gain charts, which compare the share of positive responses in the top-scoring groups with what random targeting would achieve.
### 7. Campaign simulation
- Defined a marketing scenario with assumptions on the number of customers, value per customer, response rate, and fixed and variable contact costs.
- Combined the score distribution and lift values to compute cumulative revenues, costs and profits across ventiles, and identified the number of customers to contact that maximises net profit.
## Repository contents
 
- The data used for the analysis.
- The R scripts for model estimation and scoring.
- A presentation describing the full workflow.
## Tech stack
 
R
