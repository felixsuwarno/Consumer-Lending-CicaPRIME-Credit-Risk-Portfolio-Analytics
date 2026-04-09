# Fintech CicaPRIME - Lending Product - Forecasting, Cohort Analysis & Variance Analytics  
**Forecasting • Cohort Analysis • Churn Modeling • Variance Analysis • Stress Testing**


This project analyzes three years of synthetic consumer installment lending data from a simulated fintech lending portfolio, spanning January 2023 to December 2025. The dataset contains loan-level, customer-level, and payment-level records, along with repayment schedules and internal budget plans.

The analysis evaluates revenue forecasting, budget vs. actual variance, borrower cohort behavior, churn dynamics, lifetime value and value concentration, vintage performance, and credit risk dynamics. The full workflow is built end-to-end using SQL and Python across a dataset representing the entire customer and loan lifecycle—from acquisition and origination to repayment, delinquency, and loss outcomes.

<br><br>

**➤ Executive Summary:**

CicaPRIME's lending portfolio grew steadily from 2023 through 2025, but growth came with financial predictability challenges. Cash collections fell short of scheduled payments in most months, credit losses exceeded plan and arrived in spikes rather than smoothly, and roughly 60–65% of borrowers did not return for a second loan within 180 days. Credit risk followed expected patterns — higher-risk tiers defaulted more often, and loans that reached 30 or more days past due were reliable early indicators of later defaults. The portfolio is growing, but conservative planning assumptions and early delinquency monitoring are needed to keep losses manageable.

<br><br>

➤ **Project Goal / Purpose:**  

This project evaluates how a simulated fintech lending portfolio performs over time—examining whether portfolio growth is stable, whether revenue generation is sustainable, and where the business may be exposed to downside risk.

The analysis measures trends in revenue and cash collections, compares realized results against internal plans to assess forecasting accuracy, and models borrower behavior at the borrower level. This includes analyzing borrower activation, repeat borrowing patterns, inactivity risk, and identifying which borrower segments generate the most long-term value.

At the portfolio level, the project analyzes value concentration and credit risk distribution, tracks how borrower cohorts perform across their lifecycle, and evaluates how portfolio performance changes as credit risk conditions evolve. The objective is to determine whether growth is supported by healthy fundamentals or overly dependent on a small subset of borrowers.


<br><br>

➤ **Skills Demonstrated:**  

Time-series revenue forecasting, budget vs actual variance analysis, customer cohort and churn modeling, lifetime value (LTV) analysis, concentration and dependency analysis, vintage performance tracking, probability of default (PD) modeling, loss analysis (EAD, LGD), and decision score effectiveness analysis.

**(SQL • Python • Pandas • Time-Series Forecasting • Cohort Analysis • Executive-Ready Analysis)**

<br><br>

➤ **Core Business Questions:**

**1 — Forecasting & Financial Planning** <br>
Is the lending business financially stable and predictable?

  1. **Revenue performance & outlook** <br> How did monthly interest and fee revenue perform from 2023–2025, and what is the expected revenue trajectory over the next 12 months?
  2. **Cash inflows vs contractual expectations** <br> How do actual monthly cash collections compare to scheduled cash collections from 2023–2025, and what is the resulting monthly collection gap? How large is the monthly collection gap relative to scheduled cash, and how stable is this gap over time?
  3. **Budget vs actual performance** <br> How reliable is financial planning given deviations between budgeted and realized revenue, cash inflows, and losses?
  4. **Delinquency & default trends** <br> Did borrowers begin falling behind on payments before credit losses increased sharply?

**2 — Borrower Activation, Churn & Value** <br>
Which customers create value and which ones stop borrowing?

  1. **Customer activation timing** <br> How long does it take newly acquired customers to originate their first loan?
  2. **Borrower inactivity & churn risk** <br> Which customers are most likely to stop borrowing after their initial loan?
  3. **Customer lifetime value (LTV)** <br> Which customers are expected to generate the highest lifetime value after accounting for credit losses?
  4. **Value concentration** <br> How concentrated is customer value, and how dependent is portfolio performance on top-value segments?

