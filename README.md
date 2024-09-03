# Student-Performance-Prediction

This project explores various machine learning techniques to predict student performance in higher education. The study utilizes supervised, semi-supervised, and unsupervised learning algorithms to identify students at risk of academic failure.

The project aims to develop a system that predicts students who may face academic difficulties, allowing for timely interventions. It uses data from the Higher Institute of Applied Arts in Portugal, including demographic, socio-economic, and academic factors.

## Methodology

- **Data Collection**: Data from 2008-2018 covering various disciplines such as agriculture, design, education, and more.
- **Preprocessing**: Categorical data is encoded using `LabelEncoder` and `OneHotEncoder`.
- **Oversampling Techniques**: `SMOTE` and `ADASYN` are used to address class imbalance.
- **Classification Models**: Traditional models like Logistic Regression, SVM, Decision Trees, and advanced models like XGBoost, CatBoost.
- **Anomaly Detection**: Algorithms like Isolation Forest and Local Outlier Factor are tested.
- **Dimensionality Reduction**: PCA and feature scaling techniques like `StandardScaler`.

## Results

- **Supervised Learning**: Found to be the most effective for predicting student outcomes.
- **Anomaly Detection**: IQR provided the best accuracy among outlier detection methods.
- **Ensemble Learning**: Implemented using a combination of Logistic Regression, Random Forest, Gradient Boosting, and XGBoost, improving model accuracy.


## References

[1]  Martins, M. V., Tolledo, D., Machado, J., Baptista, L. M. T., & Realinho, V. (2021). Early Prediction of student’s Performance in Higher Education: A Case Study. In Advances in intelligent systems and computing (pp. 166–175). https://doi.org/10.1007/978-3-030-72657-7_16  
[2]  Villar, A., & De Andrade, C. R. V. (2024). Supervised machine learning algorithms for predicting student dropout and academic success: a comparative study. Discover Artificial Intelligence, 4(1).
https://doi.org/10.1007/s44163-023-00079-z  
[3]  Fern, X. Z., & Brodley, C. E. (2004). Solving cluster ensemble problems by bipartite graph partitioning. https://doi.org/10.1145/1015330.1015414

## Contributors
- [Ahmad-AM0](https://github.com/Ahmad-AM0)
- [Haidar-Al-Sous](https://github.com/Haidar-Al-Sous)
- [kenan-azd-dev](https://github.com/kenan-azd-dev)
- [mariannedeeb](https://github.com/mariannedeeb/)
- [hrayrdb](https://github.com/hrayrdb/)
