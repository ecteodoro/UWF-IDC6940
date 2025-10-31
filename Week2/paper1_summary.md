# Estimating the first flowering and full blossom dates of Yoshino cherry (Cerasus × yedoensis ‘Somei‑yoshino’) in Japan using machine learning algorithms
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

- he model uses full-year temperature data including months after the bloom date; hence it cannot be used for real-time forecasting for the upcoming season (because data after bloom would not exist yet).  ￼
- Accuracy was somewhat lower at certain island sites (e.g., Tanegashima, Miyakejima) where local microclimates may introduce additional variability.
- Only temperature is considered; other environmental variables (wind, precipitation, soil moisture) are excluded.
- Future climate scenarios may exceed the range of training data and thus reduce model reliability.

**Conclusion**

This paper presents a robust, interpretable machine-learning framework that delivers highly accurate estimates of cherry blossom phenology across Japan. It demonstrates that ML models can capture the key biological mechanisms (cold dormancy, warm forcing) implicitly, and provide stable nationwide performance. While not suited for real-time bloom forecasting, the models are valuable tools for assessing past and projected climate-change impacts on phenology.