# 🎮 Analyzing Video Game Global Sales & Publishers

**Python | Pandas | NumPy | Matplotlib | Seaborn | Scikit-learn | Statsmodels**

## 📌 Project Overview

This project analyzes video game sales data to identify factors associated with global video game sales and determine whether regional sales and release characteristics can predict whether a game was published by Nintendo.

The analysis uses **16,598 video games** and combines exploratory data analysis, statistical modeling, machine learning, and model evaluation.

### Research Questions

1. **What regional markets drive global video game sales?**
2. **Can regional sales and release characteristics predict whether a game was published by Nintendo?**

---

## 🗂️ Dataset

The dataset contains information on video game titles, platforms, genres, publishers, release years, regional sales, and global sales.

### Key Variables

| Variable       | Description                         |
| -------------- | ----------------------------------- |
| `Name`         | Video game title                    |
| `Platform`     | Platform the game was released on   |
| `Year`         | Release year                        |
| `Genre`        | Video game genre                    |
| `Publisher`    | Game publisher                      |
| `NA_Sales`     | North American sales (millions)     |
| `EU_Sales`     | European sales (millions)           |
| `JP_Sales`     | Japanese sales (millions)           |
| `Other_Sales`  | Sales from other regions (millions) |
| `Global_Sales` | Total worldwide sales (millions)    |

Missing observations were removed before modeling. A binary `Is_Nintendo` variable was also created for the classification analysis, where Nintendo-published games were coded as `1` and all other games as `0`.

---

# 🔎 Exploratory Data Analysis

The project began with exploratory analysis to understand the structure and distribution of the dataset.

### EDA included:

* Dataset structure and descriptive statistics
* Publisher frequency analysis
* Correlation analysis
* Global sales distribution
* Genre distribution
* Global sales by genre
* Top 10 publishers

The sales variables were highly right-skewed, with many games generating relatively low sales and a small number of titles generating extremely high sales. A log transformation was therefore used to better visualize the distribution of global sales.

The correlation analysis showed strong positive relationships between regional sales and global sales, particularly North American and European sales.

---

# 📈 Regression Analysis

### Research Question

> **What regional markets drive global sales?**

Two regression models were compared:

* **Linear Regression**
* **Random Forest Regression**

### Features

The regression models used:

* `NA_Sales`
* `EU_Sales`
* `Year`

### Linear Regression Results

| Metric |     Result |
| ------ | ---------: |
| R²     |  **0.967** |
| RMSE   | **0.3303** |

The Linear Regression model produced a very strong fit, with an R² of **0.967** and an RMSE of **0.3303**. North American sales were identified as one of the strongest predictors, while European sales were also statistically significant.

### Random Forest Regression

| Metric |     Result |
| ------ | ---------: |
| R²     | **0.8368** |
| RMSE   | **0.7390** |

The Random Forest Regressor produced a lower R² and higher RMSE than Linear Regression. Five-fold cross-validation was also used to evaluate model generalization, with a maximum tree depth of **9** selected through cross-validation.

### Regression Conclusion

**Linear Regression was selected as the preferred regression model** because it achieved both a higher R² and lower RMSE.

One important limitation is that `Global_Sales` is calculated from regional sales, meaning the strong relationship between regional sales and global sales is partly structural rather than evidence of independent predictive power.

---

# 🤖 Classification Analysis

### Research Question

> **Can regional sales and release characteristics predict whether a game was published by Nintendo?**

Three classification models were evaluated:

* **Logistic Regression**
* **Decision Tree**
* **Random Forest**

### Features

The models used:

* `NA_Sales`
* `EU_Sales`
* `Year`

### Model Performance

| Model               | Accuracy | Precision |   Recall | F1 Score |
| ------------------- | -------: | --------: | -------: | -------: |
| Logistic Regression | **0.96** |      0.39 |     0.05 |     0.09 |
| Decision Tree       |     0.94 |      0.24 | **0.18** | **0.20** |
| Random Forest       | **0.96** |  **0.40** |     0.10 |     0.16 |

Although Logistic Regression and Random Forest achieved approximately **96% accuracy**, accuracy was not the most useful metric because Nintendo-published games represented a relatively small portion of the dataset.

The **Decision Tree** achieved the highest F1 score (**0.20**) and recall (**0.18**), making it the preferred classification model for identifying Nintendo-published games.

Five-fold cross-validation was also performed to evaluate classification model stability and identify an optimal tree depth.

---

# 💡 Key Findings

### 1. North American sales were highly influential

North American sales had the strongest regression coefficient among the evaluated regional variables, indicating a strong relationship with global sales.

### 2. European sales were also statistically significant

European sales demonstrated a statistically significant relationship with global sales in the regression analysis.

### 3. Linear Regression outperformed Random Forest Regression

Linear Regression achieved:

* **R² = 0.967**
* **RMSE = 0.3303**

compared with Random Forest Regression:

* **R² = 0.8368**
* **RMSE = 0.7390**

### 4. Classification accuracy was misleading

The classification models achieved high overall accuracy, but their ability to correctly identify Nintendo games was limited by class imbalance.

### 5. Decision Tree was the best classification model

The Decision Tree produced the highest F1 score and recall, making it more appropriate than the other classification models for the project's objective.

---

# 🛠️ Technologies & Libraries

```text
Python
├── Pandas
├── NumPy
├── Matplotlib
├── Seaborn
├── Scikit-learn
└── Statsmodels
```

### Machine Learning Techniques

**Regression**

* Linear Regression
* Random Forest Regression
* 5-Fold Cross-Validation

**Classification**

* Logistic Regression
* Decision Tree Classification
* Random Forest Classification
* Confusion Matrices
* ROC/AUC
* Precision
* Recall
* F1 Score
* 5-Fold Cross-Validation

---

# 📁 Repository Structure

```text
video-game-sales-analysis/
│
├── data/
│   └── vgsales.csv
│
├── Nguyen_Kenny_DATA201_Final-2.ipynb
├── Nguyen_Kenny_DATA201_Executive_Summary.pdf
└── README.md
```

---

# 📚 References

* Lahiguera, A. (2024). *Media & Entertainment Video Games Sector*. U.S. Department of Commerce.
* Smith, G. (2016). *Video Game Sales*. Kaggle.

---

## 🎯 Skills Demonstrated

This project demonstrates my ability to:

* Perform exploratory data analysis with Python
* Clean and prepare real-world datasets
* Analyze relationships between variables
* Build and interpret statistical regression models
* Develop machine learning classification models
* Evaluate models using multiple performance metrics
* Apply cross-validation to assess model performance
* Identify and account for class imbalance
* Communicate analytical findings through visualizations and written conclusions
