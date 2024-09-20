# Student-Performance-Prediction
## Introduction
This project explores various machine learning techniques to predict student performance in higher education. The study utilizes supervised, semi-supervised, and unsupervised learning algorithms to identify students at risk of academic failure.

The project aims to develop a system that predicts students who may face academic difficulties, allowing for timely interventions. It uses data from the Higher Institute of Applied Arts in Portugal, including demographic, socio-economic, and academic factors. You can find the dataset [here](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success).

We have three labels we have to predict (these info were colletected at enrollment):
1. **Dropout:** it means the student is a dropout and has a very probability of dropping out.
2. **Enrolled:** it means the is still still enrolled but a has moderate probability of dropping out.
3. **Graduate:** the student is graduated and thus has a low probability of dropping out.

## Methodology
### Supervised learning
We utilized supervised learning algorithms to predict student performance, starting with `Logistic Regression` as a baseline. Several techniques were tested to enhance the model's performance, including using highly correlated features, data balancing with `SMOTE`, `PCA`, and applying `StandardScaler`.

#### Baseline Model Performance
The initial `Logistic Regression` model achieved an F1 score of **0.61**. Removing features with absolute correlation values below 0.1 improved accuracy and reduced complexity.

#### Improvements with Correlated Features
Using only highly correlated features boosted the F1 score to **0.71**.

| Model                | F1 score |
|   :---:              |   :---:  |
| Logistic Regression   | 0.71     |

#### SMOTE
Applying `SMOTE` to balance the dataset led to a slight performance drop, with an F1 score of **0.66**.

| Model                | F1 score |
|   :---:              |   :---:  |
| Logistic Regression + SMOTE   | 0.66     |

#### StandardScaler
Using `StandardScaler` for normalization increased the F1 score to **0.74**. Combining this with highly correlated features improved the score to **0.75**.

| Model                                      | F1 score |
|   :---:                                    |   :---:  |
| Logistic Regression + StandardScaler       | 0.74     |
| Logistic Regression + StandardScaler + Correlated Features  | 0.75     |

#### PCA
Applying `PCA` did not yield further improvement, maintaining an F1 score of **0.75**.

| Model                | F1 score |
|   :---:              |   :---:  |
| Logistic Regression + PCA  | 0.75     |

#### Polynomial Features
Using `PolynomialFeatures` reduced the F1 score to **0.62** but improved slightly to **0.71** when combined with correlated features.

| Model                                      | F1 score |
|   :---:                                    |   :---:  |
| Logistic Regression + PolynomialFeatures   | 0.62     |
| Logistic Regression + PolynomialFeatures + Correlated Features  | 0.71     |

#### Other Machine Learning Algorithms
We also tested various algorithms, fine-tuned using `GridSearchCV`. Below are the F1 scores for each algorithm:

| Algorithm               | F1 score |
|   :---:                 |   :---:  |
| SVM                     | 0.68     |
| Random Forest           | 0.71     |
| Ridge Classifier        | 0.69     |
| Gradient Boosting       | 0.74     |
| K-Nearest Neighbors     | 0.64     |
| Naive Bayes             | 0.63     |
| Decision Tree           | 0.65     |
| Neural Network          | 0.72     |
| AdaBoost                | 0.70     |
| XGBoost                 | 0.77     |
| CatBoostClassifier      | 0.76     |

#### Performance with Correlated Features
Using correlated features improved performance for most algorithms:

| Algorithm               | F1 score |
|   :---:                 |   :---:  |
| SVM                     | 0.71     |
| Random Forest           | 0.72     |
| Ridge Classifier        | 0.71     |
| Gradient Boosting       | 0.75     |
| K-Nearest Neighbors     | 0.67     |
| Naive Bayes             | 0.65     |
| Decision Tree           | 0.68     |
| Neural Network          | 0.74     |
| AdaBoost                | 0.73     |
| XGBoost                 | 0.77     |
| CatBoostClassifier      | 0.76     |

#### Performance with StandardScaler
`StandardScaler` improved results across most models:

