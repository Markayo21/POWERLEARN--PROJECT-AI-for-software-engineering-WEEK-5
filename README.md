# POWERLEARN--PROJECT-AI-for-software-engineering-WEEK-5 
# Part 1 - Applying the AI Development Workflow

## Overview
This document presents the completion of Part 1 of the AI Development Workflow assignment, focusing on the foundational aspects of an AI project through short answer questions worth 30 points.

## Project: Student Dropout Prediction System

### 1. Problem Definition (6 Points)

**Hypothetical AI Problem:**
> Predicting dropout rates among university students using a combination of academic, behavioural, and socioeconomic data.

**Problem Background:**
- Student retention is a key challenge for educational institutions
- Dropouts negatively impact institutional rankings and student futures
- Many universities lack predictive systems that can flag at-risk students early enough to intervene

**Objectives:**
1. **Early Identification:** Detect potential dropouts before critical decision points
2. **Causal Analysis:** Uncover the most impactful features contributing to attrition
3. **Improve Retention Strategy:** Use data insights to shape personalized interventions and support systems

**Stakeholders:**
- **University Administrators:** Responsible for student welfare, retention policies, and institutional success
- **Students:** Directly impacted by targeted support, guidance, and institutional planning

**Key Performance Indicator (KPI):**
**F1 Score:** An ideal metric for dropout prediction since it balances the risk of false positives (students incorrectly flagged as at-risk) and false negatives (missed predictions). Precision and recall together offer a nuanced performance measure.

### 2. Data Collection & Pre-processing (8 Points)

**Data Sources and Types:**

1. **Student Information System (SIS):** Contains historical data such as grades, attendance, participation in extracurricular activities, and disciplinary records

2. **Student Surveys and Psychometric Assessments:** Self-reported engagement levels, satisfaction, mental health indicators, and financial pressures

**Potential Data Bias:**
**Socioeconomic Bias:** Historical records might show students from low-income families as disproportionately prone to dropping out. If not properly mitigated, this can lead to unethical profiling or unfair prioritization.

**Data Pre-processing Steps:**

1. **Missing Data Handling:**
   - Use mean or median imputation for numerical data
   - Apply domain-specific rules or predictive models for categorical data

2. **Normalization/Scaling:**
   - Standardize numerical features (e.g., GPA, attendance percentage) using Min-Max or Z-score normalization for better model convergence

3. **Categorical Encoding:**
   - Use one-hot encoding for nominal categorical features (e.g., 'Program of Study')
   - Apply ordinal encoding where a meaningful order exists (e.g., satisfaction levels: low to high)

### 3. Model Development (8 Points)

**Model Selected:**
Random Forest Classifier

**Justification for Model Choice:**
- Can handle large feature spaces and mixed data types (numerical + categorical)
- Robust to outliers and noisy data
- Ensemble method reduces risk of overfitting
- Offers feature importance scores, aiding explainability

**Data Splitting Strategy:**
- **Training Set (70%):** Used for initial learning of patterns
- **Validation Set (15%):** Used for hyperparameter tuning and model selection
- **Test Set (15%):** Used for evaluating generalization performance and final metrics

**Hyperparameters to Tune:**

1. **n_estimators:**
   - Number of trees
   - More trees usually improve accuracy but increase computational cost

2. **max_depth:**
   - Limits how deep each tree can grow
   - Prevents overfitting and helps balance precision/recall

### 4. Evaluation & Deployment (8 Points)

**Evaluation Metrics:**

1. **F1 Score:** Essential for balancing sensitivity (recall) and precision in predicting dropout risk. Reduces overreaction to false positives

2. **ROC-AUC Score:** Assesses the model's ability to separate dropout vs. non-dropout cases regardless of threshold. AUC above 0.80 suggests strong classification performance

**Concept Drift:**
**Definition:** Changes in the statistical properties of input data over time which reduce model accuracy. For example, new programs or shifting student demographics may change dropout patterns.

**Monitoring Concept Drift:**
- Deploy real-time evaluation dashboards
- Periodically retrain using newer data
- Use online drift detection tools (e.g., ADWIN, Page-Hinkley) to trigger automatic alerts for retraining

