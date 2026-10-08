# Customer Churn Retention AI

An end-to-end customer churn prediction and retention system using machine learning, explainable AI, counterfactual simulation, and an AI-powered chatbot.

## Overview

This capstone project was designed to go beyond simply predicting which customers are likely to churn.

The system was built to:

- Predict customer churn risk
- Explain the main drivers behind each prediction
- Test possible retention interventions
- Recommend personalized retention actions
- Deliver recommendations through an AI chatbot

## Live Chatbot Demo

https://churn-chatbot.vercel.app

## Project Demo

A recorded walkthrough of the project is included in this repository:

`customer_churn_project_demo.mp4`

## Dataset

The project uses the IBM Telco Customer Churn dataset from Hugging Face.

The dataset includes:

- 7,043 customer records
- 33 original features
- Demographic, service, billing, contract, and tenure information
- Binary churn target
- Approximately 27% churn

## Project Approach

The project followed this end-to-end workflow:

1. Exploratory data analysis
2. Data leakage identification and removal
3. Feature engineering
4. Baseline machine learning models
5. XGBoost tuning
6. SHAP explainability
7. Synthetic data augmentation
8. Customer risk scoring
9. Counterfactual intervention testing
10. AI-generated retention messaging
11. Customer retention chatbot

## Data Leakage Removal

An important part of the project was identifying and removing variables that revealed information about the final churn outcome.

Twelve leakage-related columns were removed, including:

- Satisfaction Score
- Total Charges
- Total Revenue
- Total Refunds
- Total Long Distance Charges
- Total Extra Data Charges
- CLTV
- Customer Status
- Churn Score
- Churn Label
- Churn Category
- Churn Reason

Removing these features prevented unrealistically high model performance and forced the model to learn from realistic customer behavior and account information.

## Feature Engineering

Additional variables were created to improve the analysis, including:

- Total Services
- Charge Per Service

Categorical variables were also encoded and prepared for machine learning.

## Machine Learning

Multiple models were evaluated, including:

- Logistic Regression
- Random Forest
- XGBoost

XGBoost was selected as the primary model because of its strong performance on structured customer data and its ability to integrate with SHAP for explainability.

The model was tuned using RandomizedSearchCV with 5-fold cross-validation.

## Explainable AI with SHAP

SHAP was used to explain why customers were predicted to be at risk of churn.

Important churn-related factors identified in the project included:

- Contract type
- Number of referrals
- Customer tenure
- Monthly charge
- Number of dependents
- Internet service type
- Average monthly data usage

This allowed the system to provide customer-specific explanations instead of only returning a churn probability.

## Customer Risk Tiers

Instead of treating churn as only a yes-or-no prediction, customers were placed into risk tiers such as:

- Low Risk
- Medium Risk
- High Risk

This makes the model more useful for prioritizing customers who may need retention attention.

## Synthetic Data Augmentation

The project used SDV to generate synthetic minority-class data and address class imbalance.

The project compared:

- Baseline models
- Tuned models
- Class-weighted models
- SDV-augmented models

This helped evaluate whether synthetic data provided additional value beyond standard class-weighting techniques.

## Counterfactual Retention Testing

The system went beyond prediction by testing possible customer retention interventions.

Examples included:

- Contract upgrades
- Additional support services
- Service changes
- Retention incentives

The purpose was to estimate which action could have the greatest effect on reducing a customer's predicted churn risk.

## AI-Powered Retention Chatbot

The final project includes a live customer retention chatbot.

The chatbot demonstrates how the predictive model can be turned into an interactive business application.

A typical customer journey includes:

1. Customer enters the chat
2. Customer profile is loaded
3. XGBoost calculates churn probability
4. A risk tier is assigned
5. SHAP identifies the main churn drivers
6. Possible retention interventions are tested
7. The chatbot asks targeted questions
8. A personalized retention offer is recommended

The chatbot is designed to use customer-specific risk factors rather than relying only on a fixed script.

## Example Customer Journey

In the project demonstration, a customer could receive a result such as:

- Churn Probability: 72%
- Risk Tier: High
- Main Drivers:
  - Month-to-month contract
  - Low tenure
  - No online security

The system then tests possible interventions and recommends an appropriate retention strategy.

An example offer from the project was:

> Switch to an annual plan and save 25%, plus receive free Tech Support for 3 months.

## Model Validation

The project used several approaches to evaluate model performance, including:

- Train/test evaluation
- RandomizedSearchCV
- 5-fold cross-validation
- Baseline model comparison
- Class-weighted modeling
- SDV-augmented modeling
- Counterfactual simulation
- Statistical testing

The project presentation reported approximate performance for the SDV-augmented model of:

- Accuracy: ~0.81
- Precision: ~0.65
- Recall: ~0.80
- F1 Score: ~0.72
- AUC-ROC: ~0.87

Exact results may vary depending on random seeds and synthetic data generation.

## Technologies Used

- Python
- Jupyter Notebook
- pandas
- NumPy
- scikit-learn
- XGBoost
- SHAP
- SDV
- SciPy
- Matplotlib
- Seaborn
- Hugging Face
- Machine Learning
- Explainable AI
- Synthetic Data Generation
- Counterfactual Analysis
- Large Language Models
- Vercel

## Project Files

- `customer_churn_capstone.ipynb` — primary machine learning and analysis notebook
- `customer_churn_final_presentation.pptx` — final capstone presentation
- `customer_churn_project_demo.mp4` — recorded project demonstration
- `README.md` — project documentation

The live chatbot was deployed separately and can be accessed using the link above.

## Key Findings

The project identified several important churn patterns:

- Month-to-month customers showed significantly higher churn risk
- Customers with lower tenure were especially vulnerable
- Long-term contracts were among the strongest protective factors
- Customers using more services generally showed lower churn
- Monthly charges and referral behavior were important predictive signals

## Key Project Decisions

Several decisions were made to improve the quality and realism of the project:

- Removed leakage variables that caused unrealistic model performance
- Used XGBoost as the primary predictive model
- Used SHAP for model explainability
- Used SDV to address class imbalance
- Used risk tiers instead of relying only on binary predictions
- Used counterfactual testing to connect predictions to possible actions

## Limitations

- The dataset contains only California customers
- The project does not include unstructured data such as call transcripts, chat logs, or emails
- The dataset represents a single snapshot rather than customer behavior over time
- Synthetic data does not perfectly reproduce the original dataset
- Counterfactual simulations do not prove true causality
- A production system would require integration with real CRM and customer data systems
- AI-generated recommendations would require human oversight in a real business environment

## Future Improvements

Future improvements could include:

- CRM integration
- Real-time scoring through an API
- Production-ready data pipelines
- Integration with real retention offers
- More advanced chatbot conversations
- NLP analysis of customer calls, chats, and emails
- Time-based customer behavior analysis
- Real A/B testing of retention strategies
- Measurement of actual ROI and revenue impact
- Continuous learning from customer outcomes

## Project Outcome

This project demonstrates how machine learning can be extended beyond prediction into an explainable decision-support system.

Instead of only answering:

> Which customers are likely to churn?

the system is also designed to answer:

> Why are they likely to churn, and what action could help retain them?

The final solution combines predictive modeling, explainable AI, intervention testing, and AI-driven customer engagement into one end-to-end retention workflow.