**3 — Credit Risk Modeling & Portfolio Loss Dynamics** <br>
How risky is the lending portfolio and how well is risk predicted?

  1. **Probability of default (PD)** <br> Which individual loans are most likely to default based on borrower, loan, and early behavior signals?
  2. **Exposure at default (EAD)** <br> How much exposure remains outstanding at the time loans default?
  3. **Loss given default (LGD)** <br> How severe are losses after recoveries, and how do they vary across segments?
  4. **Vintage risk performance** <br> How do loans from different origination months perform by the end of their first year?
  5. **Decision Score Effectiveness** <br> How effectively does the current decision score separate low-risk and high-risk borrowers?



<br><br>

**➤ The Dataset**

The raw dataset spans January 2023 through December 2025, representing a full three-year consumer installment lending lifecycle across 7 tables.

**customers**
One row per customer — signup date, acquisition channel, risk tier, and demographic buckets

**applications**
One row per credit application — approval decisions, approved amounts, and decision scores

**loans**
One row per booked loan — origination details, loan terms, and lifecycle outcomes including defaults

**payment_schedule**
One row per contractual installment — scheduled due dates and amounts

**payments**
One row per cash event — actual collections, payment types, and recoveries

**macro_monthly**
Monthly macro indexes across baseline, adverse, and severe scenarios for stress testing

**budget_plan_monthly**
Monthly planned originations, cash inflow, revenue, and net losses under base and stretch plans


<br><br>

## The Main Report - Key Questions Answered

### 1 — Forecasting & Financial Planning
Is the lending business financially stable and predictable?

<br>

**1.1. Revenue Performance & Outlook**

How did total portfolio interest and fee revenue perform on a monthly basis from 2023 through 2025, and what is the expected monthly revenue performance over the next 12 months?

<br>

**Charts**

<p align="center">
  <img src="Charts/01_1_revenue_performance_and_outlook_a_STL.png" width="100%">
</p>

<p align="center">
  <img src="Charts/01_1_revenue_performance_and_outlook_b_SARIMAX.png" width="100%">
</p>

**Key Insights**

- Revenue rose consistently from 2023 through 2025 as the loan portfolio expanded and more borrowers generated interest and fee income. 
- Early-stage growth was rapid due to the small starting base, while later growth reflects a more mature and scaled lending operation.
- The upward movement is mainly driven by portfolio expansion rather than strong seasonal effects.
- Month-to-month revenue fluctuations remain moderate relative to the overall growth trend, indicating stable performance.
- The 12-month forecast points to continued growth if current portfolio dynamics persist.

All revenue figures reflect cash actually collected from borrowers, ensuring alignment with real liquidity rather than accounting estimates.

<br><br>

**1.2. Cash Inflows vs Contractual Expectations**

How do actual cash collections compare to scheduled payments on a monthly basis from 2023 through 2025?
How stable / reliable are monthly collection gaps across this period?


<br>

**Charts**

<p align="center">
  <img src="Charts/01_2_scheduled_vs_actual_cash_flow.png" width="100%">
</p>

<br>

**Key Insights**
- Actual cash collected falls short of scheduled cash in the large majority of months (32 out of 35), indicating a consistent collection gap.
- On average, monthly collections are about 4–5% below contractual expectations.
- Over-collection occurs rarely and only by small margins, suggesting upside surprises are limited.
- The largest shortfall occurred early in the portfolio lifecycle, with performance stabilizing in later periods.
- Month-to-month variation in the gap is moderate, showing the shortfall pattern is persistent rather than random.

<br><br>

**1.3. Budget vs Actual Performance**

Did actual revenue earned, cash collected, and credit losses differ from what management planned?

<br>

**Charts**

<p align="center">
  <img src="Charts/01_3a_budget_vs_actual_on_revenue.png" width="100%">
</p>

**Key Insights**
- Revenue grew steadily from 2023 through 2025, reflecting consistent portfolio expansion.
- During 2023 and most of 2024, actual revenue remained above the base plan, indicating stronger monetization than management initially forecasted.
- Performance periodically approached the stretch target in 2024, showing that growth was temporarily aligned with aggressive expectations.
- In 2025, revenue continued rising in absolute dollars but began underperforming both base and stretch plans, signaling a slowdown relative to budgeted growth.
- The variance trend shows a shift from outperformance in early years to underperformance later, suggesting planning assumptions became more aggressive than realized revenue growth.

<br>

<p align="center">
  <img src="Charts/01_3b_budget_vs_actual_on_cash.png" width="100%">
</p>

