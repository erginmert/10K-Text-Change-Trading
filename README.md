# 📄 10-K Text Change Trading Strategy

This repository implements a systematic trading strategy based on textual differences in annual 10-K filings, inspired by *Cohen et al. (2020), "Lazy Prices."*  

The central hypothesis is that markets underreact to incremental disclosure changes in SEC filings. By measuring year-over-year textual shifts, we extract predictive signals for future stock returns.

---

## 💡 Idea

- Investors are often slow to react to subtle textual changes in corporate disclosures.  
- Comparing consecutive 10-K filings highlights changes in risk factors, tone, and emphasis.  
- These changes may serve as forward-looking signals that can be systematically traded.  

---

## 🛠️ Methodology

1. **Data Collection**  
   - Preprocessed 10-K filings from the [SRAF 10-X Parse Data](https://sraf.nd.edu/data/stage-one-10-x-parse-data/) project.  
   - Standardized text is provided, enabling efficient cross-year comparison.

2. **Change Detection**  
   - Text similarity between consecutive filings is measured using:  
     - **Cosine Similarity** → captures directional changes in text embeddings.  
     - **Jaccard Similarity** → highlights word-level additions/removals.

3. **Signal Construction**  
   - Similarity scores are converted into change signals.  
   - Larger textual changes (low similarity) are hypothesized to convey stronger informational content.

4. **Backtesting**  
   - Firms are sorted into quintiles based on signal magnitude.  
   - Long-short portfolios are formed (long: largest changes, short: smallest changes).  
   - Returns are tracked for 6 months following each filing.

---

## 📊 Results

- **Cosine Similarity Strategy**  
  - Produces statistically significant cumulative excess returns over 6 months.  
  - Suggests this metric captures meaningful disclosure shifts.  

- **Jaccard Similarity Strategy**  
  - Positive but weaker results compared to cosine similarity.  
  - Indicates that cosine similarity is more effective in capturing nuanced changes.

---

## ⚠️ Limitations

- Current analysis evaluates only **excess returns relative to the risk-free rate**.  
- No adjustment yet for systematic risk (market beta or factor exposures).  
- Next steps:  
  - Estimate alphas using **CAPM** and **Fama-French models**.  
  - Incorporate transaction costs and liquidity constraints.  
  - Explore alternative holding horizons.  

---

## 🚀 Getting Started

### Prerequisites
- Python 3.9+  
- Common data science libraries (`pandas`, `numpy`, `scikit-learn`, `matplotlib`)  

### Installation
Clone this repository and install dependencies:
```bash
git clone https://github.com/your-username/10k-text-change-strategy.git
cd 10k-text-change-strategy
pip install -r requirements.txt

