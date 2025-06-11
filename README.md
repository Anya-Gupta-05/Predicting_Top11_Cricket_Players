# 🏏 Cricket Player Performance Prediction using LSTM (India T20I)

## 📁 Project Overview

This project aims to predict the **top 11 performing Indian male cricketers** before a T20 International match using a deep learning model (LSTM). It leverages historical performance data to forecast players likely to perform well, helping selectors, analysts, and fantasy cricket users.

---

## 📦 Dataset Source

- **Primary Source:** [Cricsheet](https://cricsheet.org/) — A structured JSON archive of ball-by-ball cricket data.
- **Dataset Type:** T20 International (T20I)
- **Size:** ~12 MB unzipped

### 🧹 Dataset Processing Steps

1. **Loaded JSON Files**: Parsed each match file containing keys `meta`, `info`, and `innings`.
2. **Filtered Indian Matches**: Extracted only matches where India was one of the teams.
3. **Generated Batting DataFrame**:
   - Extracted player name, runs scored, balls faced, dismissal status, opponent, venue, and date.
   - Flattened nested data into a clean pandas DataFrame.

4. **Removed Female Cricketers**:
   - As the Cricsheet dataset does not include a `gender` column, we manually curated a list of **92 unique Indian players** and filtered out **female players**.
   - Resulted in a finalized list of **Indian male players** from the last 5 years.

5. **Filtered for Recent Years**: Included data only from **2019 onwards**.

---

## 🧠 Model - LSTM (Long Short-Term Memory)

We used an LSTM neural network due to its capability to model time-dependent sequences (like a player’s performance over matches).

### ✅ Features Used
- Runs scored
- Balls faced
- Dismissal status (encoded)
- Match date (converted to ordinal)
- Opponent (encoded)
- Venue (encoded)

### 🛠️ Preprocessing
- One-hot encoding of categorical variables
- Normalization of numerical features
- Sequence padding for time steps
- Splitting into `X_train`, `X_test`, `y_train`, `y_test`

---

## 🏋️ Model Training

- **Model:** Sequential LSTM
- **Epochs:** 80
- **Loss Function:** MSE (Mean Squared Error)
- **Metric:** MAE (Mean Absolute Error)

```plaintext
Final Test MAE: 1.33
