# Kaiburr Task 5 - Text Classification on Consumer Complaint Dataset  

**Name** : Mathivathani G
**Date** : 28.09.2025

This repository contains my solution for **Task 5: Data Science Example** as part of The Assessment. The goal was to perform **multi-class text classification** on the [Consumer Complaint Database](https://catalog.data.gov/dataset/consumer-complaint-database).  

## Problem Statement  
We had to classify consumer complaints into four categories:  

- **0**: Credit reporting, repair, or other  
- **1**: Debt collection  
- **2**: Consumer Loan  
- **3**: Mortgage  

---

## Approach  

### 1. Exploratory Data Analysis (EDA)  
- Dataset size: ~6.82 GB (too large to load fully).  
- Chosen fields:  
  - **Text** → `Consumer complaint narrative`  
  - **Label** → `Product`  
- Created a **balanced sample** of **20,000 complaints** (5,000 per class).  
- Average complaint length ~1,131 characters, with some narratives exceeding 30k characters.  
- Frequent words include `"xxxx"`, `"the"`, `"to"`, `"and"`, `"my"` etc.  

### 2. Text Preprocessing  
- Lowercasing, URL/email removal, special character cleanup.  
- Tokenization using NLTK.  
- Feature extraction with **TF-IDF** (50,000 features, unigrams + bigrams).  

### 3. Model Selection & Training  
- **Train/Test split**: 80/20 → 16,000 train / 4,000 test.  
- Models implemented:  
  - Logistic Regression (`saga`, balanced classes)  
  - SGDClassifier (`log_loss`, online learning style)


  **Logistic Regression**


  ![Logistic Regression](https://github.com/Mathivathani-G/kaiburr-task5-Data-Science/blob/main/Logistic%20Regression.png)


  **Confusion Matrix for Logistic Regression**

  ![Confusion matrix log reg](https://github.com/Mathivathani-G/kaiburr-task5-Data-Science/blob/main/Confusion%20matrix%20Logistic%20Regression.png)

  **SGDC Classifier**

  ![SGDC Classifier](https://github.com/Mathivathani-G/kaiburr-task5-Data-Science/blob/main/SGDC%20Classifier.png)

  **Confusion Matrix for SGDC CLassifier**

  ![confusion matrix for sgdc classf](https://github.com/Mathivathani-G/kaiburr-task5-Data-Science/blob/main/Confusion%20matrix%20SGDC%20Classifier.png)

### 4. Model Evaluation  
- **Logistic Regression** performed best:  
  - Accuracy: **86.18%**  
  - Macro F1 Score: **0.863**  
  - Class-wise performance:  

| Class | Precision | Recall | F1-Score |
|-------|-----------|--------|----------|
| 0: Credit Reporting | 0.85 | 0.86 | 0.85 |
| 1: Debt Collection | 0.83 | 0.81 | 0.82 |
| 2: Consumer Loan | 0.83 | 0.86 | 0.84 |
| 3: Mortgage | 0.95 | 0.91 | 0.93 |

- Confusion matrices were plotted for visual error analysis.  

### 5. Predictions  
The trained model was tested on custom examples:  
- **Credit reporting complaint** → correctly classified as 0.  
- **Debt collection calls** → correctly classified as 1.  
- **Personal loan disbursement issue** → correctly classified as 2.  
- **Mortgage payment issue** → correctly classified as 3.  

---

## How to Run  

1. Clone this repo:  
   ```bash
   git clone https://github.com/<your-username>/task5-text-classification.git
   cd task5-text-classification
