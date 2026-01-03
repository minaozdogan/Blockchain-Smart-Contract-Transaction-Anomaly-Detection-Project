# Blockchain Smart Contract Transaction Anomaly Detection

## Project Overview

This project develops an unsupervised machine learning framework for detecting anomalous smart contract transactions in decentralized finance (DeFi) environments. Using real-world Ethereum blockchain data from the Uniswap V3 USDC/WETH liquidity pool, the study applies Isolation Forest and Autoencoder models to identify transaction behaviors that deviate significantly from learned norms.

The objective is not to label transactions as fraudulent, but to provide a risk-aware screening mechanism that highlights statistically and behaviorally unusual activity for further investigation. The project emphasizes interpretability, robustness, and reproducibility, and demonstrates how blockchain event logs can be transformed into structured datasets suitable for machine learning analysis.

---

## Repository Structure

```
.
├── .vscode/
│   └── settings.json
│
├── data/
│   ├── raw/
│   │   └── uniswap_v3_usdc_weth_raw.csv
│   └── processed/
│       ├── uniswap_v3_usdc_weth_processed.csv
│       ├── feature_names.txt
│       ├── robust_scaler.pkl
│       └── X_scaled.npy
│
├── notebooks/
│   ├── data_collection_preprocessing.ipynb
│   ├── isolation_forest.ipynb
│   ├── autoencoder.ipynb
│   └── visualization_and_comparison.ipynb
│
├── results/
│   ├── isolation_forest_results.csv
│   ├── autoencoder_results.csv
│   ├── fusion_results.csv
│   ├── if_anomaly_clusters.csv
│   └── if_normal_indices.npy
│
├── .env
├── README.md
└── blockchainSmartContractTransactionAnomalyDetectionProjectReport.pdf
```

---

## Data Description

The dataset is constructed from Ethereum event logs associated with the Uniswap V3 USDC/WETH liquidity pool and collected via the Etherscan API. Raw logs include blockchain metadata and encoded event fields, which are not directly suitable for analysis.

A comprehensive preprocessing pipeline decodes Uniswap V3 swap events, converts hexadecimal fields into numerical representations, and extracts transaction-level, execution-related, and financial features. The final processed dataset contains both metadata and economically meaningful variables used for anomaly detection.

---

## Methodology

The project follows a fully unsupervised approach consisting of the following stages:

1. **Preprocessing and Feature Engineering**
   - Hexadecimal decoding of blockchain fields
   - Extraction of swap-specific parameters
   - Robust scaling to handle heavy-tailed distributions

2. **Isolation Forest**
   - Tree-based unsupervised anomaly detection
   - Produces binary anomaly labels and continuous anomaly scores
   - Used as the primary detection method

3. **PCA Visualization**
   - Applied post-hoc for interpretability
   - Provides low-dimensional visualization of anomaly separation

4. **Autoencoder**
   - Reconstruction-based anomaly detection
   - Trained exclusively on transactions classified as normal
   - Produces reconstruction error–based anomaly scores

5. **Fusion-Based Risk Assessment**
   - Combines Isolation Forest and Autoencoder outputs
   - Identifies high-confidence anomalies through model agreement

6. **Behavioral Analysis**
   - Liquidity patterns
   - Repeated sender activity
   - Transaction size extremes
   - Temporal regularity of high-risk transactions

---

## Notebooks

- `data_collection_preprocessing.ipynb`  
  Data collection from Etherscan, decoding of event logs, feature construction, and dataset preparation.

- `isolation_forest.ipynb`  
  Isolation Forest training, anomaly scoring, labeling, and initial analysis.

- `autoencoder.ipynb`  
  Autoencoder model training, reconstruction error computation, and anomaly labeling.

- `visualization_and_comparison.ipynb`  
  PCA visualization, anomaly score comparison, fusion score construction, and behavioral analysis plots.

---

## Results

Intermediate and final results are stored in the `results/` directory, including model-specific anomaly scores and labels, fusion-based risk scores, and supporting exports used in the report and figures.

---

## Reproducibility

- Numerical features are scaled using a persisted `RobustScaler`.
- Feature ordering is preserved via `feature_names.txt`.
- Scaled feature matrices are saved for consistent model input.
- Random seeds are fixed where applicable.

To reproduce the full pipeline, run the notebooks in the order listed above.

---

## Final Report

A detailed explanation of the dataset, methodology, results, and implications is provided in:

```
blockchainSmartContractTransactionAnomalyDetectionProjectReport.pdf
```

---

## Disclaimer

This project does not label transactions as fraudulent or malicious. Detected anomalies represent deviations from learned normal behavior and should be interpreted as signals for further investigation rather than definitive classifications.

---

## Authors

- Ayça Görgülü  
- Duru Yıldırım  
- Mina Özdoğan  

---

## Repository Link

https://github.com/minaozdogan/Blockchain-Smart-Contract-Transaction-Anomaly-Detection-Project
