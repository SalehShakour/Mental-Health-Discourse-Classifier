# Mental Health Discourse Classifier
### DistilBERT fine-tuned on Reddit mental health discussions

## 📌 Project Overview
Trained a lightweight NLP classifier to categorize Reddit posts about mental health conditions using HuggingFace's **DistilBERT**. The final model was optimized using Optuna, achieving **76.8% accuracy** on the test set—an **8.1% improvement** over the baseline.

## 📂 Dataset
- **Source:** [Reddit Mental Health Dataset (Kaggle)](https://www.kaggle.com/datasets/neelghoshal/reddit-mental-health-data)
- **Content:** 10k+ posts labeled by condition
- **Categories:**
  - Depression
  - Anxiety
  - Stress
  - Bipolar Disorder
  - PTSD

## ⚙️ Tuning & Performance
Hyperparameter tuning with Optuna was performed to improve upon a baseline model, yielding substantial gains in accuracy, efficiency, and resource utilization.

### Key Improvements Summary
- **Accuracy Boost:** Validation accuracy increased from **73.3% to 81.2%**, and test set accuracy rose from **68.7% to 76.8%**.
- **Training Efficiency:** Model throughput increased from **180 to 320 samples/sec**, reducing total training time by **28%**.
- **Resource Optimization:** GPU memory usage was reduced by **35%** by optimizing batch and sequence sizes.

### Performance Metrics: Baseline vs. Tuned

| Metric              | Baseline Model | Tuned Model (Final) | Improvement |
| :------------------ | :------------: | :-----------------: | :---------: |
| **Validation Acc.** |     73.3%      |      **81.2%** |   +7.9%     |
| **Test Accuracy** |     68.7%      |      **76.8%** |   +8.1%     |


### Hyperparameter Comparison

| Parameter         | Baseline             | Optimized (Tuned)                | Impact                               |
| :---------------- | :------------------- | :------------------------------- | :----------------------------------- |
| **Learning Rate** | $2 \times 10^{-5}$   | **$4.5 \times 10^{-5}$** | Key driver for accuracy gain         |
| **Batch Size** | 8                    | **32** | Faster training, stable gradients    |
| **Sequence Length** | 512                  | **256** | Reduced memory usage by 35%          |
| **Epochs** | 3                    | **10** | Allowed model to fully converge      |
| **Weight Decay** | 0.0                  | **0.1** | Added regularization, prevents overfitting |

### Training Dynamics

-   **Baseline Model:** Showed an early plateau around epoch 3, with validation loss getting stuck at 0.78.
-   **Optimized Model:** Demonstrated continuous improvement through 9 epochs, achieving a lower final validation loss of 0.67.
