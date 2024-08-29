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

- [Fern & Brodley (2004)](https://doi.org/10.1145/1015330.1015414)
- [Martins et al. (2021)](https://doi.org/10.1007/978-3-030-72657-7_16)
- [Villar & De Andrade (2024)](https://doi.org/10.1007/s44163-023-00079-z)

## Contributors
- [Ahmad-AM0](https://github.com/Ahmad-AM0)
- [Haidar-Al-Sous](https://github.com/Haidar-Al-Sous)
- [kenan-azd-dev](https://github.com/kenan-azd-dev)
- [mariannedeeb](https://github.com/mariannedeeb/)
- [hrayrdb](https://github.com/hrayrdb/)
