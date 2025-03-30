# 📈 Bitcoin Volatility Analysis using Student-t and GARCH Models

This project explores the volatility of Bitcoin log returns using:
- Static distributional fits (Normal and Student-t)
- A dynamic volatility model: **GARCH(1,1)** with **Student-t errors**

The goal is to understand whether modeling volatility dynamics significantly improves model fit and statistical realism.

---

## 🎯 Objectives

- Fit Bitcoin returns using:
  - A **Normal distribution**
  - A **Student-t distribution**
  - A **GARCH(1,1)** model with Student-t innovations
- Use statistical tests to compare these models.
- Diagnose the quality of the fitted model using standardized residuals, ACF, and the Ljung–Box test.
- Detect and model **volatility clustering** and **heavy tails**.

---

## ⚙️ Methodology

- **Data**: BTC/USD prices converted to log returns
- **Models**:
  1. Static **Normal** fit: `scipy.stats.norm.fit(...)`
  2. Static **Student-t** fit: `scipy.stats.t.fit(...)`
  3. **GARCH(1,1) + Student-t**: `arch_model(..., dist='t')`

- **Evaluation Metrics**:
  - **Log-likelihood**
  - **Likelihood Ratio Test**:
    \[
    \Lambda = -2(\log L_{\text{restricted}} - \log L_{\text{unrestricted}}) \sim \chi^2(d)
    \]
  - **Ljung–Box test** on residuals and squared residuals
  - ACF plots for \( r_t \), \( z_t \), and \( z_t^2 \)

---

## 📊 Key Results

- The **static Normal distribution** underestimates Bitcoin’s volatility and fat tails.
- The **Student-t distribution** improves the fit but fails to model volatility changes over time.
- The **GARCH(1,1) with Student-t errors** fits significantly better than both static models
---

## 🛠️ Dependencies

```bash
pip install numpy pandas matplotlib scipy statsmodels arch
