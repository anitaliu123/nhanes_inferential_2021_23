# NHANES 2021-2023 Inferential Analytics Assignment

## Objective
This project uses publicly available data from the **National Health and Nutrition Examination Survey (NHANES)** 2021–2023 cycle to perform basic inferential statistical analyses. The goal is to explore relationships among demographic, behavioral, and health variables using Python in Google Colab.  

- NHANES Data: [NHANES 2021-2023](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?Cycle=2021-2023)

## Data Preparation

- **Marital Status** (`DMDMARTZ`) - categorical, needs recoding (married or not married).
- **Education Level** (`DMDEDUC2`) - categorical, needs recoding (bachelor’s or higher vs. less than bachelor’s).
- **Age in Years** (`RIDAGEYR`) - continuous.
- **Systolic Blood Pressure** (`BPXOSY3`) - continuous.
- **Diastolic Blood Pressure** (`BPXODI3`) - continuous.
- **Vitamin D Lab Interpretation** (`LBDVD2LC`) - categorical, two levels.
- **Hepatitis B Lab Antibodies** (`LBXHBS`) - categorical, needs recoding to two levels.
- **Weak/Failing Kidneys** (`KIQ022`) - categorical, can be treated as two levels.
- **Minutes of Sedentary Behavior** (`PAD680`) - continuous, needs cleaning (remove values `7777`, `9999`, and null).
- **Current Self-Reported Weight** (`WHD020`) - continuous, needs cleaning (remove values `7777`, `9999`, and null).

## Questions for Analysis

- **Question 1**: "Is there **an association** between marital status (married or not married) and education level (bachelor’s degree or higher vs. less than a bachelor’s degree)?"  
    - A chi-square test of independence was performed to evaluate whether marital status is associated with educational attainment. The contingency table showed that among 7,772 participants, 39.5% of married individuals had a bachelor’s degree or higher compared to 27.2% of those not married. The result was statistically significant (χ² = 129.174, df = 1, p = 6.21×10⁻³⁰), indicating a strong relationship between marital status and education level. Married adults are significantly more likely to have higher educational attainment.

- **Question 2**: "Is there **a difference in the mean** sedentary behavior time between those who are married and those who are not married?"  
    - An independent-samples t-test was conducted to compare mean sedentary time between married and unmarried adults. Married participants (n = 4106) reported an average of **353.29 minutes/day** of sedentary behavior, while unmarried participants (n = 3603) averaged **371.96 minutes/day**. The difference was statistically significant (t = 3.851, p = 0.000118), suggesting that married individuals spend less time sitting compared to unmarried individuals.

- **Question 3**: "How do age and marital status affect systolic blood pressure?"  
    - A multiple linear regression model was used to predict systolic blood pressure (`SYS_MEAN`) based on age (`RIDAGEYR`) and marital status. The model included 5,858 observations and had an R² of 0.148, F(2,5855) = 507.5, p < 0.001. Age was a significant positive predictor (β = 0.4075, p < 0.001), showing that blood pressure rises approximately 0.41 mmHg per year. Marital status also had a small but significant negative coefficient (β = –1.2370, p = 0.005), indicating that married individuals tend to have slightly lower systolic blood pressure when controlling for age.

- **Question 4**: "Is there a **correlation** between self-reported weight and minutes of sedentary behavior? 
    - To examine the relationship between weight and sedentary time, both Pearson and Spearman correlations were calculated. The Pearson correlation was **r = 0.156, p = 1.70×10⁻⁴⁴**, and the Spearman correlation was **ρ = 0.138, p = 2.54×10⁻³⁵**. These results indicate a weak but statistically significant positive correlation: individuals with higher body weight tend to spend slightly more time being sedentary.

- **Question 5 (Creative Analysis)**: Develop your own unique question using at least one of the variables listed above. Ensure that your question can be answered using one of the following tests: chi-square, t-test, ANOVA, or correlation. Clearly state your question, explain why you chose the test, and document your findings.
    - For the creative analysis, an independent-samples t-test was used to test whether education level influences sedentary behavior. Participants with less than a bachelor’s degree (n = 5091) reported an average of **339.57 minutes/day**, while those with a bachelor’s degree or higher (n = 2617) averaged **405.34 minutes/day**. The difference was highly significant (t = –13.295, p = 1×10⁻³⁹), showing that individuals with higher education levels tend to spend significantly more time being sedentary.