# POWERLEARN--PROJECT-AI-for-software-engineering-WEEK-5 

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
