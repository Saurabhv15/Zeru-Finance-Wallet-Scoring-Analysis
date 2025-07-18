# Zeru Finance Wallet Credit Scoring

## 📌 Problem Statement

The goal of this project is to assign a **credit score** to each wallet address based on its transaction history in the Aave V2 protocol. The score reflects the creditworthiness of a wallet using features like deposits, borrowings, repayments, and liquidation events.

---

## 🛠️ Approach

### 1. **Data Loading**

- Loaded `user_wallet_transaction.json` into a pandas DataFrame using Google Colab.

### 2. **Parsing Transaction Amounts**

- The `actionData` column contained nested data with the transaction amount in wei.
- Parsed the amount and converted it to ether for easier interpretation.

### 3. **Feature Engineering**

Created features for each wallet:

- **Total Deposit Amount**
- **Total Borrow Amount**
- **Total Repay Amount**
- **Repay to Borrow Ratio** (higher indicates better repayment behaviour)
- **Liquidation Flag** (1 if wallet had liquidation, else 0)

### 4. **Scoring Function**

Calculated credit scores using:

\[
\text{Score} = \alpha \times \text{RepayBorrowRatio}_{norm} + \beta \times \text{DepositAmount}_{norm} - \gamma \times \text{LiquidationFlag}
\]

- Normalised each feature
- Weighted and combined them
- Scaled scores to range **0-1000**

Weights:
- α = 0.5
- β = 0.4
- γ = 0.1

### 5. **Output**

Saved the final scores as a JSON file with each wallet's address and its calculated credit score.

---

## Files

| File | Description |
| --- | --- |
| `score_wallets.ipynb` | Colab notebook containing full code |
| `wallet_credit_scores.json` | Final output file with credit scores |
| `analysis.md` | Detailed analysis of score distributions and insights |
| `score_distribution.png` | Distribution plot of credit scores |
| `credit_score_segments.png` | Bar chart of score segments |
| `credit_score_segments_pie.png` | Pie chart of score segments |

---

## How to Run

1. Upload `user_wallet_transaction.json` to your Google Drive.
2. Open `score_wallets.ipynb` in Google Colab.
3. Update the file path in the notebook to your Drive location.
4. Run all cells sequentially.
5. Final output `wallet_credit_scores.json` will be saved in your Drive.

---

## Output Format

Each record in the output JSON:

```json
{
  "userWallet": "0x0000000000e189dd664b9ab08a33c4839953852c",
  "credit_score": 432.5
}
```

---

## Author

**Saurabh Verma**  
B.Tech IT, Rajkiya Engineering College Ambedkar Nagar  
July 2025

---

## Future Work

- Incorporate temporal features (weekly/monthly trends)
- Use ML models to predict default risk based on engineered features
- Extend scoring to include cross-wallet network analysis