**Key Insights**
- Cash collections increased each year, reflecting portfolio expansion and higher repayment volumes.
- Actual cash fell below the base plan in nearly every month after early 2023, indicating consistent underperformance versus management expectations.
- The shortfall versus stretch targets was larger and persistent, showing that the aggressive growth scenario was not achieved.
- The variance trend shows the deviation becoming more negative over time, meaning the difference between expected and realized cash did not correct as the portfolio matured.
- By late 2025, the cash gap reached its widest levels, signaling structural pressure on liquidity relative to plan.

<br>

<p align="center">
  <img src="Charts/01_3c_budget_vs_actual_on_credit_loss.png" width="100%">
</p>

<br>

**Key Insights**
- Actual credit losses were much higher than planned in most months after early 2024.
- Losses increased sharply and stayed high through 2025, far above what the budget expected.
- Instead of rising slowly and smoothly, losses jumped in spikes, meaning defaults happened in waves.
- The difference between planned and actual losses became very large, especially during peak months.
- Compared to revenue and cash, credit losses were the biggest source of budget problems.

<br><br>

**1.4. Delinquency & Default Trends**<br><br>
Did borrowers begin falling behind on payments before credit losses increased sharply?

<br>

**Charts**

<p align="center">
  <img src="Charts/01_4a_delinquency_vs_default.png" width="100%">
</p>

**Key Insights**
- DPD 30+ starts rising early and keeps trending upward.
- Defaults stay low at first, then increase later.
- Defaults move more sharply month-to-month; DPD rises more steadily.
- The rise in delinquency happens before the sustained rise in defaults.

<br>

<p align="center">
  <img src="Charts/01_4b_dpd_bucket_shares_overtime.png" width="100%">
</p>

**Key Insights**
- The share of Current loans gradually declines over time.
- The 90+ delinquency bucket steadily increases.
- Early delinquency (1–29) rises before severe delinquency builds.
- Loans appear to migrate from Current → early delinquency → severe delinquency over time.

<br>

**1.5. Conclusion and Business Recommendation**<br><br>

Revenue is growing steadily as the lending portfolio gets bigger. However, the business is not fully predictable financially. Actual cash collected from borrowers is usually lower than what the payment schedule expects, and credit losses are higher than what the budget planned. Delinquency also starts increasing before defaults rise, which shows that repayment problems appear earlier than the losses recorded in the financial results.

Business Recommendation
- Watch loans that become 30+ days late. When more loans pass 30 days late, it often means defaults will rise later. This should be treated as an early warning signal.
- Make financial plans more conservative. Budgets for cash collections and credit losses should assume lower collections and higher losses than originally planned.
- Be careful when the loan portfolio grows. As more loans are issued, repayment behavior should be monitored closely so that small delinquency problems do not grow into larger losses later.

<br><br>

### 2 — Borrower Activation, Churn & Value
Which customers create value and which ones stop borrowing?

<br>

**2.1. Customer Activation Timing**

How long does it take customers to activate into credit usage by originating their first loan?
  
<br>

**Charts**

<p align="center">
  <img src="Charts/02_1_customer_activation_timing.png" width="100%">
</p>

**Key Insights**
- Early cohorts (2023–early 2024) show activation taking roughly 6–12 months, meaning customers typically borrowed long after signup.
- Recent cohorts (late 2024–2025) appear to activate much faster, but these numbers are incomplete because many customers have not yet had 6 months to convert.
- The sharp drop in activation days in the second half of the chart is partly driven by data maturity, not purely by operational improvement.
- Only the fully matured portion of the chart (older cohorts) should be used to judge true activation speed trends.
- Based on matured data only, activation improved gradually over time, but there is no clear evidence yet that activation dropped to under one month for stable cohorts.
- Recent cohorts require more time before drawing strong conclusions about structural changes in customer behavior.

<br>
<br>

**2.2. Borrower Inactivity & Churn Risk**

Which customers are likely to stop borrowing or become inactive after their initial loan?

<br>

**Charts**

<p align="center">
  <img src="Charts/02_2a_borrower_inactivity_and_churn_risk.png" style="width:75%;">
</p

<br>

<p align="center">
  <img src="Charts/02_2b_borrower_inactivity_and_churn_risk.png" style="width:75%;">
</p

<br>

<p align="center">
  <img src="Charts/02_2c_borrower_inactivity_and_churn_risk.png" style="width:75%;">
</p

<br>