**Deployment Challenge - Scalability:**
**Definition:** The system's ability to scale and maintain performance under increased load, such as being used across multiple departments or campuses.

**Solutions to Scalability:**
- **Containerization:** Use Docker to package the model with all dependencies
- **Orchestration:** Use Kubernetes to scale deployment across cloud servers
- **APIs:** Build RESTful APIs for easy integration with SIS dashboards
- **Cloud Hosting:** Utilize scalable platforms like AWS Lambda, Azure ML, or Google Cloud Run for cost-effective infrastructure

## Ethical Considerations

- **Bias Correction:** Apply re-weighting techniques, fairness-aware algorithms, or data audits
- **Interpretability:** Provide transparency using feature importance plots or model explanations (e.g., SHAP or LIME)
- **Student Privacy:** Protect sensitive data through encryption, anonymization, and robust access controls
- **Consent & Transparency:** Inform students how their data is used and give them the option to opt-in/out

## Repository Structure
```
├── README.md
├── documentation/
│   └── part1_solutions.md
├── src/
│   ├── data_preprocessing/
│   ├── model_training/
│   └── evaluation/
└── requirements.txt
```



# Part 3: Critical Thinking 🧠

## Ethics & Bias (10 points)

### How might biased training data affect patient outcomes in the case study?

Biased training data can severely distort the predictions of an AI model, especially in sensitive domains like healthcare. For example, if the training data underrepresents certain patient groups (e.g., elderly patients, women, or low-income populations), the model might underpredict their risk of readmission. This could lead to inadequate follow-up care, potentially worsening patient outcomes or even risking lives. Such biases may arise from incomplete historical data, socioeconomic disparities, or systemic issues in healthcare documentation.

### Suggest 1 strategy to mitigate this bias:

One effective strategy is to use **fairness auditing tools** such as **IBM AI Fairness 360** to evaluate model bias across different subgroups. The tool can reveal performance gaps (e.g., higher false negatives for a particular demographic), enabling developers to apply techniques like **reweighting** or **balanced sampling** during training. Additionally, involving diverse domain experts during model validation can help catch blind spots early.

---

## Trade-offs (10 points)

### Discuss the trade-off between model interpretability and accuracy in healthcare.

In healthcare, **interpretability is often prioritized over raw accuracy**. Doctors and healthcare providers need to understand *why* a model made a prediction to trust and act on it. A highly accurate but black-box model like a deep neural network may raise concerns if its decisions can’t be explained. In contrast, interpretable models like **logistic regression** or **decision trees** might be slightly less accurate but offer greater transparency, which is crucial for ethical decision-making and regulatory compliance.

### If the hospital has limited computational resources, how might this impact model choice?

With limited computational power, the hospital might avoid resource-intensive models (e.g., deep learning). Instead, lightweight models like **logistic regression**, **random forests with limited depth**, or **gradient-boosted trees with fewer estimators** can offer a good balance of performance and efficiency. Additionally, preprocessing should be optimized to reduce runtime complexity, and deployment could use **batch inference** rather than real-time processing to save resources.

---

# Part 4: Reflection & Workflow Diagram 🔁

## Reflection (5 points)

### What was the most challenging part of the workflow? Why?

The most challenging part was the **model deployment phase**. While building and evaluating the model locally was straightforward, deploying it on a cloud platform like Azure introduced several technical challenges such as environment setup, API integration, and ensuring scalability. It required knowledge beyond Python coding, including DevOps and cloud engineering skills.

### How would you improve your approach with more time/resources?

With more time and resources, I would focus on automating the entire pipeline using **MLOps tools** like MLflow or Kubeflow. I would also implement **monitoring dashboards** to track model performance post-deployment and retrain the model periodically to combat concept drift. Lastly, I would integrate fairness and explainability modules directly into the workflow for transparency.

---

## Diagram (5 points)

Here is a simplified diagram of the AI Development Workflow:

[ Data Collection ]
↓
[ Data Preprocessing ]
↓
[ Model Selection ]
↓
[ Model Training ]
↓
[ Model Evaluation ]
↓
[ Model Deployment ]
↓
[ Monitoring & Feedback ]

sql
Copy
Edit

This workflow follows the CRISP-DM methodology and ensures that AI models are not just accurate, but also ethical, interpretable, and scalable.
