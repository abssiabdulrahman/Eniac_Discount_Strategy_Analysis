# Eniac_Discount_Strategy_Analysis
The Discount Dilemma — What Works, What Doesn't, What's Next (2017–2018)

# Project Introduction
This project was completed as part of my data analytics training and focuses on evaluating Eniac's internal pricing and discount strategy using historical order data from 2017–2018.
Eniac is a premium Apple-focused e-commerce company. While discounts had become the default pricing mode — applied to over 95% of all order lines — the key question was never answered: are discounts actually driving revenue?
Through this project, I applied Python (pandas), data visualization, and business reasoning to challenge an assumption that had quietly become company-wide policy.

# Project Objective
The main objective was to analyze Eniac's discount behaviour and determine whether deeper discounts reliably increase revenue — or whether the business had been leaving money on the table.
Key questions included:

How widespread is discounting across Eniac's catalogue?
Does discount depth correlate with higher revenue?
What's driving peak revenue periods like Black Friday?
Which product categories benefit most from discounting — and which don't?
What structural data issues are limiting deeper analysis?


# The Headline Finding

Bigger discounts do not reliably increase revenue.


95.5% of all order lines are discounted
97.5% of all revenue comes from discounted products
Correlation between discount depth and revenue: (0.26) — weak

Discounts are not a strategy at Eniac. They are the default — and the data does not support the assumption that deeper cuts lead to more revenue.

# Project Workflow
This project followed three main phases:
## 1. Data Cleaning (Python / pandas)
Before any analysis could begin, the raw dataset required significant cleaning. Major issues found:

93.7% of promo_price rows had double-decimal formatting errors (e.g. 1.029.99 instead of 1029.99) — column was dropped entirely
Discount re-derived as price − unit_price
Negative discounts removed (caused by retroactive price updates to old orders)
Rows where unit_price × quantity > total_paid were dropped as logically impossible
Date columns cast to datetime to enable time-series analysis

Result: 54,250 clean order lines retained after a ~3.4% row drop.
Notebook: Exploration_Cleaning__Eniac_s_Dataset.ipynb

## 2. Exploratory Analysis (Python / pandas / matplotlib / seaborn)
Key analyses performed:

Distribution of discount depth across all order lines
Monthly revenue trends vs. average discount percentage
Category-level revenue vs. average discount comparison
Scatter analysis of discounted price vs. list price
Black Friday (November) performance deep-dive

Notebook: Eniac_Analysis.ipynb

## 3. Business Presentation
Findings were synthesised into a stakeholder-ready presentation covering the headline finding, supporting evidence, category breakdown, and three prioritised recommendations.
Presentation file: Eniac_Discount_Strategy_pptx.pdf

Key Findings
Discount Depth
Most discounts cluster between 10–25%. The median discount is 19.4%, while the mean is pulled to ~22.4% by a high-discount tail. Deep cuts above 40% are rare but do occur.
Black Friday — Volume, Not Depth
November 2017 generated 3× average monthly revenue with 6,573 orders — at an average discount of just 21.9%, the same depth seen in other months. This is the clearest evidence that volume is the lever, not discount depth.
Category Breakdown

Storage (32.7% of revenue) and Mobile (16%) are the top earners — and both carry lower-than-average discount rates
Audio carries the highest average discount (29.6%) but contributes only ~4% of revenue
High discount ≠ high revenue at the category level either


Recommended Actions
PriorityActionRationale High90-Day No-Discount TestRemove everyday discounts from the top 3 best-selling categories and measure revenue impact Quick WinProtect Black Friday — But Cap DepthNovember succeeds on volume; no need to offer deeper discounts to drive performance FoundationalFix the Data Infrastructure13.6% of order lines couldn't be categorised due to unreadable type codes; structural data issues limit future analysis

Data Quality Issues Identified
Four structural problems were flagged for engineering:

promo_price corruption — 93.7% of values malformed; validate prices at point of entry
Unreadable type codes — 126 numeric codes with no lookup table; add a product_categories mapping table
No customer_id in exports — retention, repeat-purchase rate, and LTV are currently unmeasurable; add anonymised ID (HMAC-SHA256)
Retroactive price updates — old orders affected by product price changes; snapshot list price at order time via price_at_order_time column


# What I Learned
This project pushed me beyond technical execution into genuine analytical thinking.
Key learnings:

How to clean messy, real-world transactional data at scale
How to distinguish correlation from business causation
How to construct a narrative from data that challenges an assumption rather than confirming one
How to segment analysis by time, category, and price tier to find where the real signal is
How to translate analytical findings into prioritised, actionable recommendations for a non-technical audience


# Tools Used

Python (pandas, matplotlib, seaborn),
VS Code,
Jupyter Notebook,
PowerPoint / PDF presentation,


# Project Details
Dataset: Eniac internal order data (2017–2018)
Project completed: May 2026
Project type: Internal pricing strategy analysis
Team: Mahsa Ahmadi, Namratha Nagesh, Abdul Rahman Abssi, Ian Blair