| Algorithm               | F1 score |
|   :---:                 |   :---:  |
| SVM                     | 0.72     |
| Random Forest           | 0.73     |
| Ridge Classifier        | 0.72     |
| Gradient Boosting       | 0.75     |
| K-Nearest Neighbors     | 0.70     |
| Naive Bayes             | 0.66     |
| Decision Tree           | 0.69     |
| Neural Network          | 0.75     |
| AdaBoost                | 0.74     |
| XGBoost                 | 0.77     |
| CatBoostClassifier      | 0.76     |

#### Performance with PCA
`PCA` did not significantly improve performance:

| Algorithm               | F1 score |
|   :---:                 |   :---:  |
| SVM                     | 0.71     |
| Random Forest           | 0.72     |
| Ridge Classifier        | 0.71     |
| Gradient Boosting       | 0.74     |
| K-Nearest Neighbors     | 0.68     |
| Naive Bayes             | 0.64     |
| Decision Tree           | 0.68     |
| Neural Network          | 0.73     |
| AdaBoost                | 0.72     |
| XGBoost                 | 0.77     |
| CatBoostClassifier      | 0.76     |

#### Conclusion
The best performance was achieved by `XGBoost`, with and without `StandardScaler`, reaching an F1 score of **0.77**.

We also used **Ensemble Learning**, combining multiple models (`Logistic Regression`, `Random Forest`, `Gradient Boosting`, `XGBoost`) using a `Voting Classifier`, achieving an F1 score of **0.76**.

| Model                | F1 score |
|   :---:              |   :---:  |
| Ensemble Learning    | 0.76     |

### Semi-supervised learning
The class labels are imbalanced, with "Graduate" being the most frequent, followed by "Dropout," and then "Enrolled."  Based on the assumption that the non-graduate labels ("Dropout" and "Enrolled") are anomalies compared to "Graduate," and on the further assumption that "Enrolled" is an anomaly compared to "Dropout," we have tried two anomaly detection algorithms: Local Outlier Factor (LOF) and Isolation Forest (IF). 

This approach consists of two stages:
1. **1st stage:** We separate the data into two categories: Graduate and non-graduate. Then, we apply anomaly detection algorithms.
2. **2nd stage:** We apply anomaly detection algorithms on the Dropout & Enrolled labels, where Enrolled represents the anomalies.

We've got the following results:  
| Algorithm | F1 score |
|   :---:   |   :---:  |
| LOF       | 0.33     |
| IF        | 0.32     |

Because there's data imbalance we tried `SMOTE` & `ADASYN`. We've got the following results:  
| Oversampling algorithm |  LOF  |  IF   |
|   :---:                | :---: | :---: |
| `SMOTE`                |  0.33 |  0.32 |
| `ADASYN`               |  0.33 |  0.32 |

We used `Optuna` for hyperparameter optimization + `ADASYN`:
| Algorithm | F1 score |
|   :---:   |   :---:  |
| LOF       | 0.33     |
| IF        | 0.32     |

### Unsupervised learning
We tried several clustering techniques and evaluated them using Normalized Mutual Info (NMI). We've got the following results:  
| Algorithm            | Kmeans | Kprototypes | Gaussian mixture | Bisecting kmeans |
|   :---:              |  :---: |  :---:      | :---:            | :---:            |
| Without oversampling | 0.0032 | 0.0105      | 0.0034           | 0.0032           |
| `SMOTE`              | 0.0032 | 0.0102      | 0.0142           | 0.0032           |
| `ADASYN`             | 0.0032 | 0.0097      | 0.0034           | 0.0032           |

We also tried clustering ensemble [3] by applying the following steps:
1. We apply a clustering algorithm multiple times.
2. After applying a clustering algorithm, we fill a NxN weight matrix, where N is the number of elements and clusters and W<sub>ij</sub> = 1 if element i belongs to cluster j.
3. We perform graph partitioning using spectral clustering algorithm on the weight matrix.

We applied Kmeans and Gaussian mixture for 100 iterations each and got the following results:
| Algorithm        | NMI    |
|   :---:          |  :---: |
| Gaussian mixture | 0.0025 |
| Kmeans           | 0.0025 |

## Results


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
