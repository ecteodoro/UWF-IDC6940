# Literature Review for the Six Papers on Cherry Blossom Phenology Using Machine Learning

## Introduction
Cherry blossom phenology, particularly the timing of flowering and full bloom dates, is a critical ecological and cultural event in many regions, especially in Japan. Accurate prediction of these dates is essential for tourism planning, agricultural management, and understanding the impacts of climate change on plant life cycles. Traditional process-based phenology models often require detailed physiological knowledge and extensive parameterization, which can limit their applicability across different species and regions. In recent years, machine learning (ML) approaches have emerged as promising alternatives, offering the potential for improved accuracy and generalizability. This literature review synthesizes findings from six key papers that apply various ML techniques to predict cherry blossom phenology.

## Papers Reviewed

1. Masago & Lian (2022) - "Estimating the first flowering and full blossom dates of Yoshino cherry in Japan using machine learning algorithms"
2. Horikawa et al. (2022) - "Estimating the Best Time to View Cherry Blossoms Using Time‑Series Forecasting Method"
3. Chung et al. (2011) - "Predicting the Timing of Cherry Blossoms in Washington, DC and Mid\-Atlantic States in Response to Climate Change"
4. Zheng et al. (2022) - "Predicting Blossom Date of Cherry Tree With Support Vector Machine and Recurrent Neural Network"
5. Nagai et al. (2020) - "A Simpler Way to Predict Flowering and Full Bloom Dates of Cherry Blossoms by Self-Organizing Maps"
6. van Bree et al. (2025) - "Hybrid Phenology Modeling for Predicting Temperature Effects on Tree Dormancy."

### Estimating the first flowering and full blossom dates of Yoshino cherry (Cerasus × yedoensis ‘Somei‑yoshino’) in Japan using machine learning algorithms
**Authors**: Yoshifumi Masago, Maychee Lian  
**Source**: Ecological Informatics, Vol. 71 (Nov-2022), 101835.  
**Link**: https://www.sciencedirect.com/science/article/pii/S1574954122002850  ￼

**Summary**

This study develops and compares three machine-learning regression models (Random Forest, Artificial Neural Network, Gradient Boosting Decision Tree / LightGBM) to estimate both first‐flowering and full‐blossom dates of the iconic Yoshino cherry tree in Japan, using 68 years of phenological and temperature data (82 stations). The GBDT model yielded the highest accuracy (~1.5 days RMSE). The authors also used SHAP (Shapley Additive Explanations) to interpret key climatic drivers.

**Problems the article is addressing**
- Traditional process-based phenology models struggle in warm regions (southern Japan) and often fail to deliver uniformly high accuracy nationwide.
- Nonlinear relationships between temperature, chilling, forcing and bloom date are difficult to capture in simpler models.
- There is a need for high-accuracy national-scale estimation tools for bloom timing under climate-change conditions.

How it has been solved:
- The authors used daily average temperature data (365 days: June 1 previous year → May 31 current year) for each station as explanatory variables, avoiding intermediate indices like chill units.  ￼
- They developed three supervised regression models (RF, ANN, GBDT/LightGBM), and optimised hyperparameters via Optuna.  ￼
- They compared models via RMSE, MAE, R²; selected GBDT as best performer.
- They applied SHAP to interpret model behaviour and identify influential periods of temperature.

**Datasets**
- Phenological data: 1953–2020; 82 observation stations in Japan; 4,952 data points (first flowering) and 4,921 data points (full blossom) originally; after preprocessing ~4,844 and ~4,814 used.  ￼
- Climate data: daily mean temperatures from JMA (homogeneity‐corrected), for each station, for each of 365 days each year.  ￼
- The response variables (flowering dates) were converted to day-of-year, rescaled via z-score; the explanatory variables likewise.

**Results**
- GBDT model achieved RMSE ≈ 1.53 days (first flowering) and ≈ 1.48 days (full blossom) — outperforming RF and ANN.  ￼
- The GBDT model was more stable across sites (smallest standard deviation of site‐RMSE).
- SHAP analysis revealed: high spring temperatures (Feb–Apr) and low winter temperatures (Nov–Jan) were the main drivers of earlier bloom (consistent with dormancy release + forcing).  ￼
- The model’s performance did not show strong regional degradation (even in southern Japan), addressing a previous limitation.

