# Prediction-Modeling-Loan-Risk
Final Task: Project Based Internship ID/X Partners x Rakamin Academy

## Business Understanding
**Current problem**
The client, a lending company (multifinance), faces significant challenges in accurately assessing and managing credit risk, leading to:
  1. Financial Losses Due to Defaults: The existing credit evaluation process may result in approving loans to high-risk borrowers.

  2. Limited Growth Opportunities: Potentially creditworthy applicants might be rejected, restricting business growth.

  3. Inefficiency in Credit Assessment: Current manual or heuristic-based approaches are inadequate to handle the complexity and volume of credit applications. 

**Impact**
  1. High default rates result in substantial financial losses.
  2. Suboptimal credit approval decisions negatively affect business performance.

**Needs**

1. Improve the accuracy of credit risk assessment.
2. Minimize default rates.
3. Optimize loan approval decisions.
4. Enhance overall profitability.


## Data Understanding
1. The dataset provided consists of 466,285 entries and 75 columns
2. The dataset consists of 53 numerical columns and 22 categorical columns
3. There are 40 columns with missing (null) data in the dataset
4. No duplicate data
Issue column:
1. Imbalanced Columns: pymnt_plan is identified as imbalanced with one category having a very high count compared to the other.
2. High Cardinality Columns: Columns with a large number of unique values. emp_title, url, desc, title, zip_code
3. Low Cardinality Columns: Columns with a with relatively few unique values. term, pymnt_plan, initial_list_status, application_type
4. Unnecessary columns: The column that will not be included in the model. Unnamed, id, member_id, collections_12_mths_ex_med

## Exploratory Data Analysis

