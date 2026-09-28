# Machine Learning Projects

A portfolio of three end-to-end machine learning projects built in Python, spanning **supervised classification**, **regression and time-series forecasting**, and **unsupervised clustering with dimensionality reduction**. Each project follows a complete data science workflow: data cleaning, exploratory data analysis (EDA), feature engineering, model training, and evaluation using industry-standard performance metrics. All datasets come from the UCI Machine Learning Repository.

---

## 📧 1. Email Spam Classification
**Notebook:** [Email_Spam_Predictions.ipynb](Email_Spam_Predictions.ipynb)

A binary classification model that predicts whether an email is spam, based on **57 engineered features** capturing the frequency of specific words and characters. Exploratory data analysis and correlation mapping revealed strong spam indicators, such as frequent semicolons and the word "all", which informed feature interpretation and model selection.

Five supervised learning algorithms were implemented and benchmarked to compare their strengths, limitations and suitability for the data structure:
- K-Nearest Neighbours (KNN)
- Naïve Bayes
- Logistic Regression
- Support Vector Machines (SVM)
- Neural Network (TensorFlow)

**Outcome:** Models were evaluated on **precision, recall and accuracy**. The Neural Network delivered the highest overall performance. However, Logistic Regression achieved comparable results with significantly lower computational cost and faster inference, making it the most practical choice for **real-time, production-scale email filtering**.

---

## ⚡ 2. Household Energy Consumption Forecasting
**Notebook:** [Household_Electric_Power_Consumption.ipynb](Household_Electric_Power_Consumption.ipynb)

A regression project forecasting household electricity usage across a four-year period, with sub-metered consumption for the kitchen, laundry, air conditioning and water heating. Accurate demand forecasting helps energy providers match **renewable energy supply with demand**, reducing reliance on fossil fuels.

**Approach:**
- Analysed correlations between consumption and parameters such as time of day, voltage and global reactive power
- Applied **correlation-based feature selection** to retain the most predictive variables
- Built and compared a **Linear Regression** baseline against a **Neural Network (TensorFlow)**
- Evaluated both models using a custom **Mean Squared Error (MSE)** function on the test set, alongside a predicted-vs-actual scatter plot benchmarked against an ideal-fit line

**Results:**

| Model | Test MSE |
|---|---|
| Linear Regression | 46.63 |
| Neural Network | **38.96** |

**Outcome:** The Neural Network reduced prediction error by **~16%** compared with the Linear Regression baseline. It achieved this after training on **over 2 million data points** for only 20 epochs, which demonstrates strong **scalability** and clear potential for further gains through extended training or architecture tuning.

---

## 🌫️ 3. Air Quality Assessment: Clustering & PCA
**Notebook:** [Air_quality_Assessment.ipynb](Air_quality_Assessment.ipynb)

An **unsupervised learning** project applying **K-Means clustering** to all 13 features of an urban air quality dataset. The features include pollutant concentrations (CO, NOx, NO₂, benzene), metal-oxide sensor readings and meteorological conditions (temperature, relative and absolute humidity).

Because the clustered data exists in 13 dimensions, **Principal Component Analysis (PCA)** was used for **dimensionality reduction**. This projects the data onto two principal components so the clusters can be visualised in 2D. The intuition is much like drawing a sphere on paper: a circle is the best flat approximation.

**Interpreting the components:** PCA loadings were extracted to link each principal component back to the original variables:
- **PC1, the "Pollution-Intensity Axis":** driven by pollutant variables such as the NMHC sensor (0.372), benzene (0.367), the CO sensor (0.361) and the O₃ sensor (0.359). Temperature and humidity contribute almost nothing (loadings ≤ 0.07).
- **PC2, the "Meteorology Axis":** dominated by temperature (0.575) and absolute humidity (0.506), with NOx and NO₂ loading negatively (≈ −0.30). This suggests nitrogen oxide levels tend to be lower in warmer conditions.

**Cluster profiles:** The mean conditions within each cluster reveal three distinct air quality regimes:

| Cluster | Profile | CO (mg/m³) | NOx (ppb) | NO₂ (µg/m³) | Benzene (µg/m³) | Temp (°C) | RH (%) |
|---|---|---|---|---|---|---|---|
| 0 | Moderate pollution, warm & dry | 1.82 | 159.6 | 98.7 | 9.49 | 24.7 | 43.4 |
| 1 | Low pollution, cool & humid | 1.13 | 154.7 | 93.5 | 4.12 | 12.0 | 53.5 |
| 2 | **High-pollution episodes** | **4.05** | **504.6** | **161.4** | **20.29** | 17.0 | 52.9 |

**Outcome:** Cluster 2 isolates high-pollution episodes. In this cluster, NOx levels are over **3× higher** and CO and benzene more than **2× higher** than in Cluster 0. The clustering therefore separates periods of intense emissions from cleaner conditions, which likely reflects differences in time of day and seasonal weather. A natural next step would be to feed these insights into a regression model to **predict pollutant concentrations** under varying times, temperatures and humidity levels.

---

## 🛠️ Tools & Technologies
**Languages & Libraries:** Python · pandas · NumPy · scikit-learn · TensorFlow · Matplotlib  
**Techniques:** Classification · Regression · Neural Networks · K-Means Clustering · PCA · Feature Engineering · EDA · Model Evaluation  
**Environment:** VS Code · Jupyter Notebooks · Git & GitHub

---

## ▶️ How to Run
All datasets are included in this repository, so every notebook can be run straight away.

1. Clone this repository
2. Create a virtual environment: `python -m venv .venv`
3. Activate it: `.venv\Scripts\activate` (Windows) or `source .venv/bin/activate` (Mac/Linux)
4. Install dependencies: `pip install -r requirements.txt`
5. Open any notebook and select **Run All**

> **Note:** The household power dataset (~125 MB) exceeds GitHub's file size limit, so it is included as `household_power_consumption.zip`. The notebook reads the zip file directly, so there is no need to unzip it.

---

## 📂 Data Sources
- **Spambase:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/94/spambase)
- **Individual Household Electric Power Consumption:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/235/individual+household+electric+power+consumption)
- **Air Quality:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/360/air+quality)

---

## 👤 Author
**Yaz Yagmur Sahin**, Mechanical Engineering, Queen Mary University of London  
[GitHub](https://github.com/YazY-Sahin)