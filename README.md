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


### Semi-supervised learning
The class labels are imbalanced, with "Graduate" being the most frequent, followed by "Dropout," and then "Enrolled."  Based on the assumption that the non-graduate labels ("Dropout" and "Enrolled") are anomalies compared to "Graduate," and on the further assumption that "Enrolled" is an anomaly compared to "Dropout," we have tried two anomaly detection algorithms: Local Outlier Factor (LOF) and Isolation Forest (IF). 

This approach consists of two stages:
1. **1st stage:** We separate the data into two categories: Graduate and non-graduate. Then, we apply anomaly detection algorithms.
2. **2nd stage:** We apply anomaly detection algorithms on the Dropout & Enrolled labels, where Enrolled represents the anomalies.

We've got the following results:  
| Algirthm  | F1 score |
|   :---:   |   :---:  |
| LOF       | 0.33     |
| IF        | 0.32     |

Because there's data imbalance we tried `SMOTE` & `ADASYN`. We've got the following results:  
| Oversampling algirthm  |  LOF  |  IF   |
|   :---:                | :---: | :---: |
| `SMOTE`                |  0.33 |  0.32 |
| `ADASYN`               |  0.33 |  0.32 |

We used `Optuna` for hyperparameter optimization + `ADASYN`:
| Algirthm  | F1 score |
|   :---:   |   :---:  |
| LOF       | 0.33     |
| IF        | 0.32     |

### Unsupervised learning


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