![image](https://github.com/user-attachments/assets/1b108a69-ed72-4e7b-9306-0a310090fcb3)


**Loan Classification**
- Good Loans: 88.13%
  - Loans are current, fully paid, or in a grace period.
  - Indicates strong performance and minimal risk.
- Bad Loans: 11.87%
  - Includes loans that are charged off or defaulted.
  - Represents a significant financial risk.

**Financial Overview**
- Total Profit: Approx. 5.87 billion
  - nDemonstrates significant revenue generation from the loan portfolio.
- Total Loss: Approx. 790.79 million
  - Primarily attributed to bad loans.
  - Highlights the financial risk and impact of bad loans.
 

### Analysis

**Analysis Loan by Year**

![image](https://github.com/user-attachments/assets/344927fb-cff2-42f7-a737-043200c08742)

1. Funded Amount by Loan Status (in Years):
    - The volume of loans issued has risen consistently each year.
    - Notably, Bad Loans outnumber Good Loans overall.
    - A brief dip in Bad Loans occurred around 2009, followed by a sharp rise from 2010 onwards.
    - By 2013, the gap between Good and Bad Loans narrowed, with both metrics leveling off in subsequent years.
    - This trend highlights a growing loan issuance over time.
    
    

2. DTI by Loan Status (in Years):
    - Debt-to-Income (DTI) ratios have shown a steady upward trend over time.
    - Both Good and Bad Loans experienced a dip in DTI in 2008, but increased again in subsequent years.
    - Notably, DTI patterns for Good and Bad Loans mirror each other in their rises and falls.



3. Annual Income by Loan Status (in Years):
    - Initially, Good Loans had lower annual incomes compared to Bad Loans, but this shifted as Good Loans' income grew steadily over time.
    - Conversely, Bad Loans saw a significant drop in annual income but began to recover slightly from 2011.
    - By mid-2008, the annual income for both Good and Bad Loans was similar.



4. Revolving Balance by Loan Status (in Years):
    - A sharp decline in revolving balance occurred in 2008, correlating with decreases in both annual income and DTI.
    - This trend suggests borrowers may have been working to lower their financial burdens or reduce their reliance on revolving credit.
  
**Analysis Loan by Region**

![image](https://github.com/user-attachments/assets/c71d71cf-7037-4a43-8689-08262376be4a)


- Overall Stability: Across all regions, a high percentage of loans are classified as Good Loans, with rates consistently around 87% to 89%. This suggests a relatively stable performance of loans across the country.

- Regional Variation: The Southwest region has the highest proportion of Good Loans at 88.93%, indicating potentially stronger credit quality or more favorable lending conditions compared to other regions. Conversely, the Southeast region has the lowest percentage of Good Loans at 87.69%, which might suggest a slightly higher risk profile.

- Minimal Variation: The differences in Good and Bad Loan percentages between regions are relatively minor, ranging from 87.69% to 88.93% for Good Loans and from 11.07% to 12.31% for Bad Loans. This indicates that while regional performance varies slightly, the overall credit quality remains comparable.

- Consistent Performance: The small variations in loan status percentages among regions highlight a broadly uniform lending and repayment behavior across the country, with no single region showing significantly higher or lower risk profiles.

These insights suggest that while regional differences exist, they are not dramatic, and the loan portfolio exhibits a stable credit performance across different regions.

**Analysis by State**


![image](https://github.com/user-attachments/assets/71d31806-da91-424b-aa82-d058d8dc0a61)

- Highest Credit Quality: Illinois (IL) exhibits the highest proportion of Good Loans at 89.79%, indicating the best overall credit quality among the states listed. This suggests a relatively lower risk of defaults in IL compared to other states.

- Strong Performance in TX: Texas (TX) also shows a strong performance with 89.50% of loans classified as Good Loans. This highlights a favorable credit profile in TX, similar to IL.

- Moderate Performance: California (CA) and New York (NY) have Good Loan rates of 87.83% and 87.15%, respectively. While these states still have a high percentage of Good Loans, they show slightly lower performance compared to TX and IL.

- Lowest Credit Quality: Florida (FL) has the lowest proportion of Good Loans at 86.55%. This suggests a higher rate of defaults or riskier lending conditions compared to the other states.

- Variation in Risk: The variation in Good Loan percentages across states (from 86.55% in FL to 89.79% in IL) reflects differing levels of credit risk and lending performance. While the overall credit quality remains high, states like FL might require closer scrutiny or different risk management strategies.

These insights indicate that while the overall loan quality is good across all states, there are notable differences, with IL and TX standing out as having the strongest credit performance.


**Analysis of Loan Purpose**

![image](https://github.com/user-attachments/assets/dcd3f467-f375-420f-9460-73e4fa932e20)

- Best Performance for Credit Card: Loans taken for credit card purposes have the highest proportion of Good Loans at 90.57%. This indicates a lower default rate and suggests that borrowers using loans for credit card purposes are generally more creditworthy.

- Strong Performance for Major Purchases: Major purchase loans also show a high rate of Good Loans at 89.56%, reflecting strong credit quality and suggesting that borrowers making significant purchases are likely to manage their loans effectively.

- Solid Performance for Home Improvement: Home improvement loans have a Good Loan rate of 89.20%. This is still high but slightly lower compared to credit card and major purchase loans, indicating a good but marginally higher default risk.

- Weaker Performance for Debt Consolidation: Loans for debt consolidation show a Good Loan rate of 87.67%. While this is still a favorable rate, it is lower compared to the other categories, suggesting a relatively higher risk of default among these borrowers.

- Lowest Performance for Other Purposes: Loans categorized under "other" have the lowest proportion of Good Loans at 85.31%. This indicates the highest default rate and suggests that borrowers with loans for miscellaneous purposes might be at a higher risk.

Overall, credit card and major purchase loans demonstrate the strongest credit performance, while loans categorized as "other" exhibit the highest risk of default.

**Analysis of Loan Grade**

![image](https://github.com/user-attachments/assets/372d511f-e3e9-4be2-9f56-64fa57e86801)

- The majority of clients are graded B and C, with default rates increasing as the grade decreases.
- Grade G clients have the highest number of loans, while Grade A clients, despite having the lowest default rates, have fewer loans.
- Historically, Grade G clients led in annual income, but since 2013, Grade A clients have surpassed them.
- This suggests that clients with higher annual incomes tend to take out larger loans, although this trend also correlates with a higher default rate.

## Data Preparation

![image](https://github.com/user-attachments/assets/e9ba99d2-c102-4a29-b7c7-4669dfaeb30e)

## Data Modeling

![image](https://github.com/user-attachments/assets/83f8aa38-7900-4fbf-9298-72b11eaf6809)

**Best Model:**
**XGBClassifier** shows the highest performance across most key metrics, including:
- Highest Accuracy (97.65%)
- Highest AUC (Test) (98.24%)
- Highest Precision (96.21%)
- Highest F1 Score (89.29%)
- Second-highest Cross-Validation AUC (98.22%)

XGBClassifier stands out as the best-performing model based on the provided metrics, offering superior accuracy, AUC, precision, and F1 score compared to the other models. This makes it the preferred choice for this prediction task.

**Important Features**

![image](https://github.com/user-attachments/assets/65e4460e-14b5-4144-8153-7b7576680973)

1. **term_60months** is the most important feature, suggesting that the loan term length significantly influences the model's predictions. Longer-term loans (60 months) are crucial for the model’s decision-making process.

2. **last_pymnt_amnt** ranks second, indicating that the amount of the last payment made is a strong predictor of the loan's outcome. Larger payment amounts may be associated with better loan performance.

3. **days_since_last_pymnt_d** holds the third spot, highlighting the importance of the time elapsed since the last payment. This feature likely reflects payment patterns and loan behavior over time.

4. **inq_last_6mths** (number of inquiries in the last 6 months) follows, showing that recent credit inquiries are relevant for predicting loan status, possibly reflecting the borrower's recent financial activity.

5. **grade_A** is significant, indicating that the grade of the loan plays a role in its outcome. Higher-grade loans (Grade A) tend to have a substantial impact on predictions.

6. **initial_list_status_w** (whether the loan was listed with a specific status initially) is also noteworthy, suggesting that the initial listing status affects the loan's outcome.

7. **last_pymnt_d_month** (month of the last payment) and **days_since_issue_d** (days since the loan was issued) are moderately important, reflecting the timing of payments and loan issuance.

8. **term_36months** (loan term of 36 months) is less significant compared to term_60months, indicating that while the term length matters, a 36-month term is less influential.

9. **issue_d_month** (month the loan was issued) has the lowest importance among the top features, suggesting that while it provides some context, it is less critical for the model compared to other features.


## Evaluation

**Confusion Matrix**

![image](https://github.com/user-attachments/assets/6389e336-4ab0-41c5-9860-0c9eccdeabcd)

1. High Positive Prediction Accuracy: The model excels at identifying 'Good Loans,' with an impressive 87.48% accuracy. This reflects the model's strong performance in correctly classifying truly good loans.

2. Low False Positive Rate: Only 0.66% of 'Bad Loans' are incorrectly classified as 'Good Loans.' This indicates the model effectively avoids significant errors in identifying bad loans.

3. Moderate False Negative Rate: There is a 1.69% rate of 'Good Loans' being missed. While this rate is low, there is still potential to enhance the accuracy of detecting good loans.

4. Low True Negative Rate: The model identifies only 10.16% of 'Bad Loans' correctly. This shows a need for improvement in recognizing bad loans accurately. Adjustments or alternative methods may be required to boost the model’s effectiveness in detecting bad loans.


![image](https://github.com/user-attachments/assets/99b85896-aa18-4281-970d-b61154a161b3)


1. Significant Reduction in Bad Loans: There was a substantial reduction of 44,352 in bad loans, leading to a drastic drop in the default rate from 11.9% to 2.4%. This indicates a major improvement in loan quality and risk management.

2. Increased Revenue: Total revenue increased by approximately $633 million. This suggests enhanced operational performance or increased business volume.

3. Reduction in Default Losses: The total amount lost due to defaults decreased by over $633 million, highlighting improved risk mitigation and recovery strategies.

4. Net Revenue Boost: The net revenue saw a significant increase of $1.27 billion, reflecting both improved loan performance and effective financial management.

5. Overall, the reduction in bad loans and default losses, coupled with increased total and net revenue, indicates a highly successful improvement in financial stability and profitability.

## Conclusion

- Ideal Model: XGBClassifier
- Outstanding Model Performance:
    - High Accuracy: XGBClassifier excels at identifying good loans with impressive accuracy.
    - Significant Reduction in Bad Loans: Bad loans decreased drastically from 55,332 to 10,980.
    - Decrease in Default Rate: Default rate fell from 11.9% to 2.4%.
- Financial Improvement:
    - Increased Total Revenue: Total revenue rose by approximately $633 million.
    - Reduction in Default Losses: Default losses decreased by over $633 million.
    - Net Revenue Boost: Net revenue increased by $1.27 billion.
- Risk Management and Profitability:
    - Effective Risk Mitigation: The model significantly reduces credit and default risk.
    - Enhanced Profitability: Implementation of this model boosts the company's profitability potential.