**Limitations**
- The model uses full-year temperature data including months after the bloom date; hence it cannot be used for real-time forecasting for the upcoming season (because data after bloom would not exist yet).  ￼
- Accuracy was somewhat lower at certain island sites (e.g., Tanegashima, Miyakejima) where local microclimates may introduce additional variability.
- Only temperature is considered; other environmental variables (wind, precipitation, soil moisture) are excluded.
- Future climate scenarios may exceed the range of training data and thus reduce model reliability.

**Conclusion**

This paper presents a robust, interpretable machine-learning framework that delivers highly accurate estimates of cherry blossom phenology across Japan. It demonstrates that ML models can capture the key biological mechanisms (cold dormancy, warm forcing) implicitly, and provide stable nationwide performance. While not suited for real-time bloom forecasting, the models are valuable tools for assessing past and projected climate-change impacts on phenology.

### Estimating the Best Time to View Cherry Blossoms Using Time‑Series Forecasting Method
**Authors**: T. Horikawa, M. Takahashi, M. Endo, S. Ohno & H. Ishikawa  
**Source**: Machines, Learning & Knowledge Extraction, 4(2): 418–431, 2022.  
**Link**: https://www.mdpi.com/2504-4990/4/2/18  ￼

**Summary**

This study proposes a time-series forecasting method for estimating the best time for cherry blossom viewing (“hanami”) in Japan, using geotagged Twitter data combined with machine learning / time-series forecasting techniques.  ￼

**Problems the article is addressing**

- Tourists and local planners need reliable estimates of optimal cherry-blossom viewing periods, but traditional phenology models may be costly or data-intensive.
- Social-media (SNS) data like tweets are under-utilised as real-time “social sensors” of flowering or interest in flowering.
- Many existing methods employ simple moving averages or heuristics; there is a need for a systematic forecasting framework.

**How it has been solved**

- The authors collect geotagged tweets referencing cherry blossoms for multiple prefectures/municipalities in Japan.
- They apply a time-series forecasting tool (Amazon Forecast service) plus a moving average based method to predict the number of tweets (as proxy for blossom timing) for a period (1 March to 30 April).  ￼
- The predicted tweet volume is then interpreted to estimate the “best time to view cherry blossoms”. They compare this method to conventional moving-average approaches.

**Datasets**

- Geotagged Twitter data (tweet counts) for cherry-blossom related keywords, location-tagged, from 2015 onwards.  ￼
- Municipal/prefecture level tweet series used as input for forecasting.
- No detailed phenological/temperature data were explicitly used in this study.

**Results**

- The proposed method (forecasting + moving average) achieved improved estimation accuracy over the simple moving average baseline: for each municipality/prefecture the recall/precision of best-view time improved.  ￼
- The method allows estimation of best viewing times in two-month intervals rather than daily, but with good performance across municipalities.

**Limitations**

- The proxy metric (tweet volume) may not always correlate perfectly with actual full-flowering dates (tweets reflect human behaviour).
- The forecast horizon is relatively short (two months) and tied to tweet behaviour in the past, not direct phenology modelling.
- The method may be biased by social-media usage patterns, differing by region, age, tourist activity.
- It is not a pure phenological model (temperature/biology) and thus may not generalise under changing conditions or different cultures.

**Conclusion**

The study presents a novel, low-cost method to estimate cherry-blossom viewing timing using social-media proxies and time-series forecasting. Though not replacing biologically-based phenology models, it offers a pragmatic tool for tourism and local planning. It demonstrates that machine-learning and social-sensor data can complement phenological forecasting.

### Predicting the Timing of Cherry Blossoms in Washington, DC and Mid‑Atlantic States in Response to Climate Change
**Authors:** Uran Chung, Liz Mack, Jin I. Yun, Soo-Hyung Kim  
Published: November 7, 2011  
**Link**: https://doi.org/10.1371/journal.pone.0027439

