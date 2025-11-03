# A Simpler Way to Predict Flowering and Full Bloom Dates of Cherry Blossoms by Self-Organizing Maps

**Authors**: Shin Nagai, Hiroshi Morimoto, Taku M. Saitoh

**Source**: Ecological Informatics, Volume 56 (2020), 101040

**Link**: https://doi.org/10.1016/j.ecoinf.2019.101040￼

**Summary**

This study presents a machine-learning approach using bidirectional Self-Organizing Maps (SOMs) to estimate the flowering and full bloom dates of Yoshino cherry trees (Cerasus × yedoensis) across Japan. Traditional process-based phenology models require detailed parameterization of chilling and thermal accumulation, which limits their usability for poorly studied species. In contrast, the SOM-based method relies only on temperature data and long-term bloom records to capture complex patterns between seasonal temperature profiles and observed bloom dates. The model achieved mean absolute errors (MAEs) of approximately 2.8–4.5 days, demonstrating comparable performance to established process-based models but with a simpler implementation.

**Problems the Article Is Addressing**

- Complexity of process-based phenology models: Conventional models demand detailed physiological knowledge (e.g., chilling and forcing thresholds) and large parameter sets, which are unavailable for many species.
- Limited generalizability: Parameters calibrated for one site or time period often fail under different climate conditions.
- Need for scalable, data-driven methods: A lightweight model capable of estimating bloom phenology across regions without intensive biological calibration is needed to assess climate-change impacts on flowering events.

**How It Has Been Solved**

- The authors applied a bidirectional SOM, a type of unsupervised neural-network algorithm that clusters multidimensional input data into a 2D lattice while maintaining topological relationships.
- The model was trained with daily mean temperature data as input vectors and observed bloom dates as output (teacher signals).
- Two configurations were tested:
	1.	Case 1: Temperature data from the endodormancy and thermal-accumulation periods (November–March).
	2.	Case 2: Temperature data during periods correlated with bloom dates (mostly February–April).
- Training used 36 years of data (1953–2018) and testing used the remaining 30 years. Each configuration was repeated ten times to compute average MAE.
- Implementation was done in R 3.13, allowing flexible statistical evaluation and replication.

**Datasets**

- Phenological Data:
  - Flowering (≥ 4 flowers open) and full bloom (≥ 80% open) dates from 1953–2018, published by the Japan Meteorological Agency (JMA).
  - Coverage: 42 sites for flowering and 37 sites for full bloom across Japan.
- Meteorological Data:
  - Daily and 10-day mean temperatures from JMA’s AMeDAS network, matched to the same observation sites.
- Data Preprocessing:
  - Conversion to day-of-year format; normalization and partitioning into training/testing subsets.
  - Cases 1 and 2 used varying start (Dstart) and end (Dend) periods to test correlations.

**Results**

- Prediction Accuracy:
  - MAE (Case 1): 3.03–5.17 days for flowering; 3.12–5.00 days for full bloom.
  - MAE (Case 2): 2.78–4.33 days for flowering; 2.77–4.76 days for full bloom.
  - Average MAE: 3–4 days, comparable to prior models (RMSE ≈ 2.8 days – Aono & Moriya, 2003).
- Performance: Case 2 yielded slightly better accuracy than Case 1 in most regions.
- Regional Pattern: Bloom timing followed the expected northward gradient—from late March (Kyushu) to early May (Hokkaido).
- Lead-Time Prediction: The SOM could forecast bloom events up to 10–20 days before actual flowering, useful for cultural and tourism scheduling.
- Computational Efficiency: SOM avoided explicit dormancy-process parameterization, reducing computational cost while maintaining predictive quality.

**Limitations**

- Forecast Horizon: Accuracy dropped significantly when predictions were made more than 20 days before bloom.
- Environmental Simplification: Only temperature data were used; other influencing factors (photoperiod, precipitation, soil moisture, or local topography) were ignored.
- Regional Variability: Larger errors occurred in regions with high interannual variability in bloom timing (e.g., coastal and southern sites).
- Model Transferability: Although simpler, the SOM model’s performance under future climate scenarios remains untested.
- Potential Under-representation: Some stations lacked full temperature coverage, leading to gaps in validation.

**Conclusion**

The study demonstrates that Self-Organizing Maps (SOMs) offer a simple yet effective machine-learning alternative for predicting cherry-blossom phenology. The bidirectional SOM model produced highly accurate predictions (MAE ≈ 3–4 days) comparable to complex process-based models but required minimal biological knowledge. It effectively integrated endodormancy and thermal accumulation periods into one unified learning process, reducing uncertainty and computational cost. While early-season forecasts and environmental generalization remain challenging, this approach is valuable for rapid, scalable bloom-date prediction and for evaluating climate-change impacts on flowering across regions.
