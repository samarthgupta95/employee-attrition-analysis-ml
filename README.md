# Employee Attrition Analysis & Prediction (Salifort Motors)

## 1. Business Context & Problem

Salifort Motors is experiencing increasing employee attrition, impacting productivity, team stability, and overall business performance.

The HR team lacked clarity on:
- What factors are driving employees to leave
- Whether attrition can be predicted before it happens
- What actionable steps can reduce employee turnover

Replacing an employee can cost up to 50–200% of their annual salary, making attrition not just an HR issue, but a significant business risk.

---

## 2. Exploratory Data Analysis (EDA) & Key Insights

### Data Preparation & Cleaning:
- Removed **3008 duplicate records** from 14,999 entries to ensure data integrity
- Checked for **missing/null values** (none significant)
- Standardized and cleaned **column names for consistency**
- Analyzed **feature distributions** to understand variable behavior
- Identified and reviewed **outliers** (especially in workload and tenure)

### Key Insights:

- **Attrition is not random** — it follows clear, measurable patterns

- **Low Satisfaction = High Risk**
  - Employees with satisfaction levels below ~0.5 show significantly higher attrition

- **Workload is a critical driver**
  - Employees working **270+ hours/month** or handling **6+ projects** show extremely high attrition rates
  - Overworked employees had up to **87% likelihood of leaving**

- **Tenure effect (3–5 years)**
  - Mid-tenure employees are the most vulnerable group, indicating stagnation or unmet expectations

- **Performance paradox**
  - High-performing employees are leaving at similar rates as low performers → burnout, not incompetence

- **Low signal features**
  - Department, promotions, and work accidents showed minimal impact on attrition

---

## 3. Machine Learning Approach

### Feature Engineering:
- Created **overwork_flag** to capture extreme workload conditions (hours + projects)
- Encoded categorical variables (salary levels)
- Removed low-impact features (department, work_accident, promotion_last_5years)

### Data Splitting Strategy:
- Train / Validation / Test split to ensure unbiased evaluation
- Validation set used for tuning
- Test set kept untouched for final performance

### Model Optimization:
- Applied **GridSearchCV** for hyperparameter tuning
- Focused on balancing **precision vs recall** for business usability

---

## 4. Model Selection & Justification

Three models were evaluated:

### Decision Tree
- Precision: **0.33**
- Recall: **0.94**
- Accuracy: **0.67**
- F1: **0.41**
- Insight: High recall but poor precision → too many false alarms

### XGBoost
- Precision: **0.70**
- Recall: **0.94**
- Accuracy: **0.92**
- F1: **0.80**
- Insight: Strong performance but slightly less balanced than Random Forest

### Random Forest (Selected Model)
- Precision: **0.93**
- Recall: **0.92**
- Accuracy: **0.97**
- F1: **0.92**

👉 **Why Random Forest?**
It achieved the best trade-off between precision and recall, minimizing false alarms while still identifying most employees who leave — making it the most practical model for HR deployment.

---

## 5. Final Model Performance

- **Accuracy:** 98%
- **Recall:** 92% → Detects **9 out of 10 employees who leave**
- **Precision:** 93% → Most flagged employees are actually at risk

### Confusion Matrix Insight:
- Very low false positives → HR efforts remain focused
- Very low missed cases → high-risk employees are rarely overlooked

---

## 6. Business Impact

The model enables:

- **Proactive intervention** → Identify at-risk employees before resignation
- **Targeted HR action** → Focus on high-risk individuals only
- **Data-driven strategy** → Shift from reactive to predictive HR

👉 Key Insight:
Attrition is primarily a **workload and engagement problem**, not a compensation problem.

---

## 7. Recommendation Snapshot

### 1. Enforce Workload Limits
- Cap project assignments at 5
- Flag employees exceeding 270 hours/month

### 2. Focus on Mid-Tenure Employees (3–5 years)
- Introduce career development plans
- Improve internal mobility

### 3. Replace Annual Surveys with Quarterly Pulse Checks
- Track satisfaction continuously
- Act before disengagement escalates

### 4. Protect High Performers from Burnout
- Avoid rewarding performance with more workload
- Introduce flexibility and non-monetary incentives

### 5. Deploy the Model as a Continuous HR Tool
- Integrate into HR workflows
- Retrain regularly with updated data

---

## Tools & Technologies

- Python (Pandas, NumPy)
- Data Visualization (Matplotlib, Seaborn)
- Machine Learning (Scikit-learn, XGBoost)
- Model Tuning (GridSearchCV)
- Model Evaluation Metrics (Recall score, Precision score, F1 score, Accuracy score)

---

## Project Assets

- `attrition_analysis.ipynb` → Full analysis and modeling  
- `dataset.csv` → Dataset  
- `executive_presentation.pdf` → Executive summary  

---

## Final Takeaway

Attrition at Salifort Motors is **predictable, concentrated, and preventable**.

With the right data and model, organizations can move from reacting to attrition → to actively preventing it.
