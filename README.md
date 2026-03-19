Triangular Arbitrage Analysis - Treasury Department
Project Overview
This project analyzes foreign exchange (FX) market data to identify and evaluate triangular arbitrage opportunities. Triangular arbitrage is a risk-free trading strategy that exploits temporary currency exchange rate mispricing.
Project Objective: Determine if a profitable arbitrage opportunity exists using three currency pairs (USD/PKR, EUR/USD, EUR/PKR) with an initial capital of USD 1,000,000.

Problem Statement
As a junior analyst in the Treasury Department, you have identified potential mispricing between three currency pairs in the interbank market:
Currency PairExchange RateUSD/PKR280.50EUR/USD1.0850EUR/PKR307.20
Task: Determine all possible trading paths, calculate profits/losses, and recommend the optimal strategy to the FX trader.

Files Included
1. arbitrage_code_clean.py ⭐
Main Python script that performs the triangular arbitrage analysis.

Tests all possible trading paths
Calculates final amounts and profits
Identifies the most profitable opportunity
Lines of Code: 32 (clean, minimal)
Execution
bashpython arbitrage_code_clean.py
Expected Output
Exchange Rates: USD/PKR = 280.5 | EUR/USD = 1.085 | EUR/PKR = 307.2
Initial Capital: USD 1000000

================================================================================

Quoted EUR/PKR: 307.2
Implied EUR/PKR: 304.34
Mispricing: 2.86

================================================================================

Testing all triangular paths:

Path 1: USD → EUR → PKR → USD
  Final Amount: $1,009,389.09
  Profit: $9,389.09 (0.9389%)

Path 2: USD → PKR → EUR → USD
  Final Amount: $990,698.24
  Profit: $-9,301.76 (-0.9302%)

================================================================================

✓ ARBITRAGE OPPORTUNITY FOUND
  Best Path: USD → EUR → PKR → USD
  Final Amount: $1,009,389.09
  Profit: $9,389.09
  Return: 0.9389%

Analysis Results
Mispricing Detection

Quoted EUR/PKR: 307.20
Implied EUR/PKR: 304.34 (calculated from USD/PKR × EUR/USD)
Difference: 2.86 rupees (0.94% overpriced)

Conclusion: EUR/PKR is overpriced relative to its cross-rate, creating an arbitrage opportunity.
Profitable Trading Path
Path 1: USD → EUR → PKR → USD ✓
StepCurrencyAmountCalculation0USD1,000,000.00Starting capital1EUR921,658.991,000,000 ÷ 1.08502PKR283,133,640.55921,658.99 × 307.203USD1,009,389.09283,133,640.55 ÷ 280.50
Profit: USD 9,389.09
Return: 0.9389%
Unprofitable Path
Path 2: USD → PKR → EUR → USD ✗

Final Amount: USD 990,698.24
Loss: USD 9,301.76
Return: -0.9302%


Code Logic
Section 1: Define Exchange Rates
pythonUSD_PKR = 280.50
EUR_USD = 1.0850
EUR_PKR = 307.20
initial_capital = 1_000_000
Section 2: Detect Mispricing
pythonimplied_eur_pkr = USD_PKR * EUR_USD
# Check if quoted rate differs from implied rate
Section 3: Test Path 1 (USD → EUR → PKR → USD)
pythonamount = amount / EUR_USD      # Convert USD to EUR (divide)
amount = amount * EUR_PKR      # Convert EUR to PKR (multiply)
amount = amount / USD_PKR      # Convert PKR to USD (divide)
profit_1 = amount - initial_capital
Section 4: Test Path 2 (USD → PKR → EUR → USD)
pythonamount = amount * USD_PKR      # Convert USD to PKR (multiply)
amount = amount / EUR_PKR      # Convert PKR to EUR (divide)
amount = amount * EUR_USD      # Convert EUR to USD (multiply)
profit_2 = amount - initial_capital
Section 5: Compare & Recommend
pythonbest = max(results, key=lambda x: x[2])
# Select path with maximum profit

Key Concepts
Exchange Rate Conversion Rules
When converting TO a currency:

Multiply if the currency is in the numerator of the rate
Divide if the currency is in the denominator of the rate

Example:

To convert USD → EUR using EUR/USD = 1.0850: EUR = USD ÷ 1.0850
To convert EUR → PKR using EUR/PKR = 307.20: PKR = EUR × 307.20

Cross-Rate Parity
In efficient markets:
EUR/PKR = USD/PKR × EUR/USD
307.20 ≠ 280.50 × 1.0850 = 304.34
The inequality indicates mispricing → Arbitrage opportunity exists.
Profit Calculation
Profit = Final Amount - Initial Amount
Profit % = (Profit / Initial Amount) × 100

Recommendations & Risks
Why Execute This Trade?

✓ Risk-free in theory (no directional bet)
✓ Guaranteed profit if rates hold
✓ 9,389 USD profit on 1 million capital

Important Considerations

Bid-Ask Spreads

Quoted rates are midpoints; actual trading involves wider spreads
Typical spreads: 0.0005-0.002 on major pairs
Impact: Reduces profit by 30-50%


Transaction Costs

Bank fees and commissions: 0.01-0.05% per trade leg
Impact: Additional USD 3,000-5,000 reduction


Execution Risk

All three trades must execute simultaneously
Any delay could close the arbitrage window
PKR market may have limited liquidity


Market Impact

USD 1M may move prices, especially in PKR
May require phased execution at worse prices


Net Profit After Costs

Gross: USD 9,389
After spreads: USD 4,500-6,500
After commissions: USD 1,500-3,500
Marginal but still profitable
