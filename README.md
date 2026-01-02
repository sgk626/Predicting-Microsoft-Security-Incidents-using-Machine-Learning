# Predicting-Microsoft-Security-Incidents-using-Machine-Learning
Security Incident Classification: A Study in Computational Parsimony An academic study on cybersecurity telemetry using a 10,000-sample subset of Microsoft’s incident dataset. Benchmarks ensemble models (XGBoost/Random Forest) via OLS/VIF feature pruning and SMOTE to achieve 91% accuracy within resource-constrained environments.

I. AbstractThis research optimizes automated triage systems within high-dimensional cybersecurity environments. Utilizing a statistically representative 10,000-record extraction (approx. 0.1% sampling) of the Microsoft Security Incident dataset 2222, the study evaluates the performance of supervised learning models in classifying incident grades: True Positive (TP), Benign Positive (BP), and False Positive (FP). The methodology emphasizes computational parsimony, achieving a peak accuracy of 91%.

II. Methodology & Data EngineeringThe pipeline was engineered to maximize signal-to-noise ratios while respecting local hardware limitations: 
- Stratified Sampling: A 10,000-record subset was utilized for iterative prototyping, preserving the statistical distribution of the original 13.6M record corpus.
- Technique Decoupling: Semicolon-delimited values in the MitreTechniques attribute were exploded into independent observations to isolate specific attack vector influences.
- Statistical Feature Pruning:
   - OLS Regression: Conducted to identify features with $p > 0.05$, resulting in the exclusion of 16 non-significant variables
   - Collinearity Analysis: Variance Inflation Factor (VIF) was employed to detect and remove 6 variables with $VIF > 10$, ensuring a stable covariance matrix8888.Class Rectification: Implemented SMOTE to resolve class imbalance, stabilizing the training set with equal representation across all target categories9.

III. Algorithmic BenchmarkingThe study conducted a comparative analysis of ensemble methods, identifying XGBoost as the most efficient architecture for this high-dimensional space.

<img width="653" height="357" alt="image" src="https://github.com/user-attachments/assets/1c25c89f-7daf-4507-80e6-c1804d1368cd" />

IV. Critical Insights
- Regularization: XGBoost's built-in L1 and L2 regularization protocols were decisive in mitigating overfitting during the classification of categorical telemetry.
- Efficiency: The 10,000-record strategy successfully identified optimal hyperparameters without the prohibitive cost of processing the full 13M record dataset.
- Generalization: High predictive accuracy (91%) demonstrates that rigorous statistical pruning is the primary driver of model reliability.

V. Technical Stack
- Language: Python 3.x.
- Libraries: Scikit-Learn , XGBoost , Pandas , Statsmodels , Imbalanced-Learn.
- Evaluation Metrics: Macro F1-Score , Accuracy , Precision , Recall
