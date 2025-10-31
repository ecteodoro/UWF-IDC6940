# Predicting Blossom Date of Cherry Tree With Support Vector Machine and Recurrent Neural Network

Authors: Hongyi Zheng, Yanyu Chen, Zihan Zhang
Source: arXiv preprint (2022)
Link: https://arxiv.org/pdf/2210.04406

**Summary**

This study proposes a machine-learning approach to predict the blossom date of cherry trees, framing the problem as a multi-class classification task. Two algorithms were tested: a Support Vector Classifier (SVC) and a Long Short-Term Memory (LSTM) recurrent neural network. The models used sequential daily temperature data (average, max, min) from Kyoto, Japan, and Washington, D.C., to predict the number of days remaining until bloom. The goal was to generate precise bloom-date forecasts useful for tourism, environmental monitoring, and cultural planning.

**Problems the Article Is Addressing**

- Traditional phenology models typically forecast bloom windows, not exact dates.
- Machine-learning methods (especially sequential ones like LSTM) are underused in phenology prediction.
- Accurate, data-driven forecasts can support tourism, allergy warnings, and ecological management.
- Despite abundant temperature data, few models leverage time-sequential features effectively.

**How It Has Been Solved**

- Bloom-date prediction was reformulated as a multi-class classification problem, where each class represents the number of days until bloom.
- Two ML approaches were compared:
- Support Vector Classifier (SVC): Used a one-vs-one strategy with RBF kernel; class imbalance handled via weighting and oversampling.
- LSTM Recurrent Neural Network: Many-to-one architecture trained on 10-day temperature sequences to predict bloom-day class.
- Models were evaluated with accuracy, precision, recall, and F1-score, and input variations were tested (raw sequences vs. statistical summaries).

**Datasets**

- Phenological Data:
- Kyoto, Japan: Historical full-flowering records (1881–present).
- Washington, D.C.: Tidal Basin bloom records (1921–2016).
- Weather Data:
- Kyoto: Japan Meteorological Agency daily temperature records.
- Washington, D.C.: NOAA/EPA daily weather datasets (average, max, min, humidity, precipitation).
- Features: Daily temperature sequences; label = days remaining to bloom.
- Preprocessing: Cleaned missing values, normalized sequences, balanced class distribution.

**Results**

- SVC Performance:
- Achieved ~97.9% accuracy using 10-day sequences.
- Weighted SVC improved precision from 0.435 → 0.998, though recall declined.
- Simpler statistical features reduced accuracy drastically.
- LSTM Performance:
- Lower precision (~19.9%), recall (~13.9%), and F1 (~14.4%).
- Still produced usable forecasts (within ±1 day) for practical bloom planning.
- Comparison:
- SVC unexpectedly outperformed LSTM, likely due to the small dataset and limited variability.
- Authors note possible overfitting given the high SVC accuracy on a small dataset.

**Limitations**

- Data Imbalance: Most samples clustered around specific bloom dates, biasing the classifier.
- Limited Features: Only temperature used; no photoperiod, soil, or precipitation variables.
- Overfitting Risk: Extremely high SVC accuracy may not generalize to unseen years or other regions.
- Small Dataset: Restricted data volume limits the effectiveness of LSTM models.
- Cross-location Differences: Kyoto and D.C. differ climatically; incomplete weather data affects comparability.
- Forecasting Horizon: Real-time forecasting remains untested for operational use.

**Conclusion**

The paper demonstrates that machine learning—especially SVMs and RNNs—can be applied to cherry blossom phenology prediction using sequential temperature data. While the SVC achieved high apparent accuracy, the limited data and imbalance raise doubts about generalization. The LSTM showed weaker performance but confirms the feasibility of sequential modeling. The study highlights the potential of AI-based phenology forecasting, emphasizing the need for larger, balanced datasets and richer environmental features in future research.