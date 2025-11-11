# CAPM vs Fama-French: Brazilian Stock Market Analysis
### Academic Project - Finance II Course

Comparative analysis of CAPM and Fama-French three-factor models applied to Brazilian stock market sectors (B3).

## Project Overview

This project compares the explanatory power of two foundational asset pricing models:

**CAPM (Capital Asset Pricing Model):** A single-factor model based on market risk
**Fama-French Three-Factor Model:** A multi-factor model that adds size (SMB) and value (HML) risk premiums

**Analysis Period:** June 1, 2020 - June 30, 2025 (5 years of daily data)

## Sectors Analyzed

| Sector | Characteristics | Tickers |
| :--- | :--- | :--- |
| **Retail (Cyclical)** | High sensitivity to economic cycles, consumer-driven | MGLU3, LREN3, BHIA3 |
| **Banking (Defensive)** | Lower volatility, predictable cash flows, resilient profits | ITSA4, BBAS3, BBDC4 |
| **Electric Utilities (Stable)**| Regulated sector, predictable revenues, low systematic risk | ELET3, CMIG4, TAEE11 |

## Objectives

* Build equal-weighted portfolios for each sector.
* Run OLS regressions for both CAPM and Fama-French models.
* Compare the **R²** (explanatory power), **alphas** (abnormal returns), and **betas** (factor sensitivities) across models and sectors.
* Evaluate which model better explains the returns for each sector.

## Project Structure

├── codigofin2.ipynb # Main analysis notebook (Portuguese comments) 
├── nefin_factors.csv # Fama-French factors (Requires download) 
├── requirements.txt # Python dependencies 
└── README.md # This file

## How to Run

1.  **Clone the repository**
    ```bash
    git clone [https://github.com/JAssalis/capm-fama-french-brazil.git](https://github.com/JAssalis/capm-fama-french-brazil.git)
    cd capm-fama-french-brazil
    ```

2.  **Install dependencies**
    (It's recommended to use a virtual environment)
    ```bash
    pip install -r requirements.txt
    ```

3.  **Download required data**
    This project requires the Brazilian Fama-French factors from NEFIN.

    * Go to: [NEFIN - Risk Factors](https://nefin.com.br/data/risk_factors.html)
    * Download the `risk_factors.csv` file.
    * Rename it to `nefin_factors.csv`.
    * Place it in the project's root directory (alongside the `.ipynb` file).

4.  **Run the notebook**
    ```bash
    jupyter notebook codigofin2.ipynb
    ```

## Methodology

### 1. Portfolio Construction
Equal-weighted portfolios were created for each sector:
$$R_{portfolio,t} = \frac{1}{N}\sum_{i=1}^{N}R_{i,t}$$

### 2. CAPM Model
The standard single-factor model:
$$R_i - R_f = \alpha + \beta(R_m - R_f) + \varepsilon$$
Where:
* **$\alpha$ (Alpha):** Abnormal return.
* **$\beta$ (Beta):** Market sensitivity.

### 3. Fama-French Three-Factor Model
The multi-factor model adding size and value premiums:
$$R_i - R_f = \alpha + \beta_{Mkt}(R_m - R_f) + \beta_{SMB}(SMB) + \beta_{HML}(HML) + \varepsilon$$
Additional factors:
* **SMB:** Size premium (Small Minus Big).
* **HML:** Value premium (High Minus Low).

### 4. Statistical Analysis
* OLS (Ordinary Least Squares) regression using `statsmodels`.
* Comparison of **R-squared** and **Adjusted R-squared**.
* Analysis of alpha significance (p-values).
* Interpretation of factor betas (p-values).

## Key Results

### Model Comparison (R-squared)

The Fama-French model provided superior explanatory power for all three sectors. The increase in R² shows that SMB and HML are relevant factors for explaining returns in the Brazilian market.

| Sector | R² (CAPM) | R² (Fama-French) | % Improvement |
| :--- | :--- | :--- | :--- |
| **Retail** | 0.298 | 0.380 | +27.5% |
| **Banking** | 0.457 | 0.478 | +4.6% |
| **Utilities** | 0.403 | 0.410 | +1.7% |

*(Results based on the analysis from `codigofin2.ipynb`)*

### Factor Insights

* **Retail Sector:** Showed significant, positive sensitivity to **SMB** (behaving like a small-cap) and significant, negative sensitivity to **HML** (behaving like a growth stock).
* **Banking Sector:** Showed significant, positive sensitivity to **HML** (behaving like a value stock).
* **Utilities Sector:** Also showed significant, positive sensitivity to **HML** (value stock), but no significant exposure to the SMB factor.

## Technologies Used

* **Python 3.11.6**
* **yfinance:** For downloading historical stock data from Yahoo Finance.
* **pandas:** For data manipulation and analysis.
* **numpy:** For numerical operations.
* **statsmodels:** For regression analysis.
* **plotly:** For interactive visualizations.
* **Jupyter Notebook:** For the interactive development environment.

## Academic Context

* **Course:** Finance II
* **Institution:** Universidade de São Paulo - USP
* **Semester:** 4° Semester

*Note: The code and comments in the `.ipynb` file are in Portuguese, as this was developed for a Brazilian university course. The analysis follows standard academic finance methodologies.*

## References

* Fama, E. F., & French, K. R. (1993). Common risk factors in the returns on stocks and bonds. *Journal of Financial Economics, 33(1)*, 3-56.
* Sharpe, W. F. (1964). Capital asset prices: A theory of market equilibrium under conditions of risk. *The Journal of Finance, 19(3)*, 425-442.
* NEFIN - Brazilian Center for Research in Financial Economics: [nefin.com.br](https://nefin.com.br/data/risk_factors.html)

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.

## Author

* **João Vitor Assalis Pedroso**
    * GitHub: `@JAssalis`
    * LinkedIn: `[Your LinkedIn]`

*Disclaimer: This project is for educational purposes only. The analysis and results should not be considered investment advice. Past performance does not guarantee future results.*
