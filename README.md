# Machine Learning Models for IT Ticket Automation

## Overview
In Fall 2024, as part of the *Analytics in Action* course at Columbia Business School, I collaborated with **Electric**, a Series D startup providing IT support to over 1,000 clients. The project aimed to reduce Electric's monthly operational costs of $1.32 million by automating the classification of IT tickets. By leveraging machine learning models, we achieved **80-90% accuracy** in predicting automatable tickets, saving an estimated **$2 million annually**.

## Problem Statement
Electric handles **44,000 monthly IT tickets** via Slack, email, and website submissions. Most tickets are repetitive and suitable for automation. However, the existing chat-based system relies on human agents, leading to high operational costs. Our goal was to design a model that classifies tickets based on the initial user message, enabling automation and reducing manual intervention.

## Key Challenges & Solutions
1. **Message Misalignment**: 
   - *Challenge*: Conversations contained irrelevant data for initial classification.
   - *Solution*: Focused solely on the **first user message** for category prediction.

2. **Too Many Categories & Asterisks**:
   - *Challenge*: Over 200 categories and excessive masking (asterisks) complicated predictions.
   - *Solution*: Consolidated categories into **8 actionable groups** and filtered over-masked messages.

3. **Data Imbalance**:
   - *Challenge*: Some categories had significantly more examples than others.
   - *Solution*: Balanced the dataset using **SMOTE** (Synthetic Minority Oversampling Technique).

## Model Development
We used **Snowflake’s multilingual-e5-large embedding** to convert text into numerical vectors, capturing semantic and contextual information. Five models were tested:
1. Logistic Regression
2. Random Forest
3. XGBoost
4. LightGBM
5. Multilayer Perceptron (MLP)

**LightGBM** emerged as the top performer with **83% weighted average precision**. To refine predictions, we implemented a **threshold-based approach**:
- **Top Threshold**: Output two predictions if the top prediction’s probability is below a threshold.
- **Gap Threshold**: Output two predictions if the probability difference between the top two predictions is small.

## Business Impact
By automating **15.2% of tickets (6,688 tickets/month)** with **90% precision**, we projected:
- **Monthly Savings**: $180,576
- **Annual Savings**: $2.16 million

## Future Recommendations
1. Remove asterisks and clean the dataset for better performance.
2. Develop APIs for fully automated processes.
3. Expand the model to handle more complex ticket types.

## Product Mockups
We designed mockups to demonstrate the threshold-based model:

![alt text](https://github.com/heysiridu/Electric_LLM_and_MachineLearning/blob/main/ProductMockup/Frame%20139.jpg)
- **High Confidence**: Outputs one prediction.
- **Low Confidence**: Outputs two predictions for agent review.

This project highlights how machine learning can transform IT support, enabling companies like Electric to improve efficiency, reduce costs, and focus on higher-value tasks.

---

**Code Specification**:
- Data Preparation: Snowflake’s multilingual-e5-large embedding.
- Models: Logistic Regression, Random Forest, XGBoost, LightGBM, MLP.
- Evaluation Metric: Precision (minimizing false positives).
- Techniques: SMOTE for data balancing, threshold-based refinement.

**Team Information**:
Chulhee Kim, Frank Li, Gufeng Guo, Siri Du
