# Customer Purchase Prediction

## 🛒 Retail / Marketing: Customer Purchase Predictor — TechCrush Bootcamp

---

## 📘 Project Overview

This project presents the **Customer Purchase Predictor**, a machine learning solution developed during the **TechCrush Data Science Bootcamp**. The goal is to leverage data-driven insights and predictive modeling to help e-commerce businesses understand and predict customer purchasing behavior.

Our model analyzes key browsing and demographic indicators to predict whether a customer will complete a purchase, empowering retail businesses to optimize marketing campaigns, personalize offers, and allocate advertising budgets more effectively.

> **Tagline:** *Turning Browsing Behavior into Business Intelligence*

---

## 🧩 Project Structure

```
Customer_Purchase_Prediction/
│
├── Customer_Purchase_Prediction.ipynb   # Main project notebook
├── data/                                # Contains raw and cleaned datasets
│   ├── online_shoppers_intention.csv
│   └── cleaned_shoppers.csv
├── models/                              # Trained model files
│   ├── optimized_random_forest.pkl
│   └── optimized_lightgbm.pkl
├── images/                              # Visualizations and plots
└── README.md                            # Project documentation
```

---

## 📂 Data Description

The dataset contains online shopper session records with features like:

- `Month`, `VisitorType`, `Weekend`, `SpecialDay` — Temporal & demographic info
- `ProductRelated`, `ProductRelated_Duration` — Product browsing behavior
- `Administrative`, `Administrative_Duration` — Account/admin page activity
- `Informational`, `Informational_Duration` — Informational page activity
- `ExitRates`, `BounceRates`, `PageValues` — Session quality metrics
- `TrafficType`, `Region`, `Browser`, `OperatingSystems` — Technical attributes
- `Revenue` — **Target Variable** (True = Purchase Made, False = No Purchase)

After cleaning and preprocessing, the data was stored as `cleaned_shoppers.csv` for reproducibility.

---

## 🔍 Exploratory Data Analysis (EDA)

Our EDA covered the following:

### Understand Target Variable
- Checked class balance between **Purchase (Revenue=True)** vs **No Purchase (Revenue=False)**

### Univariate Analysis
- Distribution of numerical features using histograms and boxplots
- Frequency of categorical variables using bar charts

### Bivariate Analysis (Feature vs Purchase)
- Compared averages between purchasers and non-purchasers
- Analyzed conversion rate by category
- Plotted boxplots grouped by purchase status

### Correlation Analysis
- Generated correlation matrix heatmap
- Identified multicollinearity between features

### Behavioral Pattern Detection
- Session duration vs purchase likelihood
- Pages viewed vs purchase conversion
- Demographics vs conversion rate

### Outlier Analysis
- Identified extreme values affecting purchase behavior

### Feature Insights
- Identified strong predictors of purchase intent
- Identified weak or irrelevant features for model simplification

### Key Business Insights
- **Who is most likely to purchase?** — Returning visitors with high product page engagement
- **What behaviors increase conversion?** — Longer time on product pages, lower exit rates
- **What features matter most?** — `ProductRelated_Duration`, `ExitRates`, `PageValues`, `Month`

---

## 🤖 Model Development

Two core models were trained, evaluated and optimized:

| Model | Type | Optimization |
|-------|------|-------------|
| Random Forest | Ensemble (Bagging) | ✅ Optuna (50 trials) |
| LightGBM | Gradient Boosting | ✅ Optuna (50 trials) |

The modeling pipeline included:

- Data preprocessing and encoding
- Stratified K-Fold cross-validation (5-fold)
- Hyperparameter tuning with **Optuna** (F1-weighted scoring)
- Model saving via **joblib**

---

## 📊 Model Evaluation

| Model | Accuracy | ROC-AUC | Notes |
|-------|----------|---------|-------|
| Random Forest (Baseline) | — | — | No tuning |
| LightGBM (Baseline) | — | — | No tuning |
| Optimized Random Forest | — | 0.9289 | Tuned with Optuna |
| **Optimized LightGBM** | — | **0.9304** | ✅ Best Model |

