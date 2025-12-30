# Blockchain Smart Contract Transaction Anomaly Detection

## Project Overview
This project presents an **unsupervised anomaly detection framework** for identifying abnormal smart contract transactions in decentralized finance (DeFi). Using real-world transaction data from the **Uniswap V3 USDC/WETH liquidity pool**, we combine **Isolation Forest** and **Autoencoder** models into a unified **Fusion Score** to detect high-risk transactions.

The system focuses on **behavioral risk detection** rather than explicit fraud labeling and emphasizes interpretability and practical relevance for FinTech monitoring applications.

---

## Motivation
- DeFi platforms process extremely high volumes of on-chain transactions  
- Labeled fraud data is scarce or unavailable  
- Manual monitoring is infeasible at scale  
- Automated and bot-driven activity can introduce financial and operational risk  

These challenges motivate the use of **unsupervised learning techniques** to identify unusual transaction behavior without relying on predefined fraud labels.

---

## Dataset
- **Source:** Ethereum blockchain (Uniswap V3 USDC/WETH pool)  
- **Collection Method:** Etherscan API  
- **Size:** 1,000 decoded smart contract transactions  
- **Features Include:**
  - Transaction-level attributes  
  - Swap-related token amounts  
  - Liquidity and execution-related metrics  

All features were numerically processed and scaled for model compatibility.

---

## Methodology

### Models Used
- **Isolation Forest**
  - Detects anomalies by isolating rare observations  
- **Autoencoder**
  - Detects anomalies using reconstruction error  

### Fusion Strategy
- Outputs from both models are combined into a **Fusion Score**
- The Fusion Score represents a unified transaction risk metric used to rank transactions by abnormality
- This ensemble approach improves robustness compared to single-model detection

### Thresholding
- A **quantile-based threshold** is applied to the Fusion Score distribution  
- The threshold is selected to match a target anomaly rate derived from ensemble behavior  
- Transactions exceeding the threshold are classified as **high-risk anomalies**

---

## Results & Key Findings
- Most transactions exhibit **low Fusion Scores**, indicating normal behavior  
- A small subset of transactions consistently shows **high-risk scores**  
- Behavioral analysis of anomalous transactions reveals:
  - Repeated sender addresses  
  - Extremely large token transfer amounts  
  - Predictable hourly execution patterns  
- High-risk activity appears **even under high-liquidity conditions**, suggesting anomalies are driven by **automated or strategic behavior** rather than market instability

---

## Important Note
Detected anomalies are **not labeled as fraud**.  
The system highlights transactions that deviate significantly from normal patterns and are intended to support **risk analysis and further investigation**, rather than definitive fraud classification.

---

## Environment & Execution
The project was developed and executed using **Python** in **Visual Studio Code**.  
All scripts and analysis files can be run directly within the repository after installing the required dependencies.

---

## Authors
- Mina Özdoğan  
- Ayça Görgülü  
- Duru Yıldırım  
