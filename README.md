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

A detailed EDA was conducted to uncover patterns and relationships between employee behavior and attrition.

### Key Findings:

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
- Train / Validation / Test split used to ensure unbiased model evaluation
- Validation set used for model tuning
- Test set kept untouched for final performance evaluation

### Model Optimization:
- Applied **GridSearchCV** to tune hyperparameters across models
- Ensured optimal balance between bias and variance

---

## 4. Model Selection & Justification

Three models were evaluated:
- Decision Tree
- Random Forest
- XGBoost

### Performance Comparison:

- **Decision Tree**
  - High recall but very low precision → too many false alarms

- **XGBoost**
  - Balanced performance but lower precision compared to Random Forest

- **Random Forest (Selected Model)**
  - Best balance between precision and recall
  - More stable and generalizable performance

👉 **Why Random Forest?**
It minimized false alarms while still capturing most attrition cases — making it the most practical for real-world HR use.

---

## 5. Final Model Performance

- **Accuracy:** 98%
- **Recall:** 91% → Correctly detects **9 out of 10 employees who leave**
- **Precision:** 93% → Most flagged employees are actually at risk

### Confusion Matrix Insight:
- Very low false positives → HR efforts are not wasted
- Very low missed cases → most risky employees are identified early

---

## 6. Business Impact

The model enables:

- **Proactive intervention** → Identify at-risk employees before resignation
- **Targeted HR actions** → Focus only on high-risk individuals
- **Data-driven decisions** → Move from reactive to predictive HR strategy

👉 Key Insight:
Attrition is primarily a **workload and engagement problem**, not a compensation problem.

---

## 7. Recommendation Snapshot

Based on the analysis and model insights:

### 1. Enforce Workload Limits
- Cap project assignments at 5
- Flag employees exceeding 270 hours/month

### 2. Focus on Mid-Tenure Employees (3–5 years)
- Introduce career development plans
- Improve internal mobility and growth visibility

### 3. Replace Annual Surveys with Quarterly Pulse Checks
- Track satisfaction trends in real-time
- Act before disengagement turns into attrition

### 4. Protect High Performers from Burnout
- Avoid rewarding performance with more workload
- Introduce non-monetary incentives (flexibility, project choice)

### 5. Deploy the Model as a Continuous HR Tool
- Integrate into HR workflows
- Regularly update and retrain with new data

---

## Tools & Technologies

- Python (Pandas, NumPy)
- Data Visualization (Matplotlib, Seaborn)
- Machine Learning (Scikit-learn, XGBoost)
- Model Tuning (GridSearchCV)

---

## Project Assets

- `attrition_analysis.ipynb` → Full analysis and modeling
- `dataset.csv` → Input dataset
- `executive_presentation.pdf` → Business-focused summary

---

## Final Takeaway

Attrition at Salifort Motors is **predictable, concentrated, and preventable**.

By combining data analysis with machine learning, organizations can shift from reacting to attrition → to actively preventing it.
