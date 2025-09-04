# Automated Quality Inspection for Metal Casting Using an Optimized CNN

This project showcases a comprehensive exploration of machine learning techniques to automate quality inspection for metal casting products. By testing various architectures and optimization strategies, a final Convolutional Neural Network (CNN) was developed that achieved outstanding accuracy in classifying industrial images as 'defective' or 'ok'.

**Author:** Amardip Banerjee  
**Institution:** Indian Institute of Technology, Kharagpur  
**Program:** Dual Degree (B.Tech + M.Tech), Manufacturing Science and Industrial Engineering (2021-2026)

---

### **Abstract**

Manual quality control in manufacturing is a significant bottleneck, being both time-consuming and prone to human error. This project tackles this challenge by developing and comparing a suite of data-driven, automated visual inspection systems. The process involved establishing baselines with Logistic Regression, developing custom CNNs, and exploring advanced optimization techniques like Hyperband and GridSearchCV. The best-performing model from this exploration, a fine-tuned CNN, achieved a remarkable **test accuracy of 99.16%** on a real-world dataset of 7,348 industrial images, demonstrating a highly reliable and efficient solution for industrial quality control.

---

### **1. The Industrial Challenge: Inefficiency in Quality Control**

Casting is a core manufacturing process that produces countless metal components. However, it is susceptible to various defects like blowholes, burrs, and shrinkage. Traditionally, quality control (QC) relies on human inspectors, which has several drawbacks:

- **High Cost:** Manual inspection is labor-intensive and expensive.
- **Inconsistency:** Subjective judgment and fatigue lead to unreliable results.
- **Time-Consuming:** The process is slow, creating a bottleneck in the production line.
- **Financial Risk:** A single missed defect can lead to product failure and significant financial loss.

This project's objective was to create a fast, accurate, and automated system to overcome these issues.

---

### **2. Dataset**

The project utilizes the "Casting Product Image Data for Quality Inspection" dataset from Kaggle.

- **Dataset Link:** [Real-life Industrial Dataset of Casting Product](https://www.kaggle.com/datasets/ravirajsinh45/real-life-industrial-dataset-of-casting-product)
- **Content:** The dataset consists of 64x64 pixel RGB images of submersible pump impellers.
- **Volume:**
  - **Training Set:** 6,633 images (`def_front` and `ok_front`)
  - **Test Set:** 715 images

---

### **3. Methodology: An Iterative Approach to Model Optimization**

To achieve the highest possible accuracy, this project followed an iterative process, building and refining models with increasing complexity and employing various optimization strategies.

1.  **Baseline Model (Logistic Regression):** A simple Logistic Regression model was first implemented to establish a performance baseline and demonstrate the need for a more sophisticated approach for image data.

2.  **Custom CNN Architecture:** A custom Convolutional Neural Network was designed and trained. This model immediately showed a massive improvement over the baseline, establishing the power of CNNs for this task. This architecture forms the basis of our best-performing model.

3.  **Hyperparameter Tuning Exploration:** To ensure the model architecture was robust and optimized, a phase of hyperparameter tuning was conducted. Different strategies were explored:
    - **GridSearchCV:** This classic, exhaustive search method was considered for its thoroughness in testing all possible combinations of a given set of parameters.
    - **Hyperband (KerasTuner):** This modern, more efficient algorithm was implemented to intelligently search a wide range of hyperparameters (filters, dense units, learning rate, etc.), quickly eliminating poor performers and focusing on the most promising model configurations.

This comprehensive exploration allowed for the identification of a highly effective final model.

---

### **4. Performance Analysis & Best Result**

Across all the tested methodologies, GridSearchCV gave us the best CNN architecture that has been implemented in the `Metal-Casting-CNN.ipynb` notebook.

#### **Final Model Performance**

The best-performing model demonstrated exceptional accuracy, correctly identifying **709 out of 715** test images. Hyperband may have rejected this model due to lower scores in early epochs.

- **Test Accuracy:** **99.16%**

**Classification Report:**

| Class       | Precision |  Recall  | F1-Score | Support |
| :---------- | :-------: | :------: | :------: | :-----: |
| Defective   |   1.00    |   0.99   |   0.99   |   453   |
| OK          |   0.98    |   1.00   |   0.99   |   262   |
| **Overall** | **0.99**  | **0.99** | **0.99** | **715** |

**Confusion Matrix Analysis:**

The model's performance was nearly flawless, with only **6 misclassifications** out of 715:

- **False Negatives (4):** The model incorrectly classified only 4 "defective" parts as "OK". This extremely low rate is critical for industrial quality assurance.
- **False Positives (2):** The model incorrectly classified only 2 "OK" parts as "defective".

---

### **5. Conclusion**

This project successfully demonstrates that a well-structured CNN can achieve state-of-the-art results for automating industrial quality control. The final model's accuracy of **99.16%** confirms that this technology can drastically reduce inspection time, eliminate human error, and prevent the financial losses associated with shipping defective products. The iterative process of testing multiple models and optimization strategies was key to identifying this high-performing solution.