<p align="center">
  <img src="Charts/02_2d_borrower_inactivity_and_churn_risk.png" style="width:75%;">
</p>

<br>

<p align="center">
  <img src="Charts/02_2e_borrower_inactivity_and_churn_risk.png" style="width:75%;">
</p>


**Key Insights**
- Roughly 60–65% of customers do not return for a second loan within 180 days, meaning first-loan churn is common.
- Risk tier at signup is the strongest driver of inactivity, with a wide gap between Tier A and Tier D—lower tiers are far more likely to stop borrowing.
- Income level shows only small differences in inactivity, so earning more does not strongly predict repeat borrowing.
- Age groups behave similarly, with no major separation in churn risk across age bands.
- Region has minimal impact, as inactivity rates are nearly the same across locations.
- Acquisition channel differences are modest, and no channel changes churn risk as meaningfully as risk tier does.

<br><br>

**2.3. Customer lifetime value (LTV)**

Which customer(s) are expected to generate the highest lifetime value after accounting for credit losses?

<br>

<p align="center">
  <img src="Charts/02_3_customer_LTV_180d_summary.png" style="width:25%;">
</p>

**Key Insights** <br>
All customer segments generate positive average LTV. Even the lowest segment produces about $157 in 180-day LTV, indicating that, on average, borrowers across the portfolio still generate net value after accounting for credit losses.

<br><br>

**2.4. Value Concentration**
How concentrated is customer value, and how dependent is portfolio performance on top-value segments?

<br>

<p align="center">
  <img src="Charts/02_4_value_concentration_pareto_curve.png" style="width:100%;">
</p>

**Key Insights** <br>
**Value is moderately concentrated:** About 60% of customers generate ~80% of total LTV, so the portfolio is not dependent on a tiny elite group. The portfolio is diversified and not fragile.

<br><br>

**2.5. Conclusion and Business Recommendation**
Many customers do not return for another loan after their first one, so repeat borrowing is limited. Customer value also varies across borrower segments: higher-value segments generate substantially more value per customer, while lower-value segments generate much smaller value within the same 180-day period. Risk tier at signup explains much of this behavior, while income, age, region, and acquisition channel show smaller differences.

Business Recommendation
- Prioritize higher-value borrower segments. Customers who generate stronger LTV tend to contribute more value per borrower, so focusing on these segments can improve portfolio profitability.
- Reduce first-loan churn. Since many customers do not take a second loan within 180 days, improving follow-up offers or engagement after the first loan may increase repeat borrowing.
- Monitor low-value borrower segments. Some borrower groups generate much lower value within the first 180 days, so their performance should be tracked to ensure they remain economically viable for the portfolio.

<br><br>

### 3 — Credit Risk Modeling & Portfolio Loss Dynamics
How risky is the lending portfolio and how well is risk predicted?

<br>

**3.1. Probability of default (PD)**  
Which individual loans are most likely to default based on borrower, loan, and early behavior signals?

The fully observable window in this dataset is between 2023 to 2024 dataset, so the calculations we make for this business question reflects that.

<br>

<p align="center">
  <img src="Charts/03_1a_pd_by_risk_tier.png" style="width:100%;">
</p>

**Key Insights**
- Higher risk tiers default more often, which means the risk ranking is working properly.
- Most loans are in Tier A, so its 4% default rate is statistically reliable.
- Default rates increase steadily from A to D with no unexpected reversals.
- Tier D has only 26 loans, so its 8% default rate can change easily with just one additional default.
- Overall, the model is separating safer borrowers from riskier borrowers as intended.

<br>

<p align="center">
  <img src="Charts/03_1b_pd_by_vintage.png" style="width:100%;">
</p>

**Key Insights**
- Default rates fluctuate across months, showing that credit performance changes by cohort.
- Early 2023 months have very low loan counts, so their high or low PD values are not statistically reliable.
- Mid-2023 shows a temporary PD spike around 10%, but the loan volumes there are modest.
- Most 2024 months stay between 3% and 6%, indicating more stable portfolio performance.
- There is no consistent upward pattern across vintages, suggesting underwriting quality has not steadily worsened.

<br>
<br>

**3.2. Exposure at default (EAD)**  
How much exposure remains outstanding at the time loans default?

The fully observable window in this dataset is between 2023 to 2024 dataset, so the calculations we make for this business question reflects that.

<br>