**Best Model: ✅ Optimized LightGBM (ROC-AUC = 0.9304)**

---

## 🏆 Feature Importance Findings

| Feature | Random Forest Rank | LightGBM Rank | Business Meaning |
|---------|-------------------|---------------|-----------------|
| ProductRelated_Duration | 3rd | 🥇 1st | Time on product pages = high purchase intent |
| ProductRelated | 4th | 2nd | Number of product pages visited |
| ExitRates | 2nd | 3rd | Page abandonment rate |
| Month | 6th | 4th | Seasonal purchasing patterns |
| Administrative_Duration | 7th | 5th | Time on account/checkout pages |
| PageValues | 🥇 1st | 7th | Revenue value of pages visited |
| Weekend, SpecialDay, Browser | Near zero | Near zero | Negligible predictive value |

---

## 💾 Model Saving & Loading

The trained models were saved in the `/models/` directory:

```python
import joblib

# Save models
joblib.dump(best_rf,   "models/optimized_random_forest.pkl")
joblib.dump(best_lgbm, "models/optimized_lightgbm.pkl")

# Load models
loaded_rf   = joblib.load("models/optimized_random_forest.pkl")
loaded_lgbm = joblib.load("models/optimized_lightgbm.pkl")
```

---

## 🛠️ Tools & Libraries Used

- **Languages:** Python 3.x
- **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `lightgbm`, `optuna`, `joblib`
- **Environment:** Jupyter Notebook / Google Colab

---

## 🚀 How to Run the Project Locally

**1. Clone the repository:**
```bash
git clone https://github.com/<your-username>/Customer_Purchase_Prediction.git
cd Customer_Purchase_Prediction
```

**2. Install dependencies:**
```bash
pip install -r requirements.txt
```

**3. Run the notebook:**
```bash
jupyter notebook Customer_Purchase_Prediction.ipynb
```

---

## 📌 Key Business Recommendations

1. **Deploy Optimized LightGBM** as the primary production model for predicting customer purchase behavior
2. **Invest in product page optimization** — enhance product descriptions, images, reviews and AI-powered recommendations
3. **Reduce exit and bounce rates** — conduct A/B testing, improve page load speeds and add clear calls-to-action
4. **Launch seasonal campaigns** — align flash sales and personalized promotions around peak purchasing months
5. **Streamline checkout and account management** — reduce friction in account and checkout flows
6. **Optimize traffic acquisition** — reallocate budgets toward highest-converting traffic sources
7. **Simplify future models** — remove `Weekend`, `SpecialDay`, `Browser`, `OperatingSystems` and `Region`

---

## 🔮 Future Improvements

- Real-time purchase prediction integrated into the e-commerce platform
- Deployment as a REST API or Streamlit web application
- Personalized product recommendation engine based on browsing patterns
- Retraining pipeline with live customer data to handle concept drift

---

👩🏽‍💻 Team Credits — Team Phoenix

Institution: TechCrush Data Science BootcampTagline: Customer Purchase Prediction

Member


1. Olabode Olaniyi Bolaji - DS/2025/TC5/187 

2. Jalloh Mohamed Lamarana - DS/2025/TC5/049

3. Oyebade Israel Ekundayo - DS/2025/TC5/130
   
4. Akande Moses Oluwafemi - DS/2025/TC5/053

5. Adesanya Robiat Yetunde - DS/2025/TC5/122

6. Mauton Esther Pedetin - DS/2025/TC5/177

7. Amarachi Gift Onyediako - DS/2025/TC5/135

8. Uchenna Anthony Cletus - DS/2025/TC5/090

9. Godstime Oigiangbe - DS/2025/TC5/142

10. AbdulRahman Abdulmalik Adewale - DS/2025/TC5/050

11. Moruwawon Pelumi Victoria - DS/2025/TC5/019

12. Nicholas Senu - DS/2025/TC5/021


## 💬 Acknowledgements

Special thanks to **TechCrush Data Science Bootcamp** for guidance, mentorship, and providing the platform to learn, collaborate, and build data solutions for real-world business problems most especially Miss Gift Ukpoweh.

> *"When data meets determination, impact happens."* — Team Phoenix
