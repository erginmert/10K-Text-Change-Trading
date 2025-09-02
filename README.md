# 📄 10-K Text Change Trading Strategy

This project develops and tests a systematic trading strategy that exploits textual changes in annual SEC 10-K filings. The approach is motivated by *Cohen et al. (2020), “Lazy Prices”*, which shows that markets often underreact to incremental changes in corporate disclosures. The central premise is that careful analysis of year-over-year language shifts in these filings can reveal information not immediately incorporated into stock prices, creating opportunities for excess returns.

---

## 💡 Core Idea

Financial markets tend to be slow in fully incorporating subtle textual changes from firms’ regulatory disclosures. By comparing successive 10-K filings for the same company, this project measures how much the language and emphasis in disclosures change. These measured differences are used to construct predictive signals for stock returns, under the hypothesis that investors’ delayed reactions to new information create exploitable trading opportunities.

---

## 🛠️ Methodology

### 1. Data Collection
- Annual 10-K filings are sourced from the preprocessed dataset available at [SRAF 10-X Parse Data](https://sraf.nd.edu/data/stage-one-10-x-parse-data/).  
- The dataset provides standardized and parsed filings, making systematic comparison across years possible.

### 2. Change Detection
- Textual similarity between consecutive filings is computed.  
- Two similarity measures are used:  
  - **Cosine Similarity** → captures directional changes in text representation.  
  - **Jaccard Similarity** → highlights word-level overlap and unique additions/removals.

### 3. Signal Construction
- Similarity scores are transformed into year-over-year change signals.  
- Firms with **low similarity** (larger textual changes) are expected to contain stronger new information.  

### 4. Backtesting
- Firms are sorted into quintiles based on signal magnitude.  
- A **long-short strategy** is constructed (long: lowest similarity quintile, short: highest similarity quintile).  
- Portfolio performance is tracked over fixed post-filing horizons (e.g., 6 months).  

---

## 📊 Results

- **Cosine Similarity**  
  - Produces significant cumulative excess returns in the 6 months following filing dates.  
  - Indicates this metric captures meaningful disclosure shifts.  

- **Jaccard Similarity**  
  - Returns are positive but less pronounced compared to cosine similarity.  
  - Suggests cosine similarity is more effective for this application.  

---

## ⚠️ Limitations and Next Steps

- Current testing only evaluates **excess returns relative to the risk-free rate**.  
- A proper alpha estimation requires adjusting for systematic risk factors, e.g.:  
  - **CAPM** (market beta adjustment)  
  - **Fama-French 3- and 5-Factor Models** (size, value, profitability, investment effects).  

### Future Work
- Incorporate factor models for alpha estimation.  
- Account for transaction costs and liquidity constraints.  
- Explore alternative holding periods and portfolio formation strategies.  

---

## 📚 Reference

Cohen, Lauren, Christopher Malloy, and Quoc Nguyen. *"Lazy Prices."* Journal of Finance 75, no. 3 (2020): 1371–1415.  