<p align="center">
  <img src="Charts/03_2a_ead_by_risk_tier.png" style="width:100%;">
</p

**Key Insights**
- When loans default, the remaining unpaid balance is roughly similar across risk tiers, so higher-risk tiers do not show much bigger balances at the moment of default.
- Tier B has the largest unpaid balance at default on average, meaning its defaults tend to happen with more money still owed.
- Tier D has the fewest defaults (N=5), so its average balance is not very reliable and can swing a lot from just a few loans.

<br><br>

<p align="center">
  <img src="Charts/03_2b_ead_by_vintage.png" style="width:100%;">
</p

**Key Insights**
- The average unpaid balance at default generally increases for newer origination months, meaning recent loans tend to default with more money still owed.
- Early months (like 2023-01) show extreme values because very few loans defaulted, so one large loan can distort the average.
- From mid-2024 onward, the average unpaid balance becomes consistently higher, suggesting larger loan sizes or earlier-stage defaults.
- Months with very small default counts (low N above bars) should be interpreted cautiously because averages are unstable when sample size is small.

<br>
<br>

**3.3. Loss Given Default (LGD)**  
How severe are losses after recoveries, and how do they vary across segments?

The fully observable window in this dataset is between 2023 to 2024 dataset, so the calculations we make for this business question reflects that.

<br>

<p align="center">
  <img src="Charts/03_3b_lgd_by_vintage.png" style="width:100%;">
</p

**Key Insights**
- LGD jumps around a lot in early months because some months only have 1 or 2 defaulted loans, so one loan can move the result a lot.
- November 2023 looks unusually low (around mid-40%), but it is based on only 2 loans, so it is not stable.
- From 2024 onward, when the number of defaults per month increases, LGD mostly stays between about 75% and 85%, which is more consistent.
- Many 2025 months have higher default counts (10+ loans), so those LGD numbers are more reliable than the early months.
- Overall, the pattern shows that when loans default, the bank usually loses around 80% of the unpaid principal, meaning recoveries are generally small.

<br>
<br>

**3.4. Vintage risk performance**  
How do loans from different origination months perform by the end of their first year?

The fully observable window in this dataset is between 2023 to 2024 dataset, so all of the calculations we make here reflect that.

For the purpose of answering this business question, there will be three separate reports ( tables ).
- cumulative default table
- cumulative loss table
- bucketed delinquency snapshot table

<br> 

**3.4A. Cumulative Default Rate Table**  
A cumulative default table shows, for each group of loans that started in the same month, what percentage of those loans have defaulted by a specific point in time, such as 12 months after they began. It measures how many loans have failed out of the original group and expresses that as a rate, so we can compare how different groups performed over the same time period.

<br>

<p align="center">
  <img src="Charts/03_4a_cumulative_default_rate.png" style="width:100%;">
</p>

**Key Insights :**
- Loan volume increased steadily through 2024, showing strong portfolio growth.
- Default rates were volatile in 2023, with several sharp spikes near 9–10%, indicating inconsistent risk quality early on.
- Most 2024 vintages show moderate default rates (around 3–6%), suggesting more stable underwriting during the growth phase.
- April 2024 stands out with a high default rate despite rising volume, signaling a temporary risk deterioration.
- Late 2024 combines high loan volume with controlled default rates, indicating growth without a clear structural increase in risk.

<br> 

**3.4B. Cumulative Loss Rate Table**  
A cumulative loss table shows, for each group of loans that started in the same month, how much money was lost from those loans by a specific point in time, such as 12 months after they began. It measures the total unpaid balance from loans that defaulted within that period and expresses it relative to the original group, so we can compare how severe the losses were across different vintages over the same time horizon.

<br>

<p align="center">
  <img src="Charts/03_4b_cumulative_loss_rate.png" style="width:100%;">
</p

**Key Insights :**
- Loss rates start high in early 2023 (~5%), fall mid-year, then rise again by late 2023.
- December 2023 and April 2024 show the highest spikes (around 4–5%), marking weaker vintages.
- Mid-2024 vintages improve materially (around 1–2%), indicating stronger credit quality.
- Late 2024 loss rates increase again (~3%), suggesting risk rises alongside higher origination volumes.
- Overall: Portfolio loss performance is volatile across vintages, not stable.

<br><br>

