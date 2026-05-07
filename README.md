# Anomaly-Detection-with-Isolation-Forest
A straightforward, visual demonstration of unsupervised anomaly detection (outlier detection) using the **Isolation Forest** algorithm. 

This project generates a synthetic 2D dataset, trains a machine learning model to isolate outliers without relying on labeled training data, and visualizes the model's decision boundaries.

## 🎯 Overview
In real-world scenarios (like fraud detection, network security, or manufacturing quality control), anomalies are rare and often unlabeled. Traditional classification algorithms fail here because they require balanced, labeled examples of both "normal" and "fraudulent" behavior. 

This project uses an **Isolation Forest**—an unsupervised learning algorithm that excels at finding the "needle in a haystack" by explicitly isolating anomalies rather than profiling normal data points.

---

## ⚙️ How It Works (The Pipeline)

The Jupyter Notebook executes the following end-to-end workflow:

1. **Synthetic Data Generation:** * Creates a "normal" cluster of 200 points using a 2D Gaussian distribution.
   * Scatters 20 "anomalous" points uniformly across a wider range.
2. **Unsupervised Training:** * Instantiates an `IsolationForest` model.
   * Fits the model strictly on the feature coordinates (`X`), entirely ignoring the ground truth labels (`y`). 
3. **Prediction:** * The model calculates anomaly scores and predicts `-1` for outliers and `1` for inliers.
4. **Analysis & Visualization:** * Evaluates accuracy against the hidden ground truth.
   * Generates a contour plot showing the model's learned decision boundary isolating the anomalies.

---

## 🧠 Strategic Modeling Decisions

### Why Isolation Forest?
Most anomaly detection algorithms (like One-Class SVM) try to build a profile of "normal" instances and flag anything that falls outside of it. **Isolation Forests work differently.** Because anomalies are "few and different," they are easier to isolate. The algorithm randomly partitions the data using decision trees; anomalies require fewer partitions (shorter path lengths) to be isolated than normal points. This makes it highly efficient and scalable for high-dimensional data.

### The `contamination` Parameter
In the code, the model is initialized with `contamination=0.1`. 
* **The Explanation:** This parameter tells the model the expected proportion of outliers in the dataset. Because we synthetically generated 20 anomalies out of 220 total points (~9%), we set this threshold to 10% (0.1) to guide the decision function. In a real-world, completely unlabeled scenario, this value is usually tuned based on domain expertise or business tolerance for false positives.

---

## 🛠️ Tech Stack

* **Language:** `Python 3`
* **Machine Learning:** `scikit-learn` (`IsolationForest`)
* **Data Manipulation:** `numpy`
* **Visualization:** `matplotlib.pyplot`

## output
Starting Anomaly Detection project...
Generated 220 data points (200 normal, 20 anomalous).
Training Isolation Forest model...
Prediction complete.
Model found 2 errors.
Accuracy: 99.09%

Model predicted 22 anomalies.
There were actually 20 anomalies.
Generating visualization...
