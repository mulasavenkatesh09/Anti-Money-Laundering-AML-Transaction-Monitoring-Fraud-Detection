# Anti-Money Laundering (AML) Transaction Monitoring & Financial Risk Analytics

![Python](https://img.shields.io/badge/Python-Analytics-blue)
![Tableau](https://img.shields.io/badge/Tableau-Dashboard-orange)
![AML](https://img.shields.io/badge/Domain-Financial%20Risk-green)

This project develops an **end-to-end AML transaction monitoring and financial risk analytics solution** using the **SAML-D synthetic transaction monitoring dataset**. By learning from historical transaction behaviour, the solution helps financial institutions detect high-risk activity, strengthen Anti-Money Laundering (AML) controls, and support compliance decision-making through data-driven insights.

***

## Table of Contents

1. [Key Resources](#key-resources)  
2. [Project Overview](#project-overview)  
3. [Analytics Workflow](#analytics-workflow)  
4. [Dataset Content](#dataset-content)  
5. [Personas & Stakeholders](#personas--stakeholders)  
6. [Business Requirements](#business-requirements)  
7. [Hypotheses and Validation](#hypotheses-and-validation)  
8. [Project Plan](#project-plan)  
9. [Rationale for Visualisations](#rationale-for-visualisations)  
10. [Analysis Techniques Used](#analysis-techniques-used)  
11. [Key Analytical Outcomes](#key-analytical-outcomes)  
12. [Ethical Considerations](#ethical-considerations)  
13. [Dashboard Design](#dashboard-design)  
14. [Unfixed Bugs](#unfixed-bugs)  
15. [Development Roadmap](#development-roadmap)  
16. [Deployment](#deployment)  
17. [Main Data Analysis Libraries](#main-data-analysis-libraries)  
18. [Credits](#credits)

---

## Key Resources

- **Dataset**: https://www.kaggle.com/datasets/berkanoztas/synthetic-transaction-monitoring-dataset-aml

---

## Project Overview

This project focuses on building a robust **Data Analytics with AI** solution to predict financial risk and detect suspicious transaction patterns using synthetic banking data.

- The solution analyses millions of transactions to identify **high-risk behaviour** that may indicate potential financial crime.
- The models generate **transaction-level risk flags** and **customer-level risk scores**, enabling proactive monitoring.
- Interactive AML monitoring dashboards were developed in **Tableau and Power BI** for operational risk analysis and compliance reporting.
- The ultimate goal is to empower financial institutions with **data-driven insights** to minimise financial losses and strengthen AML compliance processes.

---

## Analytics Workflow

The project follows a real-world financial analytics workflow used in AML monitoring environments:

Raw Transaction Data  
→ Data Cleaning & Feature Engineering (Python)  
→ Risk Modelling & Suspicious Pattern Detection  
→ Customer Risk Scoring  
→ Interactive Monitoring Dashboards (Tableau & Power BI)  
→ Business Decision Support

This separation between analytical modelling and operational dashboards reflects enterprise AML monitoring systems used in financial institutions.

---

## Dataset Content

The project uses the **Anti Money Laundering Transaction Data (SAML-D)** dataset created by Oztas et al. and published on Kaggle.

Key characteristics:

- ~9.5 million transactions with 12 features and 28 typologies (11 normal, 17 suspicious).
- Only ~0.1039% of transactions are labelled as suspicious, creating a highly imbalanced classification problem.

Main fields:

- **Time and Date** – chronological ordering of transactions.
- **Sender / Receiver Account IDs** – behavioural relationships.
- **Amount** – transaction value.
- **Payment Type** – credit card, debit card, cash, ACH, cross-border, cheque.
- **Sender / Receiver Bank Location** – includes high-risk regions.
- **Payment Currency & Receiver Currency** – enables mismatch detection.
- **`is_suspicious`** – binary suspicious transaction label.
- **`type`** – laundering typology classification.

Suspicious transaction patterns are aggregated into **customer-level risk features** to estimate overall risk exposure.

---

## Personas & Stakeholders

Three primary personas guide system design and evaluation.

### Compliance Officer

- Reviews AML alerts and prepares regulatory reports.
- Requires transparent risk scores and audit-ready summaries.

![Dashboard_Ann_Patel](assets/images/Dashboard_Ann_Patel.png)

Key dashboard insights:

- 950K transactions monitored
- 1,011 suspicious alerts detected
- £47.14M suspicious value identified
- Structuring identified as most common laundering typology

![Tableau_Dashboard](assets/images/Tableau_Dashboard.png)

The Tableau dashboard provides a high-level transaction monitoring overview:

- Weekly suspicious trends across payment types
- Geographic risk exposure
- Transaction volume distribution by amount bands
- Comparison of normal vs suspicious activity patterns

---

### Data Analyst

- Maintains risk models and evaluates performance.
- Requires clean features, explainability, and model comparisons.

### Branch Manager

- Oversees operational risk at branch level.
- Needs simplified dashboards and customer risk segmentation.

These personas drive dashboard design, analytics outputs, and explainability requirements.

---

## Business Requirements

Primary objective:

**Reduce financial losses and compliance risk by identifying high-risk customers and transactions early.**

Key questions:

- Which transaction behaviours correlate with suspicious activity?
- Can models predict suspicious transactions reliably despite imbalance?
- How can compliance teams operationalise insights through dashboards?

Requirements:

- Transaction-level explainable risk flags
- Customer-level risk scoring
- Interactive dashboards for monitoring and investigation

---

## Hypotheses and Validation

### Hypothesis 1
Certain transaction behaviours correlate strongly with suspicious activity.

Validation:
EDA, correlation analysis, and feature importance.

### Hypothesis 2
Customers with repeated suspicious patterns exhibit higher overall risk.

Validation:
Customer aggregation metrics and behavioural comparison.

### Hypothesis 3
Machine learning models can detect suspicious transactions despite extreme imbalance.

Validation:
Multiple classifiers and cost-sensitive evaluation metrics.

---

## Project Plan

1. **ETL & Data Management**
   - Load and validate SAML-D dataset.
   - Clean schema and store processed data.

2. **Exploratory Data Analysis**
   - Analyse distributions, typologies, regions, and currencies.

3. **Feature Engineering**
   - Transaction features (amount, time, currency mismatch).
   - Customer aggregates (frequency, diversity, suspicious ratio).

4. **Evaluation & Explainability**
   - Classification metrics and confusion matrices.
   - Feature importance analysis.

5. **Dashboarding & Reporting**
   - Tableau & Power BI dashboards aligned with stakeholder needs.

---

## Rationale for Visualisations

Visualisations support both technical and business users.

- **Executive Overview**
  - KPIs, typologies, and regional trends.

- **Risk Drivers**
  - Heatmaps, stacked charts, and amount distributions.

- **Customer Risk**
  - Risk score distributions and segmentation.

- **Model Performance**
  - Confusion matrices and feature importance visuals.

---

## Analysis Techniques Used

### Data Preparation & EDA

- `pandas`, `numpy`
- Statistical analysis and visual exploration (`seaborn`, `matplotlib`)

ETL Notebook:

`01_etl_transaction_risk.ipynb`

![ETL1](assets/images/ETL1.png)
![ETL2](assets/images/ETL2.png)

EDA Notebook:

`02_eda_exploration.ipynb`

![EDA1](assets/images/EDA1.png)
![EDA2](assets/images/EDA2.png)
![EDA3](assets/images/EDA3.png)

### Feature Engineering

`03_statistical_analysis.ipynb`

![FE1](assets/images/FE1.png)
![FE2](assets/images/FE2.png)

### Machine Learning

Algorithms used:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

Handling imbalance:

- Class weights
- SMOTE / undersampling

`04_machine_learning.ipynb`

![ML1](assets/images/ML1.png)
![ML2](assets/images/ML2.png)
![ML3](assets/images/ML3.png)
![ML4](assets/images/ML4.png)

---

## Key Analytical Outcomes

- Identified behavioural transaction patterns associated with suspicious activity.
- Generated customer-level risk scores enabling prioritised investigation workflows.
- Demonstrated effective detection despite extreme class imbalance (~0.1% suspicious rate).
- Delivered interactive dashboards supporting compliance monitoring and operational decision-making.

---

## Ethical Considerations

- Behaviour-focused modelling reduces bias risks.
- Dataset is synthetic, preserving privacy.
- Models act as **decision-support tools**, not automated enforcement systems.
- Human-in-the-loop review remains essential.

---

## Dashboard Design

### Compliance View
- Suspicious trends over time
- Typologies and geographic corridors
- Case drill-down analysis

### Risk Modelling View
- Model comparison metrics
- Feature importance diagnostics

### Branch View
- Risk KPIs by branch
- High-risk customer monitoring

---

## Development Roadmap

Future enhancements:

- Network graph analysis of account relationships
- Graph neural network experimentation
- Automated model retraining and drift monitoring

---

## Deployment

Analytical outputs were operationalised through interactive **Tableau and Power BI dashboards**, simulating real AML transaction monitoring environments used by compliance teams.

- Tableau Workbook: `Dashboard_AML_Transaction_Detection.twbx`
- Power BI Report: `Dashboard_AML.pbix`

---

## Main Data Analysis Libraries

- **pandas** — data manipulation
- **numpy** — numerical operations
- **scikit-learn** — ML modelling and preprocessing
- **matplotlib** — visualisation
- **seaborn** — statistical visualisation

---

## Credits

- **Dataset:** Anti Money Laundering Transaction Data (SAML-D) by B. Oztas et al.  
  https://www.kaggle.com/datasets/berkanoztas/synthetic-transaction-monitoring-dataset-aml

- **Research Reference:**  
  Oztas et al., *Enhancing Anti-Money Laundering: Development of a Synthetic Transaction Monitoring Dataset*, IEEE ICEBE 2023.  
  https://ieeexplore.ieee.org/document/10356193
