# 10-K Text Change Trading Strategy

This project implements a systematic trading strategy based on textual differences in annual 10-K filings, inspired by the methodology of *Cohen et al. (2002), "Lazy Prices."* The core idea is to identify how changes in a firm's disclosures may carry predictive signals for stock returns, due to delayed price reactions by the market.

## 💡 Idea

Markets underreact to subtle textual changes in SEC 10-K filings. By measuring these differences year-over-year, we aim to extract signals that forecast future returns.

## 🛠️ Methodology

- **Data Collection**: Preprocessed 10-K filings can be downloaded from https://sraf.nd.edu/data/stage-one-10-x-parse-data/
- **Change Detection**: Use cosine and jaccard similarity to detect meaningful textual shifts
- **Signal Construction**: Quantify the signal as changes in disclosures year-over-year
- **Testing**: Evaluate long-short strategies based on signal quintiles

## 📊 Results

- Strategy based on cosine similarity signal shows a cumulative excess return over 6 months after filings
- Strategy based on Jaccard similarity signals shows similar but less pronounced returns

## ⚠️ Limitations 

- The strategy currently evaluates excess returns relative to the risk-free rate only (i.e., raw stock return minus risk-free rate).
- A proper alpha estimation should incorporate market risk exposure (Beta) using factor models such as CAPM or Fama-French for more reliable inference.


# 10K-Text-Change-Trading
