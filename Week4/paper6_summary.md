# Hybrid Phenology Modeling for Predicting Temperature Effects on Tree Dormancy

Authors: Ron van Bree, Diego Marcos, Ioannis N. Athanasiadis

Source: arXiv pre-print (Jan 2025) — full PDF: https://arxiv.org/pdf/2501.16848￼  ￼

**Summary**

This study presents a hybrid phenology modelling framework that combines mechanistic (biophysical) models of tree dormancy and flowering with a machine-learning (neural network) component to improve the prediction of bloom dates for cherry and other fruit trees across multiple regions (Japan, South Korea, Switzerland). The hybrid model replaces the chilling (endodormancy release) response function in typical phenology models with a learnable multilayer perceptron (MLP) while preserving the forcing (warm-temperature) accumulation structure. It consistently outperforms both standard biophysical models and purely data-driven neural models in terms of mean absolute error (MAE) for bloom date predictions across years and locations.  ￼

**Problems the Article is Addressing**

- Traditional biophysical phenology models vary structurally (different chilling/forcing formulations) and require per-site or per-variety parameter tuning, limiting their generalisation under changing climatic conditions.  ￼
- Pure machine-learning models (neural networks, CNNs, LSTMs) can fit bloom-date data but often lack interpretability and may fail to generalise, especially when data are limited.  ￼
- The challenge of modelling bloom dates across different cultivars, climate zones, and under climate change demands a method that is both accurate and transferable.

**How It Has Been Solved**

- The authors formalised bloom-date prediction (day-of-year) as a regression task on hourly/daily temperature sequences.  ￼
- They adopted a hybrid architecture:
- Retain the generic structure of chilling → forcing → bloom from mechanistic models.
- Replace the chilling response (temperature → chilling units) function c(·) with an MLP (two hidden layers, 64 neurons each, ReLU activations) that is trained jointly with the forcing parameters.  ￼
- Model training is done via gradient descent (Adam) using PyTorch, optimising both the MLP and mechanistic parameters.  ￼
- Comparative experiments: hybrid model vs. mechanistic baselines vs. purely data-driven CNN/LSTM baseline, evaluated in three generalisation settings (temporal per location, temporal per variety, spatio-temporal).  ￼

**Datasets**

- Bloom-date records for cherry and other fruit trees across Japan (3317 samples), Switzerland (4780), South Korea (930) for the Prunus × yedoensis cultivar and others.  ￼
- Hourly temperature data from the MERRA-2 reanalysis for the matching years and locations. Seasons defined from October 1 to July 1 (~274 days).  ￼
- Locations filtered to exclude subspecies with only one site; data split into training/test sets under different evaluation scenarios.  ￼

**Results**

- In the temporal generalization per location setting (train/test separated years, same locations):
- Hybrid model MAE: Japan ≈ 2.17 ± 0.03 days; Switzerland ≈ 5.36 ± 0.15 days; South Korea ≈ 4.86 ± 0.06 days.  ￼
- Mechanistic models (e.g., Utah Chill model) had higher MAE: e.g., Japan ≈ 3.07 days; Switzerland ≈7.32 days.  ￼
- In variety-level and spatio-temporal generalisation settings: the hybrid model remained best or among best, showing stronger transferability across sites and cultivars.  ￼
- Visualization of learned chilling response functions indicate the MLP captured plausible temperature response shapes (peak around ~0°C-10°C) though with some variation across initialisations.  ￼

**Limitations**

- Although the hybrid model learns improved predictive functions, the learned MLP chilling‐response functions are not guaranteed biologically realistic; the model may learn “useful” but not interpretable relationships.  ￼
- Data quality and quantity vary by region; in low-data settings (South Korea, Switzerland) performance is degraded relative to Japan.  ￼
- The training data largely represent historic climate ranges; performance under novel climate scenarios (extreme warming) remains uncertain.
- The model still requires bloom-date observations + hourly temperature data; for regions lacking such data, applicability may be limited.
- As with many ML models, risk of overfitting and limited interpretability of the residual (learned) component remains.

**Conclusion**

This paper demonstrates that hybrid modelling, combining mechanistic phenology structures with neural-network learning for the chilling component, can significantly improve bloom-date prediction accuracy and generalisability across cultivars and regions. For forecasting cherry blossom dates under climate change (or across diverse sites), the method offers a strong template — balancing interpretability (through mechanistic structure) and adaptability (through ML). It suggests that future phenology-prediction efforts could benefit from similar hybrid methodologies.
