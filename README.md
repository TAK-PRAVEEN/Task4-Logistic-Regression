# Logistic Regression
---

**1. How does logistic regression differ from linear regression?**

1. How does logistic regression differ from linear regression?
The main difference is their output and purpose.
- Linear Regression predicts a continuous numerical value (like a house price or temperature). It fits a straight line to the data.
- Logistic Regression predicts the probability that an input belongs to a specific category (like `spam` vs. `not spam`). It's used for classification, not predicting a value. Its output is an S-shaped curve representing a probability from 0 to 1.

---

**2. What is the sigmoid function?**

The sigmoid function is a mathematical function that takes any real-valued number and maps it to a value between 0 and 1. It has a characteristic "S" shape.

Its formula is: $\sigma(z) = \frac{1}{1+e^{-z}}$

In logistic regression, it transforms the output of the linear part of the model into a probability. For example, if the sigmoid function outputs 0.85, it means there is an 85% probability of the instance belonging to the positive class.

---

**3. What is precision vs. recall?**

Precision and recall are metrics used to evaluate how good a classification model is. They provide more insight than simple accuracy, especially when classes are imbalanced.
- Precision: Answers the question: "Of all the times the model predicted positive, how many were actually correct?" It focuses on minimizing False Positives.
  + Example: High precision in a spam filter means that when it flags an email as spam, it's very likely to be spam (so important emails aren't lost).
- Recall (or Sensitivity): Answers the question: "Of all the actual positive cases, how many did the model correctly identify?" It focuses on minimizing False Negatives.
  + Example: High recall in a medical test means it correctly identifies most of the people who actually have the disease.

There is often a trade-off between them; improving one can lower the other.

---

**4. What is the ROC-AUC curve?**

The ROC-AUC curve is a tool for evaluating a classifier's performance.
- ROC Curve (Receiver Operating Characteristic): This is a graph that plots the True Positive Rate (Recall) against the False Positive Rate at various threshold settings. An ideal model's curve would hug the top-left corner, indicating high recall and a low false positive rate. A model with no skill is represented by a diagonal line.
- AUC (Area Under the Curve): This is a single number that measures the entire area under the ROC curve. It summarizes the model's ability to distinguish between the positive and negative classes.
  + AUC = 1.0: Perfect classifier.
  +AUC = 0.5: A useless classifier (same as random guessing).

---

**5. What is the confusion matrix?**

A confusion matrix is a table that summarizes the performance of a classification model by comparing its predictions to the actual outcomes. For a binary (two-class) problem, it looks like this:
 - True Positives (TP): Correctly predicted as positive.
 - True Negatives (TN): Correctly predicted as negative.
 - False Positives (FP): Incorrectly predicted as positive (a "false alarm").
 - False Negatives (FN): Incorrectly predicted as negative (a "miss").

This matrix is the foundation for calculating metrics like precision, recall, and accuracy.

---

**6. What happens if classes are imbalanced?**

Class imbalance occurs when one class is far more frequent than another (e.g., 99% non-fraud vs. 1% fraud transactions). This causes significant problems:
- Misleading Accuracy: A model can achieve high accuracy (e.g., 99%) by simply always predicting the majority class, making it useless for identifying the rare minority class.
- Model Bias: The model becomes biased towards the majority class and performs poorly in identifying the minority class (i.e., it will have very low recall).

When dealing with imbalanced classes, you should rely on metrics like the Precision-Recall Curve, F1-Score, or ROC-AUC instead of accuracy.

---

**7. How do you choose the threshold?**

The default probability threshold for classification is 0.5, but the optimal choice depends on your goal. You should choose a threshold based on whether a false positive or a false negative is more costly.
- To increase Recall (catch more positives, even at the risk of more false alarms): Lower the threshold (e.g., to 0.3). Use this for problems like medical screening.
- To increase Precision (be more certain about positive predictions): Raise the threshold (e.g., to 0.8). Use this for problems like spam filtering.

You can use a Precision-Recall curve to visualize the trade-off and pick a threshold that gives you the right balance for your needs.

---

**8. Can logistic regression be used for multi-class problems?**

Yes. While standard logistic regression is for binary (two-class) problems, it can be extended to handle multiple classes using two common techniques:
1. One-vs-Rest (OvR): This trains a separate binary classifier for each class (e.g., for classes A, B, and C, it trains one model for "A vs. not A," another for "B vs. not B," and a third for "C vs. not C"). To classify a new instance, it uses the model that returns the highest probability.
2. Multinomial Logistic Regression (Softmax Regression): This is a direct modification of logistic regression that handles all classes in a single model. It uses the softmax function instead of the sigmoid function to output a probability for each of the classes, ensuring that all probabilities sum to 1.

---
