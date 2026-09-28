# AI/ML-Based Predictive Maintenance and Vehicle Health Monitoring System

## Project Information

**Submitted by:** Rohit Roy  
**Roll No.:** 41  
**Enrolment No.:** 12023002002115  
**Course:** Wipro Automotive Course  
**Department:** Electronics and Communication Engineering  
**Institute:** Institute Of Engineering and Management, Newtown  
**Under the guidance of:** Rabi Behera  
**Date of Submission:** 29.09.2023  

---

## Overview

This project presents an AI/ML-based predictive-maintenance solution that uses vehicle operating data to estimate the likelihood of failure before a breakdown occurs.

The workflow combines conventional machine-learning classifiers with sequence-based deep-learning models and converts the model output into:

- Failure probability
- Vehicle health score
- Condition category
- Maintenance recommendation
- Explanation of influential operating factors

The project uses a synthetic dataset of 10,000 observations and nine vehicle parameters. It is intended as a proof of concept and should be validated with real sensor and service-history data before operational deployment.

---

## Project Objectives

- Prepare a structured dataset containing key vehicle operating variables.
- Clean and transform the data for predictive modelling.
- Develop and compare classical machine-learning and deep-learning approaches.
- Estimate the probability of an impending vehicle or component failure.
- Convert the prediction into a health score and operating condition category.
- Provide maintenance guidance and identify influential parameters.

---

## System Architecture

```text
Vehicle Sensors / Dataset
          ↓
    Data Ingestion
          ↓
     Preprocessing
          ↓
 Predictive ML / DL Model
          ↓
   Failure Probability
          ↓
      Health Score
          ↓
    Condition Status
          ↓
Maintenance Recommendation
          ↓
 Influential Parameters
```

---

## Dataset

The project dataset contains **10,000 records and 10 columns**. It was synthetically generated for development and testing.

The target variable is `Failure`:

```text
0 → No recorded failure
1 → Failure event
```

### Class Distribution

| Class | Records |
|---|---:|
| Non-Failure | 9,609 |
| Failure | 391 |

The dataset contains no missing values and is imbalanced. Therefore, Recall, Precision, and F1-score should be considered along with Accuracy during evaluation.

---

## Input Variables

The system uses nine vehicle operating measurements:

| Variable | Description |
|---|---|
| Engine Temperature | Thermal condition of the engine |
| RPM | Engine rotational speed |
| Oil Pressure | Lubrication-system pressure |
| Vibration | Mechanical vibration level |
| Battery Voltage | Electrical-system voltage |
| Coolant Temperature | Cooling-system temperature |
| Fuel Consumption | Fuel usage rate |
| Vehicle Speed | Vehicle operating speed |
| Operating Hours | Accumulated operating duration |

**Target:** `Failure`

---

## Data Preparation

The data preparation process includes:

1. Separating the nine vehicle measurements from the target.
2. Splitting the data into training and testing subsets.
3. Applying standardization where required.
4. Creating sequences of length 10 for LSTM, GRU, and Transformer experiments.
5. Considering class imbalance during model evaluation.

---

## Predictive Models

### Classical Machine Learning

The project compares:

- Logistic Regression
- Decision Tree
- Random Forest
- XGBoost

XGBoost is used as the final probability-estimation model for the vehicle monitoring function.

### Deep Learning

The project also evaluates:

- LSTM
- GRU
- Transformer

The LSTM and GRU models process sequential vehicle data, while the Transformer uses multi-head self-attention to investigate relationships across the input window.

---

## Evaluation Metrics

The models are evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score

Recall is particularly important for predictive maintenance because a missed failure can be more costly than an unnecessary inspection.

---

## Vehicle Health Decision Layer

The trained XGBoost model receives the nine vehicle parameters and returns a failure probability.

The health score is calculated as:

```text
Health Score = 100 - Failure Probability (%)
```

### Health Conditions

| Health Score | Condition | Recommended Action |
|---|---|---|
| 80% or above | HEALTHY | Continue normal operation and routine checks |
| 60% to below 80% | WARNING | Schedule an inspection and review abnormal parameters soon |
| Below 60% | CRITICAL | Arrange immediate inspection before continued operation where appropriate |

These thresholds are prototype interpretation rules and are not universal safety limits.

---

## Prediction Interpretation

XGBoost feature importance is used to identify influential variables.

Possible indicators include:

- Elevated vibration
- High engine temperature
- High coolant temperature
- Abnormal oil pressure
- Low battery voltage
- High fuel consumption
- High RPM
- High vehicle speed
- Extended operating hours

These indicators should be treated as signals for inspection rather than proof that a particular component has failed.

---

## Technology Stack

- **Python**
- **Google Colab**
- **NumPy**
- **Pandas**
- **Scikit-learn**
- **XGBoost**
- **TensorFlow/Keras**
- **Matplotlib**
- **Seaborn**

---

## Project Structure

```text
Vehicle-Predictive-Maintenance/
│
├── README.md
├── dataset/
│   └── vehicle_data.csv
├── notebooks/
│   └── predictive_maintenance.ipynb
├── models/
│   ├── xgboost_model
│   ├── lstm_model
│   ├── gru_model
│   └── transformer_model
├── results/
│   ├── confusion_matrix.png
│   ├── model_comparison.png
│   └── feature_importance.png
└── requirements.txt
```

---

## Limitations

This project is a proof of concept based on synthetic data. Synthetic patterns may not represent:

- Real sensor noise
- Sensor drift
- Missing readings
- Real-world class imbalance
- Complex vehicle failure modes

The sequence models also require carefully timestamped data.

---

## Future Development

Future improvements include:

- Connecting the system to real vehicle sensors and timestamped telemetry.
- Training and validating models using maintenance records and verified failure events.
- Adding sensor-quality checks.
- Implementing drift monitoring and model retraining.
- Deploying the monitoring function through an IoT gateway or edge-computing device.
- Calibrating alert thresholds using safety, downtime, and maintenance-cost requirements.
- Adding a dashboard for trends, alerts, service history, and technician feedback.

---

## References

[1] Scikit-learn Developers, “Scikit-learn: Machine learning in Python—Classification and model evaluation,” Scikit-learn Documentation.

[2] T. Chen and C. Guestrin, “XGBoost: A scalable tree boosting system,” in *Proc. 22nd ACM SIGKDD Int. Conf. Knowledge Discovery and Data Mining*, 2016, pp. 785–794.

[3] TensorFlow Developers, “TensorFlow/Keras documentation: Recurrent and attention-based neural networks,” TensorFlow Documentation.

[4] Scikit-learn Developers, “sklearn.metrics: Classification metrics and model evaluation,” Scikit-learn Documentation.

[5] XGBoost Developers, “XGBoost documentation,” XGBoost Documentation.

---

## Author

**Rohit Roy**  
Roll No.: 41  
Enrolment No.: 12023002002115  

**Electronics and Communication Engineering**  
**Institute Of Engineering and Management, Newtown**

**Wipro Automotive Course**

**Under the guidance of:** Rabi Behera

**Date of Submission:** 29.09.2023