**3.4C. Bucketed Delinquency Snapshot Table**  
A Bucketed Delinquency Snapshot table shows, for each loan within a group that started in the same month, how far behind on payments that loan was at specific points in time, such as 11 and 12 months after origination. Instead of showing the exact number of days late, the table groups loans into clear categories like current, 1–29 days past due, 30–59 days past due, 60–89 days past due, or 90+ days past due. This allows us to see how payment status changed near the end of the first year and compare delinquency patterns across different origination months.

<p align="center">
  <img src="Charts/03_4c_bucketed_delinquency_snapshot.png" style="width:100%;">
</
	
**Key Insights :**
- Early 2023 vintages show extreme distributions (100% in one bucket), indicating very small sample sizes rather than true credit performance.
- April–July 2023 represent the weakest vintages, with elevated 30–59%, meaningful 60–89%, and noticeable 90+ exposure.
- Late 2023 moderates from that peak but still carries broader delinquency dispersion compared to 2024.
- From early 2024 onward, 00_current holds consistently around ~55–65%, while 90+ remains mostly below ~5–6%, showing contained severe delinquency.
- No vintage in 2024 exhibits breakout 90+ concentration.
- Overall: Credit risk peaks mid-2023 and becomes structurally more contained through 2024, without evidence of runaway deterioration.

<br><br>

**3.4D. Conclusion**

Conclusion based on the three bullet points above :
- A small number of vintages (Aug–Sep 2023 and Apr 2024) materially drive overall first-year risk outcomes.
- The spike months show alignment across metrics: elevated default rate, elevated loss rate, and higher 30+ delinquency concentration, confirming true credit deterioration rather than measurement noise.
- 2024 vintages exhibit tighter severe-delinquency containment, even though early-stage delinquency remains persistent.
- Origination volume increases significantly in late 2024, raising total dollar exposure even when risk rates are moderate.

**Answer to the business question:**
First-year performance differs meaningfully by origination month, with identifiable high-risk vintages rather than a steady time trend. Risk concentration is episodic, and portfolio exposure grows as volumes expand.

### Business Recommendation:

Look closely at August–September 2023 and April 2024.
Those months clearly performed worse. Check what changed during those times — rules, pricing, customer type, or outside economic conditions.

Watch loans that are 30+ days late.
When more loans move past 30 days late, risk usually gets worse. Use that as a warning sign before defaults increase.

Be careful when loan volume grows.
Even if the default rate looks “normal,” a bigger book means bigger dollar losses.

Focus on stopping loans from getting worse once they are slightly late.
If you can prevent 1–29 day late loans from becoming 30–59 days late, you reduce future defaults.

<br><br>

**3.5. Decision Score Effectiveness**

How well does the current decision score predict which borrowers are more likely to default within 12 months?

<p align="center">
  <img src="Charts/03_5_decision_score_effectiveness.png" style="width:100%;">
</>

**Key Insights :**
- **The lowest visible score band shows the highest observed default risk.** The 550–599 band has a 16.67% 12-month default rate, materially above the higher score bands, although the sample size is small.
- **Score bands above 600 show substantially lower default risk than 550–599.** Default rates for scores 600 and above fall into a narrower 4%–6% range.
- **The decision score is directionally predictive, but not perfectly monotonic.** Default risk is generally lower in higher score bands, but the ordering is not exact across all bands.
- **Most booked loans are concentrated in the highest score band.** The 700+ group contains the majority of loans by count, indicating that most observed originations are concentrated among higher-scored borrowers.
- **The lowest band should be interpreted cautiously because of small sample size.** With only 24 loans, the observed default rate in 550–599 is more sensitive to random variation than the rates in larger bands.

<br><br>

**3.6. Conclusion and Business Recommendation**

Credit risk is present but generally follows the expected patterns. Higher-risk borrower tiers default more often, which shows the risk ranking is working. When loans default, most of the unpaid principal is lost, meaning recoveries are usually small. Risk also changes across origination months, with some vintages performing worse than others rather than risk rising steadily over time. The decision score helps separate safer borrowers from riskier ones, although the relationship is not perfectly ordered across score bands.

Business Recommendation
- Continue using risk tier and decision scores in underwriting. They successfully separate safer borrowers from higher-risk borrowers.
- Monitor vintages closely. Some origination months perform worse than others, so those periods should be reviewed to understand what changed.
- Improve recovery strategies after default. Since most unpaid principal is not recovered, even small improvements in recoveries could reduce total portfolio losses.
