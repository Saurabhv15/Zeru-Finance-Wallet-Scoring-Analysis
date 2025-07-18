# Zeru Finance Credit Score Analysis

This document presents the analysis and insights derived from the wallet credit scoring implementation.

---

## 1. Score Distribution

<img width="519" height="319" alt="image" src="https://github.com/user-attachments/assets/4bbe14d4-6f33-4917-a59d-4df5c8a1713f" />

### Observations:

- Majority of wallets scored between **100-400**, indicating low to moderate creditworthiness.
- **Very few wallets** achieved scores above **700**, suggesting that only a small user segment maintains high repayment and deposit behaviour.
- A small tail of wallets scored close to **1000**, representing the most financially responsible users.

---

## 2. Score Segmentation

### Bar Chart

<img width="429" height="324" alt="image" src="https://github.com/user-attachments/assets/55f902e9-ec31-4390-8418-c16321b631eb" />



### Pie Chart

<img width="281" height="277" alt="image" src="https://github.com/user-attachments/assets/f47a447a-998c-49ea-9538-606f71115cc5" />


### Insights:

- **Low Score (<400):** Largest segment. These wallets have low deposits, low repayment behaviour, and/or liquidation events.
- **Mid Score (400-700):** Moderate segment. Users with some repayment and deposit activity but room for improvement.
- **Top Score (>700):** Smallest segment. Represents wallets with high deposits, high repay-to-borrow ratios, and no liquidation.

---

## 3. Feature Impact Analysis

### Repay to Borrow Ratio
- Strong indicator of repayment behaviour.
- Wallets with ratios >1 repaid more than they borrowed, thus are low-risk.

### Deposit Amount
- Directly proportional to score. Higher deposits indicate more asset inflow, increasing creditworthiness.

### Liquidation Flag
- Presence of liquidation reduces score by a penalty, showing risk-prone behaviour.

---

## 📈 4. Top 10 Wallets by Credit Score

| Wallet | Credit Score |
| --- | --- |
| 0x... | 987.3 |
| 0x... | 954.1 |
| ... | ... |

<img width="314" height="116" alt="image" src="https://github.com/user-attachments/assets/56b23acb-2155-4527-b1d3-4485ed499b85" />


**Insight:**  
These top wallets consistently showed high deposit and repayment behaviour with no liquidation flags.

---

## 5. Business Interpretation

- **High scoring wallets (800-1000):** Ideal candidates for higher credit lines, premium borrowing features, and loyalty rewards.
- **Mid scoring wallets (400-700):** Users who can be targeted with incentive programs to improve their financial behaviour.
- **Low scoring wallets (0-400):** High-risk segment needing stricter collateral checks or borrowing restrictions.

---

## 6. Suggestions for Future Work

1. **Time-based analysis:** Weekly or monthly repayment trends.
2. **Token type weighting:** Different tokens have varying liquidity risks.
3. **Graph-based features:** Cross-wallet transactions for fraud or collusion detection.
4. **Machine learning models:** Predict credit default using engineered features as input.

---

## Conclusion

This analysis demonstrates that even with basic transaction-level features, it is possible to derive meaningful credit scores for DeFi wallets, which can be further enhanced with temporal, token-based, and graph features for production-level risk management systems.
