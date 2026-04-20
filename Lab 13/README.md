# Big Data Analytics Lab — Results Summary

## Main Lab Results

**Part 1 – Descriptive Analytics:** The dataset contains 20 transactions with a mean revenue of $385.95 per transaction. Electronics dominates revenue at ~$6,179, followed by Clothing ($800) and Food ($740). By region, North leads with $3,427 in revenue across 6 transactions.

**Part 2 – Diagnostic Analytics:** The drill-down shows North's revenue is driven almost entirely by Electronics ($3,050). The pivot confirms South is the most balanced region across categories. Monthly trends show a dip in February ($1,610) sandwiched between stronger January ($2,984) and March ($3,125). Credit card transactions average $685 each — over 5× the average cash transaction ($128).

**Part 3 – Window Functions:** Alice is the top spender at $3,112.47, followed by Grace ($1,659) and Heidi ($800). Running totals show Alice's spending trajectory across 4 transactions. Ntile quartiles split the 20 transactions evenly, with the top quartile all being Electronics purchases ($450+). Region-level rankings show Alice holds #1 in North, Grace in East, Eve in South, and Heidi in West.

**Part 4 – Feature Engineering:** Time features extracted include hour, day of week, month, and a weekend flag. RFM scoring ranks Alice as the clear leader (rfm_total = 13) with a recency of just 5 days, 4 purchases, and $3,112 in spend.

**Part 5 – Customer Segmentation:** Alice is the sole Champion. Seven customers (David, Heidi, Grace, Ivan, Bob, Frank, Eve) fall into the Loyal tier. Charlie is classified as Potential. No customers fell into the "At Risk" category — indicating healthy engagement across the board.

**Part 6 – Anomaly Detection:** With a 2σ threshold (above $1,380.71), 2 anomalies were flagged: Alice's T001 ($1,799.98, z=2.84) and Grace's T017 ($1,560.00, z=2.36) — both high-value Electronics purchases.

**Part 7 – Parquet Output:** All 20 enriched rows (including z-scores and anomaly flags) were written to Parquet and verified by reading them back.

---

## Hands-On Exercises

**Exercise 1 — Revenue Per Unit:** Electronics is the most expensive category in every region, ranging from $320/unit (South) to $716.66/unit (North).

**Exercise 2 — Credit Card vs Cash:** Credit card transactions average $684.77, which is 5.3x higher than cash at $128.25. High-value electronics purchases are almost always paid by credit card.

**Exercise 3 — Lag (Previous Purchase):** Grace had the biggest jump between purchases — from $99 (Food) to $1,560 (Electronics), a +$1,461 change. David had the biggest drop: $450 down to $17.

**Exercise 4 — High Quantity Flag:** Cash has the highest rate of bulk purchases (50% of cash transactions are quantity > 3), credit card is at 11.1%, and debit card has zero bulk buys.

**Exercise 5 — Adjusted Thresholds:** Lowering the cutoffs from 10/7/5 to 9/6/4 promoted 3 customers (David, Heidi, Grace) from Loyal to Champions, and Charlie moved from Potential to Loyal. No one remained in At Risk or Potential.

**Exercise 6 — 1.5σ vs 2σ:** With this dataset, lowering to 1.5σ didn't flag any additional anomalies — the next-highest z-score (Alice's T020 at 1.235) is still below the 1.5 threshold. The same 2 transactions (T001 and T017) are flagged at both levels.

**Exercise 7 — Region Health Score:** North ranks #1 with a perfect 1.0 score (highest revenue, highest avg order, and tied for most transactions). East is #2 (0.424), South #3 (0.200), and West #4 (0.147).