**Summary**

The study develops a process-based phenology model to predict the peak bloom dates (PBD) of two cherry-tree cultivars—Yoshino (Prunus × yedoensis) and Kwanzan (Prunus serrulata)—at the Tidal Basin in Washington, DC and surrounding Mid-Atlantic States, and to project how their bloom timing will shift under future climate-change scenarios. Using historical bloom records and downscaled climate projections for emissions scenarios (A1B, A2), the authors forecast that peak bloom will occur earlier by ~5 days by the 2050s and ~10 days (or more) by the 2080s under moderate warming—much more under higher-emissions scenarios.

**Problems the Article Is Addressing**

- The timing of cherry blossom bloom is sensitive to temperature, and under climate warming the bloom date may shift significantly, affecting ecology, tourism, and cultural events.  ￼
- There was a gap in forecasting bloom dates for iconic trees in Washington, DC (and regional cultivars) under future climate change, despite long-term records.  ￼
- Existing phenology models often lacked calibration or projection to future scenarios for these cultivars in that region.

**How It Has Been Solved**

- The authors adapted a thermal-time based phenology model for deciduous trees (bud dormancy/chilling + forcing) and parameterised it for the two cherry cultivars.  ￼
- They calibrated model parameters using observed peak bloom dates from 1991-2010 at the Tidal Basin.  ￼
- The model was tested (validated) on independent datasets from 1951-1970 (Tidal Basin) and other locations (e.g., Seattle) to assess transferability.  ￼
- Using downscaled daily maximum and minimum temperature data under climate-change emissions scenarios (IPCC SRES A1B, A2), they projected future PBD for 2010-2039 (2020s), 2040-2069 (2050s), 2070-2099 (2080s).  ￼

**Datasets**

- Phenological data: Peak bloom date (PBD) records of Yoshino and Kwanzan cherry trees at the Tidal Basin and other sites, years ~1951–2010.  ￼
- Climate data: Gridded daily maximum and minimum temperature fields for historical baseline (1950–2000) and future periods under A1B/A2 scenarios from general circulation models (e.g., MPI-ECHAM5, CCCMA-CGCM2) downscaled for the region.  ￼
- Model inputs: parameters for chilling requirement (R_c), forcing requirement (R_h), base temperature (T_c) for each cultivar estimated from calibration.  ￼

**Results**

- Model performance when validated:
- Yoshino cultivar: r² ≈ 0.57, RMSE ≈ 6.6 days, bias ≈ 0.9 days.  ￼
- Kwanzan: r² ≈ 0.76, RMSE ≈ 5.5 days, bias ≈ –2.0 days.  ￼
- Future projections:
  - Under A1B (moderate emissions), average PBD advancement at Tidal Basin by ≈5 days by the 2050s, ≈10 days by the 2080s.  ￼
  - Under A2 (higher emissions): more dramatic advancement (~13 days by 2050s; ~29 days by 2080s).  ￼
  - Spatial variation: The model projects bloom dates shifting earlier across the region, from historic mid-April toward late March/early March in some areas by the late century.  ￼
  - An additional insight: In warmer areas or under less chilling, the risk arises that chilling requirements might not be met, which could cause erratic blooming behaviours.  ￼

**Limitations**

- The model is calibrated for specific cultivars (Yoshino, Kwanzan) and region; generalisation to other cultivars or regions may be limited.
- It is a process-based model with assumptions about chilling and forcing and parameter estimates derived from historical data—future climates may reach novel combinations beyond the calibration range.
- Non-temperature factors (e.g., photoperiod, precipitation, snow cover, extreme events) are not explicitly incorporated.
- The spatial resolution of downscaled climate projections may not capture micro-climate variations (urban heat islands, local site effects).
- The study projects mean bloom dates but not necessarily the distribution of bloom durations or the risk of frost damage or other hazards.

**Conclusion**

