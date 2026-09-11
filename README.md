Olist Logistics Burden & Subsidy Allocation

An end-to-end Python analysis of Brazilian e-commerce logistics data. The project identifies states facing the greatest combination of long delivery times and high freight costs, then simulates a fixed-budget subsidy allocation for high-spending customers in those regions.

Project Overview

Olist marketplace customers experience very different delivery times and freight costs across Brazil. This project addresses two questions:

Which states face the greatest logistics burden?

Under a fixed 5,000 BRL budget, which customers would be prioritized for a simulated 50 BRL freight subsidy?

The analysis is a decision-support simulation. It does not claim that a subsidy causes retention or that historical spending equals future revenue.

Results

Using 96,470 completed orders, the composite score identified RR, AP, AM, AL, and PA as the five states with the highest combined delivery-time and freight-cost burden. Under the simulated policy, a 5,000 BRL budget funded 50 BRL subsidies for 100 customers. Those selected customers accounted for 102,211.52 BRL in historical product spending, which is 20.4 times the simulated subsidy budget.

These values describe historical customer spending represented by the allocation. They are not an estimate of incremental revenue, return on investment, or customers retained.



Methods

1. Data integration and cleaning

Loaded orders, order items, reviews, and customer records.

Restricted the analysis to completed deliveries with valid dates.

Merged customer, order, freight, price, and review information.

Engineered actual delivery duration, days relative to the promised date, and a late-delivery indicator.

2. Logistics-burden score

For each customer state, the analysis calculates:

average delivery duration;

average freight cost;

late-delivery rate;

average review score; and

number of unique orders.

Average delivery duration and freight cost are min-max normalized before being combined:

Logistics Burden Score = 0.70 × Normalized Delivery Duration
                       + 0.30 × Normalized Freight Cost

The 70/30 weights are transparent business assumptions, not statistically estimated causal effects. A production analysis should test alternative weights and validate the score against customer satisfaction or churn.

3. Simulated subsidy allocation

Selected the five states with the highest logistics-burden scores.

Aggregated historical product spending by unique customer in those states.

Ranked customers by historical spending.

Allocated a simulated 50 BRL subsidy per customer until the 5,000 BRL budget was exhausted.

Because every simulated subsidy has the same cost, ranking by historical spending maximizes the historical spending represented among selected customers. It does not prove incremental revenue or retention.

Outputs

Running the analysis creates:

outputs/
├── olist_logistics_summary.png
├── simulated_subsidy_recipients.csv
└── state_logistics_burden.csv

For the current dataset, the console reports:

number of delivered orders analyzed;

five highest-burden states;

number of customers selected;

total simulated subsidy;

selected customers' historical spending; and

historical-spend-to-subsidy multiple.

Repository Structure

Olist-Logistics-Optimization/
├── data/
│   ├── olist_customers_dataset.csv
│   ├── olist_order_items_dataset.csv
│   ├── olist_order_reviews_dataset.csv
│   └── olist_orders_dataset.csv
├── outputs/
├── Olist_Logistics_Optimization.py
├── README.md
└── requirements.txt

The Olist CSV files are not stored in this repository. On the first run, the script automatically downloads the four required public files from Olist's work-at-olist-data repository into data/. To use files already stored elsewhere, pass --data-dir PATH. To disable downloading, pass --no-download.

How to Run

python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python Olist_Logistics_Optimization.py

The first run takes longer because it downloads the public dataset. Subsequent runs reuse the local files.

Requirements

pandas
matplotlib
seaborn

Skills Demonstrated

Python and Pandas data pipelines

Multi-table joins and feature engineering

Normalization and composite-score construction

Constrained resource-allocation logic

Business-metric interpretation

Data visualization and reproducible project structure

Limitations and Next Steps

Test the sensitivity of state rankings to alternative score weights.

Estimate subsidy response using an experiment or causal-inference design.

Incorporate customer purchase frequency and recency rather than relying on historical spending alone.

Compare the ranking rule with alternative allocation strategies.

Add unit tests for feature calculations and budget constraints.

Author

Sienna Yan<br>
Carnegie Mellon University<br>
LinkedIn | GitHub

