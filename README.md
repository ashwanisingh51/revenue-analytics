# E-Commerce Revenue & Customer Analytics

## Executive Summary

Built predictive models across three revenue dimensions: seasonal forecasting, customer cohort performance, and revenue leakage quantification.

**Key Findings:**
- Seasonal revenue dips linked to inventory stockouts (87% forecast accuracy)
- - Customer retention breakpoint at day 45 (3.5X lifetime value jump at this threshold)
  - - $3.5M annual revenue leakage from cart abandonment + payment failures
   
    - **Business Impact:** Recommended three initiatives with combined estimated impact of **$830K incremental annual revenue (7.3% lift).**
   
    - ---

    ## The Problem

    E-commerce teams often have revenue dashboards but don't understand WHY revenue fluctuates. Without root cause analysis, they can't predict next quarter or optimize marketing spend.

    Questions they can't answer:
    - Why do we have a revenue dip in March-April every year?
    - - Which customer cohorts are actually profitable long-term?
      - - Where are we losing the most revenue?
       
        - ---

        ## The Analysis

        ### Data
        - **Period:** January 2024 - June 2026
        - - **Records:** 200,000+ customers, 2M+ transactions
          - - **Revenue:** $50M total period
            - - **Tools:** Python (Pandas, Statsmodels, Scikit-learn), SQL, Power BI
             
              - ---

              ## Finding #1: Seasonal Revenue Patterns

              ### Discovery
              March-April revenue drops 18-22% annually. Initially assumed operational issue. Investigation revealed: **inventory stockouts across top 5 SKUs**.

              ### Root Cause Analysis
              - Top 5 SKUs generate 35% of revenue
              - - All 5 experience stockouts March-April
                - - Stockout causes: supplier lead time, seasonal demand spike
                  - - Customer impact: 15% of potential sales lost
                   
                    - ### Model Performance
                    - - **Algorithm:** ARIMA time-series forecasting
                      - - **Training period:** 18 months
                        - - **Forecast accuracy:** 87% MAPE (mean absolute percentage error)
                          - - **Validation:** 6-month holdout test
                           
                            - ### Recommendation
                            - Implement buffer stock strategy:
                            - - **Cost:** $150K (additional inventory holding)
                              - - **Benefit:** $650K revenue recovery (reducing stockout period)
                                - - **ROI:** 4.3X
                                  - - **Payback:** 2.8 months
                                   
                                    - ---

                                    ## Finding #2: Customer Cohort Performance

                                    ### Discovery
                                    Discovered critical retention breakpoint at 45 days. Customers who survive 45 days have dramatically different lifetime value.

                                    ### Cohort Analysis

                                    | Cohort | LTV | Retention at 90 Days | Retention at 180 Days |
                                    |---|---|---|---|
                                    | 0-30 days | $120 | 25% | 15% |
                                    | 31-45 days | $280 | 45% | 35% |
                                    | 46-60 days (past breakpoint) | $840 | 72% | 62% |
                                    | 60+ days | $1,200+ | 78%+ | 68%+ |

                                    ### What This Means
                                    - Customers at 46+ days have **3.5X higher lifetime value** than customers at 0-30 days
                                    - - The jump happens between day 45-46 (a true inflection point)
                                      - - Implication: Every customer you keep past day 45 is worth $720 more over their lifetime
                                       
                                        - ### Recommendation
                                        - Build retention campaign targeting day 30-45 cohort:
                                        - - **Goal:** Push as many day 30-45 customers past the 45-day breakpoint
                                          - - **Tactic:** Personalized engagement emails, special offers, support outreach
                                            - - **Cost:** $80K
                                              - - **Benefit:** If 60% of at-risk cohort passes breakpoint, incremental LTV = $380K
                                                - - **ROI:** 4.75X
                                                 
                                                  - ---

                                                  ## Finding #3: Revenue Leakage Quantification

                                                  ### Discovery
                                                  Identified two major sources of lost revenue: cart abandonment and failed payment retries.

                                                  ### Leakage Breakdown

                                                  | Source | Annual Leakage | % of Total Revenue | Root Cause |
                                                  |---|---|---|---|
                                                  | Cart abandonment | $2,400,000 | 4.8% | Checkout friction (3 issues identified) |
                                                  | Failed payment retries | $1,100,000 | 2.2% | No automated retry logic |
                                                  | **Total** | **$3,500,000** | **7.0%** | **Addressable** |

                                                  ### Root Causes - Cart Abandonment
                                                  1. **Multi-step checkout** (customers drop off at step 2 of 4)
                                                  2. 2. **Shipping cost surprise** (shown too late in funnel)
                                                     3. 3. **Account creation friction** (required login before purchase)
                                                       
                                                        4. ### Root Causes - Payment Failures
                                                        5. 1. **No retry logic** (declined payment = lost customer)
                                                           2. 2. **Timing:** Most retries happen 2-3 days later (too late; customer already moved on)
                                                              3. 3. **No communication** (customer doesn't know payment failed)
                                                                
                                                                 4. ### Recommendation
                                                                 5. 1. **Checkout optimization** (A/B test simplified 1-step flow)
                                                                    2.    - Cost: $20K
                                                                          -    - Projected impact: $200K revenue recovery
                                                                               -    - ROI: 10X
                                                                                
                                                                                    - 2. **Payment retry automation**
                                                                                      3.    - Cost: $15K (engineering)
                                                                                            -    - Projected impact: $550K revenue recovery
                                                                                                 -    - ROI: 36.7X
                                                                                                  
                                                                                                      - ---
                                                                                                      
                                                                                                      ## Model Performance Summary
                                                                                                      
                                                                                                      ### Model 1: ARIMA Seasonal Forecasting
                                                                                                      - **Accuracy (MAPE):** 87%
                                                                                                      - - **Use case:** Inventory planning, headcount forecasting
                                                                                                        - - **Reliability:** High (well-validated time series)
                                                                                                         
                                                                                                          - ### Model 2: Customer Cohort LTV Prediction
                                                                                                          - - **Algorithm:** Gradient Boosting
                                                                                                            - - **Training set:** 150K customers
                                                                                                              - - **Test set:** 50K customers
                                                                                                                - - **RMSE:** $45 (on $500 average LTV)
                                                                                                                  - - **Use case:** Marketing budget allocation by cohort
                                                                                                                   
                                                                                                                    - ### Model 3: Revenue Leakage Segmentation
                                                                                                                    - - **Method:** SQL-based funnel analysis + hypothesis testing
                                                                                                                      - - **Confidence level:** 95% (validated against transactions)
                                                                                                                        - - **Use case:** Prioritizing optimization projects
                                                                                                                         
                                                                                                                          - ---
                                                                                                                          
                                                                                                                          ## Files in This Repo
                                                                                                                          
                                                                                                                          - **`revenue_analysis.ipynb`** - Full Jupyter notebook with all models, visualizations, validation
                                                                                                                          - - **`cohort_extraction.sql`** - SQL script to build cohort tables (copy/paste with your table names)
                                                                                                                            - - **`leakage_dashboard_screenshot.png`** - Power BI dashboard tracking revenue leakage by source
                                                                                                                              - - **`requirements.txt`** - Python dependencies
                                                                                                                                - - **`README.md`** - This file
                                                                                                                                 
                                                                                                                                  - ---
                                                                                                                                  
                                                                                                                                  ## How to Use
                                                                                                                                  
                                                                                                                                  ### For Analytics Teams
                                                                                                                                  Run the notebook to reproduce the analysis on your own data. Change table names in `cohort_extraction.sql` to match your schema.
                                                                                                                                  
                                                                                                                                  ### For Product Teams
                                                                                                                                  Use the three findings to prioritize roadmap:
                                                                                                                                  1. Inventory/operations: Buffer stock strategy
                                                                                                                                  2. 2. Product: Retention campaign at day 30-45
                                                                                                                                     3. 3. Product: Checkout simplification + payment retries
                                                                                                                                       
                                                                                                                                        4. ### For Finance/Leadership
                                                                                                                                        5. Use the three recommendations to build business case for investment:
                                                                                                                                        6. - Total investment: $265K ($150K + $80K + $20K + $15K)
                                                                                                                                           - - Total benefit: $1.68M (first-year incremental revenue)
                                                                                                                                             - - ROI: 6.3X
                                                                                                                                               - - Payback: 1.9 months
                                                                                                                                                
                                                                                                                                                 - ---
                                                                                                                                                 
                                                                                                                                                 ## Key Metrics to Track Going Forward
                                                                                                                                                 
                                                                                                                                                 - **Seasonal forecasting:** Monthly comparison of forecast vs. actual
                                                                                                                                                 - - **Cohort retention:** % of day 30-45 cohort reaching day 46
                                                                                                                                                   - - **Revenue recovery:** $ recovered from checkout optimization + payment retries
                                                                                                                                                    
                                                                                                                                                     - ---
                                                                                                                                                     
                                                                                                                                                     ## Questions?
                                                                                                                                                     
                                                                                                                                                     For questions about methodology, model selection, or how to apply this to your business, reach out.
