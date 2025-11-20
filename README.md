Detailed Analytical Report – Bank Management BI System
1. Project Overview

This project is a full-scale Bank Management Analytics System developed using PostgreSQL as the transactional database and Power BI as the analytical layer. It provides a 360° view of banking operations—customers, accounts, cards, loans, transactions, and branches—through six interactive dashboards.
The solution is designed for management, analysts, and branch operations teams to support daily decision-making, performance tracking, and risk monitoring.

2. Objective of the Analytics System

Provide real-time visibility into customer activity, transactions, and financial exposure.

Track loan portfolio health, including principal, interest, tenure, and status.

Monitor card usage, network trends, merchant spend patterns, and timing trends.

Evaluate branch performance across accounts, loans, and customer base.

Offer a Customer 360 profile for relationship managers.

Enable data-driven decisions through interactive filters and detailed summaries.

3. Data Architecture & Model
Data Source:

PostgreSQL tables:
customers, accounts, cards, transactions, loans, branches, merchant_categories, card_networks.

Data Model (Star Schema)

Fact Tables:

fact_transactions

fact_loans

fact_card_transactions

fact_account_balance

Dimension Tables:

dim_customers

dim_accounts

dim_cards

dim_loans

dim_branch

dim_date

dim_card_network

ETL Highlights

Cleaned inconsistent timestamps.

Masked card numbers for security.

Converted amounts to numeric type.

Created pre-aggregated views for hourly and category-level analytics.

4. Dashboard-by-Dashboard Analytical Insights
4.1 Card Management Dashboard

Key Insights:

Shows 585 cardholders with 800 active cards.

Card networks (Mastercard, RuPay, VISA) show varying transaction peaks.

Merchant category analysis identifies restaurants, education, fuel, groceries as top spending segments.

Hourly heatmap identifies transaction-heavy periods (1–3 AM, 10–12 AM).

Business Value:

Helps detect fraud patterns.

Helps networks & merchants plan promotions.

Shows card lifecycle: active, blocked, expired.

4.2 Loan Portfolio Dashboard

Key Observations:

331 loan holders, 400 total loans.

Loan type trends show home & business loans dominate disbursements.

Heatmap highlights active months for loan disbursement (Apr, Jun, Sep).

Pie chart shows 76% active loans, 21% closed, 3% defaulted.

Business Value:

Assesses loan book risk.

Identifies peak disbursement seasons.

Supports credit risk management.

4.3 Customer Master Dashboard

Analytics:

Lists customers with all financial obligations: accounts, cards, loans.

Provides balance, outstanding loan amounts, and total card spend.

Useful for cross-sell and segmentation (high value, dormant, high risk).

Business Value:

Relationship managers can identify:

High-value customers

Multi-product holders

Customers eligible for loans/cards

4.4 Executive Overview Dashboard

KPIs:

Total Customers: 750

Total Accounts: 1100

Total Loans: 400

Total Cards: 800

Financial insights:

Treasury value: ₹33.54M

Total balance summary: ₹87.31M

Card transaction amount: ₹55.08M

Loan book size: ₹218.37M

Business Value:

Snapshot for top management to assess financial health.

Identifies growth areas and declining segments.

4.5 Branch Performance & Geo Dashboard

Insights:

Branch-level analytics for account balance, loans, card transactions.

Geographic visualization helps identify regional performance.

Monthly trend charts show variations across branches.

Business Value:

Best-performing branches (Mumbai, Chennai, Hyderabad).

Identifies struggling branches requiring operational improvements.

4.6 Customer 360 Dashboard

Provides a single customer view:

Demographics

KYC status

Account balances

Card details (masked)

Loans (principal, interest, outstanding)

Transaction trend by mode (UPI, ATM, NEFT, IMPS)

Business Value:

Helps relationship managers offer personalized banking.

Detects unusual spending or repayment patterns.

5. Analytical Findings from the Overall System
5.1 Customer Behavior

Spending is highest in restaurants and education categories.

Fuel and groceries indicate routine transactional behavior.

High-spending customers (top 5) contribute a large share of total cards revenue.

5.2 Loan Portfolio Behavior

Home & business loans dominate portfolio value.

Default rate is small but requires monitoring.

Mid-year months show maximum disbursements.

5.3 Card Network Performance

VISA leads in transaction volume.

Mastercard shows strong merchant diversity.

RuPay sees high usage in education & utilities.

5.4 Branch-Level Performance

Metro branches outperform Tier-2 cities.

Some branches have high accounts but low loan conversions → potential sales gap.

6. Problems Identified & Solutions
6.1 Performance Problems

Issue: Report takes long to load (due to large fact tables).
Solution:

Use incremental refresh in Power BI.

Create materialized aggregates in PostgreSQL.

6.2 Visual Overload

Issue: Many visuals in one page reduces readability.
Solution:

Split into thematic pages.

Use bookmarks and drillthrough.

6.3 PII Exposure

Issue: Card numbers, emails, phone numbers displayed.
Solution:

Implement RLS and column masking.

Mask card numbers with xxxx-xxxx-xxxx-1234.

6.4 Data Quality Issues

Issue: Inconsistent date formats & nulls.
Solution:

Standardize timestamps in ETL.

Apply constraints in PostgreSQL.

7. Recommendations

Add forecasting (ARIMA/XGBoost) for loan defaults & cash flows.

Add fraud detection rules for extreme card transactions.

Use Power BI paginated reports for bank statements & exports.

Provide executive weekly email summaries via Power BI subscriptions.

8. Final Summary

This project provides a complete analytical ecosystem for a bank using PostgreSQL + Power BI. It covers KPIs, financial performance, risk monitoring, branch effectiveness, and customer-level intelligence. The dashboards enable fast decision-making, operational visibility, and predictive insights—making the system suitable for real-world banking analytics needs.