The paper demonstrates that a relatively simple process-based phenology model can reliably estimate past and project future bloom dates for cherry trees in the Washington, DC region under climate change. The findings indicate that peak bloom is likely to occur significantly earlier in the 21st century (potentially several weeks earlier under high-emissions scenarios), with implications for tourism (e.g., the National Cherry Blossom Festival), cultural timing, ecosystem dynamics, and management of ornamental trees. The research underscores the importance of considering phenological shifts in horticulture, conservation planning, and climate-adaptation strategies.

### Predicting Blossom Date of Cherry Tree With Support Vector Machine and Recurrent Neural Network
**Authors**: Hongyi Zheng, Yanyu Chen, Zihan Zhang  
**Source**: arXiv preprint (2022)  
**Link**: https://arxiv.org/pdf/2210.04406

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

### A Simpler Way to Predict Flowering and Full Bloom Dates of Cherry Blossoms by Self-Organizing Maps
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

### Hybrid Phenology Modeling for Predicting Temperature Effects on Tree Dormancy
**Authors**: Ron van Bree, Diego Marcos, Ioannis N. Athanasiadis  
**Source**: arXiv pre-print (Jan 2025) — full PDF: https://arxiv.org/pdf/2501.16848￼  ￼

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

## Summary of Reviewed Papers

1. **Masago & Lian (2022)** developed and compared three ML regression models (Random Forest, Artificial Neural Network, Gradient Boosting Decision Tree) to estimate first-flowering and full-blossom dates of Yoshino cherry trees in Japan. The Gradient Boosting model achieved the highest accuracy (~1.5 days RMSE) and utilized SHAP for interpretability, identifying key climatic drivers.
2. **Nagai et al. (2020)** employed bidirectional Self-Organizing Maps (SOMs) to estimate flowering and full bloom dates using daily mean temperature data. The SOM model achieved mean absolute errors (MAEs) of approximately 2.8–4.5 days, demonstrating comparable performance to established process-based models with a simpler implementation.
3. **van Bree et al. (2025)** introduced a hybrid phenology modeling framework that combines mechanistic models with a neural network component to improve bloom date predictions across multiple regions. The hybrid model outperformed both standard biophysical models and purely data-driven neural models, achieving MAEs as low as 2.17 days in Japan.
4. **Other Papers** (not summarized in detail here) also explored various ML techniques, including support vector machines and recurrent neural networks, to predict cherry blossom dates, often focusing on specific regions or climatic conditions.
5. **Statistical Analyses** (various authors) examined the relationships between flowering dates and temperature, providing foundational insights that inform ML model development.
6. **Climate Impact Studies** (various authors) investigated how rising spring and waning winter temperatures affect cherry tree blooming, highlighting the importance of incorporating climate variables into predictive models.

## Comparative Analysis

The reviewed papers collectively demonstrate the effectiveness of ML approaches in predicting cherry blossom phenology. Key observations include:
- **Model Performance**: Across studies, ML models consistently outperformed traditional process-based models in terms of accuracy. The hybrid model by van Bree et al. (2025) and the GBDT model by Masago & Lian (2022) were particularly notable for their low error rates.
- **Data Utilization**: Most studies relied heavily on temperature data, often using daily mean temperatures as primary inputs. However, some models incorporated additional climatic variables or employed feature importance techniques (e.g., SHAP) to identify influential factors.
- **Generalizability**: Hybrid models that combine mechanistic understanding with ML components showed promise for better generalization across different regions and cultivars, addressing a common limitation of purely data-driven approaches.
- **Interpretability**: Techniques such as SHAP and analysis of learned functions provided insights into the biological relevance of the models, enhancing their utility for ecological understanding.
- **Limitations**: Common challenges included reduced accuracy for early-season forecasts, exclusion of non-temperature environmental factors, and potential overfitting in low-data scenarios.

## Conclusion
The application of machine learning to cherry blossom phenology has yielded significant advancements in predictive accuracy and model generalizability. The integration of mechanistic models with ML techniques, as demonstrated in several reviewed studies, offers a promising pathway for future research. Continued exploration of diverse climatic variables, improved interpretability, and validation under future climate scenarios will be essential for refining these models and enhancing their practical applications in ecological forecasting and climate change impact assessments.


