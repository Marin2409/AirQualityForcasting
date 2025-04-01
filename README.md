# AirQualityForcasting

# 🌍 A Cleaner Future: Global Air Quality Forecasting

> Machine Learning for Environmental Impact  
> By: Jose Marin, Reid Dial, Jose Colchado

## 🚀 Project Overview

This project focuses on building predictive machine learning models to forecast **Air Quality Index (AQI)** categories using pollutant data. As air pollution continues to be a leading cause of premature deaths globally, our goal is to enable **early detection** of hazardous air quality events, helping inform public health responses and urban policy decisions.

We explored multiple modeling approaches, analyzed pollutant behavior, addressed class imbalance, and experimented with feature reduction to create more **generalizable and robust models**.

---

## 📊 Dataset

- **Samples:** 22,607 global records
- **Features:**
  - `PM2.5 AQI Value`
  - `CO AQI Value`
  - `NO2 AQI Value`
  - `Ozone AQI Value`
  - `Country`, `City`
  - `AQI Value`, `AQI Category`

### 🏷️ Label Encoding
The AQI categories were label encoded for classification models:

| AQI Category                     | Encoded Label |
|----------------------------------|---------------|
| Good                             | 0             |
| Moderate                         | 1             |
| Unhealthy for Sensitive Groups   | 2             |
| Unhealthy                        | 3             |
| Very Unhealthy                   | 4             |
| Hazardous                        | 5             |

---

## 🧠 Models Used

| Model                          | Features Used              | Accuracy | Notes                                                                 |
|-------------------------------|----------------------------|----------|-----------------------------------------------------------------------|
| **Linear Regression**         | PM2.5, CO, NO2, Ozone      | R² = 0.974 | High accuracy, but overfit to PM2.5 due to strong correlation         |
| **Random Forest Classifier**  | PM2.5, CO, Ozone           | 94% (val) | Good general performance; struggled with rare classes like Hazardous |
| **Gradient Boosting Classifier (GBC)** | CO, NO2, Ozone    | 64.88%     | Better generalization without PM2.5; poor recall for rare categories |
| **GBC + SMOTE**               | CO, NO2, Ozone (SMOTE)     | 56.39%     | Improved recall on rare classes, but decreased overall accuracy      |

---

## 🔍 Key Insights

- **PM2.5** is the most predictive pollutant but causes overfitting when used without caution.
- **CO, NO2, and Ozone** play crucial roles in urban environments and allow models to generalize better.
- **Class imbalance** is a major issue: over 42% of the data is classified as *Good*, while <1% is *Hazardous*.
- SMOTE can improve detection of minority classes but requires careful tuning to avoid misclassification.

---

## 🛠️ Technologies Used

- Python (Pandas, NumPy, Scikit-learn)
- Jupyter Notebook
- Matplotlib / Seaborn (for visualization)
- SMOTE (from `imblearn`)
- GridSearchCV for model tuning

---
