##

##                                                 Loan Approval Cost Benefits Analysis Portfolio

## Project Overview

**This project treats machine learning predictions as financial decisions.**

Using a public loan approval dataset sourced from Kaggle, I built an end-to-end analytics workflow that connects predictive modeling with cost–benefit analysis, approval optimization, and portfolio strategy.

The dataset contains financial and demographic information for 1,000 loan applicants, including annual income, credit score, loan amount, number of dependents, and employment status. While commonly used for binary classification (loan approved vs. denied), this project extends beyond prediction accuracy to evaluate profitability, risk trade-offs, and decision-level business impact.

Predicted approval probabilities were translated into expected revenue, expected loss, and operating costs to determine which loans should be approved, under what conditions, and why.

## Data Source

- **Dataset:** Loan Approval Dataset

- **Source:** Kaggle (https://www.kaggle.com/datasets/amineipad/loan-approval-dataset

- **Description:** Synthetic dataset designed for educational use in credit risk assessment and loan approval modeling

- **Target variable:** loan_approved (1 = approved, 0 = denied)

## Key Business Questions

- Which loan applications should be approved to maximize portfolio profit?
- How do approval thresholds impact revenue, risk, and loan volume?
- Which customer segments consistently generate or destroy value?
- How sensitive is the portfolio to changes in interest rates or default probabilities?

## Approach

1. **Data Preprocessing & Feature Engineering**  
   - One-hot encoded categorical variables (gender, marital status, employment status).  
   - Created `loan_to_income_ratio` to measure debt burden.  
   - Categorized `credit_score` into credit tiers for business interpretability.

2. **Predictive Modeling**  
   - Trained a Random Forest classifier to predict loan approval probabilities.  
   - Split data 80/20 for training and testing.  
   - Converted probabilities into risk probabilities for downstream analysis.

3. **Business Metrics Calculation**  
   - Calculated interest revenue, expected loss, operating costs, and expected profit per loan.  
   - Aggregated to portfolio-level metrics (total profit, return on capital).

4. **Portfolio Optimization & Threshold Analysis**  
   - Tested approval thresholds to maximize portfolio profit.  
   - Identified optimal threshold (~0.85) balancing volume and profit.

5. **Customer Segmentation**  
   - Clustered customers using income, loan amount, credit score, and loan-to-income ratio.  
   - Compared profitability across segments to identify high- and low-value cohorts.

6. **Scenario & Stress Testing**  
   - Simulated changes in interest rates and risk probability to assess portfolio sensitivity.

## Key Results

- Baseline portfolio is unprofitable: total expected profit = -$3,014,792  
- Optimal approval threshold = 0.85 → portfolio profit ≈ $830,783  
- Profitable customer segment identified: high-income, low-risk applicants  
- Stress testing: +3% increase in risk → portfolio profit decreases by ~$531K  
- Loan-to-income ratio and credit score are the strongest drivers of approval probability

## Visual Insights

- **Profit vs Approval Probability:** Highlights the relationship between predicted risk and expected profit.  
- **Credit Score vs Risk Probability:** Shows how credit quality impacts approval risk.  
- **Customer Segment Profitability:** Boxplots reveal which segments generate value.  
- **Debt Burden Distribution:** Histograms illustrate loan-to-income ratio across applicants.

## Assumptions

- Fixed interest rate of 9% applied to all loans  
- Loss given default (LGD) is constant at 65%  
- Operating costs = $400 (processing) + $250 (acquisition) per loan  
- Synthetic dataset; prepayment, recovery, and macroeconomic effects ignored

## Limitations

- Very high AUC suggests simplified/synthetic data  
- Real-world performance would require out-of-sample validation  
- Ignores market/behavioral risks beyond credit score and income

## Recommended Approval Policy

- Approve loans with predicted approval probability ≥ 0.85  
- Reject or reprice high-risk segments (low-income, high debt, poor credit)  
- Monitor portfolio profit regularly and adjust interest rates if risk levels increase  
- Reassess thresholds if default rates or market conditions change

## Scenario Analysis

| Scenario | Portfolio Profit |
|----------|----------------|
| Baseline | -$3,014,792 |
| +3% Risk Shock | -$3,546,067 |
| +6% Risk Shock | -$4,077,342 |

| Interest Rate | Portfolio Profit |
|---------------|----------------|
| 7% | -$3,559,690 |
| 9% | -$3,014,792 |
| 11% | -$2,469,895 |
| 13% | -$1,924,998 |

## Key Takeaways

- Model accuracy alone does not drive business value; translating predictions into financial outcomes is critical.  
- Portfolio-level thinking and scenario analysis uncover hidden risks and opportunities.  
- Segmentation can reveal high-value vs low-value customer groups for strategic decision-making.




