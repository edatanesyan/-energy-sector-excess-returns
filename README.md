# Energy Sector Excess Returns: Explanation and Prediction

Edouard Atanesyan

Originally completed for BUFN640 (Financial Data Analytics), University of Maryland, Robert H. Smith School of Business, Fall 2026. Shared with the instructor's permission.

## Question

What explains the excess returns of the U.S. Energy sector, and can they be predicted?

Energy was chosen because, of the ten Ken French industry portfolios, it is among the least explained by standard factors (CAPM R² of 0.38) and the sector where macroeconomic variables add the most explanatory power.

## Data

- Monthly returns on the 10 Industry Portfolios, the Fama-French 5 factors and the momentum factor (Ken French Data Library)
- Nine macroeconomic series from FRED: CPI, industrial production, unemployment, WTI oil price, 10-year Treasury yield, 3-month T-bill, fed funds rate, and Baa and Aaa corporate yields
- Sample: July 1963 to August 2026 (758 months, 62 full years)

## Method

1. Start from CAPM, then the factor model (Fama-French 5 plus momentum), then all 14 financial and macro variables
2. Remove variables using t-tests and joint F-tests; check that each remaining sign has an economic explanation, and test stability on a pre-2020 sample
3. Test the regression assumptions with Durbin-Watson, Breusch-Godfrey, White's test and Jarque-Bera, then re-estimate with robust (HAC) standard errors
4. Repeat at the annual frequency
5. Build predictive regressions for next-month and next-year returns using only information available at the time, and produce forecasts

## Results

| Model | Monthly adj. R² | Annual adj. R² |
|---|---|---|
| CAPM | 0.38 (R²) | 0.17 |
| Factors | 0.46 (R²) | 0.36 |
| Final model | 0.49 | 0.67 |

- Final monthly model: market, value (HML), profitability (RMW), investment (CMA) and oil price growth. A 10% rise in oil prices is associated with Energy excess returns about 1.3% higher in the same month.
- Final annual model: market, HML, RMW, oil, change in the fed funds rate and change in the default spread. The oil coefficient is larger annually (0.24) than monthly (0.13).
- Prediction: the Energy book-to-market ratio (positive) and the 3-month T-bill rate (negative) are the only useful predictors. Predictability is low: R² of 0.8% monthly and 8% annually.
- Forecasts at the end of the data (August 2026): 0.63% excess return for September 2026 and 6.9% over the next 12 months, both slightly below the historical averages (0.69% and 7.8%).

The forecasts reflect data through August 2026 and are a course exercise, not investment advice.

## How to run

```
pip install -r requirements.txt
jupyter notebook energy_sector_excess_returns.ipynb
```

Data is downloaded at run time from the Ken French Data Library and FRED through pandas-datareader, so results on a later run will include newer months.
